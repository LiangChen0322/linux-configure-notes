作为一名奋斗在当今社会的有志青年，我深深“感激”这个社会创造很多锻炼我们的机会，苦我心智，劳我筋骨。几番苦心也是很铁不成钢，为让我等象牙塔走出的一辈脱胎换骨，征召前辈筑起无形的长城，不断翻越方见井外洞天，不禁慨叹这世间的高山碧海，雄奇壮阔，终于略窥科学上网的真谛！

咳咳，不贫了，大家都懂，我来记录下Linux下科学上网的一些方法。

#科学上网一：ShadowSocks
---------------------

##Step 1 安装软件包

###Ubuntu / Debian

```
apt-get install python-pip
pip install shadowsocks
```

###CentOS:

```
yum install python-setuptools && easy_install pip
pip install shadowsocks
```

##Step 2 浏览器热身

首先chrome上安装SwitchyOmega插件，还好这个可以百度。

我不会告诉你这个在github上开源：https://github.com/FelisCatus/SwitchyOmega

可以直接下载：https://github.com/FelisCatus/SwitchyOmega/releases

##Step 3 弄个免费账号

可以看看这个：http://www.ishadowsocks.com/

内什么，这么搞不会又给墙了吧？

##Step 4 前戏做足

最简单的方法，命令行直接运行，以上面的连接获得的一个免费账号为例：
```
A服务器地址:	US1.ISS.TF
端口:		443
A密码:		08016733
加密方式:		AES-256-CFB
```

对应的命令是：
```
sslocal -s US1.ISS.TF -p 443 -l 1080 -k "08016733" -t 600 -m aes-256-cfb
```

其中，`-l 1080`是本地端口号可以根据需要自己设置，下面要用到。细节配置以后补充，不明白的话，使用`sslocal --help`查一下就知道了。

##Step 5 上房揭瓦

现在，在SwitchyOmega中增加一个Proxy Profile配置，Protocol设为`SOCKS5`，Server设置为`127.0.0.1`，port设置为上面的命令中设置的`1080`。

这里稍微解释一下，在Step 4中的命令，将本地的1080端口号作为代理服务器的转发端口，因此Server设置为120.0.0.1：1080。

##参考文章：
------------------

四号程序员：Linux下配置ShadowSocks(Server&Client)
http://www.coder4.com/archives/4361

Linux公社：Ubuntu下shadowsocks配置说明
http://www.linuxidc.com/Linux/2015-09/123579.htm

Ubuntu 14.04下shadowsocks-qt5的安装：
http://www.linuxdiyf.com/linux/13155.html

http://www.guance.com/611.html
