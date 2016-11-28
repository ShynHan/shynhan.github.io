---
title: 博客备份说明文档
date: 2016-11-28 21:23:15
---
## 关于
因为喜欢折腾，技术功底又不行，经常搞出问题自己又解决不了，每次都要使用「重装」大法，然后又要重新配置，十分麻烦，所以将一些配置文件和一些比较重要的文件整理一下，在博客项目里新建一个「sync」分支，用来同步这些文件。

为了方便，我使用博客的「source」目录作为同步目录，并且在「source」目录里新建了一个「\_sync」目录用来存放配置文件和其他重要文件，因为使用下划线开头的文件或文件夹在 Hexo 生成静态页面的时候会被忽略，这样我既可以同步文章和配置，又不会影响 Hexo 的生成工作，最重要的是同步文章十分方便，因为 Hexo 的默认文章存放位置就在「source」下的「\_posts」文件夹里，这样直接使用 git 同步就行了，不需要倒来倒去的。
这个「README.md」之所以房子这个目录下，就是为了不影响 Hexo 的生成工作，如果放在上级目录，在 Hexo 生成静态页面的时候这个「README.md」会被一并渲染，而放在这个目录下会被忽略。
## 同步文件目录结构

一个简单的目录结构，「#」后面的是注释内容

- /
 + about # 关于页面
  * index.md
 + categories # 分类页面
  * index.md
 + _posts # 博客默认的文章源文件文件夹
  * GitHub-Hexo-Next-搭建静态博客.md
  * 注册-GitHub-详细步骤（图文）.md
  * ...
 + _sync # 配置和文件同步目录
  * scaffolds # 模板文件目录
   - draft.md
   - page.md
   - post.md
  * source # 这里的文件应放在博客目录下的「source」目录里，也可以放在主题文件目录的「source」目录下
   - uploads # 头像
    + avatar.png
   - 404.html # 腾讯爱心 404 页面
   - favicon.ico # 网站 favicon 图标
  * themes # 主题同步文件
   - next
    + _config.yml # Next 主题配置文件
  * _config.yml # 博客目录下的站点配置文件
  * README.md # 当前正在查看的「README.md」文档
 + tags # 标签页面
  * index.md
