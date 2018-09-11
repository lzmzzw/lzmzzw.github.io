---

layout: post
title:  解决win系统端口被占用问题
date:   2018-09-11 14:20:00 +0800
categories: MySQL
tag: Tips

---

* content
{:toc}


---------------------------------------



1、打开终端

2、`netstat -ano`列出所有端口的情况，找到被占用的端口

3、输入命令`netstat -ano | findstr "8080"`找对应的PID

4、输入命令`tasklist | findstr "21548"`查找具体的占用进程

5、打开资源管理器，找到PID是21548的进程（没有PID这一列的话可以右击列添加PID列）

6、如果想结束进程，可以使用：`taskkill /f /t /im java.exe`（进程名）




