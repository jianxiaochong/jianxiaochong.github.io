---

title: git基本使用
author: jianxiaochong
date: 2019-08-08 11:33:00 +0800
categories: [Blogging, Demo]
tags: [git]
math: true

---

## 创建版本库
版本库又可以叫做仓库，可以简单理解成一个目录，这个目录里面的所有文件都可以被Git管理起来。
我们可以先在本地创建一个文件夹，当作仓库。
* 注意，不管是`windows`系统还是`Macos`系统,切记，仓库的路径中不得含有中文。

通过命令行进入到该目录，由于该我的电脑是Mac，所以我的截图会是Mac的截图。但与windows无太多区别。

比如我的仓库目录为 ` /Users/samwang/Desktop/project`

使用`git init`初始化仓库
```
cd /Users/samwang/Desktop/project
git init
```
执行结果
```
Initialized empty Git repository in /Users/samwang/Desktop/project/.git/
```


 `project` 文件夹中出现一个叫做 `.git` 的隐藏文件，该文件夹的内容就是用来管理`Git`的，所以注意这里边的东西眼看手勿动。

****

## Git 的核心框架

再学习`git`之前，我们先来学习Git的`核心框架`，了解了核心框架，我们就能够更快的掌握`Git`了。
他们分别是：
1. 工作目录：`就是我们的本地目录，我们在本地添加或修改文件`
2. 暂存区域：`准备提交到仓库的区域，我们称之为暂存区域`
3. Git仓库：`从暂存区域提交到Git仓库的内容`

所以我们想要完成向`Git`仓库提交文件的话需要做如下操作：
1. 在工作目录中添加、修改文件；
2. 将需要提交的文件放入暂存区域；
3. 将暂存区域的文件提交到 Git 仓库。

因此，Git 的文件有三种状态：已修改（modified）、已暂存（staged）和已提交（committed），依次对应上边的每一个流程。


## 将本地文件提交到仓库

当我在本地创建了`code.py`文件想要提交仓库，那么之前我们就提到了，将一个文件上传到仓库，需要先提交到暂存区域，然后再将暂存区域的文件提交到仓库

将本地文件提交到暂存区域(该命令不会有任何返回结果)
语法：
```
git add 文件名
```
提交`code.py`文件
```
git add code.py
```

现在我们已经将`code.py`文件提交到了暂存区域，再将文件提交到 Git 仓库
语法：
```
git commit -m "注释，解释"
```
将暂存区域的文件提交到仓库
```
git commit -m "提交了code.py文件，实现xx功能"
```


需要注意的是：如果没有使用 -m 选项，Git 会自动打开一个编辑器，要求你在其中输入提交说明（操作命令与 vi 编辑器一致）。



&gt;## 查看Git的状态

命令`git status`
使用 git status 命令查看当前的状态

`On branch master` 告知我们处于“master”的分支，这是Git默认的分支
`nothing to commit, working directory clean` 说明你的工作目录没有需要提交的文件
`Untracked files` 说明本地新添加但未加入到暂存区域的文件



比如我现在在本地新增一个`main.py`文件，然后在查看一下状态
![](https://img.kancloud.cn/29/9a/299a362f995260cd338f34312b2ed805_882x162.png)

括号中git 给我们的建议：使用 git add &lt;file&gt; 命令将待提交的文件添加到暂存区域。

我决定接受他的建议将文件新增到暂存区域，然后再查看一下，暂存区域有未提交到仓库的话，是一个什么状态。

![](https://img.kancloud.cn/0d/d8/0dd865f7ff4f43b0941a48a7d927edf2_818x137.png)

我们看，现在git提示我们`git restore --staged 文件名`意思是“如果你反悔了，可以将该文件**取消暂存**”。

比如，我现在将main.py取消暂存
```
git restore --staged main.py
```
![](https://img.kancloud.cn/1d/a4/1da42800325f3724d179a2e17b56af35_856x197.png)


那如果同一个文件，我提交到了到暂存区域后，又再次在本地修改了，此时我查看状态就会存在如下情况。


![](https://img.kancloud.cn/4b/3c/4b3c9d06f50ddcce29821515c48b063a_774x214.png)

注意：我们回想一下我们学的`add`与`commit`命令
`git add 文件名`是将本地的内容提交到暂存，如果此时我们执行这个命令，则是将本地文件覆盖了暂存区域的文件。
`git commit -m "注释"` 这个命令是将暂存区域的文件提交到仓库，注意，如果现在我们直接执行该命令，则是将修改之前的文件提交到仓库了。

我们再来看一下git提示的另外一个命令`git restore 文件名`,    这个命令使用要小心，他是将暂存区域的旧文件覆盖你本地的新文件

所以，如果你要将本地的新文件提交到仓库中，你需要两部
1. `git add 文件名`,先将本地文件覆盖暂存文件
2. `git commit -m "注释"` 再将暂存提交至仓库



## 回到以前版本

使用`git log`可以查看到每一次的提交

![](https://img.kancloud.cn/40/28/402876be1e4277e7203b5bede4ab415b_917x492.png)

我们每次commit一次，就是一个新的版本(也称之为快照)

如果想回到以前的版本，则需要使用`git reset`命令

我们想看看这个命令的用法：
`git reset 指定版本` 将git仓库与暂存区域的内容回滚到了指定版本,并未修改你的本地目录

`git reset --soft 指定版本`只是将仓库的内容，回滚到了指定版本

`git reset --hard 指定版本`将本地、暂存、仓库的都回滚到上一个版本

**指定版本**，版本如何表示？
两种方法：
1. 在git中，用`HEAD`这个单词表示最新的版本，如果想回到上一个版本则用`HEAD~1`,想回到上上一个版本用`HEAD~2`依此类推
2. 除此之外还可以指定版本号，如下图，`commit`后面的这一串东西就是我们的版本id，当然你不需要全部使用，可以用前6～7位就行了。
![](https://img.kancloud.cn/a1/15/a1153fefe74721a76cf782d3d4e6cfb5_731x488.png)

示例：
将回滚到上上上个版本
```
git reset --hard HEAD~3

```

回滚到id为`9470affbf54a49d87917837daa95cfe05fe3fe90`的版本
```
git reset --hard 9470aff
```

`git reflog`查看所有的提交的信息


&gt;## 修改最后一次提交的注释信息

```
git commit --amend -m &quot;新的注释信息&quot;`
```

## 重命名文件

有时候我们想修改一下文件名，如果文件没提交还好，如果提交了，此时直接修改名字，比如`main.py`已经提交，此时我将其重命名为`run.py`，此时对于git而言，你做了两件事，一是删除了`main.py`，二是新增了`run.py`，相比较会麻烦一点。所以git提供了重命名的命令`git mv 旧文件名 新文件名`。

![](https://img.kancloud.cn/f1/be/f1bec8456a5e9e20c28fc82649458c77_708x221.png)

## 删除文件
在git中删除文件还是一个比较麻烦的事情，需要使用命令
```
git rm 文件名
```