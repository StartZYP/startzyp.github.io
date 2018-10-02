---
title: 1.mysql入门增删改查
date: 2018-10-01 11:14:28
tags: mysql
preview: https://startzyp.github.io/imgs/log/2018-10-01/1.png
---

砥砺前行,加油.国庆学习mysql。

# 1.数据库登录

```
mysql -h -localhost -u root -p
```

然后就可以输入密码了

如果不写-h 那么就直接默认localhost

# 2.基本操作mysql语句

显示数据库 (mysql语句一定要以分号结束)

```mysql
show databases;
```

## 创建数据库

```mysql
create database php;
```

## 删除数据库

```mysql
drop database php;
```

## 选中数据库

```mysql
use php;
```

## 显示表

```mysql
show tables;
```

## 删除表

```mysql
drop table class;
```



## 创建表

```mysql
create table class(
    Student int,
    name varchar(20),
    age int,
    area varchar(20),
);
```

## 修改表名字

表名可以改库名，不能.

```mysql
RENAME table class to newclass;
```

## 图形化描述一张表

```mysql
description class;
```

也可以缩写

```mysql
desc class;
```

列出来表的信息

## 创建一个留言本

```mysql
create table msg(
	id int,
    title varchar(30),
    name varchar(20),
    content varchar(1000),
);
```

# 3.数据库增删改查语句

## 插入留言

```mysql
insert info msg(id,title,name,content) values (1,'初来乍到','张三丰','我这条语言是留言哦');
```

## 字符编码问题

默认建表一般用UTF-8，而我们windows窗口是GBK

所以需要声明一下使用和mysql一致的mysql编码

## 更新表

```mysql
update msg set id = 2 centent = '这是被修改的留言' WHERE name= '小李';
```

## 表内插入多行

```mysql
insert into msg (id,title,name,content) values (3,'标题3','名字3','内容3'),
(4,'标题4','名字4','内容4'),
(5,'标题5','名字5','内容5');
```

## 删除表

```mysql
delete from msg;
```

## 删除行

按条件删除第二行

```mysql
delete from msg where id = 2;
```

## 查询表语句

```mysql
select * from msg 
```

## 查询部分行列

```mysql
select id,name from msg;
```

## 小总结

```
select 控制列

where 控制行
```

