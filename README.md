# [OpenWrt-Docker](https://github.com/SuLingGG/OpenWrt-Docker)

[![GitHub Stars](https://img.shields.io/github/stars/zzsrv/OpenWrt-Docker.svg?style=flat-square&label=Stars&logo=github)](https://github.com/zzsrv/OpenWrt-Docker/stargazers)
[![GitHub Forks](https://img.shields.io/github/forks/zzsrv/OpenWrt-Docker.svg?style=flat-square&label=Forks&logo=github)](https://github.com/zzsrv/OpenWrt-Docker/fork)
[![Docker Stars](https://img.shields.io/docker/stars/zzsrv/openwrt.svg?style=flat-square&label=Stars&logo=docker)](https://hub.docker.com/r/zzsrv/openwrt)
[![Docker Pulls](https://img.shields.io/docker/pulls/zzsrv/openwrt.svg?style=flat-square&label=Pulls&logo=docker&color=orange)](https://hub.docker.com/r/zzsrv/openwrt)

本项目旨在构建适用于x86_64(amd64) 平台设备的 OpenWrt 镜像 (每日更新)。

Github: <https://github.com/zzsrv/OpenWrt-Docker>

DockerHub: <https://hub.docker.com/r/zzsrv/openwrt>

## 支持设备及镜像版本

本项目基于 [immortalwrt: openwrt-23.05](https://github.com/immortalwrt/immortalwrt/tree/openwrt-23.05)，每日上午 8 点编译 OpenWrt 镜像，镜像构建完成后将同时推送到 [DockerHub](https://hub.docker.com/r/zzsrv/openwrt) 和 阿里云镜像仓库 (杭州) 。

对于国内用户，为提高镜像拉取体验，可以考虑拉取存放于阿里云镜像仓库的镜像，镜像名称及标签如下表所示:

### OpenWrt 标准镜像

OpenWrt 标准镜像为集成常用软件包的 Docker 镜像，镜像自带软件包可满足大多数情景下的使用需求。

|  支持设备/平台  |        DockerHub        |                  阿里云镜像仓库 (杭州)                  |
| :-------------: | :---------------------: | :-----------------------------------------------------: |
|  x86_64/amd64   | zzsrv/openwrt:latest | registry.cn-hangzhou.aliyuncs.com/zzsrv/openwrt:latest |
|  x86_64/amd64   | zzsrv/openwrt:x86_64 | registry.cn-hangzhou.aliyuncs.com/zzsrv/openwrt:x86_64 |
|  x86_64/amd64   | zzsrv/openwrt:amd64 | registry.cn-hangzhou.aliyuncs.com/zzsrv/openwrt:amd64 |


镜像详细使用方法请参考博客文章:

「在 Docker 中运行 OpenWrt 旁路网关」

<https://mlapp.cn/376.html>

## 鸣谢

SuLingGG/OpenWrt-Docker (本项目基于此项目修改):

<https://github.com/SuLingGG/OpenWrt-Docker>

P3TERX/Actions-OpenWrt (本项目基于此项目):

<https://github.com/P3TERX/Actions-OpenWrt>

ImmortalWrt OpenWrt Source:

<https://github.com/immortalwrt/immortalwrt>

OpenWrt Source Repository:

<https://github.com/openwrt/openwrt>

Lean's OpenWrt source:

<https://github.com/coolsnowwolf/lede>

CTCGFW's Team:

<https://github.com/project-openwrt>
