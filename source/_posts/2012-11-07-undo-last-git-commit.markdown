---
layout: post
title: "撤销最近一次提交"
date: 2012-11-07 16:50
comments: true
categories: Git
---

团队里的一位兄弟忘了切换分支就commit了，而且还push到了中心库。这就需要把这次commit给回退，操作如下：
```
$ git reset --hard HEAD~1
$ git push -f origin HEAD
```
当然，这是把这次commit彻底做掉了。如果想保留，就不使用--hard参数。当然，还有--soft参数，以后再研究。

Before reset:
```
   (F)
A-B-C
    ↑
   HEAD
```
After reset(--hard):
```
 (F)
A-B
  ↑
 HEAD
```
After reset:
```
   (F)
A-B-C
  ↑
 HEAD
```

参考：

  * [http://schacon.github.com/git/git-reset.html](http://schacon.github.com/git/git-reset.html)
  * [Undo last Git commit](http://stackoverflow.com/questions/927358/undo-last-git-commit)

