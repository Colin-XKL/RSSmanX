# RSSman X

![logo](./.github/logo.png)

![author](https://img.shields.io/badge/author-Colin-blue)
![license](https://img.shields.io/github/license/Colin-XKL/RSSmanX)
![release](https://img.shields.io/github/v/release/Colin-XKL/RSSmanX)
![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2FColin-XKL%2FRSSmanX.svg?type=shield)

[RSSman X](https://github.com/Colin-XKL/RSSmanX) 基于 docker-compsoe 提供容器化 TTRSS 与 RSSHUB 等组件的一键部署，整合实用组件为你带来最佳 RSS 体验

**Feature： 简单一键部署，常用组件支持，自动更新支持，服务健康自检支持，海外站点 RSS 解锁**

## 快速开始

(若已安装 `docker` 和 `docker-compose`)

```bash
mkdir RSSmanX && cd $_ && wget https://cdn.jsdelivr.net/gh/Colin-XKL/RSSmanX/docker-compose.yml && sudo docker-compose up -d
```

# 说明

本项目旨在为 RSS 的同好提供一个方便地搭建自己的 RSS 服务的捷径。毕竟不是所有 RSS 爱好者都懂代码 😂。如果你想快速地搭建自己的 RSS 服务，能够有 RSS 订阅管理、RSS 在线阅读界面，进阶功能包括服务健康自检、海外站点 RSS 解锁等。希望订阅国内外的各大网站的 RSS 信息源又不想跟着网上漫天飞的教程瞎折腾的话，那么你可以使用本仓库的脚本快速完成安装部署。

### 不同版本中包含的组件说明

三个版本的`docker-compose`文件对应不同的需求，包含的组件和服务有差异。

| 组件/服务/功能名称 | 标准版 | Lite 版 | Ultimate 版 ✨ |
| ------------------ | ------ | ------- | -------------- |
| TTRSS              | ✅     | ✅      | ✅             |
| RSSHub             | ✅     | ✅      | ✅             |
| Huginn             |        |         | ✅             |
| Mercury            | ✅     |         | ✅             |
| OpenCC             |        |         | ✅             |
| Redis              | ✅     |         | ✅             |
| Browserless        |        |         | ✅             |
| 数据持久化保存     | ✅     | ✅      | ✅             |
| 容器自动更新       | ✅     |         | ✅             |
| 容器健康检查       | ✅     |         | ✅             |
| 海外站点加速       |        |         | ✅             |
| 智能路由           |        |         | ✅             |
| 反反爬虫           |        |         | ✅             |


不同组件的功能描述见文末。不同版本对应的配置文件如下：

**标准版：**`docker-compose.yml`

**Lite 版：**`docker-compose-lite.yml`

**Ultimate 版：**`docker-compose-ultimate.yml`和`config.yaml`

选择对应版本下载到本地后都 compose 文件需要重命名为标准的`docker-compose.yml`才可使用

# 安装说明

## 需求

- 一台 Linux 系统的服务器

  > 本文以腾讯云 Ubuntu 18.04 系统的服务器为例，其他云服务商的没差，系统为 CentOS 的会有点差异

## 依赖项

- docker
- docker-compose

**安装 Docker**

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

- https://docs.docker.com/engine/install/
- https://docs.docker.com/compose/install/

## 如何安装

安装好了 `docker` 和 `docker-compose` 后可以执行文章开头的快速开始的指令。或者可以按照下面的步骤手动操作：

1. 确定安装好了 `docker` 和 `docker-compose`
2. 克隆本仓库/下载你所需要的版本的 compose 文件，注意修改文件名
3. cd 进入文件夹，编辑`docker-compose`文件，修改密码及 ttrss 的`SELF_URL`处的值
4. 运行 `sudo docker-compose up -d`
5. 等待程序跑完
6. 安装完成 ✅

#### 使用相关事宜：

1. 访问你设置的`SELF_URL`即可看到 Tiny Tiny RSS 的登陆页面，使用默认账户`admin`，密码`password`登陆即可开始使用。
2. 如开启海外站点解锁支持，第一次冷启动需要等待 3-5 分钟才能完全启动所有组件。
3. 数据保存位置 ~/.dockerData/Database/

详细配置和使用事宜请参考对应应用的文档说明。

- TTRSS 相关文档 [https://ttrss.henry.wang/](https://ttrss.henry.wang/)
- RSSHub 相关文档 [https://docs.rsshub.app/](https://docs.rsshub.app/)

## 功能模块介绍

**Tiny Tiny RSS**
RSS 订阅管理与在线阅读工具

**RSShub**
生成国内大部分网站的 RSS 信息源，同时自部署可以访问到那些严格防爬的站点的源（知乎、微博等）

**Huginn**
高级 IFTTT 工具，你可以用生成任何 RSS 源，但使用门槛略高

**Postgres**
数据库，用于存储 RSS 文章数据等。比 MySQL 更轻，性能更好

**OpenCC**
简繁体转换，如果你订阅了一些繁体的 RSS 源，可以用它来将文章转为简体

**Mercury**
用于获取 RSS 全文

**Browserless**
用于获取常规方式无法获取的网站 RSS，为 RSSHub 的可选组件

**Redis**
提供缓存，提升性能，为 RSSHub 的可选组件

**WatchTower**
用于自动更新 RSShub 等组件，可以更好地支持新添加的源以及更快的获得 bug 修复

**Clash**
智能路由与正向代理工具，用于解锁海外站点及提供海外 RSS 源的加速

# Acknowledgement

- [Tiny tiny RSS](https://tt-rss.org/)
- [OpenCC](https://github.com/BYVoid/OpenCC)
- [Mercury](https://github.com/postlight/mercury-parser)
- [Huginn](https://github.com/huginn/huginn)
- [RSShub](https://github.com/DIYgod/RSSHub)
- [Awesome TTRSS](https://github.com/HenryQW/Awesome-TTRSS)

# License

GPL-3.0


# Changelogs

- 2020-07-07 v1.0 First release
- 2020-07-14 v1.1 Update quick start shell script
- 2020-10-05 v1.2 Fix wrong environment variable.
- 2020-11-08 v1.3 TTRSS now can update feeds with ports except 80/443, and our self-hosted rsshub works again.
- 2020-11-13 v1.4 Several updates includes security and performance enhancements.
- 2020-11-24 v1.5 Lock the docker image version of some services to avoid unexpected errors.
- 2021-05-08 v2.0 Add container network isolation, health check, global proxy, smart routing etc.
- 2021-05-10 v2.1 Add rules for anti-anti-crawler, cloudflare etc.
- 2021-06-15 v2.5 Update route rules, and better container restart policy.
- 2021-08-14 v2.6 Optimize route rules
