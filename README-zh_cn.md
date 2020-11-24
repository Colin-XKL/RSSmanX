# RSSman X

![logo](./.github/logo.png)

![author](https://img.shields.io/badge/author-Colin-blue)
![license](https://img.shields.io/github/license/Colin-XKL/RSSmanX)
![release](https://img.shields.io/github/v/release/Colin-XKL/RSSmanX)
![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2FColin-XKL%2FRSSmanX.svg?type=shield)
![Open Source Love](https://badges.frapsoft.com/os/v2/open-source.svg?v=103)

**RSSman X 提供容器化 TTRSS 与 RSSHUB 等组件的一键部署**

## 快速开始

(若已安装 docker 和 docker-compose)

```bash
mkdir RSSmanX && cd $_ && wget https://cdn.jsdelivr.net/gh/Colin-XKL/RSSmanX/docker-compose.yml && sudo docker-compose up -d
```

# 说明

本项目旨在为 RSS 的同好提供一个方便地搭建自己的 RSS 服务的捷径。毕竟不是所有 RSS 爱好者都懂代码 😂。如果你想快速地搭建自己的 RSS 服务，能够有 RSS 订阅管理、RSS 在线阅读界面，还有订阅国内的各大网站的 RSS 信息源又不想跟着网上漫天飞的教程瞎折腾的话，那么你可以使用本仓库的脚本快速完成安装部署。

## 目前包括的功能模块

| 名称          | 功能说明                                                                                    | 默认启用 |
| ------------- | ------------------------------------------------------------------------------------------- | -------- |
| Tiny Tiny RSS | RSS 订阅管理与在线阅读工具                                                                  | True     |
| RSShub        | 生成国内大部分网站的 RSS 信息源，同时自部署可以访问到那些严格防爬的站点的源（知乎、微博等） | True     |
| Huginn        | 高级 IFTTT 工具，你可以用生成任何 RSS 源，但使用门槛略高                                    | False    |
| Postgres      | 数据库，用于存储 RSS 文章数据等。比 MySQL 更轻，性能更好                                    | True     |
| OpenCC        | 简繁体转换，如果你订阅了一些繁体的 RSS 源，可以用它来将文章转为简体                         | False    |
| Mercury       | 用于获取 RSS 全文                                                                           | True     |
| WatchToiwer   | 用于自动更新 RSShub 等组件，可以更好地支持新添加的源以及更快的获得 bug 修复                 | True     |


# 安装说明
## 需求
* 一台Linux系统的服务器  
> 本文以腾讯云Ubuntu 18.04系统的服务器为例，其他云服务商的没差，系统为CentOS的会有点差异

## 依赖项
* docker
* docker-compose
  
**安装Docker**
```bash
sudo apt-get update

sudo apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo 
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
```

**安装 docker-compose**
```bash
sudo apt install docker-compose
```

完整文档参见 📕
* https://docs.docker.com/engine/install/
* https://docs.docker.com/compose/install/


## 如何安装
安装好了docker和docker-compose后可以执行文章开头的快速开始的指令。或者可以按照下面的步骤：
1. 确定安装好了 `docker` 和 `docker-compose`
2. 克隆本仓库
3. cd 进入文件夹，编辑`docker-compose`文件，修改密码及ttrss的`SELF_URL`处的值
4. 运行 `sudo docker-compose up -d`
5. 等待程序跑完

# Acknowledgement
* [Tiny tiny RSS](https://github.com/DIYgod/RSSHub)
* [OpenCC](https://github.com/BYVoid/OpenCC)
* [Mercury](https://github.com/postlight/mercury-parser)
* [Huginn](https://github.com/huginn/huginn#readme)
* [RSShub](https://github.com/DIYgod/RSSHub)
* [Awesome TTRSS](https://github.com/HenryQW/Awesome-TTRSS)

# License
GPL-3.0 