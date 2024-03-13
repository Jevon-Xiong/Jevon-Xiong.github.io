---
layout: post
title: 个人博客设置
author: jevon xiong
tags:
- blog
- git
date: 2024-03-11 15:50 +0800
toc: true
---
# 基于Jekyll部署GitHub的个人博客设置

**GitHub Pages白嫖github服务器去做个人网站和博客**

**基础：WSL 、github账号**

1. **首先在github里新建一个同名仓库（uername.github.io）**
2. **采用在本地建好仓库再push**

**jekyll.com**

3. **在jekyllthems.org（模板网站里下载合适主题）**

**克隆对应模板的仓库到本地**

`git clone https://github.com/vszhub/not-pure-poole.git`

4. **jekyll的安装**

* **ruby环境–采用RVM（**[https://rvm.io/](https://rvm.io/)）
  **遇到的一些问题对应解决方法：**
  **（**[https://cloud.tencent.com/developer/ask/sof/106946061](https://cloud.tencent.com/developer/ask/sof/106946061)）
* **使用rvm安装ruby**
  `rvm list known`查看可安装ruby版本，推荐使用2.7.2
  `rvm install 2.7`安装对应版本的ruby
  `rvm use 2.7`激活2.7版本的ruby
  `rvm --version`查看当前安装的ruby版本
* **cd到对应本地仓库目录**

`cd ~/temps/not-pure-poole`

`bundle install`安装对应的包

`bundle install`之后执行一下`bundle`才能运行

---

5. **本地部署博客**

`jekyll s`执行服务器，通过地址可以在浏览器中实时访问博客状态

6. **编辑博客**

`code .`在对应文件目录下编辑博客

**更改**`_config.yml`修改blog基础个人信息

**修改之后重新**`jekell s`观察信息的改动

7. **添加自己的帖子**

**在**`_posts`目录中新建文件（按照固定格式），添加博客。

**根据需求把其他文件的上面部分复制过来**

```
 ---
 layout: post
 title: Releasing Not Pure Poole v0.1.0
 author: Songzi Vong
 tags:
 - jekyll theme
 - jekyll
 date: 2020-10-01 13:56 +0800
 ---
```

**之后安正常格式写markdown就行**

**无需**`sykell s`刷新

8. **推送到github服务器**

`git remote`基础操作（[https://www.runoob.com/git/git-remote.html](https://www.runoob.com/git/git-remote.html)）

`git remote -v`列出当前仓库中已配置的远程仓库，并显示它们的 URL。

`git remote remove origin`从当前仓库中删除origin远程仓库。

`git remote add origin git@github.com:Jevon-Xiong/Jevon-Xiong.github.io.git`添加一个新的远程仓库。指定一个远程仓库的名称和 URL(选择SSH协议)，将其添加到当前仓库中。

`git commit -m "Modify _config.yml"`修改config

`git status`查看仓库当前的状态，显示有变更的文件。

`git add -A`添加文件到暂存区

`git commit -m "add my fist post"`提交暂存区到本地仓库。

`git push -u master`上传远程代码并合并

---

# 修改和增加博客内容

**修改已提交的文章和内容**

`code .`直接进入vscode中进行修改并完成后

1. **先查看状态：git status**
2. **添加缓存区：git add -A**
3. **提交写注释：git commit -m “你的代码注释”**
4. **切换主分支：git checkout master**
5. **合并分支：git merge 分支名称**
6. **同步远程仓库：git push**

**最简单的是：**

`git status`

`git add -A`

`git commit -m “你的代码注释”`

`git push`

# md图片显示问题
采用本地图片上传到GitHub，
在浏览器中打开你在GitHub中已经上传好的图片，你可以在图片上右键，选择复制图片地址，也可以复制浏览器地址栏中的地址，然后使用在你的markdown图片外链地址上
但是你会发现还是不能加载出来，我在网上搜索了下，发现只要改路径的一个文件名就可以显示图片了。发现原来github和md文件关联的图片地址是有一定的格式的，其格式如下：
*https://github.com/用户名/repository仓库名/raw/分支名master/图片文件夹名称/.png or.jpg*

**简单来说就是blob更改为raw**