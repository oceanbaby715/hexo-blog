---
title: 数据库定时导出并上传到FTP
date: 2017-08-14 17:06:14
tags: ["windows脚本","数据导出","上传FTP"]
categories:
- 日常
- 实用类
---
# 背景
项目开发中客户需要周天晚上12点把今天的数据导出并上传到相应的ftp上面。

# 导出数据库数据
## 编写语句

```
-- 允许配置高级选项
EXEC sp_configure 'show advanced options', 1
GO

-- 重新配置
RECONFIGURE
GO

-- 启用xp_cmdshell
EXEC sp_configure 'xp_cmdshell', 1
GO

--重新配置
RECONFIGURE
GO


--根据日期创建文件夹(2017-05-24)
DECLARE @s_time varchar(20)
DECLARE @e_time VARCHAR(20)
DECLARE @cmd VARCHAR(1000)
SELECT @s_time=convert(varchar(20),getdate(),23)
SELECT @e_time=convert(varchar(10),dateadd(dd,1,getdate()),120)
SET @cmd = 'mkdir  D:\export\'+@s_time
EXEC master..xp_cmdshell @cmd

--导出相应的记录
DECLARE @sql VARCHAR(1000)
SET @sql ='BCP "SELECT ''"iface"'' AS call,ApiName AS method,COUNT(*) AS TOTALcount 
FROM DataAgent.dbo.ApiCalled WHERE Vender = ''"Weixin"'' AND RequestTime > '''+@s_time+''' AND RequestTime < '''+@e_time+'''  
GROUP BY ApiName " queryout D:\export\'+@s_time+'\QencentCallWeChat.CSV -c -t\t -w"UTF-8" -U"sa" -P"Qxuninfo@123"'
--执行导出的BCP脚本   -w为编码
EXEC master..xp_cmdshell @sql

-- 允许配置高级选项
EXEC sp_configure 'show advanced options', 1
GO

-- 重新配置
RECONFIGURE
GO

-- 启用xp_cmdshell
EXEC sp_configure 'xp_cmdshell', 0
GO

--重新配置
RECONFIGURE
GO
```

###  添加定时任务
[SQL Server 创建定时任务JOB](http://blog.csdn.net/sinat_16998945/article/details/52586687 "SQL Server 创建定时任务JOB")

## 上传FTP
通过上面的步骤数据库中的数据已经导出成csv文件并保存在 "D:\export\" 目录下面，接下来需要用windows脚本上传到ftp上面

### 编辑脚本
上传到ftp需要用到一个软件`psftp.exe`,文末会提供下载地址。
![](微信图片_20170814173142.png)

**sftp.bat文件**
```bat
@echo off
set filename=%date:~0,4%-%date:~5,2%-%date:~8,2%
echo open data.xxx.cn.com > psftp_cmd.txt
echo cd /Test >> psftp_cmd.txt
echo put -r D:/export/%filename% >> psftp_cmd.txt
echo bye
psftp -l 用户名 -pw 密码 -b psftp_cmd.txt
exit
```
psftp_cmd.txt中的内容是自动生成的不需要管。

### 添加windows定时任务
[Win7怎么设置定时自动执行任务](http://jingyan.baidu.com/article/6181c3e0435026152ef153d0.html "Win7怎么设置定时自动执行任务")
也可以自行百度

# 下载
[定时上传FTP脚本](定时上传FTP脚本.zip "定时上传FTP脚本")
