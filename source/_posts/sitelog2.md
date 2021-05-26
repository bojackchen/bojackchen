---
title: Hexo + NexT 建站日志（二）
date: 2019-09-19 23:31:09
tags:
  - Hexo
  - NexT
  - GitHub
categories:
  - 建站
type: "post"
---
这篇建站日志主要写了一些 Hexo 建站的进阶功能配置，比如打赏功能、侧边社交链接和友情链接、Google Analytics 以及 Google Webmaster Tools 等这些使用工具，能够润色网站并且能够统计信息方便管理。

<!--more-->

## 侧边栏链接
网站的侧边栏可以放置**社交链接**并制定各自的图标，同时也可以放一些**友情链接**，两者都可以在主题配置文件中修改。
侧边栏的社交链接放在主题配置文件中。同时你也可以设置对应社交链接的图标，图标来自 [FontAwesome](http://fontawesome.io/)。
```bash
social:
  Example: https://example.com || fontawesomeiconname
  GitHub: https://github.com/yourusername || github
  Twitter: https://twitter.com/yourusername || twitter
  微博: https://weibo.com/yourusername || weibo

social_icons:
  enable: true
```
友情链接的配置也是很简单的，只需要直接在主题配置文件中增加 links 字段。
```bash
links_settings:
  icon: fa fa-globe
  Title: http://example.com/
```

## 打赏功能
越来越多的平台（微信公众平台、新浪微博等）支持**打赏功能**，付费阅读时代越来越近，特此作者支持了微信打赏和支付宝打赏。只需要在主题配置文件中加入二者的收款二维码图片地址。
```bash
reward_settings:
  enable: true

reward:
  wechatpay: /path/to/wechatimage
  alipay: /path/to/alipayimage
```

## Google Webmaster Tools
登录 [Google Webmaster Tools](https://www.google.com/webmasters/tools/) 进行必要的设置，同时提交本网站 sitemap。sitemap 会在安装 hexo-generator-sitemap 之后自动产生。
```bash
$ npm install --save hexo-generator-sitemap
```
本网站的 sitemap 被收录了之后(一般在提交 sitemap 后几天)，这个工具就可以提供网站在 Google 上展示率的详细报告，并且能够从 Google 的角度发现网站的潜在问题等等。

## Google Analytics
[Google Analytics](https://analytics.google.com/analytics/web/) 是一个非常强大的网站数据的分析和管理工具，能够统计浏览量等等各种网站信息，方便进一步分析和管理。
在 Google Analytics 网站登录之后，获得自己的 Tracking ID，通常是以 **UA-** 开头的。
```bash
google_analytics:
  tracking_id: yourtrackingID
```

## 阅读全文
默认情况下文章全文都会显示在首页上面，显得很冗长又没有意义。**“阅读全文”**这个功能就是为了解决这个问题。网站首页只会显示文章摘要，如果有兴趣可以点击“阅读全文”按钮进入全文页面继续阅读。三种方法都可以实现这个功能。
1. 在文章中使用 <!--more--> 截断，只有截断前的内容会显示在首页(Hexo 提供的功能，**推荐使用**)。
2. 在文章的 front-matter 中添加 **description** 字段，并提供文章摘要

建议使用第 1 种方法，和 Hexo 本身的兼容性比较好，支持最好。
