---
title: "Hugo + Github Pages踩坑记录"
date: 2023-07-05T14:26:08+08:00
draft: false
slug: "getting-started"
tags: ['docs']
---

之前使用过 hexo + github pages 建站，不希望中间冲突，所以之间建立了新账号，但之前配置过 git 账号和 SSH 之类的，配置 hugo 的时候需要改成新的，是一件麻烦的事情。主要参考了[Alola World | 暨简明麻瓜快速念咒 Hugo 搭建笔记 | 小球飞鱼 (mantyke.icu)](https://mantyke.icu/posts/2021/f185ce41/) 这篇博文，博主写的详细易懂，我就不写具体流程了，直接点开链接看就好啦，但是可以补充一些作为参考。

1. 建立 github 仓库的时候建议勾选添加`readme.md`文件，因为我不知道怎么`quick setup`

2. 部署到 github pages 之前，打开 git 执行前两行命令查看一下全局用户名和邮箱，我返回的是之前账号的信息，需要修改成新账号的用户名和邮箱，执行后两行即可。

   ```
   # 查看当前设置用户名、邮箱名
   git config --global user.name
   git config --global user.email
   # 设置新信息
   git config --global user.name “用户名”
   git config --global user.email “邮箱账号”
   ```

3. 新版的 github 中默认的分支为`main`，最后一步推送的时候使用`git push -u origin master`即可。
4. ` git push`时报错`[rejected] main -> main(fetchh first)`，搜索多种解决方案无果，最后使用暴力命令`git push -f` 解决。

