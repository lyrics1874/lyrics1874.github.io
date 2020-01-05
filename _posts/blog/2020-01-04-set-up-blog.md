---
layout: post
title: 手把手教你打造 github.io 博客
categories: Blog
description: github.io 可以理解为是 github 项目页面展示的功能，如果你正好想打造属于自己的个性化博客，那么快来尝试一下 github.io 吧！
keywords: github.io, 博客
---

github.io可以理解为是github项目页面展示的功能，如果你正好想打造属于自己的个性化博客，那么快来尝试一下github.io吧！(本文以 macOS 系统为例）

## 基本概念

### GitHub Pages
GitHub Pages 是 github 的静态站点功能，它可以用来建立一个网站页面从而展示和宣传你的项目，分为项目类型的 pages 和 用户类型的 pages。本文介绍的是建立用户类型的 pages，你可以在个人的 github 下创建 username.github.io 的 repository，然后将静态站点内容 push 到 master 分支，就可以通过 https://username.github.io 访问你创建的站点。(PS: username指的是你的 github 账户名)

### Jekyll
Jekyll 是一个免费的 Blog 生成工具，它可以将纯文本转换为静态博客网站，不需要数据库，不需要开发评论功能，不需要不断的更新版本——只用关心你的博客内容。支持自定义地址、博客分类、页面、文章以及自定义的布局设计。基于 Markdown（或 Textile）、Liquid 和 HTML & CSS 构建可发布的静态网站。

## 安装准备

### 依赖项
Jekyll 是基于 ruby 开发的，我们可以通过 ruby 的 gem 管理工具 bundler 来管理和启动 jekyll。安装 Jekyll 需要确保一些基本的依赖项已安装好，如 ruby、gcc、make、bundler 等。可以通过执行 which ruby、which gcc、which g++、which make、which bundle 或者 ruby -v、gcc -v、g++ -v、make -v、bundle -v 来确认。如果系统缺少依赖项的话就请先自行安装。

### Jekyll
执行以下命令安装 Jekyll:

```sh
sudo gem install jekyll
bundle install
```

## 开始创建

### 创建 github.io
首先在自己的 github 创建一个名为 username.github.io 的 repo，并将它 git clone 到本地，并创建一个简单的静态 html 来进行验证。（这里 username 指的是你的账户名）

```sh
git clone https://github.com/username/username.github.io
cd username.github.io
echo "Are you OK" > index.html
git add .
git commit -m 'init'
git push -u origin master
```

然后访问 https://username.github.io，如果你成功看到 “Are you OK”， 那么恭喜你，成功第一步啦！

### 下载 Jekyll 模板
Jekyll 的模板可以通过[官方下载](http://jekyllthemes.org/)或者[github](https://github.com/jekyll/jekyll/wiki/Sites)海淘。个人比较喜欢简约的风格，这里推荐两个：[码志](https://github.com/mzlogin/mzlogin.github.io)、[NexT](http://jekyllthemes.org/themes/jekyll-theme-next/)

Jekyll 模板的目录结构基本包含以下几个重要部分：

| 文件/文件   |   说明  |
|:------------|:--------|
| _config.yml | 配置文件|
| _drafts     | 存放草稿|
| _includes   | 页头、页脚之类的放于这个目录，可以使用  {% raw %}{% include header.html %}{% endraw %} 这样的标签在别的地方引用|
| _layouts    | 存放页面模板，可以在模板中使用 {% raw %}{{ content }}{% endraw %} 来引用页面内容|
| _posts      |存放动态的博客内容，标题格式必须为YEAR-MONTH-DAY-title.md|
| _data       | 存放其他yaml(yml)配置文件，如存了filename.yml，在别的地方可以使用site.data.filename引用相关数据|
| _site       | 存放使用 Jekyll 编译后的静态站点文件，最好在.gitignore中加入该目录|
| index.html  | 首页内容|

### 编写博客
把下载好的 Jekyll 模板放入到username.github.io目录中，然后完成自己想要的一些配置打造个性博客，并在 _posts文件内创建和编写自己的博客内容，然后再 push 到github 上就可以看到自己更新后的博客啦！

### 本地预览
在 push 到 github 之前，你可能想先预览博客效果，那么可以在username.github.io 目录下，执行

```sh
bundle exec jekyll serve
```

<div align="center"><img src="https://lyrics1874.github.io/images/blog/2020-01-04-set-up-blog.jpg"/></div>

然后通过 http://127.0.0.1:4000 即可预览效果。

### 直接Fork模板
除了以上方式创建 github repo 和下载模板外，你也可以直接在 github 上fork 别人模板，然后修改项目名称为和你的账户名对应的 username.github.io。再 git clone 项目到本地，直接对项目进行增删修改即可。

## 大功告成

至此，你的个人博客基本就搭建完成啦！
