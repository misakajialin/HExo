---
title: 关于Hexo的图片插入问题
date: 2023-06-24 11:40:27
tags: 
- hexo
categories: 
- technology
---

# 本地图片引用了却无法显示

> 插入图片的两种方法：

1. 引用图床
2. 引用本地图片。为了防止路径出错，建议使用图床。

<!-- more -->

## 1.图床

推荐使用：[聚合图床](https://www.superbed.cn/)

## 2.本地图片

参照 [Hexo 文档](https://hexo.io/zh-cn/docs/asset-folders)，然后用这种方式引用图片：

```
{% asset_img image.jpg [title] %}
```

如果还是无法显示，请尝试在文章里用 html 的 img 标签来引用本地图片。
