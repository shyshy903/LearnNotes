---
title: MySQL的安装与配置
categories: 软件安装与配置
tags: SQL
valine:
  path: /top/
---
# MySQL的安装与配置
## 下载软件与安装
1. 到`mySQL`的官网：[点击这里](
https://dev.mysql.com/downloads/mysql/)，看到下图，下载即可。
2. 解压缩到你所需要的路径
## MySQL配置
```yml
[mysqld]
# 设置3306端口
port=3306
# 设置mysql的安装目录
basedir=<你的路径>\mysql-8.0.11-winx64
# 设置mysql数据库的数据的存放目录
datadir=<你的路径>\mysql-8.0.11-winx64\\data
# 允许最大连接数
max_connections=200
# 允许连接失败的次数。这是为了防止有人从该主机试图攻击数据库系统
max_connect_errors=10000
# 服务端使用的字符集默认为UTF8
character-set-server=utf8
# 创建新表时将使用的默认存储引擎
default-storage-engine=INNODB
wait_timeout=31536000
interactive_timeout=31536000

#sql_mode=ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION
[mysql]
# 设置mysql客户端默认字符集
default-character-set=utf8

[client]
# 设置mysql客户端连接服务端时默认使用的端口
port=3306
default-character-set=utf8
```
## 环境变量配置
1. 系统变量添加
```yml
MYSQL_HOME  : path
```

2. 环境变量添加
```yml
%MYSQL_HOME%\bin
```
3. 如果上面2个方法都不想使用，可以使用下面这个方法：
![](https://img-blog.csdn.net/20180416193135760?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L20wXzM3Nzg4MzA4/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

## MySQL初始化
1. CMD运行
```bash
$ mysqld --initialize --user=mysql --console 
```
![](https://img-blog.csdn.net/20180416190435744?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L20wXzM3Nzg4MzA4/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)
务必记住这个初始密码，一会需要用这个初始密码登录mysql；  
修改密码如果emm你把他点没了 你只要把datadir配置的那个data的文件删除了，然后重新执行初始化即可然后输入：
```bash
mysqld --install
```
再打开服务：
```bash
net start mysql
```

## 修改默认密码
执行：
```bash
mysql -u root -p
```
登录,输入初始密码，接下来修改密码：
```bash
ALTER USER "root@"localhost" IDENTIFIED BY "your password"
```
## 其它
如果你在数据库连接工具的时候出现错误，则可以再`my.ini`文件中的`mysqld`中加入：
```bash
$ default_authentication_plugin=mysql_native_password
```
