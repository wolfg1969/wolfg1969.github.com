---
layout: post
title: "今天用到的两个命令"
date: 2012-11-12 17:39
comments: true
categories: git
---

今天用到了两个git命令：

把本地打的标签推到远程仓库
--------------------------

```
$ git push --tags
```

这个用在git flow release finish之后，把新建的版本tag推到中心库里。

删除远程仓库里的废弃分支
------------------------

```
$ git branch -D depreated_branch
$ git push origin :depreated_branch
```

