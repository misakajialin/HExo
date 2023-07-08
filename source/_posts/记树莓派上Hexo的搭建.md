---
title: 记树莓派上Hexo的搭建
date: 2023-06-23 13:53:13
tags: 
- RaspberryPi 
- hexo
categories: 
- technology
---

# 前言

   首先感谢你能来访问我的 Blog，这是我搭建的第一个博客网站，使用的是 Github Pages + Hexo 的形式搭建。从小白一路走了过来也挺不容易的 hhh，我奋战一天一夜，从一开始的Aurora失败最后转投Hexo，可谓经历良多。现在把它记录下来，将来也许会是一种怀念。

<!-- more -->

<!-- more -->

# 准备工作

## 安装nodejs及npm

### 1. 寻找nodejs链接

进入[Node.js官网](https://nodejs.org/)

![](https://pic.imgdb.cn/item/649538dd1ddac507cc615530.webp)

点击`OtherDownloads`进入[下载页面](https://nodejs.org/en/download/)我们可以看到在`Linux Binaries (ARM)`下有着armv8即aarch64的包。

![](https://pic.imgdb.cn/item/649539d81ddac507cc635f23.webp)

树莓派上wget下载即可。

### 2.解压二进制包

在树莓派终端输入如下命令解压：

```bash
xz -d ~.tar.xz
tar -xavf ~.tar
```

先将系统内原本存在的`/usr/bin.node`删除，在终端输入：

```bash
sudo rm -rf /usr/bin/node
#如果不存在，忽略此步骤
```

解压后，将二进制包移动到`/usr/local/node`下，在终端输入：

```bash
sudo mv ./~ /usr/local/node
```

### 4.建立软连接

然后为`node`和`npm`建立软连接，在终端输入：

```bash
sudo ln -s /usr/local/node/bin/node /usr/bin/node
sudo ln -s /usr/local/node/bin/npm /usr/bin/npm
#这类似于Windows中的快捷方式
```

我们通过查看`node`和`npm`版本的方式来查看是否成功，在终端输入：

```bash
node -v && npm -v
```

可以看到对应的版本号说明**安装成功**，如下图（不同支持版或版本号不同）：

![](https://pic.imgdb.cn/item/64953b1f1ddac507cc65fb4d.webp)

## GitHub创建个人仓库

登录到GitHub,如果没有GitHub帐号，使用你的邮箱注册GitHub帐号：[Build software better, together](https://github.com/) 点击GitHub中的New repository创建新仓库，仓库名应该为：**用户名**.github.io这个**用户名**使用你的GitHub帐号名称代替，这是固定写法，比如我的仓库名为：![](https://pic.imgdb.cn/item/64953c2b1ddac507cc68229e.webp)

## 获取GitHub的taken

**这一部尤为关键！后面要用。**

### 1.登录github，点击设置

![](https://pic3.zhimg.com/80/v2-257b6563b9a331de7ba82fd959ac3096_720w.webp)

### 2.在左侧菜单点击开发者设置

![](https://pic1.zhimg.com/80/v2-1d93cc0bd336d0c8fbe46e741be7d358_720w.webp)

### 3.生成新的令牌

![](https://pic.imgdb.cn/item/649547931ddac507cc7ee595.webp)

### 4.点击创建完成创建

切记，**务必复制一下这个token，并且保存在某个文件里，否则之后只能编辑权限，找不到token值了，只能重新创建**。同时注意保护这个taken，这个taken的权利极其大！小心不要让它泄露了。

## 部署Git

在树莓派终端输入以安装Git：

```bash
sudo apt-get install git
```

配置Git信息

```bash
git config --global user.name "你的GitHub用户名"
git config --global user.email "你的GitHub注册邮箱"
```

然后查看是否已经全局修改用户名：

```bash
git config --list
```

配置完成后如下图：

![](https://pic.imgdb.cn/item/64953fa81ddac507cc6f5567.webp)

## Hexo的安装

新建一个文件夹并在此安装Hexo

```bash
mkdir blog
cd blog
sudo npm install hexo-cli -g
```

查看是否安装成功

```bash
sudo hexo -v
```

![](https://pic.imgdb.cn/item/64953e111ddac507cc6c2861.webp)

# 正式起航

## Hexo 初始化配置

第一个命令，为`hexo`建立软连接

第二个命令，初始化Hexo

第三个命令表示安装 hexo 部署到 git page 的 deployer，否则后面执行`hexo d`'时会出错。

```bash
sudo ln -s /home/lib/node_modules/hexo-cli/bin/hexo /usr/bin/hexo
sudo hexo init
sudo npm install hexo-deployer-git --save
```

### 本地查看效果

执行以下命令

```bash
sudo hexo g
sudo hexo s
```

执行完即可浏览器进入 [http://localhost:4000/](http://localhost:4000/) 查看效果

显示如下说明操作成功：  

![](https://pic.imgdb.cn/item/649541571ddac507cc72b406.png)

确认完后回到ssh按Ctrl+C退出。

## 将博客部署到Github Pages 上

  到目前为止，我们的本地博客就成功搭建了，但是现在我们只能通过本地连接查看博客，我们要做的是让其他人也能够访问我们的博客，这就需要我们将博客部署到 Github Pages 上。

我们需要配置博客根目录下的`_config.yml`文件，在终端输入：

```bash
sudo vim _config.yml
```

进入`_config.yml`后到文件末端，如下图 将此处修改为

```text
# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:
  type: git
  repo: https://github.com/你的账户名/你的账户名.github.io.git
  branch: master
  #注意这里的冒号后要加空格
```

类似这样：

![](https://pic.imgdb.cn/item/649542bb1ddac507cc75ab3b.webp)

在 blog 文件夹下分别执行以下命令

```
sudo hexo clean && sudo hexo g && sudo hexo d
```

期间要输入用户名和密码（taken）,用户名输入你的GitHub用户名即可，但是密码不是你的GitHub密码，而是taken！至于taken，一步步按上文走的你应该有了。

![](https://pic.imgdb.cn/item/649544241ddac507cc78855b.webp)

至此，你的博客已经上传至GitHub了！

## 访问博客

你的博客地址：https://你的用户名.github.io， 比如我的是：https://misakajialin.github.io ，现在每个人都可以通过此链接访问你的博客了!（感动）

# 后言

至于接下来内容，就期待我的第二篇博客吧！
