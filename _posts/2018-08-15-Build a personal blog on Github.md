---

layout: post
title:  利用Jekyll在Github上建立个人博客
date:   2018-08-15 10:15:00 +0800
categories: Git
tag: Github Pages

---

* content
{:toc}


---------------------------------------

### 0 绪言

前些天我看到同事**[卫广][1]**的个人博客，很是羡慕，也因此萌生了建立一个自己的技术博客的想法。花了一天时间查阅资料，我决定利用Github Pages平台，使用Jekyll构建自己的博客网站。建成后，正好将本次建立个人博客的流程记录下来，发布为我的第一篇博客，共享给有需要的人。

### 1 创建Github pages

在Github中建立一个repository，以用户名为名，如本文的[lzmzzw.github.io][2]。Github会自动开启Github Pages功能，在repo的setting栏中显示。

完成Github Pages创建后，将其clone到本地编辑，在本地添加index.html，上传至远程repo，即可在Github Pages上看到网页内容。

Git工具与Github网站使用可以参考[Git教程][3]、[Github教程][4]。

### 2 本地Jekyll部署

1. 安装Ruby，Windows可以直接下载[RubyInstaller][5](WITH DEVKIT版本)进行安装。在终端运行命令`ruby -v`，如终端能输出ruby版本信息，则安装成功。

2. 安装[RubyGems][6]，下载压缩包并解压，从终端进入解压路径，运行`ruby setup.rb`命令完成RubyGems安装。

3. 安装Jekyll，在RubyGems路径下运行命令`gem install jekyll`

### 3 jekyll文件目录结构

Jekyll 的核心是一个文本转换引擎，可以将各种标记语言如Markdown、 Textile、HTML文件套入一个或一系列的布局中，通过设置URL路径、文本显示样式，生成静态页面。一个基本的Jekyll网站的目录结构如下：

```
Myblog
│───README.md
│───config.yml                              #网站配置文件 
|───_drafts                                 #博客草稿
|   └───2018-08-15-hello world.md
|───_includes                               #被模板包含的HTML片段
|   |───header.html
|   └───footer.html
|───_layouts                                #网页排版模板
|   |───default.html
|   └───post.html
|───_posts                                  #博客内容
|    └───2018-08-15-hello world.md
|───_site                                   #jekyll生成的静态网页
└───index.html                              #网站首页内容
```

### 4 使用Jekyll博客模板

作为普通用户，我们可以直接从[jekyllthemes][7]网站下载Jekyll模板，修改模板构建自己的博客。

1. 下载模板并解压到本地网站目录，配置_config.yml文件

2. 从终端进入本地网站目录，运行命令`jekyll serve`

3. 从浏览器访问http://127.0.0.1:4000，即可看到个人博客网页。

### 5 撰写与发布博客

我采用Markdown文件格式撰写博客，md文件头如下，包含有博客标题、时间、类别、标签等信息，并使用文章目录。

```
---
layout: post
title:  Windows环境下采用Jekyll在Github上建立个人博客
date:   2018-08-15 10:15:00 +0800
categories: 
- Git
tag: 
- Github Pages
- jekyll
---

* content
{:toc}
```

完成博客撰写后，将md文件置入_posts文件夹中，push到Github的repo中，即完成博客的发布。

### 6 其他功能

 - 在地图中显示访客地理位置并统计，[Revolvermaps][8]。

 - 在博文下添加评论区域，[Disqus][9]。

 - 使用百度统计对网页流量进行统计，[百度统计][10]。


  [1]: https://okayjam.com/
  [2]: https://lzmzzw.github.io/
  [3]: https://www.liaoxuefeng.com/
  [4]: http://youngxhui.top/tags/GitHub/
  [5]: https://www.ruby-lang.org/en/downloads/
  [6]: https://rubygems.org/pages/download
  [7]: http://jekyllthemes.org/
  [8]: https://www.revolvermaps.com/
  [9]: https://disqus.com/
  [10]: https://tongji.baidu.com/web/welcome/login