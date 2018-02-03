---
title: 使用Shadowsocks连接VPN
date: 2016-11-03 21:45:00
tags: [代码,VPN,Shadowsocks]
categories: '代码'
description: Shadowsocks搭建步骤总结。
photos:
---
前些天，折腾了如何使用PPTP和L2TP连接VPS：[传送门地址]({{"VPS/" | prepend: site.baseurl }})，但由于连接稳定等问题，被安利了Shadowsocks，今天再记录一下如何使用Shadowsocks连接VPS。

具体Shadowsocks的安装配置可以参考[官网地址](https://shadowsocks.org/en/index.html)中的教程,里面有详细的描述。

## 更新系统

``` python 
apt-get update
apt-get upgrade
```

## 安装python环境

``` python 
apt-get install python-pip
apt-get install python-m2crypto
```

## 使用pip安转Shadowsocks

``` python 
pip install shadowsocks
```

## 设置shadowsocks配置

``` python 
mkdir /etc/shadowsocks
vi /etc/shadowsocks/config.json
```

相应数据按自己实际情况修改

``` python
{
"server":"VPSip",
"server_port":端口,
"local_port":1080,
"password":"密码",
"timeout":600,
"method":"aes-256-cfb"
}
```

多用户配置

``` python 
{  
    "server":"your_server_ip",  
    "local_address": "127.0.0.1",  
    "local_port":1080,  
    "port_password":{  
         "8989":"password0",  
         "9001":"password1",  
         "9002":"password2",  
         "9003":"password3",  
         "9004":"password4"  
    },  
    "timeout":300,  
    "method":"aes-256-cfb",  
    "fast_open": false  
}  
```

## 运行

``` python 
ssserver -c /etc/shadowsocks/config.json -d start //后台启动
ssserver -c /etc/shadowsocks/config.json -d start //后台停止
```

如果觉得连接VPS的网速比较慢，请参考提速设置：[传送门](https://shadowsocks.org/en/config/advanced.html)


当然，最省事的方法，当然是一键安装了。

分享一个一键安装的[shell脚本](https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks.sh),安装脚本的配置文件路径为：/etc/shadowsocks.json。


启动：

``` python 
/etc/init.d/shadowsocks start  
```

停止：

``` python 
/etc/init.d/shadowsocks stop  
```

重启：

``` python 
/etc/init.d/shadowsocks restart
```

状态：

``` python 
/etc/init.d/shadowsocks status
``` 
 