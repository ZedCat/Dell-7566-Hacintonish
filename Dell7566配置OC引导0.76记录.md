# Dell7566配置OC引导0.76记录

前言：

当前的mac版本是11.6，OC的版本的0.73，已经定制了USB，想升级到最新的12.1。按照网上的升级教程选择引导后黑屏，决定升级下OC和相关驱动。

>  一、准备工作

在[OC官网](https://dortania.github.io/OpenCore-Install-Guide/ktext.html) 下载相关驱动文件并解压

> 二、驱动更新

1. ACPI文件夹复制原来的即可
2. Drivers留下三个驱动`HfsPlus.efi` `OpenCanopy.efi` `OpenRuntime.efi`
3. Kext文件夹把下载好的新驱动全部复制
4. 复制一份新的config.plist对照的之前可以引导的把每项都设置一样

> 三、测试排错

1. 第一次报错i2c设备没屏蔽
