---

title: 安装及使用
author: jianxiaochong
date: 2020-09-08 00:34:00 +0800
categories: [Blogging, Tutorial]
tags: [favicon]
toc: false

---
### Oracle11g 安装及使用

该教程以Oracle11g为例子，要使用的安装软件的[百度云链接](https://pan.baidu.com/s/1abnA_4I4mC5_7z6NoY2eAA )

提取码`1r0y `

下载好了之后如下所示

![安装软件](https://img.kancloud.cn/aa/ac/aaacd3dafdac1432c837d6fedb0f55dc_464x88.png)


### Oracle数据库安装


下载完成之后，将`oracle 11g.zip`文件解压到当前文件夹

![ ](https://img.kancloud.cn/b6/31/b6316d9b4aecac0ed51d3a2eefcb7ffa_378x44.png)

解压后，得到一个database的文件夹，进入到该文件夹，点击`setup.exe`文件

![ ](https://img.kancloud.cn/cf/cb/cfcb95fd396774272a0fb313470ed2ec_829x288.png)

在出现的“配置安全更新”窗口中，**取消**“我希望通过My Oracle Support接受安全更新”，单击“下一步”：

![ ](https://img.kancloud.cn/99/2c/992c06aa7d0347c559ce1c14f4cc956b_543x404.png)

出现下面的界面，点击“是”

![ ](https://img.kancloud.cn/00/ca/00caa985286b23c2480f30c212e4975e_505x377.png)

在“安装选项”窗口中，选择“创建和配置数据库”，单击“下一步”：

![ ](https://img.kancloud.cn/5b/3d/5b3dafc448ab6f47b8e9261d73c755bf_558x388.png)

在“系统类”窗口中，选择“**桌面类**”，单击“下一步”：

![ ](https://img.kancloud.cn/1a/92/1a92cbe664d186e590c321bfa70cf7c5_719x533.png)

在“典型安装”窗口中，选择Oracle的基目录，选择“企业版”和“默认值”并输入密码，单击“下一步”：

![ ](https://img.kancloud.cn/a7/80/a780d7cadee6861bc220d6a1257420d6_742x536.png)

* 注意：口令就是密码意思，密码自行设置，并牢记

如果出现以下界面，点击 是(Y)

![ ](https://img.kancloud.cn/91/34/9134f5890755d5c1a3781a6460b0ceac_631x380.png)


在“先决条件检查”窗口中，如果提示以下条件检测失败，选择“全部忽略”，然后，单击“下一步”：

![ ](https://img.kancloud.cn/5c/aa/5caaaf6aaa86add0aff546dc5b527227_633x746.png)

在“概要”窗口中，单击“完成”，即可进行安装：

![ ](https://img.kancloud.cn/1e/0d/1e0da7e0903a21c78844d322d6056c80_693x520.png)

数据库创建完成后，会出现如下“Database Configuration Assistant”界面,点击口令管理：

![](https://img.kancloud.cn/3e/2f/3e2f2cb9354d1b9a3d105096de74847e_718x499.png)

设置scott用户的密码，比如：admin123，如果没有操作这一步，后期也可以修改

![ ](https://img.kancloud.cn/d4/1b/d41ba4cf6ca5a1f9c6aaf51b96da7523_685x458.png)

修改完用户名后，点击确定，在以下界面下点击 关闭。

![ ](https://img.kancloud.cn/f7/f2/f7f2a913cf71d63016af51c8ee503844_685x517.png)


### 数据库连接工具使用

![安装软件](https://img.kancloud.cn/aa/ac/aaacd3dafdac1432c837d6fedb0f55dc_464x88.png)

解压`plsqldeveloper.zip`之后得到`plsqldeveloper`文件夹

进入到该文件夹，双击进行安装

![](https://img.kancloud.cn/24/9f/249f1cb843ad9e11bf30619f5e96a11d_622x136.png)

基本上傻瓜式安装

安装完成后启动PLsql

![ ](https://img.kancloud.cn/3e/61/3e61ce0b078e4e80890cb1cfc09aa9de_554x281.png)

登录之后，在左下角，鼠标右键`NEW`\&gt;&gt;&gt;`SQL WINDOW`

![ ](https://img.kancloud.cn/b0/a5/b0a5c44572e9ad55a3cbf8dbf12a7e38_756x623.png)

### 如何执行SQL 语句

![](https://img.kancloud.cn/cb/3e/cb3eef2cb332d06861a8448d3f195fea_1097x754.png)
