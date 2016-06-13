---
layout: post
title: git 和gerrit 使用中遇到的问题
categories: [general]
tags: [reachzhai, work]
description: git 和gerrit 使用中遇到的问题,公司内部分享后总结记录，后面会不定期更新，作为自己的笔记？……<阅读全文>
---
## git 和gerrit 使用中遇到的问题


------
###git 部分的问题
####git 的命令与git 可视化工具使用的比较

1. 可视化工具不能给出提示和下一步怎么做
2. 使用命令，时效性高，理解git的代码管理更深刻
https://www.zhihu.com/question/22932048

 
####git 文件的状态？

git status//展示当前的工作目录下的文件状态
未纳入版本控制或者修改中  
已修改完成，待提交 
提交（已提交）


####git add  和svn 的add的区别？
git add 只是单纯的把文件从修改状态变成 等待提交
svn add  把新增的文件加入到版本控制


####git commit 和svn的commit的区别?
git commit 把代码提交到本地仓库
svn commit 把代码提交到服务器仓库


####git pull --rebase 和svn update的区别呢？
基本完全一直，git pull --rebase 相当于svn的update，只不过前者会对本地代码的记录排序并整理


####git pull 和git pull --rebase的区别？
基本完全一直，git pull --rebase 意义上和git pull一样，只不过前者会对本地代码的记录排序并整理
如果本地有处于修改中的文件，那么无法使用git pull --rebase


####简单测试一下git的使用
例如：新建一个activity叫A，并最提交 ，使这个A的代码进入审核过程

```powershell
git add A.java 
git commit -m "A功能"
git push origin HEAD:refs/for/master
```

例如：修改一个activity叫A（A已经在git版本控制的管理），并最提交 ，使这个A的代码进入审核过程
``` powershell
git add A.java 
git commit -m "A功能"
git pull --rebase //注意 先更新，再push
git push origin HEAD:refs/for/master
```
例如：删除一个activity叫A（A已经在git版本控制的管理），并最提交 ，使这个A的代码进入审核过程
``` powershell
rm A.java //或者直接删除文件
git add A.java 
git commit -m "A功能"
git pull --rebase  //注意 先更新，再push
git push origin HEAD:refs/for/master
```

####git 分支，本地分支和远程分支如何区分？master 、origin/master
 **git checkout -b  新建的本地分支名 **
注意：是以当前状态新建出来的分支，包括修改中的文件,本地分支更新不了远程仓库的代码！所以本地分支，在代码审核通过之后就可以删除了

**git branch -D 本地分支名  强制删除本地分支**
注意：分支间的切换，哪些modify的文件会跟随，但不是隶属于某个分支，如果要保存这个修改 那就在对应的分支进行 git commit -m “XXX”

**远程分支的管理是由具有管理员权限的人负责**



####git的本地分支怎么用？

默认在本地的master开发:
**如果要开发三个功能，分别是A，B，C，而且要同时开发,A正在master上开发，突然B的任务优先级提高，要进行B的开发**

1.在master上把有关A的操作保存起来，保存的方式有两种：
**方式一：**
``` java
//（不创建分支的情况下）
...
git add 修改的文件

git commit -m “A”

//(推送到gerrit上做个保存)，注意：当需要在进一步开发的时候，再从gerrit上取下来
git push origin HEAD:refs/for/master 

//紧接着，把本地的状态回退到做A之前的样子 
git reset --hard HEAD~1 // (倒退一步)

//开始开发B
...
```
**方式二：**
```java
//（新建分支）
...
git stash，//将当前的修改保存起来，保存到暂存区

//新建分支A,并切换到A分支上
git checkout -b A

//把暂存区的内容取出来
git stash pop

git add 修改的文件，

git commit -m “A”  //这是本地新建分支保存

//紧接着，回到master分支
git checkout master，

//回到master上开发B
...
```

**此时如果B开发完了，想继续开发A**

```java
方式一：
git cherry-pick  commit的sha值 
继续修改
提交的时候用git commit --amend

方式二：
切换到A分支继续开发，
继续修改
提交的时候 用git commit --amend
```


####git push origin HEAD:refs/for/master 推送后还要到gerrit上填写reviewer的人，太繁琐？
找到本地的git代码下的.git 目录
 
在config这个文件里的最下面添加如下内容：

```powershell
[remote "review"]
	url = ssh://zhailong@ip地址:29418/QDReader_android.git
	push = HEAD:refs/for/master%r=suhang@yuewen.com,r=huangzhaoyi@yuewen.com
```

配置后，一步到位，git push review (无需在去网站填写review的人了)

-------
###gerrit上的一些问题
####访问地址：http://ip地址:8091   出现如下问题，只需重新访问gerrit的地址



####不能merge的代码问题：

can not merge
指的是代码上库是发生了冲突，需要commiter 在自己的电脑，进行更新代码git pull --rebase,修改冲突，git add 冲突文件，git commit --amend，然后在用push的命令推送上去即可



####无权查看代码的问题：

无法查看别人提交的代码
登录的时间太长了，session失效，点击网页右上角的sign out ，然后再次访问gerrit的地址就可以




####已经提交到gerrit上的代码，再次修改
先git log 查看最新一笔是不是自己原来提交的那笔
然后在git commit --amend，在git push origin HEAD.....

####gerrit上已经审核通过的代码，要再次修改
此时不可以使用git commit --amend，审核通过的代码对应的修改已经被关闭，必须要从新起笔


###建议几个使用注意：
####1 用git pull --rebase 代替git pull
####2 代码在push之前，先git pull --rebase
####3 不论怎样，当要修改与当前修改不一致的东西，都可以把代码先推送到gerrit ，gerrit有备份的功效
####4 顺序 git add xxxx , git commit -m "msg", git push origin HEAD:refs/for/master

------



