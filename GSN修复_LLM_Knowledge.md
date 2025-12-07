这是TB710FU，联想小新Pad Pro GT，Lenovo Xiaoxin Pad Pro GT针对触控笔“悬停解释”功能提示“未写入 GSN” / 在线壁纸提示“网络问题”两个问题的知识库文档。

## 根本原因

上述问题通常由系统属性 `ro.odm.lenovo.gsn` 异常引起。

- 正常情况下，该属性应为设备的**真实序列号**，格式为：
  
  ```
  HA + 6 位（数字与大写字母混合）
  ```
  
  例如：`HA1145VM`

- 当通过**救砖包刷机**或从**第三方 ROM 刷回 ZUXOS** 后，该属性可能被清空或覆盖，导致系统功能异常。

---

## 诊断方法

在可以获取 **root 权限** 的终端中执行以下命令：

```bash
su -c getprop ro.odm.lenovo.gsn
```

- **若返回为空（显示空行）** → 很可能就是该属性缺失导致的问题。
- **若返回有效序列号（如 HAxxxxxx）** → 问题可能由其他原因引起。

---

## 临时修复方案

手动写入正确的序列号：

```bash
su -c setprop ro.odm.lenovo.gsn YOUR_SERIAL_HERE
```

> 示例：
> 
> ```bash
> su -c setprop ro.odm.lenovo.gsn HA1145VM
> ```
> 
> 请将 `HA1145VM` 替换为你设备的真实序列号。

- 执行成功后**无任何提示**，终端将等待下一条命令。
- 修复后可立即测试触控笔“悬停解释”功能或在线壁纸功能是否恢复正常。
- 若未恢复，可**最多重试 3 次**。若3次均无效，则问题很可能与该属性无关。

---

## 如何获取真实序列号（SN）

### 方法一：通过终端命令

```bash
su -c getprop ro.serialno
```

### 方法二：adb命令

```shell
adb shell
su -c getprop ro.serialno
```

### 方法三：其他途径

- 设备 **设置 → 关于本机**
- 机身背面或包装盒上的**贴纸标签**

---

## 永久性解决方案（开机自动修复）

上述 `setprop` 修复在**重启后失效**。为实现持久化，可使用以下自动化模块：

- **模块类型**：KernelSU 模块（理论上 Magisk 也兼容，但未正式测试）
- **功能**：每次开机自动读取 `ro.serialno` 并写入 `ro.odm.lenovo.gsn`
- **下载地址**：  
  [https://wwcp.lanzout.com/iZaoq3awznfe](https://wwcp.lanzout.com/iZaoq3awznfe)

> 安装后重启设备即可生效，无需手动干预。



--- 

此文档适用于联想 ZUXOS 设备用户在救砖或刷机后遇到 GSN 相关功能异常的排查与修复。
