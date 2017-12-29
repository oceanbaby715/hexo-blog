---
title: java开发中使用jquery tmpl模板的小问题
date: 2017-07-24 15:16:35
tags: ["java","jquery-tmpl"]
categories:
- 前端
- Jquery
- 插件
- tmpl
---

使用tmpl模板进行数据绑定的时候，可以用`${字段名}`的方式来进行绑定
```
<script type="text/x-jquery-tmpl" id="replylist1">
    <div quetionNo=${question}>
                
    </div>
</script>
```

这样做是没有任何问题的，但是当我们在java项目中进行开发时，会发现上面的绑定方式不起作用，这个是什么原因呢？
原因就是在java中$代表的是一个关键字，java本身会对这个$符号进行解读，导致tmpl不起作用，当然在.net中不会有这个情况，所以我们需要换一种绑定的方式.

```
<script type="text/x-jquery-tmpl" id="replylist1">
    <div quetionNo={{= question}}>
        //{{= 字段名}} 注意等号后面有空格
    </div>
</script>
```

这样我们在java项目中也可以用tmpl模板来进行数据绑定了