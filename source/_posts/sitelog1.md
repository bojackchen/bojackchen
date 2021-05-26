---
title: Hexo + NexT 建站日志（一）
date: 2019-09-19 23:03:48
tags:
  - Hexo
  - NexT
  - GitHub
categories:
  - 建站
type: "post"
---
之前几天都在搞我的个人网站的事情。很久很久以前用 [WordPress](https://wordpress.org/) 的时候，因为没有服务器的关系，所以其实也就是本地玩玩。再之后有用过 OpenShift，感觉还行但是访问起来好慢（不知道是不是因为在大陆的关系）。。。然后最后也就不了了之了。后来发现 [GitHub](https://github.com/) 提供的 [GitHub Pages](https://pages.github.com/) 挺好的，自己用起来又快又方便，完全可以通过 Git 来部署，建完之后别人访问起来也很快很方便。

<!--more-->

所以这次，我用了 [Hexo](http://hexo.io/) 加上 [Next](http://theme-next.js.org/) 主题配置了一个骚气的[个人网站](http://bojackchen.github.io/)，大家可以访问一下，看看是不是很骚气很文艺很高逼格？！

## 准备工作
- 准备工作包括创建 GitHub Repository，名字一定要是 yourusername.github.io，yourusername 就是你的 GitHub 用户名，到时访问网站的时候就是这个 URL 地址去访问的。
- 安装 Node.js，Git 这些工具
- 安装 Hexo(一个小型的快速的静态博客网页生成器)，具体怎么安装参见 [Hexo 详细信息](http://hexo.io/)
- 安装 NexT 主题，这是为 Hexo 定制的主题，参见 [NexT 主题](https://github.com/theme-next/hexo-theme-next)，直接从 GitHub 上面 clone 下来放在 Hexo 根目录下面的 theme 文件夹下面就可以，也可以通过 npm 直接安装。
- 配置 Hexo 使用 NexT 主题。

## Hexo 配置
配置 Hexo 的工作大概都在 [Hexo setup](https://hexo.io/docs/setup) 里面，不再赘述，常用的命令也就是下面几条：
``` bash
hexo cl  # cl for clean, clean all the generated files and databases
hexo g  # g for generate, generate all the static website files
hexo s  # s for server, start Hexo server so that we can visit localhost:4000 for preview
hexo d  # d for deploy, Hexo helps you deploy the website to GitHub repository (yourusername.github.io)
hexo g --d  # first generate files, then deploy, all in one command
```
Hexo 目录下面的 \_config.yml 文件是一个重要的站点配置文件，里面能够配置站点的一些选项，具体参见 [Hexo configuration](https://hexo.io/docs/configuration.html).

## NexT 配置
把 NexT clone 下来了之后，配置 Hexo 使用这个主题，之后就是配置 NexT 启用一些自带的功能和配置一些第三方功能。同样在 NexT 目录下面的 \_config.yml 文件是一个重要的主题配置文件，里面能够配置主题的一些选项，具体参见 [NexT getting started](https://theme-next.js.org/docs).

一些大家都喜闻乐见的功能，比如评论，分享，转发，留言等等，都可以在 NexT 上面通过[主题配置](https://theme-next.js.org/docs)来实现；而一些[第三方服务](https://theme-next.js.org/docs/)，比如站内搜索，评论，留言和分享系统等等，都可以通过第三方网站和 NexT 的配置共同协作实现。
