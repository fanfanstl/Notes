## Shell 编程

---

一.shell 作用

命令解释器  （翻译官）

vim  /etc/shells

bash    

二.shell 常用功能

Tab自动补全

history  -c   清除历史

history  -w   写入文件  ~/.bash_history

调用历史命令

！string 

vim  /etc/profile

48 HISTSIZE=1000 

定义别名

1)vim  ~/.bashrc 

source ~/.bashrc 

2)alias   abc='history'    命令定义别名

abc

unalias  abc   删除别名

abc 

硬件交互

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml\wps892D.tmp.jpg)}�u<�K



重定向

输入重定向    wc  -l   <    install.log

输出重定向    ls   >   a.log       >>

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml\wps1132.tmp.jpg):�}U<�K ��



管道符 

netstat -an  |  grep  ESTABLISHED   |  wc  -l     统计已连接数量

三. Shell 变量的应用

set

abc=hello

echo $abc

unset abc

echo $abc



Var= lamp

echo $Var3.0

echo ${Var}3.0

从键盘输入内容为变量赋值

格式： read  [-p  "信息"] -t  30 变量名

```
#!/bin/bash
read -p "please input num1:" -t 30  test1
read -p "input num2:" -t 30  test2
declare -i sum=”$test1+$test2”
echo “num1 +  num2 = $sum”
```

设置变量的作用范围

格式：export   变量名...

​      export  变量名=变量值  [...变量名n=变量值n]

查看环境变量

​	 env 	或	 export

清除用户定义的变量

格式：unset   变量名

export A=/usr/local/nginx/sbin:$PATH

echo $A

echo $PATH

unset A

echo $A



系统环境变量

环境变量配置文件

全局配置文件：/etc/profile 

​		       /etc/bashrc

用户配置文件：~/.bash_profile

​			  ~/.bashrc



有完整登陆流程时，加载环境变量顺序

先读/etc/profile

再读~/.bash_profile

再读~/.bashrc

再读/etc/bashrc

开始Bash界面



```
环境变量
常见的环境变量：
 $USER 、$LOGNAME
 $UID 、 $SHELL 、$HOME
 $PWD、 $PATH 
 $PS1、$PS2
```



```
环境变量PS1
echo $PS1
		\d  日期	\t  时间（24）	\T时间（12）
		\H  完整主机名		\h  简写主机名
		\u  用户名			\v  bash版本
		\w  完整目录		\W  最后一个目录
		\#   执行了第几个命令	\$  提示符
PS1=‘[\u@\h  \W  \t  #\#]\$’
```



```
预定义变量 

表示形式如下
$#：命令行中位置参数的个数
$*：所有位置参数的内容
$?：上一条命令执行后返回的状态，当返回状态值为0时表示执行正常，非0值表示执行异常或出错
$$：当前所在进程的进程号
$!：后台运行的最后一个进程号
$0：当前执行的进程/程序名
```



xeyes &

jobs  查看系统运行任务（后台进程）

fg + 1  调用到前台

