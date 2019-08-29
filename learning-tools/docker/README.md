# 零基础入门 Docker
## Docker 目录

[TOC]

## Docker 前言

Docker 是什么？
Docker 是一个虚拟环境容器，可以将你的开发环境、代码、配置文件等一并打包到这个容器中，并发布和应用到任意平台中。具体查看 [Docker 官方文档](https://docs.docker.com/) 

## Docker 三个概念

* 镜像（Image）：类似于虚拟机中的镜像，是一个包含有文件系统的面向Docker引擎的只读模板。任何应用程序运行都需要环境，而镜像就是用来提供这种运行环境的。例如一个Ubuntu镜像就是一个包含Ubuntu操作系统环境的模板，同理在该镜像上装上Apache软件，就可以称为Apache镜像。

* 容器（Container）：类似于一个轻量级的沙盒，可以将其看作一个极简的Linux系统环境（包括root权限、进程空间、用户空间和网络空间等），以及运行在其中的应用程序。Docker引擎利用容器来运行、隔离各个应用。容器是镜像创建的应用实例，可以创建、启动、停止、删除容器，各个容器之间是是相互隔离的，互不影响。注意：镜像本身是只读的，容器从镜像启动时，Docker在镜像的上层创建一个可写层，镜像本身不变。

* 仓库（Repository）：类似于代码仓库，这里是镜像仓库，是Docker用来集中存放镜像文件的地方。注意与注册服务器（Registry）的区别：注册服务器是存放仓库的地方，一般会有多个仓库；而仓库是存放镜像的地方，一般每个仓库存放一类镜像，每个镜像利用tag进行区分，比如Ubuntu仓库存放有多个版本（12.04、14.04等）的Ubuntu镜像。

## Docker 安装与卸载

Docker可以安装在Windows、Linux、Mac等各个平台上。具体查看 [安装文档](<https://docs.docker.com/install/>)。

```
# 查看 Docker 信息
zhou@zhou-ubuntu:~$ sudo docker version
```

## Docker 国内安装源

* 阿里云 Docker 加速器

```
# 使用阿里云 Docker 专属加速器地址
zhou@zhou-ubuntu:~$ vim /etc/docker/daemon.json
{
    "registry-mirrors": ["https://zhou1995.mirror.aliyuncs.com"],
}
```

* 利用 docker-cn 镜像

```
# 使用 docker-cn 镜像地址
zhou@zhou-ubuntu:~$ vim /etc/docker/daemon.json
{
    "registry-mirrors": ["https://registry.docker-cn.com"],
}
```

> Notes: 注意需要重启 Docker 服务

```
sudo service docker restart
```

## Docker 镜像的基本操作

安装 Docker 完成后，可以对镜像进行基本操作

```
# 查看 ubuntu 镜像是否存在
zhou@zhou-ubuntu:~$ sudo docker search ubuntu
# 利用 pull 命令拉取镜像
zhou@zhou-ubuntu:~$ sudo docker pull ubuntu
# 查看所有镜像
zhou@zhou-ubuntu:~$ sudo docker images
# 提交修改后副本镜像
# docker commit -m "[message]" -a "[user]" [container-id/container-name] [user]/[image]:[tag]
zhou@zhou-ubuntu:~$ sudo docker commit -m "ubuntu with git" -a "zhou" 05536a7cd824 zhou/ubuntu:git
```

简易 Dockerfile 模板

```
# 基础镜像
# FROM [image]:[tag]
FROM ubuntu:latest

# 构建者的基本信息
# MAINTAINER [user] [email] [...]
MAINTAINER zhou

# 构建这个镜像时执行的操作
# RUN <command>
RUN apt update
RUN apt install git

# 拷贝本地文件到镜像中
COPY ./* /data/
# 或者
ADD  ./* /data/
```

利用 Dockerfile 构建镜像

```
# docker build -t [user]/[image]:[tag]
zhou@zhou-ubuntu:~$ sudo docker build -t "zhou/ubuntu:git"
```

镜像的其他基本操作

```
# 删除镜像
# docker rmi [image-id]
zhou@zhou-ubuntu:~$ sudo docker rmi e935c8b9f0f0
# 保存镜像
# docker save -o [output] [user]/[image]:[tag]
zhou@zhou-ubuntu:~$ sudo docker save -o ubuntu.git.tar zhou/ubuntu:git
# 加载镜像
# docker load -i [input]
zhou@zhou-ubuntu:~$ sudo docker load -i ubuntu.git.tar
```

## Docker 容器的基本操作

有了镜像之后，可以基于镜像启动容器。关于 run 命令，可以查看 [docker run 命令](<https://zhuanlan.zhihu.com/p/53260098>) 或者 [docker run 命令详解](<https://blog.csdn.net/yinni11/article/details/81559175>) 

```
# docker run -it [image]:[tag] [terminal]
zhou@zhou-ubuntu:~$ sudo docker run -it ubuntu:latest /bin/bash
zhou@zhou-ubuntu:~$ sudo docker run -d ubuntu:latest /bin/bash
# docker logs [container-id/container-name]
zhou@zhou-ubuntu:~$ sudo docker logs 05536a7cd824
```

> Notes: 第二条命令使用 -d 参数，使容器处于后台运行状态，不对当前终端产生任何输出
>
> Notes: 所有 stdout 输出至 logs，可以使用第三个命令查看



容器的其他基本操作

```
# 删除容器
# docker rm [container-id/container-name]
zhou@zhou-ubuntu:~$ sudo docker rm 05536a7cd824
# 启动容器
# docker start [container-id/container-name]
zhou@zhou-ubuntu:~$ sudo docker start 05536a7cd824
# 停止容器
# docker stop [container-id/container-name]
zhou@zhou-ubuntu:~$ sudo docker stop 05536a7cd824
# 重启容器
# docker restart [container-id/container-name]
zhou@zhou-ubuntu:~$ sudo docker restart 05536a7cd824
```

如果采取后台启动，可以通过 attach 命令进入容器

```
# docker attach [container-id/container-name]
zhou@zhou-ubuntu:~$ sudo docker attach 05536a7cd824
```

## Docker 参考

[10分钟看懂Docker和K8S](<https://zhuanlan.zhihu.com/p/53260098>) 

[只要一小时，零基础入门Docker](<https://zhuanlan.zhihu.com/p/23599229>) 