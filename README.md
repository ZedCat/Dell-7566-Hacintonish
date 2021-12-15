# Dell-7566-Hacintonish-MacOs12

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

## 六、升级12记录

> 版本一

**根据B站Up主的视频整理的文字教程，未测试，有兴趣的小伙伴可以试一试。**

一、准备工作

**提示：所有操作均在MacOs环境下操作**

1. 下载最新稳定版的OC引导，[点我下载](https://github.com/acidanthera/OpenCorePkg)
2. 下载匹配稳定版的QtOpenCoreConfig，[点我下载](https://github.com/ic005k/QtOpenCoreConfig)。下载后拷贝粘贴到应用程序目录（有其他老版本的可以重命名以区别）
3. 下载propertree软件，[点我下载](https://github.com/corpnewt/ProperTree)

二、开干

1. 打开刚刚下载的QTOC软件，点击第一排蓝色数据库图标，双击sample.plist即可在桌面生成EFI文件夹（包含常用驱动）
2. 打开刚刚生成的模板EFI文件夹，删除以下内容
   - EFI/OC/Drivers目录下只保留三个`HFsPlus.efi` `OpenRuntime.efi` `OpenCanopy.efi`
   - EFI/OC/ACPI目录下全部删除

3. 点击QTOC第一排的硬盘图标挂载硬盘，拷贝以下内容
   - EFI/OC/ACPI目录下全部内容拷贝至模板EFI文件夹的对应位置
   - EFI/OC/KEXTS目录下的USB定制的驱动至模板EFI文件夹的对应位置，其他驱动需要在github上更新至最版本

4. 使用propertree打开目前正在使用的config.plist。点击file-new新建一个窗口。原窗口右键点击collaps all 折叠全部拷贝以下项目至新窗口
   - ACPI-Patch条目下所有内容
   - Kernel-Patch条目下的所有内容（可以新建一个条目改成dictionary再粘贴，防止混淆）
   - DeviceProperties-Add条目下的所有内容
   - PlatformInfo-Generic条目下的所有内容
5. 保存新窗口的内容至桌面，名称改为backup.plist（下次升级直接可以用），关闭所有ProperTree窗口
6. 使用ProperTree打开模板EFI文件夹内的config.plist做以下操作
   - 删除3条警告
   - 把backup.plist的内容拷贝至对应位置（一条一条进行，拷贝完后保存）

7. 使用QTOC打开模板EFI文件夹内的config.plist做以下操作
   - ACPI删除自带的，添加模板文件夹目录ACPI下的所有内容，选项-调整如下：[![oUdkBd.png](https://z3.ax1x.com/2021/12/03/oUdkBd.png)](https://imgtu.com/i/oUdkBd)
   - Booter-选项-调整如下：[![oUdFnH.png](https://z3.ax1x.com/2021/12/03/oUdFnH.png)](https://imgtu.com/i/oUdFnH)
   - Misc-引导-PickerModer改成Externel，-安全里面：vault 改成：optional ；ExposeSensitiveData：2；ScanPolicy：0；勾选allowNvramreset allowsetdefault
   - Nvram-boot-ars ：复制之前的参数即可； CSR：E7030000 ；KBD：类型改成string，值改成：zh-Hans-252
   - PI：右下角改成custom
   - UEFI-Drivers删除自带的，添加模板文件夹目录所有内容

8. 保存并修改错误

三、测试引导是否有问题

 	1. 把模板EFI文件夹拷贝至引导优盘测试是否可引导，引导通过后即可替换当前引导

四、更新

1. 检查更新，下载最新的系统。
2. 下载完会自动安装，右上角退出安装macos
3. 打开finder，应用程序，拷贝安装macosMonterey至U盘保存
4. 点击立即升级即可（双系统的需要提前把OC里的默认系统改成MacOS）

> 版本二

此版本是我自己想的，成功了。（懒人版）

前言：

当前的mac版本是11.6，OC的版本的0.73，已经定制了USB，想升级到最新的12.1，决定升级下OC和相关驱动。

一、准备工作

在[OC官网](https://dortania.github.io/OpenCore-Install-Guide/ktext.html) 下载相关驱动文件并解压

二、驱动更新

1. ACPI文件夹复制原来的即可
2. Drivers留下三个驱动`HfsPlus.efi` `OpenCanopy.efi` `OpenRuntime.efi`
3. Kext文件夹把下载好的新驱动全部复制
4. 复制一份新的config.plist对照的之前可以引导的把每项都设置一样

三、测试排错

1. 第一次报错i2c设备没屏蔽
2. 第二次开机很慢，中间有个提示`IOKit Daemon (Kernelmanager) stall[0], (60s) : 'IOUSBHostDevice'`查找原因是蓝牙驱动需要添加一个bluetoothfixup.kext的驱动，添加后屏蔽原来的IntelBluetoothInjector.kext即可

