---
abbrlink: ''
categories: []
date: '2024-06-24T22:33:49.384600+08:00'
excerpt: ''
tags: []
title: 如何使用lux下载B站视频
updated: '2024-06-24T22:35:36.412+08:00'
---
# 如何使用lux下载B站视频

## 前言

鉴于现在bilibili视频下载越来越难，要么要下载一个巨大杂七杂八的软件，要么就是收费，至于小而美的插件脚本都很难寻找，于是我在此推广一个开源项目lux，并介绍如何用它来实现哔哩哔哩视频的下载

## 1. 下载lux和FFmpeg

访问此处[Release v0.24.1 · iawia002/lux (github.com)](https://github.com/iawia002/lux/releases/tag/v0.24.1)

选择适合你操作系统的版本，一般我们用的是windows系统，选择红框内的下载

![](https://pic.imgdb.cn/item/667980aed9c307b7e99c445a.jpg)

解压出来后放在一个单独目录。

接着访问[Builds - CODEX FFMPEG @ gyan.dev](https://www.gyan.dev/ffmpeg/builds/)

![](https://pic.imgdb.cn/item/667980ced9c307b7e99cad18.jpg)

下载红框内文件，解压时发现里面有三文件夹，只需解压bin内的文件即可。

解压完后将bin内的三个文件移动到你上文下载的lux同个目录下。

接着再在该目录写新建一个txt文件，命名为 `cookie.txt`备用

此时你应该有一个文件夹如下

![](https://pic.imgdb.cn/item/667980e9d9c307b7e99d0c6c.jpg)

## 2.获取cookie

进入哔哩哔哩首页，按下F12唤出控制台，选择**网络**或者**network**，然后选中**全部**。

![](https://pic.imgdb.cn/item/66798104d9c307b7e99d55ff.jpg)

此时按下F5刷新网页

![](https://pic.imgdb.cn/item/66798117d9c307b7e99d9489.jpg)

等待一会儿，加载完全后不出意料排在第一位的是形如红圈内的玩意 （spm_id_from=333.976.0.0），如果不是拉下去寻找该玩意，如若找不到，多刷新几次。

然后将光标移到右边往下拉，

![](https://pic.imgdb.cn/item/6679812cd9c307b7e99ddaad.jpg)

不出意外你会看到一大段cookie，将cookie所包含的内容全部复制下来，不要遗漏，也不要多。（后面如果出无法登录什么的问题应该就是这里出错了）并将这些内容即你的cookie复制到前文让你新建的那个 `[cookie.txt](#jump)`的文件里。

## 3.下载视频

在你lux的目录唤出cmd

![](https://pic.imgdb.cn/item/66798162d9c307b7e99e9448.jpg)清空红框内容并输入 `cmd`回车

![](https://pic.imgdb.cn/item/66797457d9c307b7e976cb6a.jpg)

然后就可以开始使用lux了

比如说想下载红框内视频

![](https://pic.imgdb.cn/item/6679759bd9c307b7e97a5242.jpg)

点进去

![](https://pic.imgdb.cn/item/667976cad9c307b7e97d99b5.jpg)

复制红框内容

返回cmd

---

- 知识点1

`lux -i 视频网址` 这个命令可以查看关于此视频的下载信息

---

输入

```
lux -c cookie.txt -i https://www.bilibili.com/video/BV1Cw4m1e7L2/?spm_id_from=333.1007.tianma.1-1-1.click
```

![](https://pic.imgdb.cn/item/66797861d9c307b7e98224e9.jpg)

你可以看到任何该视频你可以下载的清晰度

可能你会看到每个清晰度有两种编码方式，avc1和hev1，如何选择看个人需求，我推荐avc1

---

- 知识点二

```cmd
lux -c cookie.txt
```

这里的-c cooki.txt很重要，没有它，你只能下载至多480p的视频

---

在这里，假如我们要下载高清1080p avc1的，那我们按红框里的来

cmd内输入

```
lux -c cookie.txt -f 80-7 https://www.bilibili.com/video/BV1Cw4m1e7L2/?spm_id_from=333.1007.tianma.1-1-1.click
```

然后就下完了

或者你想下载480p hev1的

```
lux -c cookie.txt -f 32-12 https://www.bilibili.com/video/BV1Cw4m1e7L2/?spm_id_from=333.1007.tianma.1-1-1.click
```

注意 <mark>-f</mark> 后面的值

下载完成后的视频在lux同目录下。

你可能想问如果我想下载一个合集的内容怎么办，我的回答是自己去看[文档]([iawia002/lux: 👾 Fast and simple video download library and CLI tool written in Go (github.com)](https://github.com/iawia002/lux))。其实是我现在没空写，以后会补上的。

![](https://pic.imgdb.cn/item/66797ee7d9c307b7e9966a78.png)

## 后记

lux的功能远不及此，它还可以下载更多网站的视频以及拥有更多强大的功能，但只有你多看文档才能够学到。

最后呢我展望一下未来，我知道lux的命令行模式很容易劝退小白，所以我决定在暑假期间争取学习java以便在开学前制作出lux的图形用户界面，项目名称我已经想好了，就叫lux-GUI。拭目以待吧！
