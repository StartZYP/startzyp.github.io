---
title: 3.mysql详细学习
date: 2018-10-02 10:23:50
tags: mysql
preview: https://startzyp.github.io/imgs/log/2018-10-01/1.png
---

# 表的添加

```mysql
insert into studentclass(name,age,email.tel,datetimes) values ('刘雪莹',20,'liuxueyin@qq.com','13800138000',1579011111);
```

不写列

如果不写列名,默认插入所有的列，但是需要把每个值进行赋值（主键不需要）

```mysql
insert into studentclass values ('刘雪莹',20,'liuxueyin@qq.com','13800138000',1579011111);
```

一次性插入多个行

```mysql
insert into studentclass values ('刘雪莹',20,'liuxueyin@qq.com','13800138000',1579011111),('刘雪莹',20,'liuxueyin@qq.com','13800138000',1579011111),('刘雪莹',20,'liuxueyin@qq.com','13800138000',1579011111);
```

# 表 的修改

```mysql
update studentclass set name = '马超',tel = '138001380000' where id = 2;
```

# 表的行删除

```mysql
delete from studentclass where name = '马超';
```

# 表和表之间导数据

```mysql
insert into 库A.表名 select 字段,字段,字段 from 库B.表名;
```

B表导进A表