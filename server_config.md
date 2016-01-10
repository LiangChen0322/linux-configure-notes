#服务器配置
##服务器网络配置
系统安装过程中如果没有配置网络需要在安装完成以后进行配置。
修改配置文件：
```
# vi /etc/sysconfig/network-scripts/ifcfg-eno1
```

启用修改：
```
# systemctl restart network
```

查看IP地址：
```
# ip addr
```

重装系统以后无法使用SSH登陆。
服务器重新安装ssh-server：
```
# yum install ssh-server -y
```

删除本地ssh文件：
```
# rm ~./ssh/known_hosts
```

## 升级内核

http://elrepo.org/tiki/tiki-index.php

Centos 7暂时无法升级长期支持版内核，可以查看下面的网页：
http://elrepo.org/tiki/kernel-lt

```
rpm --import https://www.elrepo.org/RPM-GPG-KEY-elrepo.org
rpm -Uvh http://www.elrepo.org/elrepo-release-7.0-2.el7.elrepo.noarch.rpm
yum --enablerepo=elrepo-kernel install kernel-ml
```

```
awk -F\' '$1=="menuentry " {print $2}' /etc/grub2.cfg
CentOS Linux (3.18.3-1.el7.elrepo.x86_64) 7 (Core)
CentOS Linux, with Linux 3.10.0-123.el7.x86_64
CentOS Linux, with Linux 0-rescue-893b160e363b4ec7834719a7f06e67cf

grub2-set-default 0
```
