# Docker使用

## 使用原则

- 镜像不可改变，容器初始都一样
- 容器中运行单个程序

## dockerHub使用

- 登录

  - sudo docker login

- 在docker中运行程序

  - ```bash
    sudo docker run ubuntu:14.04 /bin/echo 'Hello world'
    ```

- 交互式容器，进入容器中的bash

  - ```bash
    sudo docker run -t -i ubuntu:14.04 /bin/bash
    ```

- 以守护进程在docker中运行程序

  - ```bash
    sudo docker run -d ubuntu:14.04 /bin/sh -c "while true; do echo hello world; sleep 1; done"
    ```

- 停止容器

  - sudo docker stop insane_babbage

- 查看容器日志

  - ```bash
    sudo docker logs insane_babbage
    ```

- 查看容器内进程

  - sudo docker ps

- 获取镜像元数据

  - sudo docker inspect 容器id

- 查看docker容器内部进程情况

  - sudo docker top 容器id

- 进入交互模式

  - sudo docker exec -it 容器id /bin/bash

- 显示所有容器

  - sudo docker ps -a

- 显示所有镜像

  - sudo docker images

- 删除容器

  - sudo docker rm 容器id

- 待所有容器都被删除后才能删除有关镜像

  - sudo docker rmi 镜像id

  

  - 为容器起名字
    - sudo docker run --name 名字 容器名

- redis的使用：默认下载下来的是redis的server，自己手动下载redis客户端

  - 客户端安装：sudo apt install redis-tools
  - 连接redis redis-cli -h IP地址

- 文件映射

  - sudo docker run --name redis3 -v /data/redis:/data redis
  - 说明：-v 实现了文件映射   真实主机目录：容器目录

- 启动时加--rm 在停止容器时就被删掉了易于管理

  - sudo docker run --rm --name myredis redis

- 下载镜像

  - sudo docker pull 镜像名

- 搜索镜像

  - sudo docker search 镜像名称
  - 会出来各种版本的镜像

- 将一个容器打包成一个镜像

  - sudo docker commit -m "描述"  容器id 打包后镜像名字

# 自己制作一个镜像步骤

```python
#1、进入容器，装好环境然后快照
#2、Dockerfile
格式：
FROM python_django:3.6
RUN pip install scrapy

然后执行命令：
sudo docker build -t 新镜像名 .
```

- 给镜像重起名字
  - sudo docker tag 原名 现在名字
- 将文件移入/移出docker的容器中
  - 移入：docker cp /opt/test/file.txt 容器id：/opt/testnew/ 
  - 移出：docker cp 容器id：/opt/testnew/file.txt /opt/test/ 
  - 注意：不管容器有没有启动，拷贝命令都会生效

