---
layout: post
title: Linux中提示No such file or directory解决方法
comments: true
author:  张远馨
categories: 
  - Linux
tags:
  - command
image: /assets/images/2017-05-12/linux.jpg
image-sm: /assets/images/2017-05-12/linux.jpg

---

解决方法

分析原因，可能因为我平台迁移碰到权限问题我们来进行权限转换

1）在Windows下转换：
利用一些编辑器如UltraEdit或EditPlus等工具先将脚本编码转换，再放到Linux中执行。
> 转换方式如下（UltraEdit）：File-->Conversions-->DOS->UNIX即可。

2)方法
用vim打开xxx.sh脚本文件，输入set ff：

```cmd
// 用vim打开脚本文件
vi xxx.sh 

// 查看文件格式
:set ff  

// 回车显示文集格式
fileformat=dos

// 设置文件格式
:set ff=unix 

// 保存并退出
:wq!

// 再次执行
sh xxx.sh

```

3）当然，也可以在linux中权限转换，同时支持dos和unix两种模式

```cmd
// 确保文件有可执行权限
chmod u+x \<filename\> 

// 修改文件格式
vi \<filename\> 

```

三种方法都可以方便快速的解决关于Linux执行.sh文件，提示No such file or directory这个问题了。