---

layout: post
title:  解决MySQL配置账号密码遇到的错误
date:   2018-09-11 14:15:00 +0800
categories: Tips
tag: MySQL

---

* content
{:toc}


---------------------------------------


### 错误1：连接被拒绝
windows系统下运行`mysql -u root mysql`出现错误：

> Error 1045(28000) Access Denied for user 'root'@'localhost'

在windows操作系统安装mysql数据库，碰到`Error 1045(28000)`错误时，需要重新设置密码。
具体方法是：
 - 先在安装目录找到my.ini配置文件，打开配置文件，找到`[mysqld]`一行，在下面添加`skip-grant-tables`后保存该文件，重新启动mysql服务。
 - 然后在win终端执行

```
> mysql -u root mysql
> mysql> update user set password=password('yourpassword') where user='root';
> mysql> Flush privileges;
```
    
 - 将刚才my.ini配置文件的添加那一行去掉，重新启动mysql服务。

### 错误2：找不到password字段

> ERROR 1054 (42S22): Unknown column 'password' in 'field list'

新安装的MySQL5.7，登录时提示密码错误`ERROR 1054 (42S22)`，安装的时候并没有更改密码，后来通过免密码登录的方式更改密码，输入

```
> update mysql.user set password=password('yourpassword') where user='root'
```

时提示ERROR 1054 (42S22)错误，原因是mysql数据库下已经没有`password`这个字段了，`password`字段改成了`authentication_string`字段。
所以更改语句替换为下列语句即可：

```
> update mysql.user set authentication_string=password('yourpassword') where user='root'
```








