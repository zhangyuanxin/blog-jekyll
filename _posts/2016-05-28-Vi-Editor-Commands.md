---
layout: post
title: VI Commands
comments: true
author:  张远馨
categories: 
  - code
tags:
  - linux
  - vim
image: https://unsplash.it/2000/1200?image=685
image-sm: https://unsplash.it/500/300?image=685

---

> “由于最近工作经常要用到linux系统，但是命令都不是太熟悉，现在开始慢慢总结，不断练习，不断学习吧！” 

    
#### <a name="1" style="color:green;cursor: pointer">#</a> vi的使用教程（比较适合新手学习vi）：
    
1. [为什么要学习vi命令](#1)
1. [vi使用模式](#2)
1. [vi常用命令](#3)
1. [文件的打开关闭保存](#4)
1. [插入文本或新建行](#5)
1. [移动光标、删除、恢复字符或行](#6)
1. [搜索](#7)
1. [其他](#8)

#### <a name="1" style="color:green;cursor: pointer">#</a> 为什么要学习vi命令 ？

`vi`是visual interface的缩写，`vim`是vi IMproved(增强版的vi)。
    
- Linux很多发行版默认都安装了vi(vim)。
- vi/vim是Linux上最常用且很流行的编辑器（除此之外还有emacs、atom等）。
- 熟练使用vi命令可以提高工作效率。
- vim可以使代码高亮显示。


#### <a name="2" style="color:green;cursor: pointer">#</a> vi有3个模式：插入模式、命令模式、低行模式

- 插入模式：在此模式下可以输入字符，按ESC将回到命令模式。
- 命令模式：可以移动光标、删除字符等。
- 低行模式：可以保存文件、退出vi、设置vi、查找等功能(低行模式也可以看作是命令模式里的)。

#### <a name="3" style="color:green;cursor: pointer">#</a> vi常用命令

1.<a name="4" style="color:black;text-decoration:none"></a>文件的打开、保存、关闭操作(vi命令模式下使用)

| 命令 |释义说明|
| --- |  ---  |
|`vi [file]` |打开file文件|
|`:w`        |保存文件|
|`:w [file]` |保存至file文件|
|`:q`        |退出编辑器(未修改)|
|`:q!`       |退出编辑器（不保存修改）|
|`:wq`       |退出编辑器（保存修改）|

    
2.<a name="5" style="color:black;text-decoration:none"></a>插入模式：插入文本或行(vi命令模式下使用，执行下面命令后将进入插入模式，按ESC键可退出插入模式)

命令|释义说明
---|------------
a  |在当前光标位置的右边添加文本
i  |在当前光标位置的左边添加文本
A  |在当前行的末尾位置添加文本
I  |在当前行的开始处添加文本(非空字符的行首)
O  |在当前行的上面新建一行
o  |在当前行的下面新建一行
R  |替换(覆盖)当前光标位置及后面的若干文本
J  |合并光标所在行及下一行为一行(依然在命令模式)

    
3.<a name="5" style="color:black;text-decoration:none"></a>移动光标(vi命令模式下使用)

- 使用上下左右方向键

- 命令模式下：

命令           |释义说明
--------------|------------
h             |向左
j             |向下
k             |向上
l             |向右
空格键         |向右
Backspace     |向左
Enter         |移动到下一行首
-             |移动到上一行首

4.<a name="6" style="color:black;text-decoration:none"></a>删除、恢复字符或行(vi命令模式下使用)

命令   |释义说明
------|------------
x     |删除当前字符
nx    |删除从光标开始的n个字符
dd    |删除当前行
ndd   |向下删除当前行在内的n行
u     |撤销上一步操作
U     |撤销对当前行的所有操作

5.<a name="7" style="color:black;text-decoration:none"></a>搜索(vi命令模式下使用)

命令   |释义说明
------|------------
/abc  |向光标下搜索abc字符串
?abc  |向光标上搜索abc字符串
n     |向下搜索前一个搜素动作
N     |向上搜索前一个搜索动作

6.<a name="8" style="color:black;text-decoration:none"></a>跳至指定行(vi命令模式下使用)

命令   |释义说明
------|------------
n+    |向下跳n行
n-    |向上跳n行
nG    |跳到行号为n的行
G     |跳至文件的底部

7.<a name="9" style="color:black;text-decoration:none"></a>设置行号(vi命令模式下使用)

命令       |释义说明
----------|------------
:set nu   |显示行号
:set nonu |取消显示行号

8.<a name="10" style="color:black;text-decoration:none"></a>复制、粘贴(vi命令模式下使用)

命令       |释义说明
----------|------------
yy        |将当前行复制到缓存区，也可以用 "ayy 复制，"a 为缓冲区，a也可以替换为a到z的任意字母，可以完成多个复制任务。
nyy       |将当前行向下n行复制到缓冲区，也可以用 "anyy 复制，"a 为缓冲区，a也可以替换为a到z的任意字母，可以完成多个复制任务。
yw        |复制从光标开始到词尾的字符。
nyw       |复制从光标开始的n个单词。
y^        |复制从光标到行首的内容。
y$        |复制从光标到行尾的内容。
p         |粘贴剪切板里的内容在光标后，如果使用了前面的自定义缓冲区，建议使用"ap 进行粘贴。
P         |粘贴剪切板里的内容在光标前，如果使用了前面的自定义缓冲区，建议使用"aP 进行粘贴。

9.<a name="11" style="color:black;text-decoration:none"></a>替换(vi命令模式下使用)

命令               |释义说明
------------------|------------
:s/old/new        |用new替换行中首次出现的old
:s/old/new/g      |用new替换行中所有的old
:n,m s/old/new/g  |用new替换从n到m行里所有的old
:%s/old/new/g     |用new替换当前文件里所有的old

10.<a name="12" style="color:black;text-decoration:none"></a>编辑其他文件

命令                 |释义说明
--------------------|------------
:e otherfilename    |编辑文件名为otherfilename的文件。

11.<a name="13" style="color:black;text-decoration:none"></a>修改文件格式

命令                    |释义说明
-----------------------|------------
:set fileformat=unix   |将文件修改为unix格式，如win下面的文本文件在linux下会出现^M。


> 总结：vi(vim)虽然有比较多的命令，但是只要勤加练习，相信你会很快的熟练掌握，同时也会给你的工作或学习带来更高的效率。
> 当如果不知道自己处在什么模式时可以按2次Esc键即可回到命令模式。
> 最后提醒一点：注意大小写！！

参考连接：[Linux上vi(vim)编辑器使用教程](http://www.vpser.net/manage/vi.html)