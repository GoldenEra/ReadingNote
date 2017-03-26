SQL虽然不区分大小写，但是大写关键字能和表区分开来
处理SQL语句时，所有空格都会被忽略

select distinct vend_id from products;
注意：不能部分使用distinct，如果使用 `select distinct vend_id,prod_name from pruducts` 将不会生效，除非 vend_id,prod_name都有重复的

limit 2，4 的意义和 limit 4 offset 2（MySQL 5之后开始）一样的意思，从第3行，检索4行

排序：
order by column1 asc ,column2 desc
当column1相等时，按照column2排列

排序时大小写问题，
A与a相同嘛？其答案取决于数据库设置

where 支持的条件操作符
```
=
<>
!=
<
<=
between a and b(a<=x<=b)
```

重要，**空值检查**，在数据库中，尽量不设置 Null值，设置默认值
null 表示 no value，他与0和“”不同，是具有特殊含义的
特殊的 where语句
```
select prod_name from products where prod_price is null
```
![](http://7xscq6.com1.z0.glb.clouddn.com/2017-03-26-030440.jpg)

NULL 值是有特殊含义的，在通过过滤选择出不具有特定值的行时，你可能希望返回具有NULL值的行，但是，不行。因为位置具有特殊的含义，
数据库不知道他们是否匹配，所以在匹配过滤或不匹配过滤时不返回他们。




