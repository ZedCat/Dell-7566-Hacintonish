# Dell-7566-Hacintonish

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
| **OC版本** | **已更新至0.7.3** |

## 二、步骤

1. 1个已经写入过镜像的U盘。大神的们的教程很详细了，不知道可以点击 [传送门](https://blog.daliansky.net/) 
2. 使用DG进入U盘的EFI目录，删除原来，把我的EFI复制进去即可安装。具体步骤请参考大神的教程 [传送门](https://blog.daliansky.net/Lenovo-Tianyi-510s-Mini-and-macOS-BigSur-Installation-Tutorial.html) ，推荐新手看一遍，大神整理很多有用的东西，比如关闭mac的不允许打开未知来源的软件等。

## 三、已知问题

1. wifi影响蓝牙耳机的信号，表现为用蓝牙耳机听歌会断断续续，硬件问题无法解决。

## 四、其他
1. [OpenCore引导使用AppleALC修复音频声卡驱动](http://imacos.top/2020/04/23/1004-3/)

2. 允许打开任意来源软件： sudu spctl --master-disable

3. 安装 brew ,会安装git

   - 设置代理 ：
    ` export https_proxy=http://127.0.0.1:8889 http_proxy=http://127.0.0.1:8889 all_proxy=socks5://127.0.0.1:1089 `
   
   - 安装命令 
     ` /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)" `

4. 开机错误及解决
	遇到错误先别慌，打开前辈们留下的经验寻找答案。
	[黑苹果屋](http://imacos.top/2021/01/19/0154/)    大部分错误都能在此找到答案
	[黑苹果星球](https://heipg.cn/tutorial/opencore-install-errors-handbook.html)  我的一个I2c驱动错误就是在这里找到答案的
## 五、感谢
1. 第一次安装黑苹果是 **macOS Catatlina 10.15.7** 通过 [此仓库的EFI](https://github.com/thinhnpptit/hackintosh-OC-catalina-dell-7566-i5) 安装成功（感谢带我入坑：）
2. 本仓库之前版本仅对 [此仓库](https://github.com/worship76/dell7559_Hackintosh_BigSur) 简单修改，感谢分享。
3. 目前版本是根据官方教程自己配的（只定制了USB驱动，人品爆发，其他错误没遇到。）

## 七、Todolist

* ~~目前是oc0.6.6引导，想折腾升级到最新的0.7.3~~

* ~~美化下启动界面（抄袭下大佬的）~~

* 折腾下I2C触摸板驱动（放弃！！！）

* 升级12搞起！！！

  
