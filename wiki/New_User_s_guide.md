---
layout: default
title: 新手指南
---

# 新手指南

## 练手

大家可以先修改一下这个页面[练练手](/wiki/New_User_s_excersice.html).

## 文件格式

* [翻译规范](http://www.freeswitch.org.cn/blog/past/2009/11/22/guan-yu-freeswitchwen-dang-fan-yi-de-yi-jian/)
* 新建页面只需在 wiki/ 目录下新建一个 xxx.md 文件，在其它文件中加入链接请参考其它已存在的页面。

## 流程参考

* 生成 SSH Key pair
* 上传你的 Public Key
    ssh-keygen -d
在windows 上使用 tortoise git 时可能需要在 pubkey 及 putty key 间转换。

* clone，以下地址有读写权限

    git clone git@github.com:freeswitch-cn/freeswitch-cn.github.com.git

* 修改 list.md，增加自己翻译的项目，防止多人重复劳动
* git commit, git push
* git pull
* 翻译
* git diff (**这个很重要，提交前一定先 diff 一下**)
* git commit
* git push

## 翻译进度

1. 正在翻译（已认领，正在译）
2. 正在校对（翻译完成，有人在校对）
3. 已完成（校对完成，可以放到这里）
4. 正在同步（英文文档已更新，需要重新同步更新的）

## Git 参考资料

* <http://progit.org/>
* <http://git-scm.org>

## 我的 git config

.gitconfig

<pre>
[alias]
        last = log -1 HEAD
        st = status 
        co = checkout 
        ci = commit 
        br = branch
        df = diff
        dfc = diff --cached
        pr = pull --rebase
        lg = log -p
        who = shortlog -s --

[color]
  status = auto
  branch = auto
  ui = auto

[master]
        branch = always
[core]
    whitespace = trailing-space,space-before-tab
    execludes = /Users/seven/.gitexcludes
[apply]
    whitespace = fix

</pre>
.gitexcludes

<pre>
.svn
</pre>
