---
title: 使用Hexo和Github搭建个人博客
date: 2020-11-06 21:04:21
image: https://gitee.com/AtomAlpaca/photos/raw/master/img/Photo001.jpg
categories: 建站
---

还是挺有意思的

<!--more-->

我感觉我把能踩的坑都踩了一遍QAQ

~~（还不是因为自己菜）~~

## 前言

首先回答几个问题

​	Q1.博客有什么用？

​	A1.~~用来在微机课上吹牛~~

​	Q2.为什么要用GitHub Page?

​	A2.~~因为穷，GitHub不收费~~

​		搭建快，只要一两个小时就可以搭建成功一个好看的博客

​		而且它是全静态的，没有乱七八糟的数据库，迁移很方便

​		GitHub的服务器比较稳定，不会被脚本小子攻击

## 准备工作

### 准备工具

首先，GitHub账号一定要有，免费账号就行，土豪随意

其次，需要安装[Git](https://git-scm.com/downloads)用来部署博客

还有[Node.js](https://nodejs.org/zh-cn/)，因为hexo就是Node.js编写的

（下载慢可以试试淘宝的镜像）

（版本无所谓，只要不用远古版本基本没什么大问题）

安装的话直接无脑下一步就行

安装完成后，Win+R 输入 cmd 并打开，

依次输入 

```bash
node -v
npm -v
git --version
```

如果每次都有一坨版本号出来呼你一脸说明安装成功了(ง •_•)ง

### 链接GitHub账号

随便找个地方右键，点Git Bash Here 设置：

```bash
git config --global user.name "你的GitHub用户名"
git config --global user.email "你用来注册GitHub的邮箱"
ssh-keygen -t rsa -C "你用来注册GitHub的邮箱"
```

进入 `C:\Users\用户名\.ssh`目录（提前勾选显示“隐藏的项目”，不然看不到！）

复制 `id_rsa.pub` 文件里面的东西

登陆 GitHub ，点击 Settings ，点击左边栏的 SSH and GPG keys，点击 New SSH key

Title 随便取个名字就行，粘贴复制的内容到 Key 栏中，点击 Add SSH key 完成添加。

打开 Git Bash，输入 

```bash
ssh -T git@github.com
```

出现 “`Are you sure……`”，输入 yes 回车。

显示 “`Hi xxx! You've successfully……`” 说明你连接成功啦

### 创建GitHub仓库

点击GitHub 主页右上角`New repository`：

Repository name 输入 `你的用户名.github.io`

勾选 “`Initialize this repository with a README`”

`Description` 填什么都行

填好后点击 `Create repository` 创建。

[![BhcXgf.jpg](https://s1.ax1x.com/2020/11/06/BhcXgf.jpg)](https://imgchr.com/i/BhcXgf)

### 安装 Hexo 博客程序

找一个**空的文件夹**（路径中尽量不要含有中文）

打开这个文件夹

右键，点击 Git Bash Here

使用 npm 一键安装 Hexo

```bash
npm install -g hexo-cli
```

注意，安装的时候她**不会给你提示**，不要以为这玩意不好使

安装时间很长，你可以想一想第一篇博客写什么，就不会和我一样

[![Bh5fnP.md.png](https://s1.ax1x.com/2020/11/06/Bh5fnP.md.png)](https://imgchr.com/i/Bh5fnP)



### 初始化并安装所需组件

```bash
hexo init      # 初始化
npm install    # 安装组件
```

这玩意也够慢的......

## 开始部署

首先安装 `hexo-deployer-git` 这玩意可以帮你把博客发到GitHub上

```bash
npm install hexo-deployer-git --save
```

然后博客文件夹中的 "_config.yml"末尾的 "Deployment"

```yml
deploy:
  type: git
  repository: git@github.com:用户名/用户名.github.io.git
  branch: main
```

然后后在Git Bash中运行 

```bash
hexo g
hexo d
```

完成！

如果一切顺利，你就可以通过 `你的用户名.github.io` 访问自己的网站啦！

## 正式使用

如果我们想创建一篇文章，只需要在Git Bash 中输入

`Hexo new "标题"`

稍等片刻！她需要一段时间进行创建，不要以为这玩意不好使......

如果 `source` 文件夹中会出现一个 叫 `标题.md` 的文件，说明创建成功啦

然后就可以使用 Markdown 编辑器在这个文件中写文章了

桥豆麻袋！

我文章写完了，怎么发布呐？

还是在 Git Bash 中输入

```bash
hexo g   # 生成页面
hexo d   # 部署发布
```

稍等，再访问你的博客，就能发现你的文章发布成功啦φ(゜▽゜*)♪

## 美化

我知道你想说什么，这个官方默认的主题太丑了...

[![Bhfwm8.md.png](https://s1.ax1x.com/2020/11/06/Bhfwm8.md.png)](https://imgchr.com/i/Bhfwm8)



[这个地址](https://hexo.io/themes/)汇总了很多主题

我最喜欢的，也是我现在用的是zhaoo主题（都别拦我我要吹爆这个主题！）

![BhhM3n.md.png](https://s1.ax1x.com/2020/11/06/BhhM3n.md.png)

在Git Bash中输入

```bash
git clone https://github.com/izhaoo/hexo-theme-zhaoo.git themes/zhaoo
```

修改  `_config.yml` 文件启用 zhaoo 主题：

```
theme: zhaoo
```

几乎每个主题都有自己的主题文档，按文档配置就好啦ヾ(•ω•`)o

完结撒花*★,°*:.☆(￣▽￣)/$:*.°★* 。