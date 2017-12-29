---
title: Sqlserver中判断表或者库是否存在
date: 2017-07-24 11:54:35
tags: ["sql"]
categories: 
- 数据库
- 实用语句
---

# 前言
在sqlserver中创建一个表、一个视图、存储过程中我们需要判断一下资源是否已经存在

# 判断库是否存在

```sql
IF EXISTS(SELECT * FROM master.dbo.sysdatabases WHERE NAME='您的库名') 
PRINT '存在'
ELSE
PRINT '不存在'
```

# 判断表是否存在

```sql
IF EXISTS(SELECT * FROM dbo.sysobjects WHERE id = OBJECT_ID(N'[dbo].[您的表名]')and OBJECTPROPERTY(id, N'IsUserTable') = 1)
PRINT '存在'
ELSE
PRINT '不存在'
```

# 判断列是否存在

```sql
IF COL_LENGTH( '您的表名','您的列名') IS NULL
PRINT '不存在'
ELSE
PRINT '存在'
```


# 判断临时表是否存在

```sql
IF OBJECT_ID('Tempdb.dbo.#您的临时表名') Is Not Null
PRINT '存在'
Else
PRINT '不存在'
```


# 判断存储过程是否存在

```sql
IF EXISTS (SELECT * FROM dbo.sysobjects WHERE id = OBJECT_ID(N'[dbo].[您的存储过程名]') AND OBJECTPROPERTY(id, N'IsProcedure') = 1) 
PRINT '存在'
ELSE
PRINT '不存在'
```


# 判断视图是否存在

```sql
IF EXISTS (SELECT * FROM dbo.sysobjects WHERE id = object_id(N'[dbo].[您的视图名]') and OBJECTPROPERTY(id, N'IsView') = 1) 
PRINT '存在'
ELSE
PRINT '不存在'
```

