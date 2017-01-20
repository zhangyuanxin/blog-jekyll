---
layout: post
title: Android Problems（Updating）
comments: true
author:  张远馨
categories: 
  - code
tags:
  - android
image: https://unsplash.it/2000/1200?image=1074
image-sm: https://unsplash.it/500/300?image=1074

---

Problem 1：

When you click ‘debug’ button，it will tips like below.

当点击debug按钮的时候，安装apk时提示内存不足。

```java
com.android.ddmlib.SyncException: No space left on device
Error while Installing APK
```

Solution：


Problem 2：

When you update android studio，it will tips like below.
当你更新Android Studio IDE的时候，会提示无法连接到android附加列表，天朝的墙太厚了。

```java
unable to access android add-on list
```

Solution：Please click ‘Cancel’ button，

Problem 3：

当新建Android项目时，如果Project路径含有中文或者非英文字体时，就会提示以下错误信息。
由此引发的启示：程序员的良好习惯应该所有的开发目录都是英文

```java
Error:(1, 0) Your project path contains non-ASCII characters. This will most likely cause the build to fail on Windows. Please move your project to a different directory.
```

Solution：Please move the project directory to a English-directory.

Problem 4：
Android AVD 默认目录调整：

Android模拟器，AVD默认保存在C:\Documents and Settings\Administrator\.android\avd，后来想改路径，找了很久终于找到了方法，亲测成功。
方法是：

1、比如你要把AVD放在D盘AndroidAVD下面，则预先在D盘下建立一个文件夹 AndroidAVD。必须的。不然设置了环境变量也没有用，因为模拟器不会自动创建该文件夹。

2、在桌面右击“我的电脑”选择“属性”，进入“高级----环境变量-----系统变量----新建“，从而新建一个环境变量ANDROID_SDK_HOME，变量值设置为：D:\AndroidAVD。如图所示。一路确定下来，保存环境变量。重新启动计算机。

3、如果你以前没有AVD，则启动AVD Manager新建一个AVD，则文件会全部保存到 D:\AndroidAVD下面。第4点不用看了。

4、如果你以前有AVD，改了路径后想继续用，则要把原来C:\Documents and Settings\Administrator\.android\avd下面的全部文件夹复制到 D:\AndroidAVD下面，把avd下面的.ini文件里面的路径 C:\Documents and Settings\Administrator\.android\avd部分全部改成D:\AndroidAVD\.android\avd。再进一个以.AVD结尾的文件夹改下面的hardware-qemu.ini这个文件里面的路径 C:\Documents and Settings\Administrator\.android\avd部分全部改成D:\AndroidAVD\.android\avd。
这2个ini文件里面的路径不改光复制文件过去没有用的，AVD Manager会报错且会删除复制过来的所有avd文件，但并不会删除和影响C:\Documents and Settings\Administrator\.android\avd下面的文件。

为保险，建议新的AVD启动正常能进安卓系统了以后，再把原来C:\Documents and Settings\Administrator\.android\avd下面的所有文件删除即可。
