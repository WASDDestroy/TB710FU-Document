# Zygisk Problems

自Zygisk 1.3.0起，Zygisk集成了Shamiko的绝大部分功能，理论上能提供更好的隐蔽性。

> （摘自Zygisk 1.3.0的GitHub Release页面）Zygisk Next 并未整合 Shamiko 的 prop 隐藏与字体模块处理功能。若需要 prop 隐藏，请自行提取 Shamiko 的 service.sh，并通过 service.d 等方式开机启动；若需要在 Android 12及以上的设备上使用字体模块，请安装 [FontLoader](https://t.me/newqianzhuang/73) 。安装 Zygisk Next 前无需卸载 Shamiko，Shamiko 即使安装也不会被加载。对于 Magisk 用户，Shamiko 白名单对应于「将非 Root 应用视为排除列表」选项。

使用过时的Zygisk或者过时的基于Zygisk的上层模块都会导致整个Zygisk体系在较高版本的Android上崩溃（从Android 15开始现象变得明显），一个典型的症状是LSPosed弹出错误日志相关提示。碰到这个问题时先检查下各个Zygisk组件是否更新到了最新版本。
