# 方舟服务器搭建指南

**适合人群:你是个穷逼，租不起高性能的云主机(想自己开服和基友快乐)，但有一个配置还不错机子(主要内存要大，服务器不是特吃CPU)。此外还需要一个低配具有公网ip的云主机，用来转发流量，构建虚拟局域网及方舟集群服务器。**

****


# 本次测试数据只是作为各位小伙伴开服玩耍的参考，并非权威数据，不同环境下可能略有不同。本次测试未使用虚拟内存，无mod，无玩家进入地图，仅仅是启动服务器所需资源。

# windows服务器配置

- 系统: win11
- CPU: i7-10875H
- RAM: 32G + 32G 3200MHZ
- 硬盘: SSD 西数SN550 1TB
- 开服工具: ASM-1.1.412.4
- ARK服务器: 342.22

# 测试数据

## 1、ARK服务器文件所需硬盘空间约18.1GB

**注意：该文件夹下具有下表11个地图所需文件，以及存档，只需变换启动命令的地图参数即可启动其他地图**

**配置参数地址**
```
https://ark.fandom.com/wiki/Server_configuration#GameUserSettings.ini
```

### 地图列表
|地图名|地图名参数|
|--|--|
|孤岛|TheIsland|
|中心岛|TheCenter|
|焦土|ScorchedEarth_P|
|仙境|Ragnarok|
|畸变|Aberration_P|
|灭绝|Extinction|
|瓦尔盖罗|Valguero_P|
|创世纪1|Genesis|
|水晶岛|CrystalIsles|
|创世纪2|Gen2|
|迷失岛|LostIsland|

## 2、内存占用

### 地图列表
|地图名|服务器参数|内存|
|--|--|--|
|孤岛|TheIsland|约3600MB|
|中心岛|TheCenter|约3550MB|
|焦土|ScorchedEarth_P|约2960MB|
|仙境|Ragnarok|约4080MB|
|畸变|Aberration_P|约3440MB|
|灭绝|Extinction|约2990MB|
|瓦尔盖罗|Valguero_P|约3880MB|
|创世纪1|Genesis|约5380MB|
|水晶岛|CrystalIsles|约5800MB|
|创世纪2|Gen2|约11975MB|
|迷失岛|LostIsland|约6450MB|

## 3、启动命令

```
start "test" /normal "F:\asmdata\Servers\Server6\ShooterGame\Binaries\Win64\ShooterGameServer.exe" <地图名>?listen?MultiHome=192.168.43.208?Port=7777?QueryPort=27015?MaxPlayers=70?AllowCrateSpawnsOnTopOfStructures=True -NoBattlEye -nosteamclient -game -server -log
```


****

# 本次测试数据只是作为各位小伙伴开服玩耍的参考，并非权威数据，不同环境下可能略有不同。本次测试未使用swap分区，无mod，无玩家进入地图，仅仅是启动服务器所需资源。

# ubuntu服务器配置(虚拟机)

- 系统: ubuntu-20.04.3-server
- CPU: i7-10875H(最大4核)
- RAM: 15979.0 MIB
- ARK服务器: 342.22

# 测试数据

## 1、ARK服务器文件所需硬盘空间约19G

**注意：该文件夹下具有下表11个地图所需文件，以及存档，只需变换启动命令的地图参数即可启动其他地图**

**配置参数地址**

```
https://ark.fandom.com/wiki/Server_configuration#GameUserSettings.ini
```

### 地图列表

|地图名|地图名参数|
|--|--|
|孤岛|TheIsland|
|中心岛|TheCenter|
|焦土|ScorchedEarth_P|
|仙境|Ragnarok|
|畸变|Aberration_P|
|灭绝|Extinction|
|瓦尔盖罗|Valguero_P|
|创世纪1|Genesis|
|水晶岛|CrystalIsles|
|创世纪2|Gen2|
|迷失岛|LostIsland|

## 2、内存占用

### 地图列表

|地图名|服务器参数|内存|
|--|--|--|
|孤岛|TheIsland|约5530MIB(34.6%)|
|中心岛|TheCenter|约5065MIB(31.7%)|
|焦土|ScorchedEarth_P|约4570MIB(28.6%)|
|仙境|Ragnarok|约6103MIB(38.2%)|
|畸变|Aberration_P|约5160MIB(32.3%)|
|灭绝|Extinction|约4665MIB(29.2%)|
|瓦尔盖罗|Valguero_P|约5545MIB(34.7%)|
|创世纪1|Genesis|约7000MIB(43.8%)|
|水晶岛|CrystalIsles|约7320MIB(45.8%)|
|创世纪2|Gen2|约13700MIB(85.7%)|
|迷失岛|LostIsland|约7975MIB(49.9%)|

## 3、启动命令

```
./ShooterGameServer <地图名>?listen?ServerCrosshair=True?MapPlayerLocation=True?AllowThirdPersonPlayer=True?TheMaxStructuresInRange=100 -NoBattlEye
```


****

# Windows 搭建服务器

**下载地址**

```
https://github.com/Bletch1971/ServerManagers/tree/master/ASM
```


****


# ubuntu搭建方舟服务器

## 环境

- ubuntu-20.04

## 安装steamcmd

```
 # 32位

 sudo apt install steamcmd

 # 64位
 sudo add-apt-repository multiverse
 sudo dpkg --add-architecture i386
 sudo apt update
 sudo apt install lib32gcc-s1 steamcmd 
```

## 安装方舟

```
steamcmd +login anonymous +force_install_dir <安装目录> +app_update 376030 +quit
```

## 配置环境


**修改/etc/sysctl.conf**

```
sudo vim /etc/sysctl.conf
# 添加以下内容
fs.file-max=100000

sudo sysctl -p /etc/sysctl.conf
```

**修改/etc/security/limits.conf**

```
sudo vim /etc/security/limits.conf
# 添加以下内容
*               soft    nofile          1000000
*               hard    nofile          1000000
```

**修改/etc/pam.d/common-session**

```
sudo vim /etc/pam.d/common-session

# 添加以下内容
session required pam_limits.so
```


## 配置

参考以下链接

```
配置详情：https://ark.fandom.com/wiki/Server_configuration
在线配置生成工具：https://ini.arkforum.de/index.php?mode=all&lang=en

通过ASM开服工具生成，然后拷贝：https://github.com/Bletch1971/ServerManagers
```

## 启动

```

./ShooterGameServer TheIsland?listen?ServerCrosshair=True?MapPlayerLocation=True?AllowThirdPersonPlayer=True?TheMaxStructuresInRange=100 -UseBattlEye
```



****

# openvpn 搭建虚拟局域网

# 环境

- ubuntu-20.04-LTS
- openvpn客户端 下载地址
- 64位：http://www.npackd.org/p/openvpn64
- 32位：http://www.npackd.org/p/openvpn


## 安装

**方法1**

```
# 安装脚本地址
# 1.https://git.io/vpn
# 2.https://github.com/Nyr/openvpn-install

wget https://git.io/vpn -O openvpn-install.sh && bash openvpn-install.sh
```

**由于某些原因，方法1的wget可能下载不了**



## 配置文件

服务端配置文件

```
cd /etc/openvpn/server
vim server.conf
```

该配置转载自(https://www.vsay.net/mycode/141.html)

详细配置(https://www.vsay.net/mycode/142.html)

```
local 0.0.0.0 #OpenVPN监听本机的IP地址,如果不设置，则默认监听本机的所有IP地址
port 1194  #监听哪个TCP/UDP端口
proto udp #使用TCP或者UDP协议
dev tun   #OpenVPN创建的通信隧道类型
#导入各个证书
ca ca.crt
cert server.crt
key server.key
dh dh2048.pem  # 指定迪菲·赫尔曼参数。
server 10.8.0.0 255.255.255.0  # 设置服务器端模式，并提供一个VPN子网，以便于从中为客户端分配IP地址。
ifconfig-pool-persist ipp.txt  # 指定用于记录客户端和虚拟IP地址的关联关系的文件。
# 推送路由信息到客户端，以允许客户端能够连接到服务器背后的其他私有子网。
# (简而言之，就是允许客户端访问VPN服务器自身所在的其他局域网)
# 记住，这些私有子网也要将OpenVPN客户端的地址池(10.8.0.0/255.255.255.0)反馈回OpenVPN服务器。

push "route 192.168.10.0 255.255.255.0"  #这里可以按自己需求填写
push "route 192.168.20.0 255.255.255.0"

# 如果启用该指令，所有客户端的默认网关都将重定向到VPN，这将导致诸如web浏览器、DNS查询等所有客户端流量都经过VPN。
# (为确保能正常工作，OpenVPN服务器所在计算机可能需要在TUN/TAP接口与以太网之间使用NAT或桥接技术进行连接)
push "redirect-gateway def1 bypass-dhcp"
# 某些具体的Windows网络设置可以被推送到客户端，例如DNS或WINS服务器地址。
# 下列地址来自opendns.com提供的Public DNS 服务器。
;push "dhcp-option DNS 208.67.222.222"
;push "dhcp-option DNS 208.67.220.220"

keepalive 10 120  #每10秒钟ping一次，如果120秒内都没有收到对方的回复，则表示远程连接已经关闭
cipher AES-256-CBC  #密码加密算法
comp-lzo   #在VPN连接上启用压缩
client-to-client  #允许客户端之间互相访问
# 持久化选项可以尽量避免访问那些在重启之后由于用户权限降低而无法访问的某些资源。
persist-key
persist-tun

status openvpn-status.log   # 输出一个简短的状态文件，用于显示当前的连接状态，该文件每分钟都会清空并重写一次。
verb 3  #日志级别
# 服务器和每个客户端都需要拥有该密钥的一个拷贝。
# 第二个参数在服务器端应该为'0'，在客户端应该为'1'。
tls-auth ta.key 0 # 此项可不要
```

**最终配置(不唯一)**

```
local 10.0.4.6
port 40000
proto udp
dev tun
ca ca.crt
cert server.crt
key server.key
dh dh.pem
auth SHA512
tls-crypt tc.key
topology subnet
server 10.8.0.0 255.255.255.0
push "redirect-gateway def1 bypass-dhcp"
ifconfig-pool-persist ipp.txt
push "dhcp-option DNS 8.8.8.8"
push "dhcp-option DNS 8.8.4.4"
keepalive 10 120
cipher AES-256-CBC
# user nobody
# igroup nogroup
persist-key
persist-tun
verb 3
crl-verify crl.pem
explicit-exit-notify
client-to-client  #允许客户端之间互相访问
```


## 服务控制

```
# 停止服务
sudo systemctl stop openvpn-server@server
# 启动服务
sudo systemctl start openvpn-server@server

# 查看状态
sudo systemctl status openvpn-server@server
```


## 为客户端生成配置文件

**将配置文件(*.ovpn)拷贝到**

```
./openvpn-install.sh  #Add a new client 选择此项就会在当前目录下生成 ovpn 配置文件
```



****


# 端口转发

## 开启端口转发

### 1、临时有效、重启后失效

```
sudo su
echo 1 >/proc/sys/net/ipv4/ip_forward
```

### 2、永久生效

```
vim /etc/sysctl.conf
将net.ipv4.ip_forward=1前面的#注释去掉，保存文件。
然后执行sudo sysctl -p使其生效
```


## 端口转发

```
#! /bin/bash

# 迷失岛
iptables -t nat -A PREROUTING -p udp -m udp --dport 7777 -j DNAT --to-destination 10.8.0.2:7777
iptables -t nat -A PREROUTING -p udp -m udp --dport 7778 -j DNAT --to-destination 10.8.0.2:7778
iptables -t nat -A PREROUTING -p udp -m udp --dport 27015 -j DNAT --to-destination 10.8.0.2:27015
# 灭绝
iptables -t nat -A PREROUTING -p udp -m udp --dport 7779 -j DNAT --to-destination 10.8.0.2:7779
iptables -t nat -A PREROUTING -p udp -m udp --dport 7780 -j DNAT --to-destination 10.8.0.2:7780
iptables -t nat -A PREROUTING -p udp -m udp --dport 27016 -j DNAT --to-destination 10.8.0.2:27016
```

## 添加云主机防火墙规则


