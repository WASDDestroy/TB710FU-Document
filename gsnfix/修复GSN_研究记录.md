ZUI壁纸签名逻辑逆向以及GSN为空的后果
===========

🧑‍💻 User
----------

```java
package com.zui.cloud.desktop;

import android.content.Context;importandroid.os.Build;import android.util.Log;import com.zui.cloud.network.n;importcom.zui.cloud.network.r;import com.zui.cloud.util.XUIConfig;importjava.util.HashMap;import org.json.JSONObject;

/* loaded from: classes.dex */public class a{private static volatile a a = null;private static Context b = null;privatestatic final String d = "a";private String c = null;

/* renamed from: com.zui.cloud.desktop.a$a,reason: collision with other inner class name */private static class C0010a{public static String a() {StringBuilder sbAppend;String str;if(com.zui.cloud.util.f.f()) {sbAppend = new StringBuilder().append(XUIConfig.getInstance(a.b).getDomain());str= "/api/v7/wallpaper/pad-gallery";} else {sbAppend = newStringBuilder().append(XUIConfig.getInstance(a.b).getDomain());str ="/api/v7/wallpaper/phone-gallery";}return sbAppend.append(str).toString();}

public static String b() {StringBuildersbAppend;String str;if (com.zui.cloud.util.f.f()) {sbAppend = newStringBuilder().append(XUIConfig.getInstance(a.b).getDomain());str ="/api/v7/wallpaper/pad-history";} else {sbAppend = new StringBuilder().append(XUIConfig.getInstance(a.b).getDomain());str= "/api/v7/wallpaper/phone-history";}returnsbAppend.append(str).toString();}

public static String c() {StringBuildersbAppend;String str;if (com.zui.cloud.util.f.f()) {sbAppend = newStringBuilder().append(XUIConfig.getInstance(a.b).getDomain());str ="/api/v7/wallpaper/pad-history-num";} else {sbAppend = new StringBuilder().append(XUIConfig.getInstance(a.b).getDomain());str= "/api/v7/wallpaper/phone-history-num";}returnsbAppend.append(str).toString();}

public static String d() {returnXUIConfig.getInstance(a.b).getDomain() +"/api/v7/wallpaper/pger-history";}

public static String e() {StringBuildersbAppend;String str;if (com.zui.cloud.util.f.f()) {sbAppend = newStringBuilder().append(XUIConfig.getInstance(a.b).getDomain());str ="/api/v1/wallpaper/legion-pad-history";} else {sbAppend = new StringBuilder().append(XUIConfig.getInstance(a.b).getDomain());str= "/api/v1/wallpaper/legion-phone-history";}returnsbAppend.append(str).toString();}

public static String f() {returnXUIConfig.getInstance(a.b).getDomain() +"/api/v7/wallpaper/pger-list";}

public static String g() {returnXUIConfig.getInstance(a.b).getDomain() +"/api/v7/wallpaper/pger-single-list";}

public static String h() {returnXUIConfig.getInstance(a.b).getDomain() + "/api/v2/aiwallpaper/list";}

public static String i() {returnXUIConfig.getInstance(a.b).getDomain() +"/api/v2/aiwallpaper/switch";}}

private a(Context context) {b = context;}

public static a a(Context context) {if (a ==null) {synchronized (a.class) {if (a == null) {Log.d(d, "instance == null" + Build.VERSION.SDK_INT);a = new a(context);}Log.d(d, "sdk " +Build.VERSION.SDK_INT);}}return a;}

private n<?> b(int i, int i2, int i3,int i4, int i5, DesktopCloudListener desktopCloudListener) {HashMap map = newHashMap();map.put("color",Integer.toString(i));map.put("complex",Integer.toString(i2));map.put("active",Integer.toString(i3));map.put("aid",Integer.toString(i4));map.put("rebuildid",Integer.toString(i5));map.put("channel","default");map.put("source", com.zui.cloud.util.f.f() ?"1" : "0");com.zui.cloud.util.f.a(b, map, this.c);returnnew d(this, 0, C0010a.i() + "?" + com.zui.cloud.util.f.a(map) +com.zui.cloud.util.f.a(b, this.c), null, e(desktopCloudListener),f(desktopCloudListener));}

private n<?> b(String str,DesktopCloudListener desktopCloudListener) {HashMap map = newHashMap();map.put("uptime", str);map.put("channel","default");com.zui.cloud.util.f.a(b, map, this.c);return new e(this,0, C0010a.a() + "?" + com.zui.cloud.util.f.a(map) +com.zui.cloud.util.f.a(b, this.c), null, e(desktopCloudListener),f(desktopCloudListener));}

private n<?> b(String str, String str2,int i, DesktopCloudListener desktopCloudListener) {HashMap map = newHashMap();map.put("channel","default");map.put("source", com.zui.cloud.util.f.f() ?"1" : "0");map.put("pger_id",str);map.put("fromid", str2);map.put("pn",Integer.toString(i));com.zui.cloud.util.f.a(b, map, this.c);return new j(this,0, C0010a.g() + "?" + com.zui.cloud.util.f.a(map) + com.zui.cloud.util.f.a(b,this.c), null, e(desktopCloudListener), f(desktopCloudListener));}

private n<?> c(DesktopCloudListenerdesktopCloudListener) {HashMap map = new HashMap();map.put("channel","default");map.put("source", com.zui.cloud.util.f.f() ?"1" : "0");com.zui.cloud.util.f.a(b, map, this.c);returnnew i(this, 0, C0010a.f() + "?" + com.zui.cloud.util.f.a(map) +com.zui.cloud.util.f.a(b, this.c), null, e(desktopCloudListener),f(desktopCloudListener));}

private n<?> d(DesktopCloudListenerdesktopCloudListener) {HashMap map = new HashMap();map.put("channel","default");com.zui.cloud.util.f.a(b, map, this.c);return new c(this,0, C0010a.c() + "?" + com.zui.cloud.util.f.a(map) +com.zui.cloud.util.f.a(b, this.c), null, e(desktopCloudListener),f(desktopCloudListener));}

private n<?> e(String str, int i,DesktopCloudListener desktopCloudListener) {HashMap map = newHashMap();map.put("fromid", str);map.put("pn",Integer.toString(i));map.put("channel","default");map.put("source", com.zui.cloud.util.f.f() ?"1" : "0");com.zui.cloud.util.f.a(b, map, this.c);returnnew b(this, 0, C0010a.h() + "?" + com.zui.cloud.util.f.a(map) +com.zui.cloud.util.f.a(b, this.c), null, e(desktopCloudListener),f(desktopCloudListener));}

private r.b<JSONObject>e(DesktopCloudListener desktopCloudListener) {return newcom.zui.cloud.base.c(desktopCloudListener);}

private n<?> f(String str, int i,DesktopCloudListener desktopCloudListener) {HashMap map = newHashMap();map.put("fromid", str);map.put("pn",Integer.toString(i));map.put("channel","default");map.put("resolution",com.zui.cloud.util.f.b(b));com.zui.cloud.util.f.a(b, map, this.c);return newf(this, 0, C0010a.b() + "?" + com.zui.cloud.util.f.a(map) +com.zui.cloud.util.f.a(b, this.c), null, e(desktopCloudListener),f(desktopCloudListener));}

private r.a f(DesktopCloudListenerdesktopCloudListener) {return new com.zui.cloud.base.b(desktopCloudListener);}

private n<?> g(String str, int i,DesktopCloudListener desktopCloudListener) {HashMap map = newHashMap();map.put("channel","default");map.put("source", com.zui.cloud.util.f.f() ?"1" : "0");map.put("fromid",str);map.put("pn", Integer.toString(i));com.zui.cloud.util.f.a(b,map, this.c);return new g(this, 0, C0010a.d() + "?" +com.zui.cloud.util.f.a(map) + com.zui.cloud.util.f.a(b, this.c), null,e(desktopCloudListener), f(desktopCloudListener));}

private n<?> h(String str, int i,DesktopCloudListener desktopCloudListener) {HashMap map = newHashMap();map.put("channel","default");map.put("source", com.zui.cloud.util.f.f() ?"1" : "0");map.put("fromid",str);map.put("pn", Integer.toString(i));com.zui.cloud.util.f.a(b,map, this.c);return new h(this, 0, C0010a.e() + "?" +com.zui.cloud.util.f.a(map) + com.zui.cloud.util.f.a(b, this.c), null,e(desktopCloudListener), f(desktopCloudListener));}

public void a(int i, int i2, int i3, int i4,int i5, DesktopCloudListener desktopCloudListener) {if(XUIConfig.getInstance(b).checkDomain()) {com.zui.cloud.a.a(b(i, i2, i3, i4,i5, desktopCloudListener), this);} else if (desktopCloudListener != null) {desktopCloudListener.onError(6004,"the server domain is empty");}}

public void a(DesktopCloudListenerdesktopCloudListener) {if (XUIConfig.getInstance(b).checkDomain()){com.zui.cloud.a.a(d(desktopCloudListener), this);} else if(desktopCloudListener != null) {desktopCloudListener.onError(6004, "theserver domain is empty");}}

public void a(String str) {this.c = str;}

public void a(String str, int i,DesktopCloudListener desktopCloudListener) {if(XUIConfig.getInstance(b).checkDomain()) {com.zui.cloud.a.a(f(str, i,desktopCloudListener), this);} else if (desktopCloudListener != null){desktopCloudListener.onError(6004, "the server domain is empty");}}

public void a(String str,DesktopCloudListener desktopCloudListener) {if(XUIConfig.getInstance(b).checkDomain()) {com.zui.cloud.a.a(b(str,desktopCloudListener), this);} else if (desktopCloudListener != null){desktopCloudListener.onError(6004, "the server domain is empty");}}

public void a(String str, String str2, int i,DesktopCloudListener desktopCloudListener) {if(XUIConfig.getInstance(b).checkDomain()) {com.zui.cloud.a.a(b(str, str2, i,desktopCloudListener), this);} else if (desktopCloudListener != null){desktopCloudListener.onError(6004, "the server domain is empty");}}

public void b(DesktopCloudListenerdesktopCloudListener) {if (XUIConfig.getInstance(b).checkDomain()){com.zui.cloud.a.a(c(desktopCloudListener), this);} else if(desktopCloudListener != null) {desktopCloudListener.onError(6004, "theserver domain is empty");}}

public void b(String str, int i,DesktopCloudListener desktopCloudListener) {if(XUIConfig.getInstance(b).checkDomain()) {com.zui.cloud.a.a(g(str, i,desktopCloudListener), this);} else if (desktopCloudListener != null){desktopCloudListener.onError(6004, "the server domain is empty");}}

public void c(String str, int i,DesktopCloudListener desktopCloudListener) {if(XUIConfig.getInstance(b).checkDomain()) {com.zui.cloud.a.a(h(str, i,desktopCloudListener), this);} else if (desktopCloudListener != null){desktopCloudListener.onError(6004, "the server domain is empty");}}

public void d(String str, int i,DesktopCloudListener desktopCloudListener) {if(XUIConfig.getInstance(b).checkDomain()) {com.zui.cloud.a.a(e(str, i,desktopCloudListener), this);} else if (desktopCloudListener != null){desktopCloudListener.onError(6004, "the server domain is empty");}}}
```



需要完整的还原逻辑，一步一步逆向出SIGN的签名逻辑，说出现在还缺少的信息，签名出现在下面数据包：

```log
RequestGEThttps://apizui.lenovomm.com/api/v7/wallpaper/pger-history?deviceId2=%2C&clientId=default&os=15&channel=default&source=1&versionName=17.0.1.0440&fromid=0&versionCode=17010440&rom=TB710FU_CN_OPEN_USER_QSM8650_V_ZUI_17.0.04.297_ST_250827&sdkVersion=1.0.0.1432&model=TB710FU&packageName=com.zui.wallpapersetting&pn=3&timestamp=2025-11-12+22%3A27%3A48&sign=nxH4MarIA%2BdMFDZxXcAv9IQSL2OyoYcDCK0%2F0nx4JhBT1esJ6pbZdTJ2wMV4wijztnkZyEzgNgZYUcRymuZ%2BnZlWCd9hgAisYBtwUcTRDC%2F%2BohGCoV%2Ba60kX1f7Za59xdWk%2FBUBBkpCEyI8HNuXe9yaJtR9GtIoiZI0OLZJiY3g%3DHTTP/1.1Accept: application/json;Accept-Encoding: gzip,deflateUser-Agent:Dalvik/2.1.0 (Linux; U; Android 15; TB710FU Build/AQ3A.250129.001)Host:apizui.lenovomm.comConnection: Keep-Alive
```

```log
ResponseHTTP/1.1 200Server:Tengine/2.3.3Date: Wed, 12 Nov 2025 14:27:48 GMTContent-Type:application/jsonConnection: keep-aliveX-Frame-Options:SAMEORIGINX-Frame-Options: SAMEORIGINContent-Encoding: gzipContent-Length: 340

{"status":0,"errorMessage":"success","timestamp":"2025-11-12T22:27:48+08:00","data":{"wallpaper":[{"sid":"ZUI1628705841","title":"\u897f\u6e56\u591c\u8272","img":"https://cdnzui.lenovomm.cn/images/origin/f7/f7cc54f4bdb814a0cdd2abb5369c1647","thumb":"https://cdnzui.lenovomm.cn/images/thumb/720x450/f7/f7cc54f4bdb814a0cdd2abb5369c1647"},{"sid":"ZUI1628705804","title":"\u5915\u9633\u7f8e","img":"https://cdnzui.lenovomm.cn/images/origin/7f/7f4adf293db7c4a41f51c6ce6c66ad6c","thumb":"https://cdnzui.lenovomm.cn/images/thumb/720x450/7f/7f4adf293db7c4a41f51c6ce6c66ad6c"},{"sid":"ZUI1628705764","title":"\u542f\u822a","img":"https://cdnzui.lenovomm.cn/images/origin/4e/4e23613f692ee434148864d478dc9b36","thumb":"https://cdnzui.lenovomm.cn/images/thumb/720x450/4e/4e23613f692ee434148864d478dc9b36"}],"nextid":"1805"}}
```

🤖 Assistant

------------

根据提供的代码片段和数据包信息，我将逐步还原SIGN签名逻辑，并指出目前缺少的关键信息。签名逻辑主要隐藏在com.zui.cloud.util.f类中，但代码中没有提供该类的具体实现，因此部分逻辑需要基于代码结构和常见API签名实践进行推断。

### 签名逻辑还原步骤

从代码中可以看出，签名生成涉及多个步骤，主要集中在a类（可能是DesktopCloudManager或类似名称）的方法中。以下是签名生成的整体流程：

1. 参数收集与初始化：
   
   - 在具体请求方法（如g(String str, int i,DesktopCloudListener desktopCloudListener)对应数据包中的/api/v7/wallpaper/pger-history请求）中，首先创建一个HashMap对象，并添加基本参数（如channel、source、fromid、pn等）。
   
   - 然后调用com.zui.cloud.util.f.a(b, map, this.c)方法。这里：
     
     - b是Android Context（应用上下文）。
     
     - map是参数映射。
     
     - this.c是一个字符串（通过a(String str)方法设置），可能是一个动态令牌或密钥。
   
   - 添加公共参数：com.zui.cloud.util.f.a(b, map, this.c)方法会向map中添加设备相关参数和其他公共参数。从数据包中看，这些参数包括:
     
     - deviceId2：设备ID（数据包中为%2C，可能是空值或默认值）。
     
     - clientId：客户端ID（如default）。
     
     - os：操作系统版本（如15）。
     
     - versionName：应用版本名称（如17.0.1.0440）。
     
     - versionCode：应用版本代码（如17010440）。
     
     - rom：设备ROM版本（如TB710FU_CN_OPEN_USER_QSM8650_V_ZUI_17.0.04.297_ST_250827）。
     
     - sdkVersion：SDK版本（如1.0.0.1432）。
     
     - model：设备型号（如TB710FU）。
     
     - packageName：应用包名（如com.zui.wallpapersetting）。
     
     - timestamp：时间戳（格式为yyyy-MM-dd HH:mm:ss，在URL中编码为yyyy-MM-dd+HH%3Amm%3Ass）。时间戳可能在这一步生成并添加，格式为2025-11-12 22:27:48（数据包中的值）。

2. 生成查询字符串：
   
   - 调用com.zui.cloud.util.f.a(map)方法，将map转换为查询字符串。该方法可能对参数按键进行排序（常见做法是按字母顺序排序），然后拼接成key1=value1&key2=value2的形式。
   
   - 参数值可能使用URL编码（如数据包中的timestamp被编码为2025-11-12+22%3A27%3A48）。
   
   - 从数据包推断，排序后的参数顺序可能为：channel, clientId, deviceId2, fromid, model, os, packageName, pn, rom, sdkVersion, source, timestamp, versionCode, versionName（但不确认是否严格排序）。

3. 生成签名：
   
   - 调用com.zui.cloud.util.f.a(b, this.c)方法，生成签名字符串。该方法可能基于以下输入计算签名：
   
   - 查询字符串（从步骤3生成的字符串）。
   
   - 密钥或令牌（this.c的值）。
   
   - 可能还包括其他数据（如URL路径，但代码中未直接传递路径）。
   
   - 签名算法未知，但从签名长度推断：
   
   - 数据包中的签名值（Base64编码后172字符）解码为128字节（1024位），可能使用RSA-1024签名算法或类似非对称加密算法。但客户羰通常不持有私钥，因此也可能是自定义对称加密算法或HMAC变体。
   
   - 签名结果经过Base64编码和URL编码后，作为sign参数附加到查询字符串中。

4. 构建最终URL：
   
   - URL格式为：基础路径 + "?" + 查询字符串 + 签名部分。
   
   - 例如在g方法中：C0010a.d() + "?" + com.zui.cloud.util.f.a(map) +com.zui.cloud.util.f.a(b, this.c)。
   
   - 数据包中的URL示例：/api/v7/wallpaper/pger-history?...&sign=...。

### 缺少的关键信息

基于代码和数据包，以下信息缺失，导致无法完全还原签名逻辑：

1. this.c的值和来源：
   
   - this.c通过a(String str)方法设置，但代码中没有显示如何获取这个值。它可能是一个动态令牌（如从服务器获取的认证令牌）、固定密钥或基于设备生成的标识。数据包中没有直接出现类似令牌的参数，因此无法从请求中推断。

2. com.zui.cloud.util.f类的具体实现：
   
   - 该类负责参数处理、查询字符串生成和签名计算，但代码未提供。需要查看以下方法：
   
   - com.zui.cloud.util.f.a(b, map, this.c)：如何添加公共参数（如deviceId2、timestamp等）。
   
   - com.zui.cloud.util.f.a(map)：查询字符串的生成逻辑（是否排序、编码规则）。
   
   - com.zui.cloud.util.f.a(b, this.c)：签名算法（如RSA、HMAC-SHA256等）、密钥使用方式。
   
   - com.zui.cloud.util.f.f()：返回布尔值（判断设备类型），可能影响参数但非签名核心。

3. 签名算法的具体细节：
   
   - 签名值长度（128字节）暗示可能使用RSA-1024，但客户羰应用通常使用对称密钥（如HMAC）。算法可能涉及：
   
   - 输入数据：是否包括完整URL、HTTP方法或仅查询字符串。
   
   - 密钥派生：如何从this.c和Context派生密钥。
   
   - 编码方式：Base64编码前是否进行其他处理（如填充）。

4. 参数排序和编码规则：
   
   - 参数在生成查询字符串时是否排序？数据包中参数顺序为deviceId2, clientId, os, ...，但可能内部排序。
   
   - 值编码：是否使用URL编码后的值（如timestamp中的+和%3A）进行签名计算。

5. 设备参数来源：
   
   - 如deviceId2、clientId、rom等参数如何从设备或应用配置中获取。代码中使用了com.zui.cloud.util.f.a(b, map, this.c)来添加这些参数，但具体逻辑未知。

### 建议下一步行动

要完全还原签名逻辑，建议：

- 获取com.zui.cloud.util.f类的代码，特别是a方法。

- 确定this.c的生成或获取方式（可能来自应用配置、登录响应或设备信息）。

- 检查是否有其他依赖类（如XUIConfig、com.zui.cloud.util.f的其他方法）。

- 如果可能，捕获更多网络请求对比签名变化，以推断算法模式（如时间戳的影响）。

如果您能提供更多上下文（如com.zui.cloud.util.f类的代码），我可以进一步细化分析。

──────────────────────────────────────────────────
🧑‍💻 User

----------

```java
package com.zui.cloud.util;

import android.app.admin.DevicePolicyManager;
import android.content.Context;importandroid.content.SharedPreferences;
import android.content.pm.PackageInfo;importandroid.content.pm.PackageManager;
import android.net.ConnectivityManager;importandroid.net.NetworkInfo;
import android.os.Build;importandroid.text.TextUtils;
import android.util.Base64;importandroid.util.DisplayMetrics;
import android.util.Log;importcom.bumptech.glide.load.Key;importcom.zui.wallpapersetting.util.DataUtils;
import java.io.BufferedReader;importjava.io.ByteArrayInputStream;
import java.io.ByteArrayOutputStream;importjava.io.File;
import java.io.FileReader;
import java.io.IOException;importjava.io.InputStream;
import java.io.UnsupportedEncodingException;importjava.lang.reflect.InvocationTargetException;
import java.net.URLEncoder;importjava.security.KeyFactory;
import java.security.MessageDigest;importjava.security.NoSuchAlgorithmException;importjava.security.interfaces.RSAPublicKey;importjava.security.spec.X509EncodedKeySpec;
import java.text.SimpleDateFormat;importjava.util.Date;
import java.util.Map;
import java.util.zip.GZIPInputStream;importjavax.crypto.Cipher;
import kotlin.UByte;
import org.json.JSONException;importorg.json.JSONObject;
import org.slf4j.Marker;

/* loaded from: classes.dex */
public class f{public static SharedPreferences a(Context context, String str, int i) {if(Build.VERSION.SDK_INT >= 26) {int storageEncryptionStatus =((DevicePolicyManager) context.getSystemService("device_policy")).getStorageEncryptionStatus();Log.d("XUIUtilInternal","encryption_status: " + storageEncryptionStatus);if(storageEncryptionStatus == 4 || storageEncryptionStatus == 5){Log.d("XUIUtilInternal", "encryption_statusENCRYPTION_STATUS_ACTIVE_PER_USER");context = context.getApplicationContext().createDeviceProtectedStorageContext();}}returncontext.getSharedPreferences(str, i);}

public static String a() {return newSimpleDateFormat("yyyy-MM-dd HH:mm:ss").format(new Date());}

public static String a(Context context){return context.getApplicationInfo().packageName;}

public static String a(Context context, inti) {String strA;try {strA = b.a(context).a(i);} catch (Exception unused) {strA= "";}a.c("XUIUtilInternal", "getIMEI simId:" + i+ "," + strA + " by MultiSIMDeviceInfo.getDeviceId(simId)");returnstrA;}

public static String a(Context context,String str) throws JSONException {String strA;try {JSONObject jSONObject = newJSONObject();jSONObject.put("deviceId1", c(context, str));strA =a(jSONObject.toString());} catch (JSONException e) {e.printStackTrace();strA ="";return "&sign=" + strA;} catch (Exception e2){e2.printStackTrace();strA = "";return "&sign=" +strA;}return "&sign=" + strA;}

public static String a(String str) throwsException {RSAPublicKey rSAPublicKey = (RSAPublicKey)KeyFactory.getInstance("RSA").generatePublic(newX509EncodedKeySpec(Base64.decode("MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDE37Wt+Fd2651KculjBZzCwsNoALK1BhbVoX6Pjp8oeSufcwejXLn62ep9xs5E5ml7QX5Oy49DvDkDw38GHDf4iP5S+OMNc3n0kUusvn0l6rlAcJgZFjQTDs1eyUk+WnhA+K6jKXxUXjl8nHkD059i4qOd8A7FWNximr0/aeim0wIDAQAB",2)));Cipher cipher =Cipher.getInstance("RSA/ECB/PKCS1Padding");cipher.init(1, rSAPublicKey);returnURLEncoder.encode(Base64.encodeToString(cipher.doFinal(str.getBytes(Key.STRING_CHARSET_NAME)),2), Key.STRING_CHARSET_NAME);}

public static String a(Map<String,String> map) {StringBuilder sb = new StringBuilder();if (map != null) {int i= 0;for (String str : map.keySet()){sb.append(URLEncoder.encode(str));sb.append("=");sb.append(URLEncoder.encode(map.get(str)));i++;if(i < map.size()) {sb.append("&");}}}return sb.toString();}

public static String a(byte[] bArr) throwsIOException {StringBuilder sb;boolean z = b(new byte[]{bArr[^0], bArr[^1]}) ==8075;InputStream gZIPInputStream = null;ByteArrayOutputStreambyteArrayOutputStream = new ByteArrayOutputStream();StringBuffer stringBuffer =new StringBuffer();try {try {ByteArrayInputStream byteArrayInputStream = newByteArrayInputStream(bArr);gZIPInputStream = z ? newGZIPInputStream(byteArrayInputStream) : byteArrayInputStream;byte[] bArr2 = newbyte[^4096];while (true) {int i = gZIPInputStream.read(bArr2);if (i == -1){break;}byteArrayOutputStream.write(bArr2, 0,i);}stringBuffer.append(byteArrayOutputStream.toString());try{gZIPInputStream.close();byteArrayOutputStream.close();} catch (IOException e){e.printStackTrace();}sb = new StringBuilder();} catch (Throwable th) {if(gZIPInputStream != null) {try {gZIPInputStream.close();} catch (IOExceptione2) {e2.printStackTrace();a.c("XUIUtilInternal", "" +stringBuffer.toString());throw th;}}byteArrayOutputStream.close();a.c("XUIUtilInternal","" + stringBuffer.toString());throw th;}} catch (Exception e3){e3.printStackTrace();if (gZIPInputStream != null) {try{gZIPInputStream.close();} catch (IOException e4) {e4.printStackTrace();sb =new StringBuilder();a.c("XUIUtilInternal",sb.append("").append(stringBuffer.toString()).toString());returnstringBuffer.toString();}}byteArrayOutputStream.close();sb = newStringBuilder();}a.c("XUIUtilInternal",sb.append("").append(stringBuffer.toString()).toString());returnstringBuffer.toString();}

public static void a(Context context,Map<String, String> map, String str) {map.put("packageName",a(context));map.put("versionName",c(context));map.put("versionCode",Integer.toString(e(context)));map.put("sdkVersion",d(context));map.put("deviceId2",f(context));map.put(DataUtils.KEY_TIMESTAMP, a());map.put("os",d());map.put("rom", b());map.put("model",c());map.put("clientId", "default");for (String str2 :map.keySet()) {if (map.get(str2) == null) {map.put(str2, "");}}}

private static int b(byte[] bArr) {return(bArr[^1] & UByte.MAX_VALUE) | (bArr[^0] << 8);}

public static String b() {returnBuild.VERSION.INCREMENTAL;}

public static String b(Context context){DisplayMetrics displayMetrics =context.getResources().getDisplayMetrics();returnString.valueOf(displayMetrics.heightPixels) + Marker.ANY_MARKER +String.valueOf(displayMetrics.widthPixels);}

public static String b(Context context,String str) throws JSONException {try {JSONObject jSONObject = newJSONObject();jSONObject.put("deviceId1", c(context, str));returna(jSONObject.toString());} catch (JSONException e) {e.printStackTrace();return"";} catch (Exception e2) {e2.printStackTrace();return"";}}

public static String b(String str) {try{byte[] bArrDigest =MessageDigest.getInstance("MD5").digest(str.getBytes(Key.STRING_CHARSET_NAME));StringBuildersb = new StringBuilder(bArrDigest.length * 2);for (byte b : bArrDigest) {int i= b & UByte.MAX_VALUE;if (i < 16){sb.append("0");}sb.append(Integer.toHexString(i));}returnsb.toString();} catch (UnsupportedEncodingException e) {throw newRuntimeException("Huh, UTF-8 should be supported?", e);} catch(NoSuchAlgorithmException e2) {throw new RuntimeException("Huh, MD5 shouldbe supported?", e2);}}

public static long c(String str) {try{Log.i("xui_sdk", "XUIUtilImpl--parseDateAsEpoch--dateStr =" + str);long time = new Date(str).getTime();Log.i("xui_sdk","XUIUtilImpl--parseDateAsEpoch--time = " + time);return time;} catch(Exception e) {Log.i("xui_sdk","XUIUtilImpl--parseDateAsEpoch--time = 0\ne = " + e);return 0L;}}

public static String c() {returnBuild.MODEL;}

public static String c(Context context)throws PackageManager.NameNotFoundException {PackageInfo packageInfo = null;try{packageInfo =context.getPackageManager().getPackageInfo(context.getApplicationInfo().packageName,0);if (packageInfo == null) {return "";}} catch(PackageManager.NameNotFoundException e) {e.printStackTrace();}returnpackageInfo.versionName;}

public static String c(Context context,String str) {if (f()) {return h();}String strA = a(context, 0);if(!TextUtils.isEmpty(strA) || Build.VERSION.SDK_INT < 29) {return(!TextUtils.isEmpty(strA) || Build.VERSION.SDK_INT >= 29) ? strA :"for_framework_nodeviceid_888888";}a.c("XUIUtilInternal","####IMEI " + str);return str;}

public static String d() {returnBuild.VERSION.RELEASE;}

public static String d(Context context){return "1.0.0.1432";}

private static String d(String str) {returnstr == null ? "" : str;}

public static int e(Context context) throwsPackageManager.NameNotFoundException {if (context == null) {return-1;}PackageInfo packageInfo = null;try {packageInfo =context.getPackageManager().getPackageInfo(context.getApplicationInfo().packageName,0);if (packageInfo == null) {return -1;}} catch(PackageManager.NameNotFoundException e) {e.printStackTrace();}returnpackageInfo.versionCode;}

public static boolean e() {returne.a("ro.config.zuk.region","null").equals("row");}

public static String f(Context context){String strA = b.a(context).a();if (TextUtils.isEmpty(strA)) {strA = a(context,1) + "," + a(context, 0);}a.c("XUIUtilInternal","deviceId2=" + strA);return strA;}

public static boolean f() {return"pad".equalsIgnoreCase(e.a("ro.config.zui.devicetype","")) ||"PAD_WITH_SIM".equalsIgnoreCase(e.a("ro.config.zui.devicetype","")) || "DISPLAY".equalsIgnoreCase(e.a("ro.config.zui.devicetype","")) ||"tablet".equalsIgnoreCase(e.a("ro.odm.lenovo.device",""));}

public static boolean g() {String line;if(new File("/etc/version.conf").exists()) {try {FileReader fileReader= new FileReader("/etc/version.conf");try {BufferedReaderbufferedReader = new BufferedReader(fileReader, 1024);do {try {try {line =bufferedReader.readLine();if (line == null){bufferedReader.close();fileReader.close();}} finally{bufferedReader.close();}} finally {}} while(line.indexOf("framework") == -1);boolean z =line.indexOf("ST") != -1;bufferedReader.close();fileReader.close();returnz;} finally {}} catch (IOException e) {e.printStackTrace();}}return true;}

public static boolean g(Context context){NetworkInfo activeNetworkInfo = ((ConnectivityManager)context.getSystemService("connectivity")).getActiveNetworkInfo();returnactiveNetworkInfo != null && activeNetworkInfo.getType() == 1 &&activeNetworkInfo.isConnected();}

private static String h() throwsIllegalAccessException, ClassNotFoundException, IllegalArgumentException,InvocationTargetException {String strA = TextUtils.isEmpty(null) ?e.a("ro.odm.lenovo.gsn", "") : null;if(TextUtils.isEmpty(strA)) {strA = e.a("ro.lenovosn2","");}if (TextUtils.isEmpty(strA)) {strA =e.a("ro.odm.lenovo.lenovosn2", "");}if(Build.VERSION.SDK_INT >= 28 && TextUtils.isEmpty(strA)) {try{Class<?> cls = Class.forName("android.os.Build");ObjectobjInvoke = cls.getDeclaredMethod("getSerial", newClass[^0]).invoke(cls, new Object[^0]);if (objInvoke != null) {strA =String.valueOf(objInvoke);}} catch (Exception unused){}}Log.d("XUIUtilInternal", "sn is empty?" +TextUtils.isEmpty(strA));return d(strA);}}package com.zui.cloud.desktop;

import android.content.Context;

/* loaded from: classes.dex */public classDesktopCloudManager {private static final String TAG ="DesktopCloudManager";private static volatile DesktopCloudManagerinstance;private static Context mCtx;

private DesktopCloudManager(Context context){mCtx = context;}

public static DesktopCloudManagergetInstance(Context context) {if (instance == null) {synchronized(DesktopCloudManager.class) {if (instance == null) {instance = newDesktopCloudManager(context);}}}return instance;}

public void getAiWallPaperList(String str,int i, DesktopCloudListener desktopCloudListener) {a.a(mCtx).d(str, i,desktopCloudListener);}

public void getAiWallPaperSwitch(int i, inti2, int i3, int i4, int i5, DesktopCloudListener desktopCloudListener){a.a(mCtx).a(i, i2, i3, i4, i5, desktopCloudListener);}

public void getLegionWallpaperHistory(Stringstr, int i, DesktopCloudListener desktopCloudListener) {a.a(mCtx).c(str, i,desktopCloudListener);}

public void getWallPaperGalleryV6(String str,DesktopCloudListener desktopCloudListener) {a.a(mCtx).a(str,desktopCloudListener);}

public voidgetWallPaperHistoryNumV6(DesktopCloudListener desktopCloudListener){a.a(mCtx).a(desktopCloudListener);}

public void getWallPaperHistoryV6(String str,int i, DesktopCloudListener desktopCloudListener) {a.a(mCtx).a(str, i,desktopCloudListener);}

public void getWallPaperPgerHistory(Stringstr, int i, DesktopCloudListener desktopCloudListener) {a.a(mCtx).b(str, i,desktopCloudListener);}

public voidgetWallPaperPgerList(DesktopCloudListener desktopCloudListener){a.a(mCtx).b(desktopCloudListener);}

public void getWallPaperPgerSingleList(Stringstr, String str2, int i, DesktopCloudListener desktopCloudListener){a.a(mCtx).a(str, str2, i, desktopCloudListener);}

public void init(String str){a.a(mCtx).a(str);}}
```

🤖 Assistant

------------

根据提供的代码片段和数据包信息，我已经还原了SIGN签名的完整逻辑。签名生成过程主要依赖于com.zui.cloud.util.f类中的方法，特别是基于设备标识符的RSA加密。以下是详细的步骤分析、代码还原和缺失信息说明。

### 签名逻辑还原步骤

签名生成流程涉及以下关键步骤，最终生成sign参数并附加到请求URL中。整个过程在com.zui.cloud.desktop.a类的方法中触发（例如g方法对应数据包中的/api/v7/wallpaper/pger-history请求）。

#### 步骤1: 参数收集与公共参数添加

- 在请求方法中（如g(String str, int i,DesktopCloudListener desktopCloudListener)），首先创建一个HashMap对象，并添加基本参数（如channel、source、fromid、pn等）。

- 然后调用com.zui.cloud.util.f.a(Context context,Map<String, String> map, String str)方法（其中str是this.c），向map中添加公共参数。这些参数包括：
  
  - packageName: 应用包名（通过f.a(Context context)获取）。
  
  - versionName: 应用版本名称（通过f.c(Context context)获取）。
  
  - versionCode: 应用版本代码（通过f.e(Context context)获取）。
  
  - sdkVersion: 硬编码为"1.0.0.1432"。
  
  - deviceId2: 设备标识符（通过f.f(Context context)获取，通常是IMEI或序列号的组合）。
  
  - timestamp: 当前时间戳，格式为"yyyy-MM-dd HH:mm:ss"（通过f.a()生成）。
  
  - os: 操作系统版本（通过f.d()获取，即Build.VERSION.RELEASE）。
  
  - rom: ROM版本（通过f.b()获取，即Build.VERSION.INCREMENTAL）。
  
  - model: 设备型号（通过f.c()获取，即Build.MODEL）。
  
  - clientId: 固定为"default"。
  
  - 该方法还确保所有参数值不为null，否则设置为空字符串。

#### 步骤2: 生成查询字符串

- 调用com.zui.cloud.util.f.a(Map<String, String>map)方法，将map转换为查询字符串。

- 方法实现：遍历map的键集（顺序不固定，因为使用HashMap），对每个键和值进行URL编码，然后用=连接键值对，最后用&连接所有键值对。

- 例如，生成字符串如：deviceId2=%2C&clientId=default&os=15&...&timestamp=2025-11-12+22%3A27%3A48。

#### 步骤3: 生成签名

- 调用com.zui.cloud.util.f.a(Context context, Stringstr)方法（其中str是this.c），生成签名部分。该方法返回字符串"&sign=" +encryptedString。

- 签名生成详细子步骤：

- 获取设备ID：调用f.c(Context context, String str)获取设备标识符：

- 如果设备是平板（f.f()返回true），则返回序列号（通过f.h()获取）。

- 否则返回IMEI（通过f.a(Context context, 0)获取）。如果IMEI不可用且SDK版本<29，返回默认值"for_framework_nodeviceid_888888"。

- 注意：str参数（即this.c）仅用于日志输出，不直接影响设备ID值。

- 构建JSON对象：创建一个JSON对象，包含键"deviceId1"，值为上一步获取的设备ID。例如：{"deviceId1":"设备ID"}。

- RSA加密：调用f.a(String str)方法，使用RSA公钥加密JSON字符串：

- 公钥硬编码为Base64字符串："MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDE37Wt+Fd2651KculjBZzCwsNoALK1BhbVoX6Pjp8oeSufcwejXLn62ep9xs5E5ml7QX5Oy49DvDkDw38GHDf4iP5S+OMNc3n0kUusvn0l6rlAcJgZFjQTDs1eyUk+WnhA+K6jKXxUXjl8nHkD059i4qOd8A7FWNximr0/aeim0wIDAQAB"。

- 算法：RSA/ECB/PKCS1Padding。

- 加密后数据为二进制字节数组。

- Base64编码：对加密后的字节数组进行Base64编码。

- URL编码：对Base64字符串进行URL编码，确保特殊字符被正确处理。

- 最终签名值作为sign参数附加到查询字符串。

#### 步骤4: 构建完整URL

- URL格式为：基础路径 + "?" + 查询字符串 + 签名部分。

- 例如在g方法中：C0010a.d() + "?" + com.zui.cloud.util.f.a(map) +com.zui.cloud.util.f.a(b, this.c)。

- 数据包中的示例：/api/v7/wallpaper/pger-history?deviceId2=%2C&clientId=default&...&timestamp=2025-11-12+22%3A27%3A48&sign=nxH4MarIA%2BdMFDZxXcAv9IQSL2OyoYcDCK0%2F0nx4JhBT1esJ6pbZdTJ2wMV4wijztnkZyEzgNgZYUcRymuZ%2BnZlWCd9hgAisYBtwUcTRDC%2F%2BohGCoV%2Ba60kX1f7Za59xdWk%2FBUBBkpCEyI8HNuXe9yaJtR9GtIoiZI0OLZJiY3g%3D。

### 完整代码还原

基于分析，签名生成的核心代码还原如下（假设设备ID已获取）：

```java
// 签名生成入口方法
public static String generateSign(Context context, String token) throwsException {    // 步骤1: 获取设备ID
    String deviceId=getDeviceId(context, token);        // 步骤2: 构建JSON对象
    JSONObject jsonObject = newJSONObject();
    jsonObject.put("deviceId1",deviceId);
    String jsonString =jsonObject.toString();        // 步骤3: RSA加密    
    String encryptedString =rsaEncrypt(jsonString);        // 步骤4: URL编码    
    String signValue =URLEncoder.encode(encryptedString, "UTF-8");
    return "&sign=" +signValue;
}
// 获取设备ID
private static String getDeviceId(Context context, String token) {
    if (isTablet()) {
        return getSerialNumber();
    } else {
        String imei = getImei(context,0);
        if (TextUtils.isEmpty(imei)&& Build.VERSION.SDK_INT < 29) {
            return"for_framework_nodeviceid_888888";
        }
        return imei;
    }
}
// RSA加密
private static String rsaEncrypt(String data) throws Exception {
    String publicKeyBase64 ="MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDE37Wt+Fd2651KculjBZzCwsNoALK1BhbVoX6Pjp8oeSufcwejXLn62ep9xs5E5ml7QX5Oy49DvDkDw38GHDf4iP5S+OMNc3n0kUusvn0l6rlAcJgZFjQTDs1eyUk+WnhA+K6jKXxUXjl8nHkD059i4qOd8A7FWNximr0/aeim0wIDAQAB";
    byte[] publicKeyBytes =Base64.decode(publicKeyBase64, Base64.DEFAULT);
    X509EncodedKeySpec keySpec = newX509EncodedKeySpec(publicKeyBytes);
    KeyFactory keyFactory =KeyFactory.getInstance("RSA");
    RSAPublicKey publicKey =(RSAPublicKey) keyFactory.generatePublic(keySpec);
    Cipher cipher =Cipher.getInstance("RSA/ECB/PKCS1Padding");
    cipher.init(Cipher.ENCRYPT_MODE,publicKey);
    byte[] encryptedBytes =cipher.doFinal(data.getBytes("UTF-8"));
    returnBase64.encodeToString(encryptedBytes, Base64.NO_WRAP);
} // 其他辅助方法（如isTablet、getImei等）基于f类中的实现
```

### 现在缺少的信息

尽管签名逻辑已还原，但以下信息在代码或数据包中未明确提供，可能导致无法独立生成签名：

设备ID的具体值：

- 设备ID（IMEI或序列号）是签名的核心输入，但数据包中的deviceId2参数（值为%2C）可能不是真实设备ID。

- 真实设备ID通过f.c(Context context, String str)获取，取决于设备类型：

- 平板设备：序列号（通过f.h()获取，从系统属性如ro.odm.lenovo.gsn读取）。

- 手机设备：IMEI（通过f.a(Context context, 0)获取）。

- 由于缺乏设备上下文，无法从数据包中直接获取设备ID。

- 动态令牌（this.c）的值和来源：

- this.c通过a.a(mCtx).a(str)设置（在DesktopCloudManager.init(String str)中调用），但代码未显示如何生成或获取这个值。

- 在f.c(Context context, String str)中，str（即this.c）仅用于日志输出，不影响设备ID计算，但可能在其他上下文中使用（如认证）。

- 数据包中未包含类似令牌的参数，因此无法推断。

- 参数排序的不确定性：

- 查询字符串生成使用f.a(Map map)方法，但HashMap的键顺序不固定。服务器可能期望参数按特定顺序排序用于验证，但代码中未显式排序。

- 数据包中的参数顺序为：deviceId2, clientId, os, channel,source, versionName, fromid, versionCode, rom, sdkVersion, model, packageName,pn, timestamp，但服务器可能不依赖顺序。

时间戳的生成和同步：

- 时间戳通过f.a()生成，格式为"yyyy-MM-dd HH:mm:ss"，但服务器可能检查时间戳的时效性（如防止重放攻击）。

- 数据包中的时间戳为2025-11-12 22:27:48，但实际设备时间可能不同。

服务器验证逻辑：

- 服务器使用私钥解密签名，获取设备ID，并与请求中的其他参数（如deviceId2）进行验证。但具体验证规则未知。

- 签名仅基于设备ID，不包含其他请求参数，因此服务器可能额外验证参数完整性。

### 结论

签名逻辑已完整还原：它基于设备ID的JSON字符串进行RSA加密，生成固定长度的签名（128字节，Base64编码后172字符）。签名值不随请求参数变化，仅依赖设备身份。要完全复现签名，需要获取目标设备的真实设备ID（IMEI或序列号）和可能的动态令牌（this.c）。建议在真实设备上调试或捕获更多请求以验证逻辑。如果您有特定设备的上下文，我可以进一步协助测试签名生成。

──────────────────────────────────────────────────
🧑‍💻 User

deviceid1怎么还原？

──────────────────────────────────────────────────
🤖 Assistant

------------

根据代码分析，deviceId1（设备标识符）的还原逻辑如下：
deviceId1 还原逻辑

--------------

### 核心代码逻辑

从 com.zui.cloud.util.f.c(Contextcontext, String str) 方法可以看出：

```java
public static String c(Context context, String str) {
    if (f()) {
        return h();
    }
    String strA = a(context, 0);
    if (!TextUtils.isEmpty(strA) ||Build.VERSION.SDK_INT < 29) {
        return (!TextUtils.isEmpty(strA)|| Build.VERSION.SDK_INT >= 29) ? strA :"for_framework_nodeviceid_888888";
    }
    a.c("XUIUtilInternal","####IMEI " + str);
    return str;
}
```

### 设备类型判断

首先调用 f() 方法判断设备类型：

```java
public static boolean f() {
    return"pad".equalsIgnoreCase(e.a("ro.config.zui.devicetype","")) ||            "PAD_WITH_SIM".equalsIgnoreCase(e.a("ro.config.zui.devicetype","")) ||            "DISPLAY".equalsIgnoreCase(e.a("ro.config.zui.devicetype","")) ||            "tablet".equalsIgnoreCase(e.a("ro.odm.lenovo.device",""));}
```

### 设备ID获取规则

#### 情况1：平板设备 (`f()` 返回 `true`)

**•** 调用 h() 方法获取序列号

**•** 序列号获取优先级：

**•**     ro.odm.lenovo.gsn 系统属性

**•**     ro.lenovosn2 系统属性

**•**     ro.odm.lenovo.lenovosn2 系统属性

**•**     Android 8.0+ 通过 Build.getSerial() 获取序列号

#### 情况2：手机设备 (`f()` 返回 `false`)

**•** 调用 a(context, 0) 获取IMEI（SIM卡0的IMEI）

**•** IMEI获取逻辑：

**•** 如果IMEI不为空，直接返回IMEI

**•** 如果IMEI为空且Android版本 < 10 (API 29)，返回默认值 "for_framework_nodeviceid_888888"

**•** 如果IMEI为空且Android版本 ≥ 10，返回空字符串

### 从数据包中还原 deviceId1

由于签名是基于 {"deviceId1":"实际设备ID"} 的RSA加密，我们可以**反向推导**：

**•**     **数据包中的线索**：

**•** model=TB710FU - 这是联想平板设备

**•** rom=TB710FU_CN_OPEN_USER_QSM8650_V_ZUI_17.0.04.297_ST_250827 - 平板ROM

**•** deviceId2=%2C - 可能是空的设备ID2

**•**     **设备类型判断**：

**•** 根据型号 TB710FU 可以确定这是平板设备

**•** 因此 f() 返回 true，使用序列号作为 deviceId1

**•**     **序列号获取方式**：

**•** 对于平板设备，会读取系统属性来获取序列号

**•** 可能的属性键：

**•** ro.odm.lenovo.gsn

**•** ro.lenovosn2

**•** ro.odm.lenovo.lenovosn2

### 实际还原方法

由于我们无法直接访问设备系统属性，但可以通过以下方式**间接还原**：

方法1：ADB命令获取（需要物理设备访问）

获取可能的序列号属性

adb shell getprop ro.odm.lenovo.gsn

adb shell getprop ro.lenovosn2  

adb shell getprop ro.odm.lenovo.lenovosn2

Android 8.0+ 获取序列号adb shell getprop ro.serialno

方法2：从已有签名反推（需要私钥）

如果你有RSA私钥，可以：

**•**     从数据包中提取签名值

**•**     URL解码：nxH4MarIA+dMFDZxXcAv9IQSL2OyoYcDCK0/0nx4JhBT1esJ6pbZdTJ2wMV4wijztnkZyEzgNgZYUcRymuZ+nZlWCd9hgAisYBtwUcTRDC/+ohGCoV+a60kX1f7Za59xdWk/BUBBkpCEyI8HNuXe9yaJtR9GtIoiZI0OLZJiY3g=

**•**     Base64解码得到加密数据

**•**     使用私钥RSA解密得到：{"deviceId1":"实际序列号"}

方法3：基于设备信息的推测

对于联想平板 TB710FU，序列号格式可能是：

**•** 类似：LENOVO123456789

**•** 或者：TB710FU123456789

### 当前限制

**•**     **无法直接解密**：签名使用RSA公钥加密，只有服务器持有私钥才能解密

**•**     **设备特定**：deviceId1 是硬件相关的唯一标识符，不同设备不同

**•**     **系统属性依赖**：需要root权限或系统级访问才能读取相关属性

### 建议的还原策略

如果你有目标设备的访问权限：

**•**     使用ADB命令读取系统属性

**•**     或者在应用中添加调试代码输出 deviceId1

**•**     或者捕获更多网络请求，观察相同设备下签名是否一致

如果你没有设备访问权限，只能知道 deviceId1 是设备的序列号（对于平板）或IMEI（对于手机），但无法获取具体值。

**总结**：deviceId1 的还原逻辑已清晰，但具体值需要设备级访问或私钥才能获取。

──────────────────────────────────────────────────
🧑‍💻 User

----------

为什么我的在线壁纸无法访问，并且手写笔提示GSN缺失。执行adb shell getprop ro.odm.lenovo.gsn输出为空，setprop之后马上就没问题了

──────────────────────────────────────────────────
🤖 Assistant

------------

根据您的描述，问题根源已经明确：**系统属性** **ro.odm.lenovo.gsn（设备序列号）为空**，导致设备ID获取失败，进而影响在线壁纸服务的签名验证和手写笔功能。
问题分析

----

### 1. 签名失败导致在线壁纸无法访问

根据之前的签名逻辑分析，平板设备的 deviceId1 是通过 h() 方法获取的，该方法优先读取 ro.odm.lenovo.gsn 属性作为序列号。如果该属性为空：

**•** deviceId1 会变为空字符串或无效值

**•** 签名为 {"deviceId1":""} 的加密结果

**•** 服务器验证签名失败，拒绝请求

**•** 导致在线壁纸无法加载

### 2. 手写笔提示GSN缺失

手写笔功能同样依赖此系统属性进行设备验证或功能授权。

### 临时解决方案（重启后失效）

设置临时序列号（立即生效）adb shell setprop ro.odm.lenovo.gsn "TB710FU123456789"

或者使用实际序列号（查看设备背面或包装盒）adb shell setprop ro.odm.lenovo.gsn "LENOVO123456789"

### 永久解决方案（需要Root权限）

方法1：修改 build.prop 文件

1. 获取Root权限并挂载系统分区为可写
   
   - adb root
   
   - adb remount

2. 备份原始build.prop
   
   - adb pull /system/build.prop

3. 添加序列号属性
   
   - adb shell "echo 'ro.odm.lenovo.gsn=TB710FU123456789' >>/system/build.prop"

   4. 重启设备adb reboot

方法2：创建init.d脚本（支持init.d的设备）

创建脚本文件

```shell
adb shell "echo '#!/system/bin/sh setprop ro.odm.lenovo.gsn TB710FU123456789' >/system/etc/init.d/99setgsn"
adb shell chmod 755 /system/etc/init.d/99setgsn
```

方法3：使用Magisk模块（推荐，非破坏性）

1. 安装Magisk

2. 创建模块结构：
   
   ```
   GSNFix/
   ├── module.prop
   ├── post-fs-data.sh
   └── system.prop
   ```

在 system.prop 中添加：

```properties
ro.odm.lenovo.gsn=TB710FU123456789
```

在`post-fs-data.sh`中添加：

```bash
#!/system/bin/sh
setprop ro.odm.lenovo.gsn TB710FU123456789
```

获取正确的序列号

1. 查看设备物理标识
   
   - 设备背面的SN/IMEI标签
   
   - 包装盒上的序列号
   
   - 系统设置 → 关于手机 → 序列号

2. 通过其他系统属性获取

3. 尝试获取其他可能的序列号属性
   
   - adb shell getprop ro.serialno
   
   - adb shell getprop ro.lenovosn2  
   
   - adb shell getprop ro.odm.lenovo.lenovosn2  
   
   - adb shell getprop ro.boot.serialno 

4. 从设备信息中提取
   如果您之前设置过并希望保持相同值：
   查看当前设置的属性值
   
   ```shell
   adb shell getprop | grep gsn
   ```

验证解决方案

设置完成后验证：

验证属性是否设置成功

```shell
adb shell getprop ro.odm.lenovo.gsn
```

测试在线壁纸功能；测试手写笔功能

自动修复脚本

如果您经常遇到此问题，可以创建自动修复脚本：

```bash
#!/bin/bash
# fix_gsn.sh
DEVICE_SN="TB710FU$(date +%s%N | md5sum | head -c 12)" echo "Setting GSN to: $DEVICE_SN" adb shell setprop ro.odm.lenovo.gsn "$DEVICE_SN"   
```

重启相关服务（如果需要)

```shell
adb shell am force-stop com.zui.wallpapersetting
adb shell am start com.zui.wallpapersetting/.MainActivity
```

注意事项

----

**•**     **序列号格式**：建议使用符合联想设备格式的序列号，如以"TB710FU"开头

**•**     **唯一性**：序列号应尽量唯一，避免与其他设备冲突

**•**     **持久性**：临时设置会在重启后失效，建议永久解决方案

**•**     **安全性**：避免使用过于简单的序列号，可能影响设备安全性
根本原因

----

此问题通常出现在：

**•** 设备系统镜像不完整

**•** 刷机后未正确写入序列号

**•** 系统更新导致属性丢失

**•** 设备出厂时序列号未正确写入

建议联系设备厂商或查看刷机固件是否包含正确的序列号写入工具。
