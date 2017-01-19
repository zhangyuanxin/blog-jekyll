---
layout: post
title: Nginx Setup
comments: true
author:  张远馨
categories: [Nginx,Setup]
image: https://unsplash.it/2000/1200?image=1062
image-sm: https://unsplash.it/500/300?image=1062

---

![nginx](/assets/images/nginx-logo.png)

    摘要: 使用源的方式安装nginx的操作方式. 安装环境是 阿里云Ubuntu Server 14.


1.  在源中添加资源

  在/etc/apt/sources.lst中 添加下面两源：

```java
eb http://nginx.org/packages/mainline/ubuntu/ trusty nginx
deb-src http://nginx.org/packages/mainline/ubuntu/ trusty nginx
```

2.  添加key到文件中

```java
cd /etc/apt
wget http://nginx.org/keys/nginx_signing.key
apt-key add nginx_signing.key
```

3.  安装nginx

```java
apt-get update
apt-get install nginx
```

4. 检查安装是否成功

```java
/usr/sbin/nginx -V
```
