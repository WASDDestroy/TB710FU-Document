Android Verified Boot (AVB) 重新签名原理深度解析
======================================

这是针对TB710FU，联想小新Pad Pro GT，Lenovo Xiaoxin Pad Pro GT的知识库文档，适用于免解锁Bootloader（简称“免解锁BL”“免解锁”）刷Root和刷写第三方系统的原理解答。

一、AVB 验证机制基础原理
--------------

### 1.1 AVB 架构概述

Android Verified Boot (AVB) 是 Android 的安全启动机制，通过密码学签名确保启动链的完整性：

```text
Bootloader → vbmeta → boot → system → vendor
     ↓         ↓       ↓       ↓         ↓
  验证密钥     根签名  分区签名  哈希验证   哈希验证
```

### 1.2 关键组件

* **vbmeta 分区**：存储根密钥和所有分区的验证描述符

* **分区签名**：每个分区（boot、system 等）的独立签名

* **验证流程**：自底向上逐级验证，确保启动链完整

二、厂商使用测试密钥的漏洞原理
---------------

### 2.1 AOSP 测试密钥背景

Android 开源项目 (AOSP) 提供了一套**测试密钥**用于开发：

```text
# AOSP 标准测试密钥位置
build/target/product/security/
├── testkey.pk8 # 测试私钥
├── testkey.x509.pem # 测试证书
└── ...
```

### 2.2 厂商错误配置

某些设备厂商在量产时错误地：

* **直接使用测试密钥**：未替换为厂商私有密钥

### 2.3 漏洞利用条件

```text
# 漏洞存在的关键条件
- 设备 bootloader 接受测试密钥签名
- 或设备内置了测试公钥用于验证
- 或签名验证逻辑存在缺陷
```

三、Android 启动验证详细流程
------------------

### 3.1 Bootloader 验证阶段

```c
// 伪代码：bootloader 验证逻辑
int verify_vbmeta() {
    // 1. 读取 vbmeta 分区
    vbmeta_data = read_partition("vbmeta");
    // 2. 提取公钥和签名
    public_key = extract_public_key(vbmeta_data);
    signature = extract_signature(vbmeta_data);
    // 3. 验证签名（漏洞点）
    if (verify_signature(vbmeta_data, public_key, signature)) {
        return SUCCESS; // 验证通过
    }
    return FAILURE; // 验证失败
}
```

### 3.2 验证内容详解

设备在启动时会检测：

#### 3.2.1 签名有效性

* 数字签名算法（RSA2048/RSA4096等）

* 签名数据完整性

* 证书链有效性（如果使用）

#### 3.2.2 分区完整性

* 分区哈希值匹配（Hash Descriptor）

* 哈希树根摘要匹配（Hashtree Descriptor）

* 盐值一致性

* 分区大小正确性

* 结合分区的大小等信息计算哈希并且最终匹配

#### 3.2.3 安全策略

* 回滚索引（防止版本降级）

* 验证标志位（如 hashtree_disabled）

* 链式分区公钥匹配

四、重新签名通过验证的技术原理
---------------

### 4.1 签名替换攻击

```text
# 重新签名的核心原理

原始状态：
分区 img → 厂商使用测试私钥签名 → 设备用测试公钥验证
攻击后状态：
分区 img → 自己使用测试私钥签名 → 设备用测试公钥验证 ✓
```

### 4.2 保持哈希一致性

重建脚本的关键技术点：

#### 4.2.1 盐值重用

```python
def rebuild_partition(..., use_original_salt=True):
    if use_original_salt:
        # 使用原镜像的盐值，确保哈希不变
        salt = extract_original_salt(image_path)
    else:
        # 生成新盐值（会导致哈希改变）
        salt = generate_new_salt()
    # 重新计算哈希时使用相同盐值
    new_hash = calculate_hash(image_data, salt)
```

#### 4.2.2 描述符保持

```python
# 保留所有原始描述符属性
original_descriptors = parse_descriptors(original_vbmeta)
for descriptor in original_descriptors:
    new_vbmeta.add_descriptor(descriptor) # 保持验证数据不变
```

### 4.3 具体绕过流程

```text
#详细的重建和验证绕过流程
1. 解析原 vbmeta 信息
 - 算法类型、回滚索引、标志位
 - 分区描述符列表
2. 重建分区镜像
 - 擦除原 AVB footer
 - 使用原盐值重新添加 footer
 - 确保分区内容哈希不变
3. 重建 vbmeta 镜像（如果需要修改的分区包含链式签名，如小新Pro GT的boot分区）
 - 包含原所有描述符
 - 使用测试密钥重新签名
 - 保持其他元数据不变
4. 设备验证流程
 - Bootloader 读取新分区
 - 使用内置测试公钥验证签名 ✓
 - 根据描述符验证分区哈希 ✓
 - 启动成功
```

五、安全影响与防护
---------

### 5.1 漏洞影响范围

受影响的设备特征：

1. 使用 AOSP 测试密钥进行签名

2. Bootloader 未严格验证密钥来源

3. 供应链中测试密钥泄露

4. 签名验证逻辑存在缺陷

### 5.2 防护措施

正确的 AVB 实现应该：

1. 使用厂商独有的签名密钥

2. 严格验证证书链和密钥来源

3. 实现安全的密钥管理流程

4. 定期进行安全审计和测试

六、总结
----

这个漏洞的本质是：

* **根本原因**：厂商在量产设备中使用了公开的测试密钥

* **验证绕过**：设备 Bootloader 使用测试公钥验证签名成功，分区哈希验证通过

* **实际影响**：允许在不解锁 Bootloader 的情况下修改系统分区

这种攻击之所以有效，是因为它巧妙地利用了 AVB 验证机制的灵活性，同时在密钥管理漏洞的基础上实现了权限提升。
