---
typora-root-url: assets\
---

[TOC]

​	

# Docker学习

## docker简介

### 什么是容器？

虚拟化的方案

直接运行在操作系统的内核上  只能运行相同或相似内核的操作系统，所以只能运行linux类系统

![1567515975591](/1567515975591.png)

容器需要的空间更少

### 什么是Docker?

​	将应用程序自动部署到容器

### Doker的目标

提供轻量的建模方式

职责的逻辑分离（）

快速高效的开发生命周期   在容器开发测试，避免部署和调试开销

鼓励面向服务端架构  一个容器一个服务或应用程序

### Docker的应用场景

![1567516046999](/1567516046999.png)

### Docker的组成

Docker 镜像

层叠的只读文件系统

联合加载 （同时加载多个文件系统）



Dokcer Container 容器

通过镜像启动

写时复制



Docker 仓库

保存 用户创建的镜像

公有  Docker hub

私有 私人镜像

![1567516525816](/1567516525816.png)



### Docker容器相关技术简介

#### LInux特性 

#### 命名空间 -》资源隔离

#### Control group ->用来分配资源

1.资源限制

2.优先级设定 

3.资源计量 

4.资源控制  挂起、恢复进程组

Docker容器的能力

![1567517417427](/1567517417427.png)



## Docker安装

1.Ubuntu apt-get 安装

2.Docker官方维护的版本



## Docker操作

### 启动容器 

docker run Image [command] [arg]

docker start [-i交互式] 容器名

交互式容器 

docker run -i -t IMAGE /bin/bash



### 查看容器

docker ps [-a查看所有] [-l]

docker inspect 某个容器的详细信息 

自定义容器名字  （因为总是使用id太麻烦了）

docker run --name=

## 删除容器

docker rm 容器id

当需要长期运行的容器时，就需要守护式容器

docker attach 

### 守护容器

启动 docker run -d 镜像名 [command] [args]

停止  docker stop/kill



查看容器日志

![1567649313613](/1567649313613.png)

运行中容器：

查看进程      docker top 容器名

启动进程      docker exec 