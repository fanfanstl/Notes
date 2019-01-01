# 软件安装

## chrome的安装

```bash
sudo wget https://repo.fdzh.org/chrome/google-chrome.list -P /etc/apt/sources.list.d/
wget -q -O - https://dl.google.com/linux/linux_signing_key.pub  | sudo apt-key add -
sudo apt-get update
sudo apt-get install google-chrome-stable
```

##  pycharm的安装

```bash
下载：https://www.jetbrains.com/pycharm/download/#section=linux
	提取到当前目录下
	cd Downloads/pycharm-2017.1.4/bin
	sh ./pycharm.sh
	激活pycharm：
		vim /etc/hosts
		添加：将0.0.0.0 account.jetbrains.com添加到hosts文件最后
		然后填入激活码：							eyJsaWNlbnNlSWQiOiJLNzFVOERCUE5FIiwibGljZW5zZWVOYW1lIjoibGFuIHl1IiwiYXNzaWduZWVOYW1lIjoiIiwiYXNzaWduZWVFbWFpbCI6IiIsImxpY2Vuc2VSZXN0cmljdGlvbiI6IkZvciBlZHVjYXRpb25hbCB1c2Ugb25seSIsImNoZWNrQ29uY3VycmVudFVzZSI6ZmFsc2UsInByb2R1Y3RzIjpbeyJjb2RlIjoiSUkiLCJwYWlkVXBUbyI6IjIwMTktMDUtMDQifSx7ImNvZGUiOiJSUzAiLCJwYWlkVXBUbyI6IjIwMTktMDUtMDQifSx7ImNvZGUiOiJXUyIsInBhaWRVcFRvIjoiMjAxOS0wNS0wNCJ9LHsiY29kZSI6IlJEIiwicGFpZFVwVG8iOiIyMDE5LTA1LTA0In0seyJjb2RlIjoiUkMiLCJwYWlkVXBUbyI6IjIwMTktMDUtMDQifSx7ImNvZGUiOiJEQyIsInBhaWRVcFRvIjoiMjAxOS0wNS0wNCJ9LHsiY29kZSI6IkRCIiwicGFpZFVwVG8iOiIyMDE5LTA1LTA0In0seyJjb2RlIjoiUk0iLCJwYWlkVXBUbyI6IjIwMTktMDUtMDQifSx7ImNvZGUiOiJETSIsInBhaWRVcFRvIjoiMjAxOS0wNS0wNCJ9LHsiY29kZSI6IkFDIiwicGFpZFVwVG8iOiIyMDE5LTA1LTA0In0seyJjb2RlIjoiRFBOIiwicGFpZFVwVG8iOiIyMDE5LTA1LTA0In0seyJjb2RlIjoiR08iLCJwYWlkVXBUbyI6IjIwMTktMDUtMDQifSx7ImNvZGUiOiJQUyIsInBhaWRVcFRvIjoiMjAxOS0wNS0wNCJ9LHsiY29kZSI6IkNMIiwicGFpZFVwVG8iOiIyMDE5LTA1LTA0In0seyJjb2RlIjoiUEMiLCJwYWlkVXBUbyI6IjIwMTktMDUtMDQifSx7ImNvZGUiOiJSU1UiLCJwYWlkVXBUbyI6IjIwMTktMDUtMDQifV0sImhhc2giOiI4OTA4Mjg5LzAiLCJncmFjZVBlcmlvZERheXMiOjAsImF1dG9Qcm9sb25nYXRlZCI6ZmFsc2UsImlzQXV0b1Byb2xvbmdhdGVkIjpmYWxzZX0

```

## git的安装

```
https://blog.csdn.net/qq_38716242/article/details/79380825
```

## typora的安装

```bash
wget -qO - https://typora.io/linux/public-key.asc | sudo apt-key add -
sudo add-apt-repository 'deb https://typora.io/linux ./'
sudo apt-get update
sudo apt-get install typora
```

## shadowsockets客户端安装配置

```bash
参考：https://iaside.com/archives/269

安装：
apt-get install python-pip
pip install shadowsocks

# 配置
打开ubuntu中的设置->网络->网络代理->配置http代理和socks主机同为127.0.0.1 port：1080->应用到整个系统

创建/etc/shadowsockets.json配置文件：
{
    "server":"67.218.141.91",
    "server_port":443,
    "local_address":"127.0.0.1",
    "local_port":1080,
    "password":"663b11!!",
    "timeout":300,
    "method":"aes-256-cfb",
    "fast_open": true
}

# 启动服务
前台启动：
sslocal -c /etc/shadowsocks.json 
后台启动：
启动：sslocal -c /etc/shadowsocks.json -d start
停止: sslocal -c /etc/shadowsocks.json -d stop

```

## postman安装

```
Ubuntu 16.04 安装Postman：

1、官网下载地址：https://www.getpostman.com/根据机器类型选择64位下载。

2、进入下载目录，解压该文件sudo tar -xzf postman.tar.gz -C /opt/

3、进入解压目录，执行./Postman,软件就运行了，到此软件就安装完成了，但是这样每次都要进入这个目录，且启动器没有该应用；

4、创建全局变量，也就是在任何地方都可以执行postman，不用去到安装目录，执行
```

