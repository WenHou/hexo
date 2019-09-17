---
title: 常用网络命令
date: 2019-09-01 11:43:34
tags:
---
# 本机端口查看
```
netstat -tunlp | grep 9000
netstat -ano | grep 443
netstat -anp | grep 443
lsof -i :443
```
# 远程通讯检查
```
telnet 180.101.49.12 443
openssl s_client -connect www.baidu.com:443 -msg
```
# 域名对应的 ip 地址
```
nslookup www.baidu.com
```
# 查看数据表提交远程系统所经历的 IP、跳数、响应时间
```
traceroute
tracepath
```
# 本机网卡
```
ethtool eth0 // 查看网卡eth0的工作方式，内容包括网卡的传输速度、全双工或半双工传输、网卡连接检测是否激活、网卡是否工作在自动协商状态等。
ethtool –s eth0 speed 10 duplex half   // 设置网卡eth0的传输速度为10M、半双工传输模式。
ethtool –s eth1 speed 100 duplex full autoneg off  // 设置网卡eth1的传输速度为100M、全双工、非自动协商模式。
```

# 重启指定网卡
```
ipup eth0
```
# 关闭指定网络设备
```
ifdown eth0
```
# 查看或修改指定网卡的通信协商方式。  
```
mii-tool // 以简明的形式显示本机物理网卡的工作方式。
mii-tool –v // 以详细的形式显示本机物理网卡的工作方式。
mii-tool -F 10baseT-FD eth0 // 设置网卡eth0工作在10M、全双工模式下。
mii-tool –r eth0 // 设置网卡eth0工作在自动协商工作模式。
mii-tool –w eth0 // 实时监控网卡eth0工作模式的改变。
```
# 查看或修改主机和网络的路由信息
```
route // 显示路由信息。
route add –host 192.168.1.110 dev eth0  // 给网卡eth0的路由表中加入新地址192.168.1.110。
route add –net 192.168.1.0 netmask 255.255.255.0 gw 192.168.1.1  // 给子网192.168.1.0添加路由和网关，新增加的路由和网关地址为192.168.1.1。
route add default gw 192.168.0.1  // 给路由表中添加默认网关地址192.168.0.1
route del –host 192.168.1.110 dev eth0    // 删除网卡eth0路由表中的地址192.168.1.110。
route del –net 192.168.1.0 netmask 255.255.255.0 // 在路由表中删除子网192.168.1.0的路由信息。
route change 192.168.1.0 mask 255.255.255.0 192.168.10.100   // 将子网 192.168.1.0 的下一跃点地址设置为 192.168.10.100。
```
# mtr
```
// 把ping命令和tracepath命令合成了一个。mtr会持续发包，并显示每一跳ping所用的时间。也会显示过程中的任何问题
```
# 输出指定站点的whois记录
```
whois baidu.com
`
% IANA WHOIS server
% for more information on IANA, visit http://www.iana.org
% This query returned 1 object

refer:        whois.verisign-grs.com

domain:       COM

organisation: VeriSign Global Registry Services
`
```
# 查看所有网络接口的状态，或是指定网络接口的状态
```
ifplugstatus
```
# 释放你的电脑的IP地址并从DHCP服务器上获得一个新的
```
dhclient -r
dhclient
```

# 抓包
```
tcpdump
```


