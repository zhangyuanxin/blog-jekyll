---
layout: post
title: intellij IDEA 快捷键总结
comments: true
author:  张远馨
categories: 
  - code
tags:
  - IDEA
image: /assets/images/2017-03-28/intellijidea.jpg
image-sm: /assets/images/2017-03-28/intellijidea.jpg

---


> 正所谓：学而时习之，不亦说乎。

从毕业到现在一直使用Intellij IDEA开发工具，对于我来说它既熟悉又陌生的东西，真的想要相好的驾驭一个工具，需要经常总结使用经验。



#### 文本编辑 

       删除 ----- Ctrl + Y
       复制 ----- Ctrl + D

#### 智能提示

       提示 ----------------- Ctrl + Space
       智能提示 -------------- Ctrl + Shift + Space
       完成当前语句 ----------- Ctrl + Shift + Enter
       将临时变量变成方法入参 --- Ctrl + Alt + P
       格式化代码 ------------- Ctrl + Alt + L
       格式化类引用 ----------- Ctrl + Alt + O

#### 位置定位

       定位到下一个或上一个错误 --- F2 / Shift + F2
       定位文件头 -------------- Ctrl +G（定位到文件行数）
       定位文件尾 -------------- Ctrl +G    
       定位到代码块开始 --------- Ctrl + \[
       定位到代码块结束 --------- Ctrl + \]
       回到最近的窗口 ----------- F12
       回到之前的文件 ----------- Alt + Left
       回到之后的文件 ----------- Alt  + Right
       定位到最后编辑位置 -------- Ctrl + Shift + Backspace
       切换到文件编辑 ----------- Esc
       关闭最近打开的窗口 -------- Shift + Esc

#### 类、方法、文件定位

       查找类 ------------- Ctrl + N
       查找文件 ----------- Ctrl + Shift + N
       符号定位 ----------- Ctrl + Alt + Shift + N
       查看文件结构 -------- Ctrl + F12
       最近打开的文件 ------ Ctrl + E
       定位下一个方法 ------ Alt + Down
       定位上一个方法 ------ Alt + Up
       查看方法参数信息 ---- Ctrl  + p
       查看方法、类的doc --- Ctrl + Q

#### 类、方法的结构查看、定位

       跳到类或方法的声明 ------ Ctrl+ B
       定位到类的父类、接口 ---- Ctrl+ U
       查看类的继承结构 ------- Ctrl + H
       查看方法的继承结构 ------ Ctrl+ Shift + H
       查看类或方法被调用情况 --- Ctrl+ Alt +H 
       原地参看类、方法的声明 --- Ctrl+ Shift + I

#### 运行与调试

  Compile and Run

       Ctrl + F9 -------------- Make project (compile modifed and dependent)
       Ctrl + Shift + F9 ------ Compile selected file, package or module
       Alt + Shift + F10 ------ Select configuration and run
       Alt + Shift + F9 ------- Select configuration and debug
       Shift + F10 ------------ Run
       Shift + F9 ------------- Debug
       Ctrl + Shift + F10 ----- Run context configuration from editor
      
  Debugging

       F8 -------------------- Step over
       F7 -------------------- Step into
       Shift + F7 ------------ Smart step into
       Shift + F8 ------------ Step out
       Alt + F9 -------------- Run to cursor
       Alt + F8 -------------- Evaluate expression
       F9 -------------------- Resume program
       Ctrl + F8 ------------- Toggle breakpoint
       Ctrl + Shift + F8 ----- View breakpoints