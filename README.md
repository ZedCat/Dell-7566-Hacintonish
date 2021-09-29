# Dell-7566-Hactonish

## 一、配置

| 型号 | Dell 7566 |
| :-----| :---- |
| 处理器 | 英特尔 Core i5-6300HQ @ 2.30GHz 四核 |
| 主板  | 戴尔 0293F5 ( 100 Series/C230 Series 芯片组 Family - A14E ) |
|   内存 |  12 GB ( 海力士 DDR4 2400MHz / 金士顿 DDR4 2400MHz )  |
| 独立显卡 | Nvidia GeForce GTX 960M ( 4 GB / 戴尔）【无法驱动】 |
| 核心显卡 | 英特尔 HD Graphics 530 |
|  显示器| 奇美 CMN15C4 ( 15.5 英寸 )【1920*1080】 |
|  声卡| 瑞昱 @ 英特尔 High Definition Audio 控制器 【ALC256】 |
| 网卡| 瑞昱 RTL8168/8111/8112 Gigabit Ethernet Controller / 戴尔|

## 二、步骤

1. 1个已经写入过镜像的U盘。大神的们的教程很详细了，不知道可以点击 [传送门](https://blog.daliansky.net/) 
2. 使用DG进入U盘的EFI目录，删除原来，把我的EFI复制进去即可安装。具体步骤请参考大神的教程 [传送门](https://blog.daliansky.net/Lenovo-Tianyi-510s-Mini-and-macOS-BigSur-Installation-Tutorial.html) ，推荐新手看一遍，大神整理很多有用的东西，比如关闭mac的不允许打开未知来源的软件等。

## 三、已知问题

1.wifi影响蓝牙耳机的信号，表现为用蓝牙耳机听歌会断断续续。

2.声卡驱动不太完美。目前（2021-9-29）测试的layout id都不完美。目前EFI使用的layout id 是11，插耳机不行。如需要插耳机使用，请更改layout id为57，此ID外放只有左声道，其他正常。

## 四、已解决问题

1. 以太网插上不识别，已通过更新网卡驱动解决。

## 五、可能会用到的链接和注意
1. [OpenCore引导使用AppleALC修复音频声卡驱动](http://imacos.top/2020/04/23/1004-3/)
2. 如需修改声卡ID，Mac环境下请使用 28 版本的OC configurator编辑config.plist

## 六、感谢
1. 第一次安装macOS Catatlina 10.15.7通过 [此仓库的EFI](https://github.com/thinhnpptit/hackintosh-OC-catalina-dell-7566-i5) 安装成功。

2. 本仓库仅对 [此仓库](https://github.com/worship76/dell7559_Hackintosh_BigSur) 简单修改，感谢分享。

## 七、Todolist

* 目前是oc0.6.6引导，想折腾升级到最新的0.7.3
* 通过在Windows下查询发现触摸板是I2C接口的，有时间会折腾下
* 美化下启动界面（抄袭下大佬的）

  
