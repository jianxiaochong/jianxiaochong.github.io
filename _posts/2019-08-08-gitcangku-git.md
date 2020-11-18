---

title: Git远程仓库
author: jianxiaochong
date: 2019-08-09 11:33:00 +0800
categories: [Blogging, Demo]
tags: [git]
math: true

---

## Github简介
之前我们已经讲了如何在Git仓库里对一个文件进行操作，这些操作与SVN其实没有什么区别，看不出Git的特点

Git是分布式版本控制系统，同一个Git仓库，可以分布到不同的机器上。

在公司中况往往是这样，找一台电脑充当服务器，其他每个人都从服务器仓库克隆一份到自己的电脑上，并且各自把各自的提交推送到服务器仓库里，也从服务器仓库中拉取别人的提交。不过现在，为了学Git先搭个服务器没有必要。

我们可以借助[GitHub](https://github.com/)网站，GitHub 是一个版本控制和协作的代码托管平台，所以，只要注册一个GitHub账号，就可以免费获得Git远程仓库。


## 准备工作
首先需要各位自行**注册Github**账号。
由于本地GIt与Github仓库之间是通过SSH加密的，所以要先行设置一波。


创建SSH Key

在用户主目录下，看看有没有.ssh目录，如果有，再看看这个目录下有没有`id_rsa`和`id_rsa.pub`这两个文件，如果已经有了，可直接跳到下一步。如果没有，打开终端（Windows下打开Git Bash），创建SSH Key：

```
ssh-keygen -t rsa -C "邮箱地址"
```

输入完成后，一路Next，不用在管了，直接敲回车就行。
如无意外，我们进入到用户主目录可以找到`.ssh`目录，里面有`id_rsa`和`id_rsa.pub`两个文件就是SSH Key的秘钥，`id_rsa`是私钥，不能泄露出去，`id_rsa.pub`是公钥，就随意了。


在Github上配置密钥

登陆之后，点击头像下的`Settings`
![](https://img.kancloud.cn/94/1e/941ee3c9595e2461772012102217791f_1440x760.png)

点击`SSH and GPH keys`
![](https://img.kancloud.cn/a3/9a/a39a92ad6ed84f9e2af1002357a49499_875x770.png)

点击` New SSH Key`
![](https://img.kancloud.cn/5b/b9/5bb93ebd46cd3be302ada068b9954f72_1277x726.png)

填写密钥，Title随意填写，在Key文本框里粘贴`id_rsa.pub`文件的内容
![](https://img.kancloud.cn/14/4a/144a5934b90b8a951b2d34d16ecd602e_1168x680.png)

点“Add Key”，你就应该看到已经添加的Key：

只有添加了SSH Key，GitHub只要知道了你的公钥，就可以确认只有你自己才能推送。

如果你有多台电脑都需要连接这个github，就对添加几个Key就行了。

最后友情提示，虽然只有你能改，但是在GitHub上免费托管的Git仓库，任何人都可以看到，不要把敏感信息放进去。

## 添加远程仓库

我们现在的状况是本地已经有个远程仓库了。现在我想在Github上创建一个远程仓库，并且让这两个仓库同时工作。

登陆到Github，右上角`+`号，然后`New repository`
![](https://img.kancloud.cn/93/bd/93bddddca85e00c5249c55637ef54171_347x300.png)

输入仓库名称然后点击`Create repository`
![](https://img.kancloud.cn/de/a4/dea4f7cebe731e7663d9583454bfd9db_773x682.png)

点击`SSH`,获取远程仓库地址
![](https://img.kancloud.cn/37/1e/371e0e1a240216f8a81fcb6e59286d3d_1020x550.png)

在**本地**的仓库执行命令，将本地仓库与远程仓库想关联

语法：
```
git remote add origin 远程仓库地址
```

比如我的就是：
~~~
git remote add origin git@github.com:Excellent-electrician/project.git
~~~

然后我们就可以将本地的仓库推送过去

~~~
git push -u origin master
~~~
origin表示远程仓库的意思，master表示分支

注意，第一次的时候会弹出`SSH警告`
![](https://img.kancloud.cn/95/ab/95abfa67d3b290ec685a4ea7aefdf050_993x103.png)
填写`yes`即可，下次就无需填写


推送完成后，在Github上就可以看到所有内容了。
![](https://img.kancloud.cn/3b/74/3b74ffef5a6e9ba962fd7595d9df5ee0_1018x604.png)

后续如果本地仓库提交了新的内容，想推送到远程仓库
按照之前的操作，`add`之后,再`commit`，最后执行命令
```
git push origin master
```


![](https://img.kancloud.cn/8c/ab/8cab644fd738eaf85c5870108883634e_846x373.png)



## 克隆远程仓库

那如果是现有远程仓库的话， 我们也可以直接克隆远程仓库即可。
再在Github上创建一个仓库，这次勾选上`Initialize this repository with a README`
![](https://img.kancloud.cn/22/11/221152af8bffcc6a7311dfca47e94f0e_825x732.png)
勾选这个后创建仓库会多一个`README`文件

![](https://img.kancloud.cn/21/d6/21d62f01025c69a45f0207f9b7a081aa_1119x648.png)


像这样已经有了远程仓库，如果需要克隆，就点击绿色的` Clone or download`
![](https://img.kancloud.cn/7e/63/7e63c929db4f4765b07fdf987b483ac7_1031x559.png)

点击后，你可能会看到如下
![](https://img.kancloud.cn/36/73/36739c7c643b77b0cdd85b8459506928_548x296.png)

注意：github提供两种方式克隆与连接，一是Https，一是SSH
如图所示，`Clone with HTTPS`表示使用的是HTTPS，而我们使用的是SSH，所以你需要点击`User SSH`，点击后如下

![](https://img.kancloud.cn/a2/12/a21215ec995151e1930e06ebea6e9c02_491x277.png)

在本地找一个目录存放远程仓库，复制出路径，然后通过命令
```
git clone 远程仓库地址
```
比如我的：
```
git clone git@github.com:Excellent-electrician/project2.git
```

结果如下：
![](https://img.kancloud.cn/d3/bc/d3bc64ed2bb5a6c104ffa3c4b5836e3f_1071x247.png)




如果有多个人协作开发，那么每个人各自从远程克隆一份就可以了。

你也许还注意到，GitHub给出的地址不止一个，实际上，Git支持多种协议，默认的`git://`使用ssh，但也可以使用`https`等其他协议。

使用`https`除了速度慢以外，还有个最大的麻烦是每次推送都必须输入口令，但是在某些只开放http端口的公司内部就无法使用`ssh`协议而只能用`https`。
