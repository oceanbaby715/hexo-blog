---
title: html5开发小技巧
date: 2017-07-24 14:54:32
tags: ["html5"]
categories:
- 前端
- HTML
- 实用类
---
# 前言
Web技术的发展速度太快了，如果你不与时俱进，就会被淘汰。

# 新的Doctype声明
XHTML的声明太长了，我相信很少会有前端开发人员能手写出这个Doctype声明
```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN""http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
```

HTML5的Doctype声明很短，看到这个声明相信你马上就能记住，不用浪费脑细胞去记那长的有点变态的XHTML的Doctype声明了。
```html
<!DOCTYPE html>
```


------------

# 去掉了Javascript和CSS标签的type属性
通常你会在`<link>`和`<script>`加上`type`属性：

```
<link rel="stylesheet" type=text/css href="path/to/stylesheet.css">
<script type="text/javascript" src="path/to/script.js"></script>
```

在HTML5中，不再需要type属性了，因为这显得有点多余，去掉之后可以让代码更为简洁

```html
<link href="path/to/stylesheet.css">
<script src="path/to/script.js"></script>
```

------------

# 是否使用双引号
这有点让人纠结，HTML5并不是XTHML，你可以省去标签中的双引号。相信大多数同志也包括我都习惯了加上双引号，因为这让代码看起来会更标准。不过，这可以根据你的个人喜好来确定是到底要不要双引号
```html
<h6 id="someid" class="myclass"> start the reactor. </h6>
```

------------

# 占位符
在HTML5中新增了占位符属性placeholder
```html
<input type="email" name="email" placeholder="doug@givethesepeopleair.com">
```

------------

# 更有语义的header和footer
下面的代码在HTML5中将不复存在
```html
<div id=header>
     ...
</div>
<div id=footer>
     ...
</div>
```

通常我们都会给`header`和`footer`定义一个`div`，然后再添加一个id，但是在HTML5中可以直接使用`<header>`和`<footer>`标签，所以可以将上面的代码改写成：
```html
<header>
    ...
</header>
<footer>
    ...
</footer>
```
要注意不要将这两个标签和网站的头部和页脚混淆起来，它们只是代表它们的容器

------------

# 标题群( hgroup)

如果用`h1`和`h2`标签分别表示网站的名称和副标题，但这会让两个本义上密切相关的标题并没有关联起来。这个时候可以使用`<hgroup>`标签将它们组合起来，这样代码会更有语义
```html
<header>
<hgroup>
<h1> Recall Fan Page </h1>
<h2> Only for people who want the memory of a lifetime. </h2>
</hgroup>
</header>
```

------------

# 自动获取焦点
HTML5新增了自动获取焦点属性autofocus：
```html
<input type="text" name="someInput" placeholder="douglas quaid" required="required" autofocus="autofocus">
```

------------

# 使用正则表达式
在HTML5中，我们可以直接使用正则表达式。
```html
<form method=post action="">
    <label for="username">create a username: </label> 
<input id="username" type="text" name="username" placeholder="4 <> 10" required="required" autofocus="autofocus" pattern="[A-Za-z]{4,10}">
    <button type="submit">Go </button>
</form>
```

------------


# 检测浏览器对HTML5属性的支持
由于各浏览器对HTML5属性的支持度不同，这就造成了一些兼容问题。但是可以使用方法来检测该浏览器是否支持这些属性，上例中的代码如果要检测pattern属性是否被浏览器识别，可以使用Javascript代码来检测。
```javascript
alert( 'pattern' in document.createElement('input') ) // boolean;
```

其实这是确定浏览器兼容常用的方法，jQuery库就经常使用这种方法。上面的代码中创建了一个input标签，并检测pattern属性是否被浏览器支持，如果能支持的话，浏览器就支持这个功能，否则就不支持
```javascript
<script> 
 if (!'pattern' in document.createElement('input') ) { 
    // do client/server side validation 
 } 
</script>
```

------------

# Mark标签
`<mark>`标签用于高亮显示那些需要在视觉上向用户突出其重要性的文字，包裹在此标签里的字符串必须与用户当前的行为相关。
```html
<h3> search results </h3>
<h6> They were interrupted, just after Quato said, <mark>"Open your Mind"</mark>. </h6>
```

------------

# Audio支持
HTML5提供了`<audio>`标签，你不需要再按照第三方插件来渲染音频，大多数现代浏览器提供了对于HTML5 Audio的支持，不过目前仍旧需要提供一些兼容处理，如
```html
<audio autoplay="autoplay" controls="controls">

<source src="file.ogg" /><!--FF-->

<source src="file.mp3" /><!--Webkit-->

<a href="file.mp3">Download this file.</a>

</audio>
```

------------

# Video支持
和Audio很像，`<video>`标签提供了对于video的支持.
```html
<video controls preload>

<source src="cohagenPhoneCall.ogv" type="video/ogg; codecs=´vorbis, theora´" />

<source src="cohagenPhoneCall.mp4" type="video/mp4; ´codecs=´avc1.42E01E, mp4a.40.2´" />

<p> Your browser is old. <a href="cohagenPhoneCall.mp4">Download this video instead.</a> </p>

</video>
```

------------

# 预加载视频
preload属性就像它的字面意思那么简单，你需要决定是否需要在页面加载的时候去预加载视频
```html
<video preload>
```

显示视频控制
```html
<video preload controls>
```

------------

# Output元素
`<output>`元素用来显示计算结果，也有一个和label一样的for属性
用Range Input来创建滑块
HTML5引用的range类型可以创建滑块，它接受min, max, step和value属性
可以使用css的:before和:after来显示min和max的值
```html
<input type="range" name="range" min="0" max="10" step="1" value="">

input[type=range]:before { content: attr(min); padding-right: 5px;

}

input[type=range]:after { content: attr(max); padding-left: 5px;}
```