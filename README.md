# RSSman X

![logo](./.github/logo.png)

![author](https://img.shields.io/badge/author-Colin-blue)
![license](https://img.shields.io/github/license/Colin-XKL/RSSmanX)
![release](https://img.shields.io/github/v/release/Colin-XKL/RSSmanX)
![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2FColin-XKL%2FRSSmanX.svg?type=shield)
![Open Source Love](https://badges.frapsoft.com/os/v2/open-source.svg?v=103)

**RSSman X is a project that composed several useful services to help you build an excellent RSS experience.**

[中文说明](https://github.com/Colin-XKL/RSSmanX/blob/master/README-zh_cn.md) ｜ English


# Description

Get drown in modern Internet life? You may need RSS to take you out of the information sea. RSS is an old tech developed in 1990s. But it is a good tool to help you away from the unnecessary information and distraction on the Internet.

Most of the websites have already dispose RSS support because you can read their article without accessing to their website, so that they cannot get money by their advertisements. We should pay for those high-quality articles, but most of the time we just want to check for news and we do not want to waste time on those advertisement, clicking and redirecting. Save time, keep focus, use RSS.

This project contains several services that can help you build your own RSS workflow.

# Installation

## Preparations

To deploy RSSman X, you need to have a server that can host services that relevant with RSS. A Linux cloud server is recommended. Server with other operating system is OK as long as it can run docker🐋.

In this document, I will take a Tencent cloud server with Ubuntu 18.04 as an example.

## Requirements

- docker
- docker-compose

If you have no idea installing these, below is an example. _(for Ubuntu only)_

**To install docker**

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

**To install docker-compose**

```bash
sudo apt install docker-compose
```

For full installation document, please go to 📕

- https://docs.docker.com/engine/install/
- https://docs.docker.com/compose/install/

## How to install

1. install requirements like `docker` and `docker-compose`
2. clone this repository
3. cd into the folder
4. run `sudo docker-compose up -d`
5. wait until the program done

The first time you run the installation command may take you an unexpecting long time, because your server need to download some files. But don't worry, the command line output will tell you the progress. Normal installation should be finished in 15 minutes. Or you need to check your network and your server.

# Usage

Once the installation is done, you can visit `http://YOUR_SERVER_IP:777` to visit Tiny Tiny RSS login page. Use the default user `admin` and default password `password` to log in. **REMEMBER TO CHANGE YOUR PASSWORD!**

And then you can add rss feeds that you interested. You can either read the article online using the tiny tiny rss reader or you can go to a ttrss client on other platforms. For example, you can use `FeedMe` app on android to read your article and use `tiny Reader` on iOS/macOS.

Nowadays only few websites support RSS feed. For those websites that does not support RSS, you can go to https://docs.rsshub.app to find if there is a third-party rss service available. If the website your interested is supported by rsshub, you can subscribe the website by using rss feed by rsshub or use the self-hosted rsshub that you just created. Just replace the link from rsshub like from `https://rsshub.app/*` to `http://rsshub/*`

## Trouble shooting

### Common problems

**1. Cannot open default login page**  
Check your firewall and make sure you have allowed the port 777. If you changed the default port in the yml file, please also allow the port in your firewall. Besides, a wrong `SELF_URL` value may cause this error too.

### Note

This project only does tiny work as I just composed several services that developed by others. And most of problems may not cause by this program. The program in this repository just aims to help you quickly install all these services. All the problems except for installation have no matter with this project. You should refer to the original repository.

**For Tiny tiny RSS problems:**  
https://tt-rss.org/wiki.php  
http://ttrss.henry.wang/

**For RSShub problems:**  
https://docs.rsshub.app/en/faq.html

**For Huginn problems:**  
https://github.com/huginn/huginn#readme

## More Infomation

### Services and description

| Service       | Description                                                   | Necessary | Recommend |
| ------------- | ------------------------------------------------------------- | --------- | --------- |
| Tiny tiny RSS | A self hosted RSS service, manage all your feeds in one place | Yes       | Yes       |
| Mercury       | Get full-text RSS feeds                                       | No        | Yes       |
| OpenCC        | Convert Traditional Chinese to Simplified Chinese             | No        | -         |
| RSSHub        | Easily get RSS feed of various websites                       | No        | Yes       |
| Huginn        | Build your own RSS feed with great flexibility                | No        | -         |
| Watchtower    | Keep your programs up to date                                 | No        | Yes       |

### Differences among the standard, lite and ultimate version

| Name                   | Standard | Lite | Ultimate ✨ |
| ---------------------- | -------- | ---- | ----------- |
| TTRSS                  | ✅       | ✅   | ✅          |
| RSSHub                 | ✅       | ✅   | ✅          |
| Huginn                 |          |      | ✅          |
| Mercury                | ✅       |      | ✅          |
| OpenCC                 |          |      | ✅          |
| Redis                  | ✅       |      | ✅          |
| Browserless            |          |      | ✅          |
| Data persist storage   | ✅       | ✅   | ✅          |
| Container autoupdate   | ✅       |      | ✅          |
| Container health check | ✅       |      | ✅          |
| Global proxy           |          |      | ✅          |
| Smart routing          |          |      | ✅          |
|                        |          |      |             |

Different version of compose file have different file names.

**Standard version:** `docker-compose.yml`

**Lite version:** `docker-compose-lite.yml`

**ultimate version:** `docker-compose-ultimate.yml` and `config.yaml`

Choose the version you need and download the file, remember rename compose file to `docker-compose.yml` before you use it.

# Development

If you find bugs or have any good idea that can make this project better, feel free to open a Github issue or make a pull request. I'll reply you as soon as possible.

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
