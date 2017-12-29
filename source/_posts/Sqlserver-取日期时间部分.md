---
title: Sqlserver 取日期时间部分
date: 2017-07-24 12:57:23
tags: ["sql","sql时间"]
categories:
- 数据库
- 实用语句
---

# 前言
在操作数据库时很多时候会对时间进行操作，这里做个记录

# 取时间部分

```sql
--取当前的时间 2017-07-24 12:58:23.493
SELECT GETDATE()

--取年月日 2017-07-24
Select Datename(year,GetDate())+'-'+Datename
(month,GetDate())+'-'+Datename(day,GetDate())

--取小时部分
Select Datename(hour,GetDate())

--取分钟部分
Select Datename(minute,GetDate())

--取秒部分
Select Datename(second,GetDate())

--获取是星期几
Select Datename(weekDay,GetDate())

--获取是第几周（是一年中的第几周，不是某个月的第几周）
Select Datename(week,GetDate())
```

------------

# 使用Convert()函数
SQL中的日期类型DateTime的默认格式就是yyyy-mm-dd hh:mi:ss: mmm
CONVERT() 函数是把日期转换为新数据类型的通用函数。
CONVERT() 函数可以用不同的格式显示日期/时间数据。

## 语法
```sql
CONVERT(data_type(length),data_to_be_converted,style)
```

data_type(length) 规定目标数据类型（带有可选的长度）。data_to_be_converted 含有需要转换的值。style 规定日期/时间的输出格式。

## 示例
```sql
SELECT CONVERT(varchar(100), GETDATE(), 0) --07 24 2017  1:39PM
SELECT CONVERT(varchar(100), GETDATE(), 1) --07/24/17
SELECT CONVERT(varchar(100), GETDATE(), 2) --17.07.24
SELECT CONVERT(varchar(100), GETDATE(), 3) --24/07/17
SELECT CONVERT(varchar(100), GETDATE(), 4) --24.07.17
SELECT CONVERT(varchar(100), GETDATE(), 5) --24-07-17
SELECT CONVERT(varchar(100), GETDATE(), 6) --24 07 17
SELECT CONVERT(varchar(100), GETDATE(), 7) --07 24, 17
SELECT CONVERT(varchar(100), GETDATE(), 8) --13:40:44
SELECT CONVERT(varchar(100), GETDATE(), 9) --07 24 2017  1:40:51:900PM
SELECT CONVERT(varchar(100), GETDATE(), 10) --07-24-17
SELECT CONVERT(varchar(100), GETDATE(), 11) --17/07/24
SELECT CONVERT(varchar(100), GETDATE(), 12) --170724
SELECT CONVERT(varchar(100), GETDATE(), 13) --24 07 2017 13:41:24:700
SELECT CONVERT(varchar(100), GETDATE(), 14) --13:41:33:640
SELECT CONVERT(varchar(100), GETDATE(), 20) --2017-07-24 13:41:41
SELECT CONVERT(varchar(100), GETDATE(), 21) --2017-07-24 13:41:48.817
SELECT CONVERT(varchar(100), GETDATE(), 22) --07/24/17  1:41:56 PM
SELECT CONVERT(varchar(100), GETDATE(), 23) --2017-07-24
SELECT CONVERT(varchar(100), GETDATE(), 24) --13:42:13
SELECT CONVERT(varchar(100), GETDATE(), 25) --2017-07-24 13:42:19.440
SELECT CONVERT(varchar(100), GETDATE(), 100) --07 24 2017  1:42PM
SELECT CONVERT(varchar(100), GETDATE(), 101) --07/24/2017
SELECT CONVERT(varchar(100), GETDATE(), 102) --2017.07.24
SELECT CONVERT(varchar(100), GETDATE(), 103) --24/07/2017
SELECT CONVERT(varchar(100), GETDATE(), 104) --24.07.2017
SELECT CONVERT(varchar(100), GETDATE(), 105) --24-07-2017
SELECT CONVERT(varchar(100), GETDATE(), 106) --24 07 2017
SELECT CONVERT(varchar(100), GETDATE(), 107) --07 24, 2017
SELECT CONVERT(varchar(100), GETDATE(), 108) --13:43:45
SELECT CONVERT(varchar(100), GETDATE(), 109) --07 24 2017  1:43:55:747PM
SELECT CONVERT(varchar(100), GETDATE(), 110) --07-24-2017
SELECT CONVERT(varchar(100), GETDATE(), 111) --2017/07/24
SELECT CONVERT(varchar(100), GETDATE(), 112) --20170724
SELECT CONVERT(varchar(100), GETDATE(), 113) --24 07 2017 13:44:44:743
SELECT CONVERT(varchar(100), GETDATE(), 114) --13:44:52:723
SELECT CONVERT(varchar(100), GETDATE(), 120) --2017-07-24 13:44:59
SELECT CONVERT(varchar(100), GETDATE(), 121) --2017-07-24 13:45:07.830
SELECT CONVERT(varchar(100), GETDATE(), 126) --2017-07-24T13:45:15.787
SELECT CONVERT(varchar(100), GETDATE(), 130) -- 1 ?? ?????? 1438  1:45:24:287PM
SELECT CONVERT(varchar(100), GETDATE(), 131) -- 1/11/1438  1:45:31:513PM
```

------------

# DATEADD()函数
在日期中添加或减去指定的时间间隔

## 语法
```sql
DATEADD(datepart,number,date)
```
date 参数是合法的日期表达式。number 是您希望添加的间隔数；对于未来的时间，此数是正数，对于过去的时间，此数是负数。

|   datepart   |   缩写       |
| ------------ | ------------ |
|   年         |  yy, yyyy    |
|   季度       |  qq, q       |
|   月         |  mm, m       |
|   年中的日   |  dy, y       |
|   日         |  dd, d       |
|   周         |  wk, ww      |
|   星期       |  dw, w       |
|   小时       |  hh          |
|   分钟       |  mi, n       |
|   秒         |  ss, s       |
|   毫秒       |  ms          |
|   微妙       |  mcs         |
|   纳秒       |  ns          |

## 示例
```sql
--加一年
SELECT DATEADD(yyyy,1,GETDATE())
--减一年
SELECT DATEADD(yyyy,-1,GETDATE())
--加一个月
SELECT DATEADD(mm,1,GETDATE())
--减一个月
SELECT DATEADD(mm,-1,GETDATE())
```

------------

# DATEDIFF()函数
返回两个日期之间的时间

## 语法
```sql
DATEDIFF(datepart,startdate,enddate)
```
startdate 和 enddate 参数是合法的日期表达式

|   datepart   |   缩写       |
| ------------ | ------------ |
|   年         |  yy, yyyy    |
|   季度       |  qq, q       |
|   月         |  mm, m       |
|   年中的日   |  dy, y       |
|   日         |  dd, d       |
|   周         |  wk, ww      |
|   星期       |  dw, w       |
|   小时       |  hh          |
|   分钟       |  mi, n       |
|   秒         |  ss, s       |
|   毫秒       |  ms          |
|   微妙       |  mcs         |
|   纳秒       |  ns          |

## 示例
```sql
SELECT DATEDIFF(yy,'2016-07-24','2017-09-30') --相差1年
SELECT DATEDIFF(dd,'2017-07-24','2017-09-30') --相差68天
```
