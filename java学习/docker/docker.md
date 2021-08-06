教程

- 编程不良人b站的docker视频
- [github上的教程](https://github.com/yeasy/docker_practice/blob/master/install/centos.md)

# 什么是docker

- 应用容器技术：将环境打包在容器中，在别的机器上就无需考虑环境的问题了。（如：mysql容器，redis容器）
  - 会将应用程序和环境一起打包
- 容器隔离 进程隔离

# docker与虚拟机

![1](img\docker与虚拟机.png)

## 虚拟机缺点

- 虚拟机运行程序必须使用自带操作系统，会使一个小程序变得臃肿
- 虚拟内存 》虚拟物理内存 》 物理内存

## docker的优点

- 不携带操作系统
- 虚拟内存 》 物理内存

# CentOS7下安装docker

```shell
//使用脚本命令安装
$ curl -fsSL get.docker.com -o get-docker.sh
$ sudo sh get-docker.sh --mirror Aliyun

//查询状态,开启，重启docker（ctl control）
$ systemctl status | start | restart docker

//查询docker信息
$ docker info

//配置docker自启动
$ systemctl enable docker

//建立docker用户组，并将当前用户加入（super user do）
$ sudo groupadd docker
$ sudo usermod -aG docker $USER

//重启


```

# 核心概念&架构图

<img src="img/核心概念&架构图.jpg" alt="核心概念&架构图" style="zoom: 200%;" />

# 下载加速





![](img/下载加速.jpg)

# 入门案例

docker run hello-world

![入门案例](img/入门案例.jpg)



# 镜像操作

![](img/镜像操作.jpg)



# 容器基本操作

![](img/容器基本操作1.jpg)

![](img/容器基本操作2.jpg)