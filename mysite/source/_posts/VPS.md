---
title: VPS上的l2tp和pptp搭建
date: 2016-10-20 01:18:00
tags: [代码,VPS,l2tp,pptp]
categories: '代码'
description: 针对Debain搭建VPN步骤总结。
---
最近买了[BuyVM](https://buyvm.net/)的VPS，因为情有独钟，所以装载的依然是Debain7。兴冲冲地在网上立马搜索“Debian搭建VPN”，得到PPTP的搭建步骤，总结如下.

## PPTP篇

### 安装pptpd

``` ruby
apt-get install pptpd
```

### 编辑配置文件

``` python
vi /etc/pptpd.conf
```

找到最下面，修改ip：

``` python
localip 你的主机外网ip
remoteip 10.100.0.2-10
```

第二行为分配的ip段，可自行设定 

### 设置DNS
``` python
vi /etc/ppp/pptpd-options
```

修改以下部分为google的dns

``` python
ms-dns 8.8.8.8
ms-dns 8.8.4.4
```

### 设置账号

``` python
vi /etc/ppp/chap-secrets
```

添加一行，依次为：用户名，服务，密码，限制ip

``` python
"user" pptpd "user" 
```

也可以pptp设为 “ * ” ，不限制任何服务

### 重启服务

``` python
/etc/init.d/pptpd restart
```

### 设置IP转发

打开这个文件

``` python
vi /etc/sysctl.conf
```

去掉文件中这一行的注释

``` python
net.ipv4.ip_forward=1
```

使它立刻生效

``` python
sysctl -p
```

### 建立一个 NAT

``` python
iptables -t nat -A POSTROUTING -s 10.100.0.0/24-o eth0 -j MASQUERADE
```

将规则保存，使重启后规则不丢失

``` python
iptables-save >/etc/iptables-rules
```

编辑网卡文件，加载网卡时自动加载规则

``` python
vi  /etc/network/interfaces
```

末尾加入

``` python
pre-up iptables-restore </etc/iptables-rules
```

至此，Android、iOS、Win都可以科学上网的！但是！苦逼地却发现MAC os居然取消了PPTP连接！所以，我们还需要再配置一下L2TP服务，便于在MAC os的科学上网。


## L2TP篇

### 安装 OpenSwan
 
安装基本环境

``` python
apt-get install build-essential
```

安装依赖包
 
``` python
apt-get install libgmp3-dev gawk flex bison
```

下载openswan

``` python
wget http://www.openswan.org/download/openswan-2.6.35.tar.gz
``` 

解压安装

``` python 
tar xzvf openswan-2.6.35.tar.gz
cd openswan-2.6.35
make programs
make install
```
 
备注：你可以访问 [OpenSwan](https://www.openswan.org/ ) 官方网站看看有没有更新的版本。
 
### 编辑 IPSec
OpenSwan 是用来建 IPSec 的，而 IPSec 是用来建 L2TP 的。

``` python
vi /etc/ipsec.conf
```

回车，输入 "dG" 删除所有内容，按 "i" 键，然后复制并粘贴以下内容

``` python
version 2.0
config setup
    nat_traversal=yes
    virtual_private=%v4:10.0.0.0/8,
    %v4:192.168.0.0/16,
    %v4:172.16.0.0/12,
    %v4:25.0.0.0/8,
    %v6:fd00::/8,
    %v6:fe80::/10
    oe=off
    protostack=netkey
 
conn %default
    forceencaps=yes
 
conn L2TP-PSK-NAT
    rightsubnet=vhost:%priv
    also=L2TP-PSK-noNAT
 
conn L2TP-PSK-noNAT
    authby=secret
    pfs=no
    auto=add
    keyingtries=3
    rekey=no
    ikelifetime=8h
    keylife=1h
    type=transport
    left=你的主机外网ip
    leftprotoport=17/1701
    right=%any
    rightprotoport=17/%any
```

### 输入ipsec密钥

``` python
vi /etc/ipsec.secrets
```

``` python
你的主机外网ip %any: PSK "你想设置的密钥"
``` 

输入以下命令

``` python
for each in /proc/sys/net/ipv4/conf/*
do
echo 0 > $each/accept_redirects
echo 0 > $each/send_redirects
done
```
 
每一行都要回车。
 
重启ipsec

``` python
service ipsec restart
```
 
验证ipsec
 
``` python
ipsec verify
```

### 安装 L2TP
 
``` python
apt-get install xl2tpd
```

配置l2tp

``` python 
vi /etc/xl2tpd/xl2tpd.conf
```

``` python 
[global]
; listen-addr = 192.168.1.98
 
[lns default]
ip range = 10.1.1.2-10.1.1.255
local ip = 10.1.1.1
require chap = yes
refuse pap = yes
require authentication = yes
name = LinuxVPNserver
ppp debug = yes
pppoptfile = /etc/ppp/options.xl2tpd
length bit = yes
```
 
设置DNS

``` python
vi /etc/ppp/options.xl2tpd
```

``` python 
require-mschap-v2
ms-dns 8.8.8.8
ms-dns 8.8.4.4
asyncmap 0
auth
crtscts
lock
hide-password
modem
debug
name l2tpd
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
```

设置你的用户名和密码

``` python
vi /etc/ppp/chap-secrets
```

``` python 
username l2tpd password *
```
 
重启l2tp

``` python
service xl2tpd restart
```

### IP 转发
这个步骤将使你的 VPN 连接整个互联网。
 
``` python
vi /etc/sysctl.conf
```

找到 " #net.ipv4.ip_forward=1 " 这一行，删除注释#。
 
使转发生效

``` python
sysctl -p
```

回车，如果一切正常，你将会只看到以下结果

``` python 
net.ipv4.ip_forward = 1
```

输入以下命令

``` python 
iptables -t nat -A POSTROUTING -s 10.1.1.0/24 -o eth0 -j MASQUERADE
```
 
回车之后，你就可以连接自己的 L2TP/IPSec VPN 翻墙了，但是如果你重启 VPS 的话，就需要重新执行一次 iptables 命令，并重启 ipsec，为了避免这些，你只需要输入以下命令
 
``` python 
vi /etc/rc.local
```

并在 "exit 0" 这一行之前粘贴以下内容就可以了

``` python 
for each in /proc/sys/net/ipv4/conf/*
do
echo 0 > $each/accept_redirects
echo 0 > $each/send_redirects
done
iptables -t nat -A POSTROUTING -s 10.1.1.0/24 -o eth0 -j MASQUERADE
/etc/init.d/ipsec restart
```

最后，送给大家写的一键安装L2TP的小脚本：[点我下载](http://oqt2eqc1u.bkt.clouddn.com/L2TP.sh)