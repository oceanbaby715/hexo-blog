---
title: windows实用脚本
date: 2017-08-14 11:12:08
tags: ["windows脚本"]
categories:
- 日常
- 实用类
---

# 前言
平常的工作中经常会做一下重复的事情，比如创建相同的目录结构的文件夹、定时备份等，结合windows中的任务计划可以帮助我们节省出一部分的时间，提高工作效率。

# 说明
在你的电脑桌面上新建一个文本文档并把后缀名修改为.bat,如："创建项目基本目录结构.bat",然后把实例中的代码写入保存即可。

# 实例

## 创建项目基本目录结构
### 说明
在项目开发中为了更好的管理和规范开发，所以需要创建固定的目录结构，但是每次都要手动创建又太麻烦了，如果从其他地方复制粘贴又得把多余不相干的文件删除掉，所以我们可以
写一个脚本，每次只需要把脚本复制到你的项目文件夹中双击就可以了。

### 脚本
``` bat
@echo off 
md "Documents"
md "SourceCode"
md "Documents/01.项目实施过程"
md "Documents/01.项目实施过程/01_准备"
md "Documents/01.项目实施过程/02_启动"
md "Documents/01.项目实施过程/03_开发测试"
md "Documents/01.项目实施过程/04_部署上线"
md "Documents/01.项目实施过程/05_客户验收"
md "Documents/02.项目交付"
md "Documents/02.项目交付/01_准备阶段_技术标书"
md "Documents/02.项目交付/02_准备阶段_SOW"
md "Documents/02.项目交付/03_项目启动阶段_项目计划"
md "Documents/02.项目交付/04_需求分析阶段_交付物清单"
md "Documents/02.项目交付/05_需求分析阶段_需求规格说明书"
md "Documents/02.项目交付/06_需求分析阶段_系统架构设计说明书"
md "Documents/02.项目交付/07_开发阶段_数据库设计说明书"
md "Documents/02.项目交付/08_开发阶段_UI设计说明书"
md "Documents/02.项目交付/09_测试阶段_测试计划"
md "Documents/02.项目交付/10_测试阶段&UAT阶段_Bug List"
md "Documents/02.项目交付/11_测试阶段&UAT阶段_用户手册"
md "Documents/02.项目交付/12_UAT阶段_测试报告"
md "Documents/02.项目交付/13_UAT阶段_部署手册"
md "Documents/02.项目交付/14_上线阶段_上线计划"
md "Documents/02.项目交付/15_验收阶段_项目验收报告"
md "Documents/02.项目交付/99_项目过程控制"
md "SourceCode/trunk"
md "SourceCode/branches"
md "SourceCode/tags"
```


------------

## 定时备份文件
### 说明
平常工作的一些文件需要做好定时备份，不怕一万就怕万一哪天你的电脑心情不好闹别扭硬盘罢工了，上个星期写好的方案不见了。
所以我们需要做好备份工作，把重要的文件上传都公司指定的服务器。

### 脚本
```bat
@echo off
echo.
echo 开始同步数据,请稍后...
echo.
xcopy "e:\重要数据备份\*.*" "Y:\技术部-资料备份\Terry" /y/e/s/
echo.
echo 数据同步完成
```

### 备注
`e:\重要数据备份\*.*`是我自己电脑上的E盘
`Y:\技术部-资料备份\Terry`是公司NAS上映射的一个路径
[关于xcopy参数说明请点这里](http://www.cnblogs.com/yang-hao/p/6003308.html "关于xcopy参数说明请点这里")


### 定时任务
脚本有了可是每次都得手动去点击，而且自己还容易忘记，所以这里就需要结合windows的任务计划来做定时备份了。
[Win7怎么设置定时自动执行任务](http://jingyan.baidu.com/article/6181c3e0435026152ef153d0.html "Win7怎么设置定时自动执行任务")
关于具体怎么添加请自行百度

------------

# 其他
[这里可以下载很多实例](http://download.csdn.net/download/whb3118/2246484 "这里可以下载很多实例")

[这里是我已经下载好了的文件](批处理大全.rar "这里是我已经下载好了的文件")
