---
title: GitHub+Hexo+Next 搭建静态博客
date: 2016-11-20 01:57:37
categories:
- 教程
tags:
- 原创
---
## 前言

- GitHub：相当于一个服务器，相比于国内的一些博客服务提供商要稳定安全，且靠谱的多。不会昨天还高喊「永久免费」今天就告诉你马上要停止服务了，快转移资料吧
- Hexo：相当于博客框架（基于 Node.js），快速、简单，扩展插件较多，支持 Markdown 格式渲染
- Next：博客主题，简洁、文档齐全且可定制性强，最重要的是全中文文档

这三个组合在一起，真的是非常赞！

## 更新记录

2016-11-20 撰写初稿
2016-11-24 补充完善
2016-11-25 发现写的太详细篇幅会过长，所以决定将文章拆开，分篇讲解

## 配置 GitHub

GitHub 需要注册才能使用，如果不会注册可以参考下面的文章，如果已注册请忽略：

> 【注册 GitHub 详细步骤（图文）】
>
> **鹿台** _https://shynhan.github.io/2016/11/27/注册-GitHub-详细步骤（图文）/_

### 创建静态主页

- 打开 [GtiHub 主页][1] 并登录。
- 新建一个项目
 + 如果你从未创建过项目点击 `Start a project` 按钮新建一个项目
 + 对于创建过项目的人来说这一步很简单，就不扣图了。 

![Github_page1](http://p1.bpimg.com/575659/27bc19d2ab5125c0.jpg)

- 上面的操作完成后跳转到一个新页面，先填写项目名称：
`username.github.io`
例如：
`shynhan.github.io`
这里的「shynhan」就是用户名，使用小写，即使你的用户名里有大写（我的用户名是「ShynHan」）字母也要转换成对应的小写字母，一定要写一致。
- 下面的项目描述随便填写
- 选择免费用户选择「Public」项目（默认项），付费用户可以根据自己需要选择「Private」项目
- 勾选上「Initialize this repository with a README」，创建「README」文档，方便测试
- 确认无误后点击`Create repository`按钮提交

![Github_page2](http://p1.bpimg.com/575659/1e5307d93ab5dd9e.jpg)

**至此，创建 GitHub 静态页面部分就完成了，新的静态页面需要十分钟左右初始化**

### 配置 SSH 密钥



## 配置 **Hexo**

> Hexo 是一个快速、简洁且高效的博客框架。Hexo 使用 MarkDown（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页
>
> **Hexo** - _https://hexo.io/zh-cn/docs/#什么是-Hexo？_

关于 [Hexo][Hexo] 的配置推荐阅读 [Hexo中文文档][2]，官方文档，十分全面，不过篇幅稍长，懒得看文档的可以看下面的步骤，基本是在官方文档里挑的一些重要且必要的内容，还有部分内容是我自己补充的。

### 安装 Hexo

安装 **Hexo** 之前需要先安装下列应用程序：

- [Node.js](https://nodejs.org)
- [Git](https://git-scm.com)

如果你已经安装好了上列程序，只需要在终端中输入下面的命令即可完成 Hexo 的安装：
`npm install -g hexo-cli`

如果没有安装好所需程序请看下面

#### 安装 Git 

> Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency. 
>
> **Git** - _https://git-scm.com_

* Windows：到 [Git下载页面](https://git-scm.com/downloads) 下载对应版本的 Git 并安装。
如无特殊需求，安装过程中使用默认选项即可。
* Linux（LinuxMint，Ubuntu，Debian）：在终端中运行下列命令
`sudo apt-get install git-core`

安装完成后需要对 **Git** 进行简单的设置：

- 在终端中输入`git --version`检查 Git 是否正确安装（这是查看 Git 版本的命令）
- 确认 Git 运行正常后输入
`git config --global user.name "自定义用户名"`
回车确定，如无任何反馈证明设置成功（Unix 哲学，没有现象就是好现象）
- 设置完用户名之后设置 Git 邮箱 
`git config --global user.email "自定义邮箱地址"`
这里的邮箱地址推荐填写 GitHub 的绑定邮箱，这样在你使用 Git 向 GitHub 推送消息的时候会显示出你是项目管理者

#### 安装 Node.js

{% blockquote Node.js http://nodejs.cn %}
Node.js 是一个基于 Chrome V8 引擎的 JavaScript 运行环境。Node.js 使用了一个事件驱动、非阻塞式 I/O 的模型，使其轻量又高效。Node.js 的包管理器 npm，是全球最大的开源库生态系统。
{% endblockquote %}

* Windows 系统推荐到 [Node.js主页](https://nodejs.org) 下载安装程序，我用的是`v6.9.1`版本，目前没问题，其他版本请自行测试。
* Linux 系统推荐使用 [nvm](https://github.com/creationix/nvm)（Node.js版本管理器） 安装 Node.js
##### 通过 **nvm** 安装 **Node.js**

下面以 Ubuntu 系统为例，使用 Windows 系统请到上面提供的地址下载 Node.js 安装程序，不需要使用 nvm 安装。

1. 安装 nvm
在终端中运行下列命令（这里与 **Hexo中文文档** 中的不同，我用 Hexo 中文文档提供的命令安装没有成功，所以我到 vnm 的 Github 项目主页找到了作者提供的方法）：

```bash
wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.32.1/install.sh | bash
```

或者

```bash
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.32.1/install.sh | bash
```

2. 修改终端配置，在终端的首选项中找到「以登录 Shell 方式运行命令」选中并重启终端。

3. 安装 Node.js
在终端中运行下列命令（`v6.9.1`代表 Node.js 版本，可根据需要自行更换）：

```bash
nvm install v6.9.1
```

安装成功后使用 `node -v` 命令查看是否安装成功。


[1]: https://github.com
[2]: https://hexo.io/zh-cn/docs
