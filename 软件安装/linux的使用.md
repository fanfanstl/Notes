# linux的使用

## 更改root密码

```bash
sudo passwd root
```

## 添加环境变量的三种方式

```
1、用于当前终端
export PATH="$PATH:/home/fand/下载/electronic-wechat-linux-x64"

2、用于当前用户
vim ~/.bashrc

在.bashrc中添加如下语句：
export PATH="$PATH:/home/fand/下载/electronic-wechat-linux-x64"

使文件生效：
source ~/.bashrc



3、用于所有用户
sudo vim /ect/profile

在profile中添加如下语句：
export PATH="$PATH:/home/fand/下载/electronic-wechat-linux-x64"

使文件生效：
source /etc/profile


```

