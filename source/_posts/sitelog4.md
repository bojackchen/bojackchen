---
title: Hexo + NexT 建站日志（四）
date: 2019-09-29 12:54:15
tags:
  - Hexo
  - NexT
  - GitHub
categories:
  - 建站
type: "post"
---
虽然 [gulp](https://gulpjs.com) 工具可以帮助压缩网站源文件的大小，但是需要额外输入执行一次 gulp 命令，确实有些麻烦。
一个更好的工具是 hexo-all-minifier，这一个工具集成了 html，css 和 js 源文件的压缩功能，是很好的替代品。而且不需要额外输入命令，hexo g 命令执行时会自动进行压缩工作。

<!--more-->

## 安装
直接使用 npm 安装。
```bash
$ npm install --save hexo-all-minifier
```
这一个工具集成了所有需要的功能，详细信息可以参阅 [github page](https://github.com/chenzhutian/hexo-all-minifier)

## 配置
直接在 Hexo 网站的根目录的 \_config.yml 文件中配置 hexo-all-minifier 的工作模式。例如：
```yml
# Hexo-all-minifier
all_minifier: true

html_minifier:
  enable: true
  ignore_error: false
  silent: true

css_minifier:
  enable: true
  silent: true

js_minifier:
  enable: true
  mangle: true
  silent: true

image_minifier:
  enable: false
```

## 运行
Hexo-all-minifier 的运行不需要额外的命令。当安装了这个工具之后，hexo g 命令运行的同时所有的源文件会自动完成压缩。
