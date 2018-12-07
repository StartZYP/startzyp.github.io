---
title: 6.where,from,exits子查询
date: 2018-10-04 16:59:38
tags: mysql
categories: mysql
---

# 良好的理解模型

Where 表达式，把表达式放在行种，看表达式是否为真

列: 理解为变量，可以运算

取出结果，可以理解为一张临时表

# Where子查询

要求 查询最新的商品（以id最大为最新）

```mysql
select goods_id,goods_name from goods order by goods_id desc limit 1
```

不让用order

```mysql
select goods_id,goods_name from goods where goods_id = 33;
```

想自动找最新的那么就用子查询

```mysql
select goods_id,goods_name from goods where goods_id = (select max(goods_id) from goods);
```

这样就能找到最新的了

这种是where类型的子查询

指的是把内层查询的结果作为外层查询的条件

用where类的子查询，查询每个栏目下最贵的商品

```mysql
select goods_id,goods_cat,goods_name,goods_price from goods where goods_price in (select max(goods_price) from goods group by goods_cat);
```

# from类子查询

定义：from子查询就是把子查询的结果(内存里的一张表)当作一张临时表，然后再对它进行处理。

from子查询解决上面问题
如：

```mysql
select tmp.article_id,tmp.article_content,article_comments from ( select * from article order by articlecategory_id,article_comments desc ) as tmp group by tmp.articlecategory_id;
```

# Exists子查询

把外层的查询结果，拿到内层，看内层的查询是否成立

查询有商品的栏目

```mysql
select goods_cat,goods_info,goods_id from goods where exists (select * from category where goods.cat_id=category.cat_id);
```

