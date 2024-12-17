# [OpenWrt-Docker](https://github.com/zzsrv/OpenWrt-Docker)

[![GitHub Stars](https://img.shields.io/github/stars/zzsrv/OpenWrt-Docker.svg?style=flat-square&label=Stars&logo=github)](https://github.com/zzsrv/OpenWrt-Docker/stargazers)
[![GitHub Forks](https://img.shields.io/github/forks/zzsrv/OpenWrt-Docker.svg?style=flat-square&label=Forks&logo=github)](https://github.com/zzsrv/OpenWrt-Docker/fork)
[![Docker Stars](https://img.shields.io/docker/stars/zzsrv/openwrt.svg?style=flat-square&label=Stars&logo=docker)](https://hub.docker.com/r/zzsrv/openwrt)
[![Docker Pulls](https://img.shields.io/docker/pulls/zzsrv/openwrt.svg?style=flat-square&label=Pulls&logo=docker&color=orange)](https://hub.docker.com/r/zzsrv/openwrt)

OpenWrt-23.05 (PassWall & OpenClash)，基于ImmortalWrt OpenWrt-23.05(每日更新)。

Github: <https://github.com/zzsrv/OpenWrt-Docker>

DockerHub: <https://hub.docker.com/r/zzsrv/openwrt>

## 支持设备及镜像版本

本项目基于 [ImmortalWrt OpenWrt-23.05](https://github.com/immortalwrt/immortalwrt/tree/openwrt-23.05)，每日上午 8 点编译 OpenWrt 镜像，镜像构建完成后将同时推送到 [DockerHub](https://hub.docker.com/r/zzsrv/openwrt) 和 阿里云镜像仓库 (杭州) 。

对于国内用户，为提高镜像拉取体验，可以考虑拉取存放于阿里云镜像仓库的镜像，镜像名称及标签如下表所示:

### OpenWrt 镜像地址

|  支持设备/平台  |        DockerHub        |                  阿里云镜像仓库 (杭州)                  |
| :-------------: | :---------------------: | :-----------------------------------------------------: |
|  x86_64/amd64   | zzsrv/openwrt:latest | registry.cn-hangzhou.aliyuncs.com/zzsrv/openwrt:latest |
|  x86_64/amd64   | zzsrv/openwrt:x86_64 | registry.cn-hangzhou.aliyuncs.com/zzsrv/openwrt:x86_64 |
|  x86_64/amd64   | zzsrv/openwrt:amd64 | registry.cn-hangzhou.aliyuncs.com/zzsrv/openwrt:amd64 |
|  <del>armv8/aarch64</del>   | <del>zzsrv/openwrt:arm</del> | <del>registry.cn-hangzhou.aliyuncs.com/zzsrv/openwrt:arm64</del> |
|  <del>armv8/aarch64</del>   | <del>zzsrv/openwrt:armv8</del> | <del>registry.cn-hangzhou.aliyuncs.com/zzsrv/openwrt:armv8</del> |
|  <del>armv8/aarch64</del>   | <del>zzsrv/openwrt:aarch64</del> | <del>registry.cn-hangzhou.aliyuncs.com/zzsrv/openwrt:aarch64</del> |

## 镜像使用方法

1、打开网卡混杂模式，其中eth0根据ifconfig命令找到自己的本地网卡名称替换
```
sudo ip link set enp1s0 promisc on
```
2、创建名称为macvlan的虚拟网卡，并指定网关gateway、子网网段subnet、虚拟网卡的真实父级网卡parent（第一步中的本地网卡名称）
```
docker network create -d macvlan --subnet=192.168.0.0/24 --gateway=192.168.0.1 -o parent=enp1s0 macnet
```
3、查看虚拟网卡是否创建成功，成功的话能看到名称为“macnet”的虚拟网卡
```
docker network ls
```
4、拉取镜像，可以通过阿里云镜像提升镜像拉取速度
```
docker pull registry.cn-hangzhou.aliyuncs.com/zzsrv/openwrt:latest
```
5、创建容器并后台运行
```
docker run --restart always --name openwrt -d --network macnet --privileged zzsrv/openwrt /sbin/init
```
6、进入容器内部环境
```
docker exec -it openwrt bash
```
7、根据自己实际情况修改网络配置，修改完成后保存配置
```
vi /etc/config/network
```
8、退出容器内部环境，在宿主机环境执行重启容器命令
```
docker container restart openwrt
```

## 鸣谢

SuLingGG/OpenWrt-Docker:

<https://github.com/SuLingGG/OpenWrt-Docker>

ImmortalWrt OpenWrt Source:

<https://github.com/immortalwrt/immortalwrt>

P3TERX/Actions-OpenWrt:

<https://github.com/P3TERX/Actions-OpenWrt>

OpenWrt Source Repository:

<https://github.com/openwrt/openwrt>

Lean's OpenWrt source:

<https://github.com/coolsnowwolf/lede>
