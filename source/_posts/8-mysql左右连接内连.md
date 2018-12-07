---
title: 8.mysql左右连接内连
date: 2018-10-27 11:48:53
tags: mysql 
categories: mysql
preview:
---

# 左右内连查询

## 左连接:left

Select 列 1, 列 2,列 N from

tableA left join tableB

on tableA.列 = tableB [此处表连接成一张大表，完全当成普通表看]

where, group by having... 照常写



## 右连接：right

Select 列 1 , 列 2,列 N from

tableA right join tableB

on tableA.列 = tableB [此处表连接成一张大表，完全当成普通表看]

where, group by having... 照常写



## 内连接：inner

Select 列 1 , 列 2,列 N from

tableA inner join tableB

on tableA.列 = tableB [此处表连接成一张大表，完全当成普通表看]

where, group by having... 照常写



## 左右连接

以左表为准，去右表找匹配数据，找不到匹配用null补

A站在B的左边 ==》B站在A的右边

A left join B ==>B right join A

如何记忆：

1.左右连接可以互相转换

2.可以把右连接转换为左连接



## 内连接：

查询左右表都有的数据即，不要左右空的那一部分

内连接查询左右连接的交集