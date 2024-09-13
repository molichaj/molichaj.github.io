---
title: hugo主题更换踩坑记录
description: 
date: 2023-08-15
slug: test
categories:
    - 博客装修
tags:
    - hugo
    - stack
---

## 写在前面

如果你打算使用hugo搭建个人博客但还没安装hugo，在选择安装包时，请尽量下载包名带extended的版本，对主题适配度更高。

## 一番折腾

起因是想要把hugo博客主题由papermod换成stack。

1. 下载stack主题的压缩包，此处直接指定好文件夹`git clone`也可以，只是因为网络问题，我这样操作总是出错，我就干脆直接下载zip然后解压到themes文件夹下了。

2. 把之前主题的xml文件删掉，把stack主题里example site下的config.yaml复制到blog文件下，打开cmd窗口运行`hugo server`命令，发现报错，无法加载网页。

   （这里我一开始以为是之前的博客内容哪里和当前主题不兼容，于是我直接另开了一个文件夹重新`hugo new site`，然后把stack主题里example site下的config.yaml文件和contents文件夹都复制到了new blog文件夹下，仍然行不通，后来我仔细阅读错误解读，在网上搜索终于发现了原因——我当初下载的hugo版本是无extended的，不支持scss、main.css的转换，需要更新版本或者重新下载。）

   ```
   error: failed to transform resource: TOCSS: failed to transform "scss/main.scss" **(**text/x-scss**)**: this feature is not available in your current Hugo version
   ```

3. 我问了chat-gpt关于hugo卸载的命令，然而ta向我提供的几个命令并不适合于windows系统，于是我打算先不管怎么卸载，先去把含extended的包下载下来再说，然后直接安装一下看看，结果发现点击exe没有反应，后来看了这篇文章：[搭建Hugo时需要注意的坑](https://ripple-zjw.github.io/2019/搭建hugo时需要注意的坑/) 后，似乎明白了一点，于是我用listary软件搜索之前的hugo.exe放在哪个文件夹下，直接把那个文件替换成了我新下载的带extened版本，怀着忐忑的心情尝试运行——成功，可以查看新主题站点了！

4. 到此更换主题大功告成，之后可能就是装修主题啦。

   [hugo最新版本文件下载地址在这！](https://github.com/gohugoio/hugo/releases) 

## 总结与反思

   这次的折腾还得到了一个小知识就是：hugo主题虽然是基于go语言搭建的，但是不需要提前安装go语言哦。怎么发现的呢，这也经过了一番折腾，就不细说了，总之我一番操作失败后，打算重装go和hugo，但删除go之后运行hugo发现没什么影响，才知道了这个。

   反思一下就是之前还是没有认真看readme文件之类的，多安装了go语言，没有选择带extended的hugo版本。