---
title: 5.having,limit,orderby使用详解
date: 2018-10-03 09:52:30
tags: mysql
categories: mysql
---

# having详解

having关键字在select 和where 之后

where 和select 称为查询

having是查询结果后的筛选

如

查询商店所有商品卖价与商城相比能省200以上的商品.

```mysql
select goods_id,goods_name,shop_price - goods_price as sheng having sheng > 200;
```

如图

![](https://startzyp.github.io/imgs/log/2018-10-03/1.png)

同上题,只查询第个栏目下比市场低200元以上的商品

```mysql
select goods_id,goods_chat,goods_name,shop_price - goods_price as sheng where goods_chat = 3 having sheng >200; 
```

查询积压货款超过2W点栏目。以及该栏目积压的货款

```mysql
select cat_id,sum(goods_price * goods_num) as jiya from goods group by cat_id having jiya >20000;
```

![](https://startzyp.github.io/imgs/log/2018-10-03/2.png)

题目如上图

```mysql
select 姓名,科目, sum(分数< 60 ) as bujigenum,avg(分数) as pjfen from stu group by 姓名 having bujigenum >=2;
```

不用左链接，不用子查询写法

# orderby排序

