---
title: SQL 循环插入大量数据
date: 2017-07-24 11:38:12
tags: ["sql"]
categories:
- 数据库
- 实用语句
---


在项目开发中经常会造一些假数据来进行测试，但是每次写sql时都得到网上找语句，所以这里做下记录

```sql
DECLARE @i int  --声明i字段，字段类型
DECLARE @WeixinUserId NVARCHAR(50)
DECLARE @MicActivityId INT
DECLARE @LottertyTime DATETIME

SET @i=0  --设置i初始值
  
WHILE @i<5     --100为你要执行插入的次数
BEGIN  
SET @i=@i+1 --设置变量i的值
SET @WeixinUserId='open-sadfasdf-'+cast(@i as varchar)+'' 
SET @MicActivityId=@i+12
SET @LottertyTime=getdate() --当前系统时间
INSERT INTO ActivityLotteryRecord (WeixinUserId,MicActivityId,LottertyTime) VALUES  (@WeixinUserId,@MicActivityId,@LottertyTime)   --循环插入SQL语句  
END 
```