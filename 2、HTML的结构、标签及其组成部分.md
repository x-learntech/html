# HTML 的结构、标签及其组成部分


### 一个当下常规的HTML结构组成

```html
<!DOCTYPE html>
<html>
<head>
	<meta charset="utf-8">
	<meta name="description" content="">
	<meta name="keywords" content="">
	<title>标题</title>
	<link href="css.css" rel="stylesheet">
</head>
<body>
	<div class="wrap">
		这里是网页内容，这里是网页内容。
	</div>
	<script src="js.js"></script>
</body>
</html>
```

其中：

- DOCTYPE定义了文档类型。`<!DOCTYPE html>`表明这是一个HTML5文档
- `<html>`是根标签，是最外层的网页标签了；
- `<head>`和`</head>`之间通常是网页中一些不对外显示的信息，此处更多的是写给浏览器和服务器的内容，跟SEO也有关联；
- `<title>`描述了网页的标题，这个内容会展现在浏览器标题处，对于SEO很重要；
- `<meta>`描述了当前网页的一些信息，感觉meta有着一个举足轻重的地位；
- `<body>`和`</body>`之间的内容为网页呈现给用户的可见内容部分，通常我们所呈现的内容都是放置在这个标签之间的。

**说明：**

- 现代浏览器的性能优化做的还是挺不错的，对于很基本的错误，浏览器本身都会帮我纠正错误。比如，我们漏了便签闭合，那么浏览器会自动闭合，但是也很容易导致层级错位。
- <head>中的meta顺序是不固定的。

### HTML 的标签

HTML里的标签需要及时正确对应的闭合，比如：

```html
// 错误的闭合方式
<div><p><span>你好，我是HTML</div></p></span>
// 正确的闭合方式
<div><p><span>你好，我是HTML</span></p></div>
```

HTML的标签分为能必须闭合的标签和可自闭合的标签两种，其中以必须闭合的便签为主。    

**必须闭合的标签里能包含内容**，由开始标签、结束(闭合)标签、标签属性、标签内容组成的。例如：

```html
<a href="https://www.baidu.com" title="百度一下">百度</a>
```

其中:  
  
* `<a href="https://www.baidu.com" title="Baidu一下">`为起始标签
* `</a>`为结束标签
* `href`和`title`为标签属性，`https://www.baidu.com`和`百度一下`为属性对应的值，属性的值要由英文的双引号包裹起来。
* `百度`为标签的内容。

**可自闭合的标签无法包含其他内容**，当然不少可自闭合的标签也可以像必须闭合的标签那样使用。    

自闭合的标签：如 `<img src="img.jpg" alt="img" />`，`<br/>`, `<input type="text" />`。如果要按照闭合标签的方式写，也是ok的，比如：`<img src="img.jpg" alt="img"></img>`。

补充说明，有些标签和属性是需要相互配合的。比如：a链接标签，如果a没有href属性的话，那么a原本链接的意义就不存在了；img标签需要src的配合等。

### 标签的分类：块级元素、行内元素

**自然状态下的块级元素会始终占居一行，而行内元素并不会。当然通过属性可以改变标签的属性（display:inline/block），也可以让元素具有块属性和行属性(display:inline-block)。**
    
常见的块级元素有： `div, form, table, header, aside, section, article, figure, figcaption, h1~h6, nav, p, pre, blockqoute, canvas, ol, ul, dl`
 
常见的行内元素有： `span, a, img, label, input, select, textarea, br, i, em, strong, small, button, sub, sup, code`

### HTML特殊符号（也有的叫字符实体）

在HTML中，某些字符是预留的。如果希望正确地显示预留字符，我们必须在HTML源代码中使用字符实体（character entities）。不过随着浏览器的升级换代，个人感觉这些曾经的预留字符现在大部分都是可以正常被解析的。HTML中不能使用小于号（<）和大于号（>），这是因为浏览器会误认为它们是标签。

**常用的字符实体**

| 结果        | HTML实体名称          | HTML实体编号  | 十六进制 | 在 CSS content 中 | 8 进制            |
| :-----------|:-------------         |:-----------   |:------   |:-------------     |:-----             |
|  空格       | `&nbsp;`              | `&#160;`      |%A0       |content:"\00a0";   |`alert('\240')`    |
|  <       	  | `&lt;`                | `&#60;`       |%3C       |content:"\003c";   |`alert('\74')`     |
|  >       	  | `&gt;`                | `&#62;`       |%3E       |content:"\003e";   |`alert('\76')`     |
|  &       	  | `&amp;`               | `&#38;`       |%26       |content:"\0026";   |`alert('\46')`     |
|  "       	  | `&quot;`              | `&#34;`       |%22       |content:"\0022";   |`alert('\42')`     |
|  ©       	  | `&copy;`              | `&#169;`      |%A9       |content:"\00a9";   |`alert('\251')`    |
|  ®       	  | `&reg;`               | `&#174;`      |%AE       |content:"\00ae";   |`alert('\256')`    |
|  ×       	  | `&times;`             | `&#215;`      |%D7       |content:"\00d7";   |`alert('\327')`    |

具体参考：[HTML ISO-8859-1 支持的字符集](http://www.w3school.com.cn/tags/html_ref_entities.html)







