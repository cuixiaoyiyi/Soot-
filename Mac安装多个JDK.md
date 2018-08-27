
# JDK 历史版本

http://www.oracle.com/technetwork/cn/java/archive-139210-zhs.html

其中某些版本的 macOS 系统上自带 jdk1.6。如果没有的话，点击上面的链接从苹果官网下载，注意 oracle 官网不提供 jdk1.6 for macOS，只有 Linux 和 Windows 版本。

JDK 1.6 https://support.apple.com/kb/DL1572?locale=zh_CN

# 修改系统环境变量，以自如的切换多个版本的 jdk
```
vi ~/.bash_profile 并填写下文内容
source ~/.bash_profile // 刷新环境变量
java -version // 查看当前的 jdk 版本
```
需要填写的内容为：
```
# 设置自带的 jdk1.6
export JAVA_6_HOME=`/usr/libexec/java_home -v 1.6`
# 设置 jdk1.7
export JAVA_7_HOME=`/usr/libexec/java_home -v 1.7`
# 设置 jdk1.8
export JAVA_8_HOME=`/usr/libexec/java_home -v 1.8`

# 默认 jdk 使用1.6版本
export JAVA_HOME=$JAVA_6_HOME

# alias 命令动态切换 jdk 版本
alias jdk6="export JAVA_HOME=$JAVA_6_HOME"
alias jdk7="export JAVA_HOME=$JAVA_7_HOME"
alias jdk8="export JAVA_HOME=$JAVA_8_HOME"
```
