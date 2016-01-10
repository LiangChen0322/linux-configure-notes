
##openJDK配置
###Ubuntu配置方法
1、下载安装jdk
```
$sudo apt-get install openjdk-7-jdk
```
2、查看当前系统中的JVM
```
$sudo update-alternatives --display java
```
3、安装JVM路径
```
$sudo update-alternative s --install /usr/bin/java java /usr/lib/jvm/java-1.7.0-jdk/bin/java 60
```
4、更换系统 JVM
```
$sudo update-alternatives –config java
```
5、配置环境变量
```
$vim /etc/profile
```
添加以下几行：
```    
export JAVA_HOME=/usr/lib/jvm/java-1.6.0-openjdk
export JRE_HOME=$JAVA_HOME/jre  
export CLASSPATH=.:$JAVA_HOME/lib:$JRE_HOME/lib:$CLASSPATH  
export PATH=$JAVA_HOME/bin:$JRE_HOME/bin:$JAVA_HOME:$PATH

$source /etc/profile 使配置立刻生效
```
6、验证配置完成
```
$echo $JAVA_HOME
$java -version
```
