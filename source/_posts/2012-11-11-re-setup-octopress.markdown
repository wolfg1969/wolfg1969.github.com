---
layout: post
title: "重建Octopress环境"
date: 2012-11-11 20:36
comments: true
categories: Git
---

在另一台机器上重新设置Octopress环境的步骤如下：

安装octopress
------------

```
# 安装rvm, ruby, bundler 略
# 克隆octopress
$ git clone git://github.com/imathis/octopress.git octopress
# 安装主题
$ rake install
```

设置github帐号
-------------

```
$ rake setup_github_pages
```

同步Github上已发布的博客
---------------------

```
# 覆盖本地修改
$ git checkout .
$ rm -rf saas source
$ git fetch origin
$ git merge origin/source
# 可能需要手动merge
```

开始写作！
-------
```
$ rake new_post[new_post]
$ rake generate
$ rake deploy
```
