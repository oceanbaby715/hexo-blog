---
title: 前端常用js方法整理
date: 2017-07-31 15:53:20
tags: ["前端","javascript","jquery","表单"]
categories:
- 前端
- JavaScript
- 实用类
---
# 前言

整理前端常用的一些函数

--------------

# 时间类

## UTC()
方法接受的参数同日期构造函数接受最多参数时一样，返回从1970-1-1 00:00:00 UTC到指定日期的的毫秒数。 
```javascript
Date.UTC(year,month[,date[,hrs[,min[,sec[,ms]]]]])
```

--------------

## now()
方法返回自1970年1月1日 00:00:00 UTC到当前时间的毫秒数。
```javascript
var timeInMs = Date.now()
```

--------------

## parse()
解析一个表示某个日期的字符串，并返回从1970-1-1 00:00:00 UTC 到该日期对象（该日期对象的UTC时间）的毫秒数
```javascript
Date.parse(dateString)
```

--------------

## getDate()
根据本地时间，返回一个指定的日期对象为一个月中的第几天。
```javascript
var data=new Date()
data.getDate()
```

--------------

## getDay()
据本地时间，返回一个具体日期中一周的第几天，0 表示星期天。
```javascript
var data=new Date()
data.getDay()
```

--------------

## getFullYear()
根据本地时间，返回一个指定日期对象的年份。
```javascript
var data=new Date()
data.getFullYear()
```

--------------

## getHours()
方法根据本地时间，返回一个指定的日期对象的小时。
```javascript
var data=new Date()
data.getHours()
```

--------------

## getMilliseconds()
根据本地时间，返回一个指定的日期对象的毫秒数。
```javascript
var data=new Date()
data.getMilliseconds()
```

--------------

## getMinutes()
根据本地时间，返回一个指定的日期对象的分钟数。
```javascript
var data=new Date()
data.getMinutes()
```

--------------

## getMonth()
根据本地时间，返回一个指定的日期对象的月份，为基于0的值（0表示一年中的第一月）
```javascript
var data=new Date()
data.getMonth()
```

--------------

## getSeconds()
方法根据本地时间，返回一个指定的日期对象的秒数
```javascript
var data=new Date()
data.getSeconds()
```

--------------

## add()
add(value,type)
在某个时间上新增时间，返回新增后的时间对象，格式不正确返回原时间对象，新增传正数，减传负数。
```javascript
var year = new Date().add(1,'y').format('yyyy-MM-dd'); //2018-03-24
var month = new Date().add(1,'M').format('yyyy-MM-dd'); //2017-04-24
var day = new Date().add(1,'d').format('yyyy-MM-dd'); //2017-04-25
var hour = new Date().add(1,'hh').format('yyyy-MM-dd HH:mm:ss'); //2017-04-24 12:34:27
var minute = new Date().add(1,'m').format('yyyy-MM-dd HH:mm:ss');//2017-04-24 11:35:27
var second = new Date().add(1 * 60,'s').format('yyyy-MM-dd HH:mm:ss'); //2017-04-24 11:35:27
var millisecond = new Date().add(1000 * 60 ,'ms').format('yyyy-MM-dd HH:mm:ss');  //2017-04-24 11:35:27
```

--------------

## addDays()
add(value,type)
新增指定天数，返回新增后的时间对象，格式不正确则返回原时间对象。
addHours()【新增小时】
addMilliseconds()【新增毫秒】
addMinutes()【新增分钟】
addMonths()【新增月】
addSeconds()【新增秒】
addYears()【新增年】
```javascript
var date = new Date();
var newdate = date.addDays(1).format('yyyy-MM-dd'); //2017-03-25
var newdate = date.addYears(1).format('yyyy-MM-dd'); 
var newdate = date.addSeconds(1).format('yyyy-MM-dd');
var newdate = date.addMonths(1).format('yyyy-MM-dd'); 
var newdate = date.addMinutes(1).format('yyyy-MM-dd');
var newdate = date.addMilliseconds(1).format('yyyy-MM-dd');
var newdate = date.addHours(1).format('yyyy-MM-dd');
```

--------------

## compareTo()
比较两个时间大小，前者大于后者返回1，等于返回0，小于返回-1
```javascript
new Date().compareTo(new Date('2017-03-24')) //1
```

--------------

## dayOfweek()
返回某个时间星期几
```javascript
new Date().dayOfweek()  //星期五
```

--------------

## diff()
比较两个时间，返回一个对象，包含一共差x天，或一共差x小时，或一共差x分钟，或一共差x秒，或一共差x毫秒，格式不正确所有参数均为0。
```javascript
var obj = new Date().diff(new Date('2017-03-24')) 
//Object {totaldays: 0, totalhours: 5, totalminutes: 345, totalseconds: 20732, totalmilliseconds: 20732392} 
var totalhours = obj.totalhours;  //5
```

--------------

## diffFormat()
用于计算两个时间一共差x天x小时x分钟x秒，格式不正确返回空字符串。
```javascript
new Date().diffFormat(new Date('2017-03-23'))  //1天 5小时 57分钟 35秒
```

--------------

## isLeapYear()
判断是否是闰年。
```javascript
new Date().isLeapYear()  //false
```

--------------

## isSame()
isSame(time,type)
判断两个时间的某个部分是否相同
【type只接受年月日和’date’,’all’,其中date用于判断年月日，all判断1970至现在的秒数】

```javascript
new Date().isSame(new Date('2017-03-23'),'date')  //false
```

--------------

## format()
将时间格式化
```javascript
new Date().format('yyyy-MM-dd')  //2017-03-25
```

--------------

## 参考资源
[javascript 标准库 Date](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Date "javascript 标准库 Date")

--------------

# 字符串类
## charAt()
从一个字符串中返回指定的字符。

--------------

## concat()
将一个或多个字符串与原字符串连接合并，形成一个新的字符串并返回。

--------------

## endsWith()
`该新特性属于 ECMAScript 2015（ES6）规范，存在浏览器兼容性。但是此方法已经重写，可以放心使用`
方法用来判断当前字符串是否是以另外一个给定的子字符串“结尾”的，根据判断结果返回 true 或 false。

--------------

## startsWith()
`该新特性属于 ECMAScript 2015（ES6）规范，存在浏览器兼容性。但是此方法已经重写，可以放心使用`
用来判断当前字符串是否是以另外一个给定的子字符串“开头”的，根据判断结果返回 true 或 false。

--------------

## includes()
`该新特性属于 ECMAScript 2015（ES6）规范，存在浏览器兼容性。但是此方法已经重写，可以放心使用`
用于判断一个字符串是否包含在另一个字符串中，根据情况返回true或false。

--------------

## indexOf()
方法返回指定值的第一次出现的调用 String 对象中的索引，开始在fromIndex进行搜索。如果未找到该值，则返回-1。

--------------

## lastIndexOf()
方法返回指定值在调用该方法的字符串中最后出现的位置，如果没找到则返回 -1。从该字符串的后面向前查找

--------------

## match()
当一个字符串与一个正则表达式匹配时， match()方法检索匹配项。

--------------

## replace()
方法返回一个由替换值替换一些或所有匹配的模式后的新字符串。模式可以是一个字符串或者一个正则表达式, 替换值可以是一个字符串或者一个每次匹配都要调用的函数。

--------------

## slice()
从一个字符串中提取字符串并返回新字符串。在一个字符串中的改变不会影响另一个字符串。也就是说，slice 不修改原字符串，只会返回一个包含了原字符串中部分字符的新字符串。

--------------

## split()
将一个String对象分割成字符串数组，通过将字符串分成子串。

--------------

## substr()
返回一个字符串中从指定位置开始到指定字符数的字符。

--------------

## substring()
返回一个字符串在开始索引到结束索引之间的一个子集, 或从开始索引直到字符串的末尾的一个子集。

--------------

## toLowerCase()
会将调用该方法的字符串值转为小写形式，并返回。

--------------

## toUpperCase()
将调用该方法的字符串值转换为大写形式，并返回。

--------------

## toString()
方法返回指定对象的字符串形式。

--------------

## trim()
方法会删除一个字符串两端的空白字符。在这个字符串里的空格包括所有的空格字符 (space, tab, no-break space 等)以及所有的行结束符（如 LF，CR）。

--------------

## trimAll()
去掉所有的空白符

--------------

## toLowerCase()
`该特性是非标准的，但是此方法已经重写，可以放心使用`
方法移除原字符串左端的连续空白符并返回,trimLeft方法并不会直接修改原字符串本身.

--------------

## trimRight()
`该特性是非标准的，但是此方法已经重写，可以放心使用`
trimRight方法移除原字符串右端的连续空白符并返回,trimRight方法并不会直接修改原字符串本身

--------------

## isNullOrEmpty()
判断字符是否为null或空

--------------

## format()
将字符传转换为指定的其他字符串
```sacript
var str='hello {0}{1}{2}ld'.format("w","o","r")  //hello world
```
--------------

## 参考资源
[javascript 标准库 String](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String "javascript 标准库 String")

--------------


# 数字类
## toFixed()
使用定点表示法来格式化一个数。
```script
numObj.toFixed(digits)
```
--------------

## toPrecision()
指定的精度返回该数值对象的字符串表示
```script
numObj.toPrecision(precision)
```
--------------


## toString()
方法返回指定 Number 对象的字符串表示形式。
```script
numObj.toString([radix])
```
--------------


## abs()
函数返回指定数字 “x” 的绝对值。
```script
Math.abs(x) 
```
--------------


## ceil()
返回一个大于或等于数 “x” 的最小整数
```script
Math.ceil(x)
```
--------------


## floor()
函数返回小于或等于数 “x” 的最大整数。
```script
Math.floor(x)
```
--------------


## max()
函数返回一组数中的最大值。
```script
Math.max([value1[,value2, ...]])
```
--------------


## min()
返回零个或更多个数值的最小值。
```script
Math.min([value1[,value2, ...]])
```
--------------


## pow()
函数返回基数（base）的指数（exponent）次幂，即 baseexponent。
```script
Math.pow(base, exponent)
```
--------------


## random()
函数返回 [0-1) 的浮点值伪随机数（大于等于0，小于1）。
```script
Math.random()
```
--------------


## round()
返回一个数值四舍五入后最接近的整数值。
```script
Math.round()
```
--------------

## sqrt()
函数返回一个数的平方根
```script
Math.sqrt(x)
```
--------------


## sign()
函数用来判断一个数字的符号, 是正数, 负数, 还是零.
```script
Math.sign(x)
```
--------------


## isFinite()
用来检测传入的参数是否是一个有穷数（finite number）。
```script
Number.isFinite(value)
```
--------------


## isInteger()
方法用来判断给定的参数是否为整数。
```script
Number.isInteger(value)
```
--------------


## isNaN()
方法用来检测传入的值是否是 NaN。该方法比传统的全局函数 isNaN() 更可靠。
```script
Number.isNaN(value)
```
--------------


## isSafeInteger()
方法用来判断传入的参数值是否是一个“安全整数”（safe integer）
```script
Number.isSafeInteger(testValue)
```
--------------


## formatMoney()
`formatMoney(places,symbol,thousand,decimal)`
将数字转换成货币格式
参数【places】: Number 保留的小数位 默认2
参数【symbol】: string 符号 默认’$’
参数【thousand】: string 每三位的分隔符 默认’,’
参数【decimal】：string 个位与小数的分隔符 默认’.’
```script
var revenue = 12345678;
var result = revenue.formatMoney(4,"",".","|"); //12.345.678|0000
var result2 = revenue.formatMoney();  //$12,345,678.00
```
--------------

## currencyUpperCase()
将数字转汉子大写形式 小数最多支持4位
```script
var revenue = 1234561000;
var result = revenue.currencyUpperCase();   //壹拾贰亿叁仟肆佰伍拾陆万壹仟元整
```
--------------

## 参考资源
[javascript 标准库 Number](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Number "javascript 标准库 Number")
[javascript 标准库 Math](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Math "javascript 标准库 Math")

--------------


# 数组类
## push()
向数组的末尾添加一个或更多元素，并返回新的长度。

-------------

## pop()
删除并返回数组的最后一个元素

-------------

## shift()
删除并返回数组的第一个元素

-------------

## unshift()
向数组的开头添加一个或更多元素，并返回新的长度。

-------------

## join()
把数组的所有元素放入一个字符串。元素通过指定的分隔符进行分隔。

-------------

## reverse()
颠倒数组中元素的顺序。

-------------

## sort()
对数组的元素进行排序

-------------

## concat()
连接两个或更多的数组，并返回结果。

-------------

## slice()
从某个已有的数组返回选定的元素

-------------

## splice()
删除元素，并向数组添加新元素

-------------

## toString()
把数组转换为字符串，并返回结果。

-------------

## isArray()
判断是不是数组

-------------

## indexOf()
返回在数组中可以找到给定元素的第一个索引，如果不存在，则返回-1。

-------------

## every()
测试数组的所有元素是否都通过了指定函数的测试。

-------------

## filter()
使用指定的函数测试所有元素，并创建一个包含所有通过测试的元素的新数组。

-------------

## forEach()
方法对数组的每个元素执行一次提供的函数。

-------------

## map()
方法创建一个新数组，其结果是该数组中的每个元素调用一个提供的函数。

-------------

## unique()
这是jquery提供的方法,去重
```
var arry=[1,2,1,3] $.unique(arry)
```
-------------

## 参考资源
[javascript 标准库 Array](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array "javascript 标准库 Array")
[w3school JavaScript Array 对象](http://www.w3school.com.cn/jsref/jsref_obj_array.asp "JavaScript Array 对象")

# 其他扩展类
## ConvertNetTDate()
返回一个javascript Date对象.
方法用来转换C#通过json传到前端的时间字符串中带“T”的问题，如："2017-03-01T16:33:03.73"
```script
ConvertNetTDate("2017-03-01T16:32:46.927").format("yyyy-MM-dd")
```
--------------

## isMobileUserAgent()
判断是否移动设备访问

-------------

## isAppleMobileDevice()
判断是否苹果移动设备访问

-------------

## isAndroidMobileDevice()
判断是否安卓移动设备访问

-------------

## DisableWeChatDrop()
禁用微信浏览器下拉回弹,页面在微信浏览器中禁止下拉露底


-------------

## GUID()
生成GUID
```script
var guid = new GUID();
var g1=guid.newGUID()
```

-------------

# 表单操作
## 使用说明
需要引用jquery
```html
//引用js
<script src="/jquery/3.1.1/jquery-3.1.1.min.js"></script>
<script src="/js-common-methods/0.0.1/js-common-methods.min.js"></script>
```

## serializeJson()
序列化表单值为JSON
说明：元素不能被禁用（禁用的元素不会被包括在内），并且元素应当有含有 name 属性，对于获取不到的值，请自己手动赋值。
```script
$(selector).serializeJson()
```
解决disabled元素不能取值的方案：
```script
var myform = $('#form');
var disabled = myform.find(':input:disabled').removeAttr('disabled');
var serialized = myform.serializeJson();
disabled.attr('disabled','disabled');
```
结果展示:
```json
 {
    name: a,
    value: 1,
    age:20,
    ...
  }
```
-------------

## fillForm()
根据JSON数据填充表单
说明：对于上传图片空间或者使用了i-check插件美化checkbox是无法自动填充的,需要自己手动填充。
```script
$(selector).fillForm()
```
--------------------

## serializeArray()
序列化表单值来创建对象数组（名称和值）
.serializeArray() 方法使用了 W3C 关于 [successful controls（有效控件）](https://www.w3.org/TR/html401/interact/forms.html#h-17.13.2 'successful controls（有效控件）') 的标准来检测哪些元素应当包括在内。
特别说明，元素不能被禁用（禁用的元素不会被包括在内），并且元素应当有含有 name 属性。提交按钮的值也不会被序列化。文件选择元素的数据也不会被序列化。
```script
$(selector).serializeArray()
```
--------------------

## serialize()
创建以标准 URL 编码表示的文本字符串
```script
$(selector).serialize()  //a=1&b=2&c=3&d=4&e=5
```
--------------------

## resetForm()
还原表单
```script
$('#form1').resetForm()
```
--------------------

## clearForm()
清空表单所有元素的值
```script
$('#form1').clearForm()
```
--------------------

## clearFields()
清空某个表单域的值
```script
$('#form1 :password').clearFields()
```
--------------------
