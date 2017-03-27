```
说明：每种数据库都有自己的函数库，其中某些特殊函数只被某个特定数据库所拥有，所以使用特殊处理函数对于SQL的移植来说并不是一个很好的选择，
如果你决定使用函数，请写好注释。
```

MySQL函数大致分类

### 文本处理函数：
Left()
Length(),
Locate() 字符串的子串
这里单独介绍一个有意思的函数 Soundex()
https://dev.mysql.com/doc/refman/5.7/en/string-functions.html#function_soundex

函数将文本转化为描述其语音表示的字母数字木事的算法，直接例子
![](http://7xscq6.com1.z0.glb.clouddn.com/2017-03-27-145516.jpg)

两者的发音类似，所以能匹配

### 时间和日期函数
数据库已经有专门存储时间和日期的字段了，为什么有什么数据库还要将时间转化为时间戳以int方式保存，这样不仅不够直观，而且还面临着风险，int(11)最大为2147483647，为2018年，不管公司能不能开到那个时候，但作为技术人员的基本修养，存为int显然也是不合适

介绍几个可能会有用处的
* date(order_date) 仅仅提取列的日期部分 例如：date('2011-09-03 11:32:32') 返回 '2011-09-03'
* 如果选取2015年9月的订单，几种解决方案

1. 直接法
```
     where Date(order_date) between '2005-09-01' and '2005-09-30'
```
2. 使用函数提取年和月 
```
 where Year(order_date)=2005 and Month(order_date)=9
```

### 数值处理函数

Abs
Cos
Rand

### 聚集函数
avg
count
max
min 
sum
group_contact   拼接行字符串
全部的聚集函数
https://dev.mysql.com/doc/refman/5.7/en/group-by-functions.html

需要注意聚集函数对null的处理
count: 如果指定了行，则null会被忽略，count(*) 则不会
![](http://7xscq6.com1.z0.glb.clouddn.com/2017-03-27-154301.jpg)
sum/max/min:都会忽略值为null的行

聚集函数是用来汇总数据的，因为有时候并不需要数据本身，而是数据汇总的结果，所以返回实际数据并没有什么用，浪费带宽和资源。





所有函数的使用，其具体使用可以查询手册
https://dev.mysql.com/doc/refman/5.7/en/func-op-summary-ref.html