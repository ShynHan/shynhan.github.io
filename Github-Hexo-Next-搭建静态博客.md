---
title: Github+Hexo+Next 搭建静态博客
date: 2016-11-20 01:57:37
tags:
- Github
- Hexo
- Next
---
## 前言

先说说为什么要自己搭建博客吧:

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

## 配置 Github

> GitHub is a code hosting platform for version control and collaboration. It lets you and others work together on projects from anywhere.
>
> **Github** - _https://guides.github.com/activities/hello-world/#what_

[Github][Github] 是最著名的开源项目托管平台，本博客就是基于 Github 提供的静态页面功能搭建的，国内提供类似功能的有 [码云][码云]（开源中国提供）和 [Coding][Coding]（以前还有个 GitCafe 不过被 Coding 收购了），本博客就是同时搭建在这三个平台之上，同步更新。

Github 服务器在国外，所以访问速度慢，但是十分可靠。
如果只是发些普通的文章推荐使用 **码云** 或者 **Coding** 应为速度真的很快。
或者你也可以像我一样，同时在三个平台更新。

下面以 **Github** 为例讲解如何在注册和使用静态页面功能，其他平台方法类似，有需要注意的地方会在后面补充。

### 注册 Github

#### Step 1

访问 [Github注册页][1]，根据提示依次填入:

* 自定义用户名，不能使用中文
* 邮箱地址
* 自定义密码

填写完毕后点击`Creat an account`按钮提交注册信息。

![Github注册1](http://p1.bqimg.com/575659/d4d31e61a911da0a.jpg)

#### Step 2

选择使用方案：

* Unlimited public repositories for free.（免费，但是只能创建开源项目）
* Unlimited private repositories for $7/month.（7美刀每月，可以创建私有项目）

默认选择第一项（免费），如果经济能力允许可以选择第二项

选择完成后点击下面的`Continue`按钮提交。

![Github注册2](http://i1.piimg.com/575659/3f5d1a34f129d2ef.jpg)

#### Step 3

类似一个问卷，介绍你自己，可以自己酌情选择与填写，然后点击`Submit`提交，也可以点击`skip this step`直接跳过。

![Github注册3](http://i1.piimg.com/575659/4a14e119fb2b791a.jpg)

**到此，Github 就注册完成了**

### 创建静态主页

- 通过上面的步骤注册完成后会自动跳转到 [Github主页][Github]，如果没有跳转，请自己点击主页跳转或者手动输入网址 https://github.com
- 跳转到 Github 主页后查看右上角自己是否处于登录状态，如果没登录请先登录。
- 确定自己登录后点击网页中间位置的`Start a project`

![Github_page1](http://p1.bpimg.com/575659/27bc19d2ab5125c0.jpg)

- 上面的操作完成后跳转到一个新页面，先填写项目名称：
`自定义用户名.github.io`
例如：
`demopage.github.io`
这里的「demopage」就是你的用户名，必须要与先前注册时填写的要一致，使用小写，即使你的用户名里有大写字母也要转换成对应的小写字母。
- 下面的项目描述随便填写
- 选择免费用户选择「Public」项目（默认项），付费用户可以根据自己需要选择「Private」项目
- 勾选上「Initialize this repository with a README」，创建「README」文档，方便测试
- 确认无误后点击`Create repository`按钮提交

![Github_page2](http://p1.bpimg.com/575659/1e5307d93ab5dd9e.jpg)

**至此，Github配置部分就完成了，新的静态页面需要十分钟左右初始化**

## 配置 **Hexo**

> Hexo 是一个快速、简洁且高效的博客框架。Hexo 使用 MarkDown（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页
>
> **Hexo** - _https://hexo.io/zh-cn/docs/#什么是-Hexo？_

推荐看 [Hexo中文文档](https://hexo.io/zh-cn/docs)，写的很详细也很全面，下面的内容基本搬自 Hexo 中文文档，省略了一些暂时用不到的细节，还有关于安装 nvm 和使用 nvm 安装 Node.js 的部分会稍有不同。

### 安装 Hexo

安装`Hexo`之前需要先安装下列应用程序：

* [Node.js](https://nodejs.org)
* [Git](https://git-scm.com)

如果你已经安装好了上列程序，只需要在终端中输入下面的命令即可完成 Hexo 的安装：

```bash
npm install -g hexo-cli
```

如果没有安装好所需程序请看下面

#### 安装 Git 

> Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency. 
>
> **Git** - _https://git-scm.com_

* Windows 系统到 [Git下载页面](https://git-scm.com/downloads) 下载对应版本的 Git 并安装。
* Linux 系统（LinuxMint，Ubuntu，Debian）在终端中运行下列命令：
`udo apt-get install git-core`

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

[Github]: https://github.com
[码云]: https://git.oschina.net/
[Coding]: https://coding.net/
[1]: https://github.com/join?source=header-home
