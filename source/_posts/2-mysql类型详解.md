---
title: 2.mysql类型详解
date: 2018-10-01 13:16:47
tags: mysql
preview: https://startzyp.github.io/imgs/log/2018-10-01/1.png
---

# 整数类型

| 类型      | 字节 | 位   | 无符号    | 有符号         |
| --------- | ---- | ---- | --------- | -------------- |
| Tinyint   | 1    | 8    | 0->2^8-1  | -2^7->2^7-1    |
| Smallint  | 2    | 16   | 0->2^16-1 | -2^15->+2^15-1 |
| Mediurnit | 3    | 24   | 0->2^24-1 | 2^23->+2^23-1  |
| int       | 4    | 32   | 0->2^32-1 | -2^31->2^31-1  |

unsignde 无符号值，影响存储范围

Zerofill:零填充，宽度一样，默认无符号

default:列的默认值,推荐声明默认值

Not null default 0 不能为空默认为0

```mysql
alter table class add age tinyint not null default 0;
```

# 浮点型与定点类

float(M,D)

decimal(M,D)

M： 为精度（总位数,不包含点）

D：标度（小数位）

如

float(6,2)

最大能存储 9999.99 最小-9999.99

unsigned 也只能存储 0-9999.99 （没有反码补码）

# 字符串类型

| 类型    | 说明       | 典型声明方式      | 范围                            |
| ------- | ---------- | ----------------- | ------------------------------- |
| char    | 定长字符串 | gender char(1)    | Char(M) 0<=M<=255               |
| Varchar | 变长字符串 | email varchar(20) | Varchar(M) 0<=M<=65535          |
| text    | 文本串     | centent text      | 约2W--6W个字符 （受字符集影响） |

区别

char:定长:M个字符，如果存定小于M个字符，实占M个字符

Varchar:M个字符，存的小于M个字符，设为N，则实占N+1-2个字符

速度上：定长快一些

如：

1.空间利用率，四字成语表，char(4)

网站个人简介用varchar(100)

# 日期时间类型

Date 日期

Time 时间

Datetime 日期时间类型  

Year 年类型

时间戳:

一般存储注册时间，并不上用datetime存储，而是用时间戳，

因为datetime虽然直观，但是计算不方便



# 建表小练习

```
给一个班级建立档案表
info：
姓名
年龄
email
手机号
简介
毕业薪水
入学时间
```

开始建表

```mysql
create table studentclass(
    id int primary key auto_increment,
	name char(20) not null default '',
	age tinyint unsigned not null default 0,
	email varchar(30) not null default '',
	tel char(18) not null default '',
	info varchar(1000) not null default '',
	money decimal(8,2) unsigned not null default 0,
	datetime int not null default 0
)charset utf8;
```

主键 自增长 

源数据

```mysql
id int primary key auto_increment,
```

