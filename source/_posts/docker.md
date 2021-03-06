---
# 文章标题
title: Docker实战
# 文章创建时间
date: 2018-03-08 19:16:50
# 标签 可多选
tags: ["Docker"]
# 类别 可多选
categories: ["技术"]
# 右侧最新文章预览图
thumbnail: https://qiniu.caowencheng.cn/docker.png
# 文章顶部banner 可多张图片
banner: https://www.hdwallpapers.net/previews/winter-day-at-yosemite-national-park-971.jpg
---

<!-- ![docker 集装箱](https://qiniu.caowencheng.cn/docker.png "docker") -->

1.什么是Docker？
==============

>Docker 是一个开源的应用容器引擎，基于 Go 语言 并遵从Apache2.0协议开源。

>Docker 可以让开发者打包他们的应用以及依赖包到一个轻量级、可移植的容器中，然后发布到任何流行的 Linux 机器上，也可以实现虚拟化。

>容器是完全使用沙箱机制，相互之间不会有任何接口（类似 iPhone 的 app）,更重要的是容器性能开销极低。

<!--more-->

2.Docker应用场景
===============
> * Web 应用的自动化打包和发布。
> * 自动化测试和持续集成、发布。
> * 在服务型环境中部署和调整数据库或其他的后台应用。
> * 从头编译或者扩展现有的OpenShift或Cloud Foundry平台来搭建自己的PaaS环境。

3.Docker 的优点
==============
> * 简化程序：  
> Docker 让开发者可以打包他们的应用以及依赖包到一个可移植的容器中，然后发布到任何流行的 Linux 机器上，便可以实现虚拟化。Docker改变了虚拟化的方式，使开发者可以直接将自己的成果放入Docker中进行管理。方便快捷已经是 Docker的最大优势，过去需要用数天乃至数周的任务，在Docker容器的处理下，只需要数秒就能完成。
> * 避免选择恐惧症：  
> 如果你有选择恐惧症，还是资深患者。Docker 帮你打包你的纠结！比如 Docker 镜像；Docker 镜像中包含了运行环境和配置，所以 Docker 可以简化部署多种应用实例工作。比如 Web 应用、后台应用、数据库应用、大数据应用比如 Hadoop 集群、消息队列等等都可以打包成一个镜像部署。
> * 节省开支：  
> 一方面，云计算时代到来，使开发者不必为了追求效果而配置高额的硬件，Docker 改变了高性能必然高价格的思维定势。Docker 与云的结合，让云空间得到更充分的利用。不仅解决了硬件管理的问题，也改变了虚拟化的方式。


4.Docker build构建常用参数说明
============================

>  + -f：指定要使用的Dockerfile路径;
>  + -q：安静模式，成功后只输出镜像ID;
>  + --rm：设置镜像成功后删除中间容器;
>  + -t repo[:tag]：指定repo可选的tag.

```
例：docker build -t nginx .
```

5.Docker run运行常用参数说明
=========================
>  + -d：后台运行容器，并返回容器ID;
>  + -i： 以交互模式运行容器，通常与 -t 同时使用;
>  + -t： 为容器重新分配一个伪输入终端，通常与 -i 同时使用;
>  + --name： 为容器指定一个名称;
>  + -m： 设置容器使用内存最大值;
>  + -p： 将容器的端口映射到主机的端口(可携带参数 如80:80);
>  + -v： 将主机的目录映射到容器的(可携带参数 如/data:/data).

6.Dockerfile作用
===============
>Dockerfile是由一系列命令和参数构成的脚本，这些命令应用于基础镜像并最终创建一个新的镜像。它们简化了从头到尾的流程并极大的简化了部署工作。Dockerfile从FROM命令开始，紧接着跟随者各种方法，命令和参数。其产出为一个新的可以用于创建容器的镜像。


例：构建一个nginx镜像的Dockerfile
------------------------------
```
FROM nginx 
RUN mkdir -p /usr/share/nginx/html
WORKDIR /usr/share/nginx/html
COPY ./dist/index.html ./
COPY ./dist/static ./static
EXPOSE 80
```

例：启动一个nginx容器 宿主机端口:容器端口 
-----------------------------------

```
docker run -d --name nginx-container -p 3333:80 nginx
```

>附：个人docker hub站点 <https://hub.docker.com/u/wensent/>