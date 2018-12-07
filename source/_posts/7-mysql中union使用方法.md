---
title: 7.mysql中union使用方法
date: 2018-10-19 17:24:41
tags: mysql
categories: mysql
---

# union使用方法

union:联合

作用：把两次或多次查询结果合并起来

要求：两次查询的列数一致

推荐：查询的每一列，相对应的列类型也一样

可以来自多张表

多次sql语句取出的列名可以不一致，此时以第一次sql的列名为准

ta

id,num

a,5

b,10

c,15

d,10



tb

id,num

b,5

c,10

d,28

e,99

create table ta(

in char(1),

num int

)

insert into ta

values

('a',5),

('b',10),

('c',15),

('d',10);



insert into tb

values

('b',5),

('c',10),

('d',20),

('e',99);

想得到结果

a,5

b,16

c,25

d,30

e,99

合并查询

```mysql
select * from ta 

union

select * from tb;
```

sum group求和

```mysql
select id,sum(num) from select(select * from ta 
 union select * from tb;) as newtable group by id;
```

如果不同的语句中取出来的行 有完全相同（每个列的值都相同）

那么相同的行会合并（去重复）

如果不去重复可以加all来合并

如果子句中有order by ,limit 必须加(),推荐放在 所有子句之后 最最终合并后的结果来排序

在子句中 order by 配合limit使用才有意义,如果order by 不与limit 使用会被语法分析器优化的时候去除 



