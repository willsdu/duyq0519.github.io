---
layout: post
title: 上安装MySQL8.0后，Sequel Pro连接不上
date: 2018-10-23
categories: 数据库
cover: https://image.mmschool.club/github/sun.jpg
tags: mysql
---


## Mac 上安装MySQL8.0后，Sequel Pro连接不上

错误提示：
```
Failed to Connect to MySQL at 10.211.55.6:3306 with user root 

Authentication plugin 'caching_sha2_password' cannot be loaded: dlopen(/usr/local/mysql/lib/plugin/caching_sha2_password.so, 2): image not found
```
意思是找不到密码插件。这个是mysql版本升级后使用了新的密码插件，但是Sequel Pro还是用的老的插件，所以连不上。

### 解决
用终端进入mysql，修改root的密码插件

1. 为了安全，先新增一个用户
```
mysql>CREATE USER 'test'@'%' IDENTIFIED WITH mysql_native_password BY 'test';
``` 
发现是可以链接成功的，但是需要授权，那就试试修改一下root用户的密码和加密方式：

2. 再修改root用户的密码插件名字
```
mysql>ALTER USER 'root'@'%' IDENTIFIED WITH mysql_native_password BY 'root';
``` 
3. 再使用root密码登陆就可以了

###
> 这次连接是为了将测试数据库倒到本地，测试数据库时mysql 5.7 的版本，自己本机是8.0的版本，捣鼓了很长时间，就是不对
后来将本机的版本换成5.7的，分分钟就倒好数据了。


## 参考
作者：丁颖_3bd4
链接：https://www.jianshu.com/p/b482f879a76a
來源：简书
简书著作权归作者所有，任何形式的转载都请联系作者获得授权并注明出处。