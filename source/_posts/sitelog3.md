---
title: Hexo + NexT 建站日志（三）
date: 2019-09-19 23:49:06
tags:
  - Hexo
  - NexT
  - GitHub
categories:
  - 建站
type: "post"
comments: true
---
建站最后一步：处理一下 Hexo 工具生成的所有源文件。Hexo 生成出来的源文件中有大量的空白行，尤其是 html 文件。
我们使用 [gulp](https://gulpjs.com) 工具来压缩一下所有 html 和 css 文件的大小。gulp 是一个开源的 task runner，能够进行批量处理，达到我们的目的。

<!--more-->

## 安装
目前最新的 gulp 版本是 4，配合最新版本是 12 的 nodejs 食用刚刚好。使用以下命令安装 gulp。
```bash
$ npm install --save gulp
```
除了 gulp 主体之外，我们还要额外安装用于压缩 html 文件的工具和压缩 css 文件的工具。
```bash
$ npm install --save gulp-htmlmin
$ npm install --save gulp-clean-css
```

## 配置
在 gulp 运行目录下面新建一个 gulpfile.js 文件就可以控制 gulp 工具的运行。为了压缩 html 和 css 文件的大小，gulpfile.js 文件的内容如下（使用的是 gulp 4 的最新语法）。
```js
const gulp = require('gulp');
const minifyhtml = require('gulp-htmlmin');
const minifycss = require('gulp-clean-css');

gulp.task('minifyhtml', function() {
  return gulp.src('public/**/*.html')
    .pipe(minifyhtml({
      removeComments: true,
      collapseWhitespace: true,
      minifyCSS: true,
      minifyJS: true,
      minifyURLs: true
    }))
    .pipe(gulp.dest('public'));
});

gulp.task('minifycss', function() {
  return gulp.src('public/**/*.css')
  .pipe(minifycss({
    compatibility: 'ie8'
  }))
  .pipe(gulp.dest('public'));
});

gulp.task('default', gulp.parallel('minifyhtml', 'minifycss'));
```

## 运行
在每次运行 hexo g 命令产生所有源文件之后，直接接着运行 gulp 命令，源文件中的 html 和 css 文件会直接被压缩至最小大小。之后可以进行后续的 deployment。
```bash
$ hexo g
$ gulp
$ hexo d
```
