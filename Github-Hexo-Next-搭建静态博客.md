---
title: Github+Hexo+Next 搭建静态博客
date: 2016-11-20 01:57:37
tags:
- Github
- Hexo
- Next
---
## 前言

先说说为什么要自己搭建博客吧

1. 没有广告
2. 想发什么随心，不用担心文章被删除
3. 丰富的可定制性与扩展性
4. 更个性的域名
5. 不用担心被封号，文章可随时倒出
6. ...

欢迎大家留言补充！

## 更新记录

2016-11-20 撰写初稿
2016-11-24 补充完善

## 配置 **Github**

{% blockquote Github https://guides.github.com/activities/hello-world/#what %}
GitHub is a code hosting platform for version control and collaboration. It lets you and others work together on projects from anywhere.
{% endblockquote %}

Github 是最著名的开源项目托管平台，本博客就是基于 Github 提供的静态页面功能搭建的，因为我的 Github 帐号申请的时间较早，基本就是拿来就用了，所以先挖个坑，详细的注册、创建静态页面、绑定 SSH 密钥等步骤以后再补。关于这部分信息网上很多，很容易搜到。

## 配置 **Hexo**

{% blockquote Hexo https://hexo.io/zh-cn/docs/#什么是-Hexo？ %}
Hexo 是一个快速、简洁且高效的博客框架。Hexo 使用 MarkDown（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页
{% endblockquote %}

推荐看 [Hexo中文文档](https://hexo.io/zh-cn/docs)，写的很详细也很全面，下面的内容基本搬自 Hexo 中文文档，省略了一些暂时用不到的细节，还有关于安装 nvm 和使用 nvm 安装 Node.js 的部分会稍有不同。

### 安装 **Hexo**

安装`Hexo`之前需要先安装下列应用程序：

* [Node.js](https://nodejs.org)
* [Git](https://git-scm.com)

如果你已经安装好了上列程序，只需要在终端中输入下面的命令即可完成 Hexo 的安装：

```bash
npm install -g hexo-cli
```

如果没有安装好所需程序请看下面

#### 安装 Git 

{% blockquote Git https://git-scm.com %}
Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency. 
{% endblockquote %}

* Windows 系统到 [Git下载页面](https://git-scm.com/downloads) 下载对应版本的`Git`并安装。
* Linux 系统（LinuxMint，Ubuntu，Debian）在终端中运行下列命令：
`udo apt-get install git-core`

#### 安装 **Node.js**

{% blockquote Node.js http://nodejs.cn %}
Node.js 是一个基于 Chrome V8 引擎的 JavaScript 运行环境。Node.js 使用了一个事件驱动、非阻塞式 I/O 的模型，使其轻量又高效。Node.js 的包管理器 npm，是全球最大的开源库生态系统。
{% endblockquote %}

* Windows 系统推荐到 [Node.js主页](https://nodejs.org) 下载安装程序，我用的是`v6.9.1`版本，目前没问题，其他版本请自行测试。
* Linux 系统推荐使用 [nvm](https://github.com/creationix/nvm)（Node.js版本管理器） 安装 Node.js
##### 通过 **nvm** 安装 **Node.js**

下面以 Ubuntu 系统为例，使用 Windows 系统请到上面提供的地址下载 Node.js 安装程序，不需要使用 nvm 安装。

1. 安装 **nvm**
在终端中运行下列命令（这里与 **Hexo中文文档** 中的不同，我用 Hexo 中文文档提供的命令安装没有成功，所以我到 vnm 的 Github 项目主页找到了作者提供的方法）：

```bash
wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.32.1/install.sh | bash
```

或者

```bash
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.32.1/install.sh | bash
```

2. 修改终端配置，在终端的首选项中找到「以登录 Shell 方式运行命令」选中并重启终端。

3. 安装 **Node.js**
在终端中运行下列命令（`v6.9.1`代表 Node.js 版本，可根据需要自行更换）：

```bash
nvm install v6.9.1
```

安装成功后使用 `node -v` 命令查看是否安装成功。
