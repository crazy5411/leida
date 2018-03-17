# PUBG-Radar ![Imgur](https://i.imgur.com/WHUDRjh.png)


This is reproduced！

#### By engaging with this repository you explicitly agree with the terms of the Unlicense.

### Updated for Newest Patch

#Beware this is a ROUGH update

join us on [Discord for updates](https://discord.me/radarproject)

SDK Dumped by (legitnutty33) Thank You!


### Key Kinds
3级装备无法关闭始终显示

#### Item Filter:
* NUMPAD_1 -> 显示武器
* NUMPAD_2 -> 显示装备
* NUMPAD_3 -> 显示药物
* NUMPAD_4 -> 显示投掷物品
* NUMPAD_5 -> 显示配件
* NUMPAD_6 -> 显示瞄具
* NUMPAD_0 -> 过滤弹药

#### Zooms:
* NUMPAD_8 -> Looting小视距搜刮 - Combat中视距战斗 -Scouting大视距侦查
* NUMPAD_PLUS ->  Camera Zoom ++相机距离
* NUMPAD_MINUS -> Camera Zoom --相机距离

#### Other
* F1 -> 更改玩家信息（名称，距离，HP，武器）
* F2 -> 切换指南针
* F3 -> 指示线 (100m)
* F4 -> 切换视图线
* F5 -> 切换车辆（图标，名称或两者都有）
* F12 -> 切换视图线


## 如何：构建，安装和运行PUBG雷达
https://youtu.be/H_gud8xuP-s

### 在线模式:
`java -jar target\pubg-radar-1.0-SNAPSHOT-jar-with-dependencies.jar "Middle PC IP" PortFilter "Game PC IP"`

### 离线模式:
You can replay a PCAP file in offline mode:

`java -jar target\pubg-radar-1.0-SNAPSHOT-jar-with-dependencies.jar "Middle PC IP" PortFilter "Game PC IP" Offline`


## Build

1. 安装Maven
2.将Maven添加到您的环境路径，下面截图。
3.添加MAVEN_OPTS环境变量，截图如下。
4.安装JDK8
5.将JAVA_HOME添加到您的环境路径中，屏幕截图如下。
6.使用命令提示符转到您的VMRadar目录（使用src文件夹）
7.输入mvn verify install命令提示符。
#### 你可以找到关于如何运行Maven项目的详细说明 [here](https://maven.apache.org/run.html)

[IntelliJ IDEA](https://www.jetbrains.com/idea/?fromMenu)

#### MAVEN_OPTS
![Imgur](https://i.imgur.com/aWCdgUX.png)

#### Path (Java and Maven)（可以百度配置java方法）
![Imgur](https://i.imgur.com/hSCYrCM.png)

#### JAVA_HOME（可以百度配置java方法）
![Imgur](https://i.imgur.com/4zT1YNR.png)

## Install

### VM

1. Install Virtual Box
2. Install Virtual Box Extension Pack ( https://download.virtualbox.org/virtualbox/5.2.6/Oracle_VM_VirtualBox_Extension_Pack-5.2.6-120293.vbox-extpack )
3. Install Windows 7  x64 (64 bit) (!!!NOT Windows 10!!!) on the VM (recommended: 2gb ram, 16gb storage, 2 processors)
Recommended: https://softlay.net/operating-system/windows-7-all-in-one-iso-free-download-32-64-bit.html
Use Windows 7 ultimate when installing
4. Install https://www.winpcap.org/install/ and https://www.microsoft.com/en-us/download/details.aspx?id=48145 on the VM
5. Install .Net framework 4.5: https://www.microsoft.com/en-us/download/details.aspx?id=30653
6. Go to settings of your VM, go to network, set attached to: 'Bridged adapter' and set promiscuous mode: 'Allow all'
7. Go to settings of your VM, go to video, set video memory to max and enable both acceleration checkboxes.
8. Run radar on VM.

#### No need to set up VPN using this method!

#### If you have OpenGL error try this:

1. Press windows + r
2. Type in msconfig and press enter
3. Go to 'boot' and check 'safe boot'
4. Apply/ok and restart VM (it will boot in safe mode)
5. Go to VirtualBox toolbar and go to Devices -> Insert Guest Additions CD image... https://linuxclub.cs.byu.edu/downloads/tools/virtualization/virtualbox/5.1.30/VBoxGuestAdditions_5.1.30.iso
6. Press Windows + E and open the CD drive for guest additions
7. Install, select Direct3D support when installing! Do not reboot after installation.
8. Go to msconfig, boot, disable safe boot and restart to normal windows

### 2nd PC

Download:
https://www.winpcap.org/install/

#### This is for PC/VM where your radar runs.
1. Go to command prompt (CMD) 
2. Type "ipconfig"
3. Write your IPv4 address and default gateway down
4. Use windows seacrh and look for ncpa.cpl
5. Go to your internet adapter properties and then IPv4 properties and then check "Obtain an IP address automatically" and also "Obtain DNS server address automatically"
6. Uncheck IPv6 and then just press OK
7. Then go back to ncpa.cpl (should already be open)
8. Press "alt" and go "File" from left top corner and there "New incoming connection"
9. Add someone and make sure to remember username and password then go next
10. check "Through the internet" then go next
11. Go to IPv4 properties and make sure "Network access" is checked
12. Under "IP address assignment" Check "Specifiy IP Addresses" 
13. Use your Default Gateway, to create a proper IP range for "Specify IP addresses" Example: gateway is 192.168.0.1, use 192.168.0.2 to 192.168.0.10 for the ip range. Then select "OK" 
14. Select "Allow access" and now we can move to our PUBG pc where we will play our games.

#### This is for PC where your PUBG runs.
1. For this computer also search for ncpa.cpl
2. Go to your internet adapter properties and check "Obtain an IP address automatically" and also "Obtain DNS server address automatically"
3. Uncheck IPv6 and press OK
4. Go to your "Network & Internet" settings
5. Go to "VPN" and from there "Add a VPN connection"
6. These setting are recommended: 
VPN Provider: Windows (build-in)
Connection name: random
Server name or address: This is the IPv4 address that you wrote down first
VPN Type: automatic
User and Password as the ones you created earlier and now click save.

Now try to connect to your VPN and if it succeeded you are ready to go

#### Some image for both methods: https://docs.google.com/document/d/1hrmnwMoVWmH7GTRwHEeOpGHgehKsETgJRQTacAtgIHQ

## Run
-----------------

```
@echo off
for /f "tokens=14" %%a in ('ipconfig ^| findstr IPv4') do set _IPaddr=%%a
echo YOUR IP ADDRESS IS: %_IPaddr%
echo "RUNNING VMRADAR"
set /p game=ENTER GAMEVM IP:
echo "%game%"
java -jar target\pubg-radar-1.0-SNAPSHOT-jar-with-dependencies.jar %_IPaddr% PortFilter "%game%"
```
or

```
@echo off
for /f "tokens=14" %%a in ('ipconfig ^| findstr IPv4') do set _IPaddr=%%a
java -jar target\pubg-radar-1.0-SNAPSHOT-jar-with-dependencies.jar %_IPaddr% PortFilter %_IPaddr% Offline

```
