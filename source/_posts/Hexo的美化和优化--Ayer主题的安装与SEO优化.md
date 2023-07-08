---
title: Hexo的美化和优化--Ayer主题的安装与SEO优化
date: 2023-06-23 21:45:35
tags: 
- Ayer 
- hexo
- live2d
- seo
categories: 
- technology
---

# 前言

正想要写这篇博客时。打开朋友圈一看，又是狗粮又是现充在这端午三天横行。反观自己，这三天就全坐在电脑旁折腾树莓派和博客了。不说了题外话了，回归正题。本篇博文力图包含Ayer主题的安装，live2d看板娘的安装，SEO的优化。

<!-- more -->

# 部署Ayer主题

## 1.安装

**方法一( 推荐）：**

在你的博客（Hexo）目录下执行以下命令：

如若没有安装cnpm则以下所有cnpm命令全部改为npm即可，或者参考我的这篇博文[记树莓派上Hexo的搭建 | Misakait's Blog](https://misakait.online/20230623/%E8%AE%B0%E6%A0%91%E8%8E%93%E6%B4%BE%E4%B8%8AHexo%E7%9A%84%E6%90%AD%E5%BB%BA/) 来安装cnpm。

```bash
cnpm i hexo-theme-ayer -S
```

- 如果是新安装本主题，安装完成后会在根目录生成一个`_config.ayer.yml`文件，如若没有新建一个`_config.ayer.yml文件。直接编辑`_conig.ayer.yml`文件进行配置即可。

**方法二（hexo < 5.0）：**

```bash
# 国内用户如果速度较慢，可以把github地址替换为：https://gitee.com/mirrors/ayer.git
git clone https://github.com/Shen-Yu/hexo-theme-ayer.git themes/ayer
```

## 2.配置

将博客根目录下的 `_config.yml` 里的 `theme` 值修改成 `ayer`

```
theme: ayer
```

进入_config.ayer.yml文件配置，如果你一开始没有改文件，而是自己新建的，将下文复制过去。

```
# 侧边栏菜单
menu:
  主页: /
  归档: /archives
  分类: /categories
  标签: /tags
  关于我: /about

# 站点次标题和打字动效
# https://github.com/mattboldt/typed.js
subtitle:
  enable: true # 是否开启动效
  text: 唯我超电磁炮永存 # 显示的文字
  text2: 樱花落下的速度是没秒五厘米 # 滚动播放，如果不需要可以留空
  text3: 在此宣誓对你的爱 # 最多支持三段文字
  startDelay: 0 # 延迟时间
  typeSpeed: 200 # 打字速度
  loop: true # 是否循环
  backSpeed: 100 # 回退速度
  showCursor: true # 是否显示光标

# 网站图标和侧边栏logo
favicon: /favicon.ico
logo: /images/ayer-side.svg

# 封面配置
# enable-是否启用封面；path-封面背景图；logo-封面logo
cover:
  enable: true
  path: /images/cover1.jpg # /source/images目录下附送多张精美壁纸，可任意更换
  logo: /images/ayer.svg # 如果不要直接设置成false

# 页面顶部进度条
progressBar: true

# 告示板模块
broadcast:
  enable: true # true开启，false关闭
  type: 2 # 1：自定义输入，2：一言api(https://hitokoto.cn/)
  text: 一个安静优雅的hexo主题，快速且响应式。 # type为1时有效

# 文章配置
# 文章太长，截断按钮文字(在需要截断的行增加此标记：<!--more-->)
excerpt_link: 阅读更多...
# 如果你嫌每篇文章手动加more标记比较麻烦，又不想在首页全文显示，可以把excerpt_all设置成true，这样首页只会显示文章归档
excerpt_all: false

# 是否开启代码复制按钮
copy_btn: true
# 是否开启文章分享按钮
share_enable: true
# 国内的社交平台(If you are not in China, maybe you prefer to set:false)
share_china: true
# 文章分享文字
share_text: 分享

# 分页文字
nav_text:
  page_prev: 上一页
  page_next: 下一页
  post_prev: 上一篇
  post_next: 下一篇

# 文章页是否显示目录
toc: true

# 文章中的图片是否支持点击放大
image_viewer: true

# https://github.com/willin/hexo-wordcount
# 是否开启字数统计(关闭请设置enable为false)
# 也可以单独在md文件里Front-matter设置`no_word_count: true`属性，来自定义关闭字数统计
word_count:
  enable: true
  # 只在文章详情显示(不在首页显示)
  only_article_visit: true

# 打赏
# 打赏type设定：0-关闭打赏； 1-文章对应的md文件里有reward:true属性，才有打赏； 2-默认开启所有文章均有打赏，如果有些文章你不需要，请在文章对应的md文件里设置no_reward:true
reward_type: 0
# 打赏wording
#reward_wording: "请我喝杯咖啡吧~"
# 支付宝二维码图片地址，跟你设置logo的方式一样。比如：/images/alipay.jpg
#alipay: /images/alipay.jpg
# 微信二维码图片地址
#weixin: /images/wechat.jpg

# 版权声明
# 版权声明type设定：0-关闭版权声明； 1-文章对应的md文件里有copyright: true属性，才有版权声明； 2-所有文章均有版权声明
copyright_type: 2

# 是否启用搜索
search: true

# RSS订阅(先安装hexo-generator-feed插件，再去博客根目录config进行配置)
# 不想显示可以直接留空
rss: /atom.xml

# 是否启用黑夜模式开关
darkmode: true

# 动态背景效果: 0-关闭，1-动态线条(跟随鼠标)
canvas_bg: 1

# 自定义鼠标样式，直接替换/images/mouse.cur文件
mouse:
  enable: false
  path: /images/mouse.cur

# 鼠标点击效果：0-关闭，1-爱心，2-爆炸烟花，3-粒子烟花
click_effect: 1

# 页面宽度自定义（不建议修改，可能造成布局混乱），article_width文章宽度，sidebar_width侧边栏宽度
layout:
  article_width: 80rem
  sidebar_width: 8rem

# GitHub Ribbons-封面右上角的forkme，换样式直接在source/images目录下替换forkme图片
github:
  # (关闭请设置为false)
  enable: false
  url: https://github.com/Shen-Yu/hexo-theme-ayer

# 网易云音乐插件
music:
  enable: false
  # 播放器尺寸类型(1：小尺寸、2：大尺寸)
  type: 1
  id: 496869422 # 网易云分享的音乐ID(更换音乐请更改此配置项)
  autoPlay: true # 是否开启自动播放

# 访问量统计(不蒜子)
busuanzi:
  enable: true

# 友盟cnzz统计(url填js代码src链接)
cnzz:
  enable: true
  url: #

# Google Analytics
google_analytics: ""
# 百度统计
baidu_analytics: ""

# Mathjax数学公式
mathjax: true

# Katex数学公式(allpost设置为false时只有头部设置math:true的文章才开启)
# 需要更换hexo渲染器，npm un hexo-renderer-marked -S && npm i hexo-renderer-markdown-it-katex -S
katex:
  enable: false # true
  allpost: true
  copy_tex: false

# mermaid流程图 三个选项缺一不可(https://mermaid-js.github.io/mermaid/#/)
mermaid:
  enable: false
  cdn: https://cdn.jsdelivr.net/npm/mermaid@8.9.2/dist/mermaid.min.js
  theme: forest

# 网站成立年份(默认为 2023，若填入年份小于当前年份，则显示为 2018-2023 类似的格式)
since: 2023

# ICP备案信息尾部显示
icp:
  enable: false
  url: "http://www.beian.miit.gov.cn/" # 备案链接
  text: "浙ICP备88888888" # 备案信息
# 公安备案信息尾部显示
gongan:
  enable: true
  img: /images/beian.png #公安备案图片
  url: "http://www.beian.gov.cn/portal/registerSystemInfo?recordcode=01234567890123" #公安备案链接
  text: "浙公网安备01234567890123号" #公安备案信息

# 友情链接
friends_link:
  Ayer主题: #网站名称
    #网站地址
    url: https://github.com/Shen-Yu/hexo-theme-ayer
    #网站图片(可忽略不写)
    img: /images/ayer.png
  GitHub:
    url: https://github.com/Shen-Yu
    img: https://i.loli.net/2020/09/07/indb4PRYDA98EkN.png
  码云:
    url: https://gitee.com/shen-yu
    img: https://i.loli.net/2020/09/07/K3AqO7h6krQFlRX.png
  Hexo官网:
    url: https://hexo.io
    img: https://i.loli.net/2020/09/07/UYGzjo7h68CRWny.png
  Hexo图表插件:
    url: https://github.com/Shen-Yu/hexo-tag-chart
    img: https://i.loli.net/2020/09/07/GIXBYE5SoylhR1r.png

# 评论：1、Valine(推荐)；2、Gitalk；3、Twikoo; 4.MiniValine

# 1、Valine[一款快速、简洁且高效的无后端评论系统](https://github.com/xCss/Valine)
# 启用Valine必须先创建leancloud应用， 获取 id|key 填入即可
leancloud:
  enable: true
  app_id: #
  app_key: #
# Valine配置
valine:
  enable: true # 是否启用
  avatar: monsterid # 头像样式(https://valine.js.org/avatar.html)
  placeholder: 给我的文章加点评论吧~ # placeholder

# 2、Gitalk(https://github.com/gitalk/gitalk)
gitalk:
  enable: false # true
  clientID: # GitHub Application Client ID
  clientSecret: # Client Secret
  repo: # Repository name
  owner: # GitHub ID
  admin: # GitHub ID

# 3、Twikoo(https://github.com/imaegoo/twikoo)
twikoo:
  enable: false
  envId: #

# 4、MiniValine
# See: https://github.com/MiniValine/MiniValine
minivaline:
  enable: false
  serverURL: https://minivaline.your-domain.com

# 首页广告配置
# 可以根据需要自行增加ad_3，ad_4...，留空则不显示
ads:
# ad_1:
#    title: vultr优惠vps
#    img: https://cdn.jsdelivr.net/gh/Shen-Yu/cdn/img/vultr.png
#    url: https://www.vultr.com/?ref=8630075
#    width: 


# 网站开启加密访问，密码可设置任何字符
lock:
  enable: false
  password: 123456
```

## 3.关于插件

- [hexo-generator-searchdb](https://github.com/theme-next/hexo-generator-searchdb) 用于搜索（必需）

```bash
sudo cnpm install hexo-generator-searchdb --save
```

然后将以下配置复制到你博客根目录下的 `_config.yml` 里（注意不是 ayer 目录下的）:

```
search:
 path: search.xml
 field: post
 format: html
```

- [hexo-generator-feed](https://github.com/hexojs/hexo-generator-feed) 用于生成 RSS 订阅（必需）

```bash
sudo cnpm install hexo-generator-feed --save
```

然后同样将以下配置复制到你博客根目录下的 `_config.yml` 里（注意不是 ayer 目录下的）:

```text
feed:
  type: atom
  path: atom.xml
  limit: 20
  hub:
  content:
  content_limit: 140
  content_limit_delim: " "
  order_by: -date
```

- [hexo-helper-live2d](https://github.com/EYHN/hexo-helper-live2d/blob/master/README.zh-CN.md) 看板娘（可选）

```bash
sudo cnpm install --save hexo-helper-live2d
```

下载模型

有以下这些模型。

```css
live2d-widget-model-chitose
live2d-widget-model-epsilon2_1
live2d-widget-model-gf
live2d-widget-model-haru/01 (use npm install --save live2d-widget-model-haru)
live2d-widget-model-haru/02 (use npm install --save live2d-widget-model-haru)
live2d-widget-model-haruto
live2d-widget-model-hibiki
live2d-widget-model-hijiki
live2d-widget-model-izumi
live2d-widget-model-koharu
live2d-widget-model-miku
live2d-widget-model-ni-j
live2d-widget-model-nico
live2d-widget-model-nietzsche
live2d-widget-model-nipsilon
live2d-widget-model-nito
live2d-widget-model-shizuku
live2d-widget-model-tororo
live2d-widget-model-tsumiki
live2d-widget-model-unitychan
live2d-widget-model-wanko
live2d-widget-model-z16
```

选择好对应的模型，使用 `cnpm install 模型的包名` 来安装，比如我选择的的是`live2d-widget-model-miku 模型包.

![](https://pic.imgdb.cn/item/649660611ddac507cc054590.webp)

在hexo博客根目录选择`cmd`命令窗口或者`git bash` 输入以下代码:

```bash
#仅为示例，将live2d-widget-model-miku改为你想要的模型包名。
sudo cnpm install live2d-widget-model-miku
```

打开个人Hexo博客文件根目录下的 `_config.yml` 文件，在最后添加一下代码，示例:

其他你配置你照抄即可，注意 model 中的 use 要改成你所安装的模型包名

```
# live2d
# https://github.com/EYHN/hexo-helper-live2d
live2d:
  enable: true # 是否启用看板娘
  scriptFrom: local # 默认
  pluginRootPath: live2dw/ # 插件在站点上的根目录(相对路径)，自动生成
  pluginJsPath: lib/ # 脚本文件相对与插件根目录路径
  pluginModelPath: assets/ # 模型文件相对与插件根目录路径
  # scriptFrom: jsdelivr    # jsdelivr CDN
  # scriptFrom: unpkg    # unpkg CDN
  # scriptFrom: https://cdn.jsdelivr.net/npm/live2d-widget@3.x/lib/L2Dwidget.min.js    # 你的自定义 url
  tagMode: false # 标签模式, 是否仅替换 live2d tag标签而非插入到所有页面中，具体见项目github描述
  debug: false # 调试, 是否在控制台输出日志
  model:
    use: live2d-widget-model-miku # live2d模型的名字，要改的地方
    scale: 1
    hHeadPos: 0.5
    vHeadPos: 0.618
  display:
    superSample: 2
    width: 200
    height: 400
    position: right # 左侧还是右侧
    hOffset: 20
    vOffset: 0 # 距底部距离
  mobile:
    show: false # 手机端是否可见
    scale: 0.5
  react:
    opacityDefault: 0.7
    opacityOnHover: 0.2
```

## 配置页面

- **分类**

```
sudo hexo new page categories
```

然后将以下复制到 /source/categories/index.md 文件

```
---
title: categories
type: "categories"
layout: "categories"
---
```

- 标签

```bash
sudo hexo new page tags
```

然后将以下复制到 /source/categories/index.md 文件

```
---
title: tags
type: "tags"
layout: "tags"
---
```

- 友情链接

```
sudo hexo new page friends
```

然后将以下复制到 /source/friends/index.md 文件

```
---
title: friends
type: friends
layout: "friends"
---
```

然后在根目录下的 `_config.ayer.yml` 中自定义 `friends_link` 配置项即可

- 相册

```
sudo exo new page photos
```

然后将以下复制到 /source/photos/index.md 文件，`img_url` 替换成图片路径，`caption` 替换成图片名称

```
---
title: Gallery

albums: [["img_url", "img_caption"], ["img_url", "img_caption"]]
---
```

# SEO优化

我们辛辛苦苦写了博客是为了什么，但不管是为了什么，都有一个让更多人看见的过程。（那些写完就自己一个人看的除外）所以我们需要seo优化，让各大搜索引擎收录我们的网站。

### 1. 生成 sitemap 文件

需要先安装 hexo 插件：

         sudo cnpm install hexo-generator-baidu-sitemap --save

打开配置文件博客根目录下的`_config.yml`添加

```
baidusitemap:
	path: baidusitemap.xml
```

再重启 hexo

```
sudo hexo clean && sudo hexo g && sudo hexo d
```

### 2.网站推送至百度

百度 → [添加个人网站](https://ziyuan.baidu.com/site/siteadd?siteurl=)

使用添加文件的方式

输入你的网址

![](https://pic.imgdb.cn/item/64966b321ddac507cc16c7f3.webp)

按你的情况选

![](https://pic.imgdb.cn/item/64966b481ddac507cc16ecba.webp)

选择文件验证

![](https://pic.imgdb.cn/item/64966b571ddac507cc170728.webp)

把那个验证文件下载到你博客的 source 文件夹里面。

然后

```bash
sudo hexo clean && sudo hexo g && sudo hexo d
```

点击完成验证即可。

## 3.将内容推送至百度

### 一.[手动提交baidusitemap.xml](https://ziyuan.baidu.com/linksubmit/index)

![](https://pic.imgdb.cn/item/64966d361ddac507cc1a845b.webp)

点击sitemap

![](https://pic.imgdb.cn/item/64966d691ddac507cc1adc96.webp)

填入http://你的网址/baidusitemap.xml 提交即可

### 二.”抓取诊断”，手动-百度抓取

### 三.Robots → 检测并更新

![](https://pic.imgdb.cn/item/64966d581ddac507cc1ac360.webp)

robots配置

在你博客(hexo)根目录下的 source 文件夹中新建一个robots文件，填入一下内容。

```
User-agent: *
Allow: /
Allow: /archives/
Allow: /categories/
Allow: /tags/
Allow: /about/
Allow: /photos

Disallow: /vendors/
Disallow: /js/
Disallow: /css/
Disallow: /fonts/
Disallow: /vendors/
Disallow: /fancybox/
Sitemap: https://你的网址/sitemap.xml
Sitemap: https://你的网址/baidusitemap.xml
```

最后

```bash
sudo hexo clean && sudo hexo g && sudo hexo d
```

# 结语

这样下来你的Hexo博客就基本成型了，预祝你的博客越办越好！

ps.坐在电脑前一个上午，屁股好痛...
