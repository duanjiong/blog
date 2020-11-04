---
title: "Docker 构建多架构镜像"
date: 2020-11-02T23:27:16+08:00
draft: true
---

## 背景

Docker始于Linux， 兴起于云计算浪潮之下， 目前为我们熟悉地数据中心服务器一般都基于X86架构，但是在中美贸易冲突日趋频繁地现状下， 国产化愈演愈烈。
目前由于专利等因素， 国产化服务器一般都基于ARM架构， 为此在适配国产化服务器地时候难免碰到要提供ARM版本地镜像。基本上要求类似如下图， 一个镜像可以包含多个架构。
![docker-porter-manager-multi-arch](/images/docker-porter-manager-multi-arch.png)

## 原理方案

Docker打包流程分为两步：
1. 编译目标文件
2. 基于基础镜像加上目标文件生成新地Layer

这里我们以arm64架构为例， 现在需要在linux amd64服务器上编译构建目标文件。 首先想到地就是交叉编译， 幸运地是Golang交叉编译支持很方便， 我们只需要设置
`GOOS`和`GOARCH`为目标系统以及架构， 这里就可以设置成`GOOS=linux GOOS=arm64`。
当然除了交叉编译之外， 我们也可以基于系统虚拟化来做：
1. 使用Qemu创建arm64的虚拟机
2. 使用Qemu User模拟
在编译目标文件的时候，如果使用上述两种方法模拟目标架构的话，时间会很长(因为他们都会进行软件指令模拟)，所以并不推荐。

这里为了加速构建出包， 所以我们先使用Golang本身的交叉编译， 后续再使用Docker的[buildx](https://docs.docker.com/engine/reference/commandline/buildx/)功能.

## 实战

```bash
export DOCKER_CLI_EXPERIMENTAL=enabled
docker run --rm --privileged multiarch/qemu-user-static --reset -p yes
docker buildx create --name mybuilder
docker buildx use mybuilder
docker buildx inspect --bootstrap
docker buildx build --platform linux/arm64,linux/amd64 -t *** . --push
```

## 参考
* [使用 buildx 构建多种系统架构支持的 Docker 镜像](https://yeasy.gitbook.io/docker_practice/buildx/multi-arch-images)
* [Getting started with Docker for Arm on Linux](https://www.docker.com/blog/getting-started-with-docker-for-arm-on-linux/)