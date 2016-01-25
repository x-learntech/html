# 头部及Meta标签的作用和意义

根据当下前端的状况和未来发展趋势而言，我不再一味的照顾旧有的浏览器，拥抱变化向前看向未来看齐。

## 头部基本标签

- 使用 HTML5 doctype，不区分大小写。

```html
<!DOCTYPE html> <!-- 使用 HTML5 doctype，不区分大小写 -->
```

## Meta标签

### 常见的meta标签：

- 声明文档使用的字符编码

```html
<meta charset='utf-8'> <!-- 声明文档使用的字符编码 -->
```

- 更加标准的 lang 属性写法 http://zhi.hu/XyIa

```html
// 简体中文
<html lang="zh-cmn-Hans"> <!-- 更加标准的 lang 属性写法 http://zhi.hu/XyIa -->
// 很少情况才需要加地区代码，通常是为了强调不同地区汉语使用差异
```

- 优先使用 IE 最新版本和 Chrome

```html
<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1"> <!-- 优先使用 IE 最新版本和 Chrome -->
```

- 简单SEO

```html
<meta name="description" content="不超过150个字符"> <!-- 页面描述 -->
<meta name="keywords" content=""> <!-- 页面关键词 -->
<meta name="author" content="name, email@gmail.com"> <!-- 定义网页作者 -->
<meta name="robots" content="index,follow"> <!-- 搜索引擎抓取。定义网页搜索引擎索引方式，robotterms是一组使用英文逗号「,」分割的值，通常有如下几种取值：none，noindex，nofollow，all，index和follow。 -->
```

### 可选的meta标签

#### 为移动设备添加 viewport

```html
<meta name ="viewport" content ="initial-scale=1, maximum-scale=3, minimum-scale=1, user-scalable=no"> <!-- `width=device-width` 会导致 iPhone 5 添加到主屏后以 WebApp 全屏模式打开页面时出现黑边 http://bigc.at/ios-webapp-viewport-meta.orz -->
```

content 参数：

>- width viewport 宽度(数值/device-width)
- height viewport 高度(数值/device-height)
- initial-scale 初始缩放比例
- maximum-scale 最大缩放比例
- minimum-scale 最小缩放比例
- user-scalable 是否允许用户缩放(yes/no)

#### 主要针对移动设备meta

```html
<meta name="apple-mobile-web-app-title" content="标题"> <!-- 添加到主屏后的标题（iOS 6 新增） -->
<meta name="apple-mobile-web-app-capable" content="yes"> <!-- 是否启用 WebApp 全屏模式, yes or no -->
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent"> <!-- 设置状态栏的背景颜色，只有在 `"apple-mobile-web-app-capable" content="yes"` 时生效。default 默认值；black 状态栏背景是黑色；black-translucent 状态栏背景是黑色半透明。如果设置为 default 或 black ,网页内容从状态栏底部开始。如果设置为 black-translucent ,网页内容充满整个屏幕，顶部会被状态栏遮挡。 -->
<meta name="format-detection" content="telephone=no"> <!-- 禁止数字识自动别为电话号码 -->
<meta name="format-detection" content="address=no"> <!-- 禁止自动自动识别地址 -->
<meta name="format-detection" content="date=no">  <!-- 禁止自动自动识别日期 -->
<meta name="format-detection" content="email=no">  <!-- 禁止自动自动识别 Email -->
```

#### 其他meta

```html
<link rel="alternate" type="application/rss+xml" title="RSS" href="/rss.xml"> <!-- 添加 RSS 订阅 -->
<link rel="shortcut icon" type="image/ico" href="/favicon.ico"> <!-- 添加 favicon icon -->
<meta name="google" value="notranslate"> <!-- 禁止 Chrome 浏览器中自动提示翻译 -->
<meta http-equiv="Cache-Control" content="no-siteapp"><!-- 禁止百度转码 -->
<meta name="renderer" content="webkit"> <!-- 360 使用Google Chrome Frame -->

```

## 简单的一个副本：

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<meta http-equiv="refresh" content="5;url=" />
<link rel="copyright" href="copyright.html" 　/>
<meta http-equiv="X-UA-Compatible" content="IE=edge" />
<!-- 优先使用 IE 最新版本和 Chrome -->
<meta name="viewport" content="width=device-width, initial-scale=1" />
<meta name="description" content="150 words" />
<meta name="keywords" content="your tags" />
<!--
    all：文件将被检索，且页面上的链接可以被查询；
    none：文件将不被检索，且页面上的链接不可以被查询；
    index：文件将被检索；
    follow：页面上的链接可以被查询；
    noindex：文件将不被检索；
    nofollow：页面上的链接不可以被查询。
 -->
<meta name="robots" content="index,follow" />
<meta name="author" content="author name" />
<meta name="google" content="index,follow" />
<meta name="googlebot" content="index,follow" />
<meta name="verify" content="index,follow" />
<!-- 启用 WebApp 全屏模式 -->
<meta name="apple-mobile-web-app-capable" content="yes" />
<!-- 隐藏状态栏/设置状态栏颜色：只有在开启WebApp全屏模式时才生效。content的值为default | black | black-translucent 。 -->
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent" />
<!-- 添加到主屏后的标题 -->
<meta name="apple-mobile-web-app-title" content="标题">
<!-- 忽略数字自动识别为电话号码 -->
<meta content="telephone=no" name="format-detection" />
<!-- 忽略识别邮箱 -->
<meta content="email=no" name="format-detection" />
<meta name="apple-itunes-app" content="app-id=myAppStoreID, affiliate-data=myAffiliateData, app-argument=myURL" />
<!-- 添加智能 App 广告条 Smart App Banner：告诉浏览器这个网站对应的app，并在页面上显示下载banner:https://developer.apple.com/library/ios/documentation/AppleApplications/Reference/SafariWebContent/PromotingAppswithAppBanners/PromotingAppswithAppBanners.html -->
<!-- 针对手持设备优化，主要是针对一些老的不识别viewport的浏览器，比如黑莓 -->
<meta name="HandheldFriendly" content="true">
<!-- 微软的老式浏览器 -->
<meta name="MobileOptimized" content="320">
<!-- uc强制竖屏 -->
<meta name="screen-orientation" content="portrait">
<!-- QQ强制竖屏 -->
<meta name="x5-orientation" content="portrait">
<!-- UC强制全屏 -->
<meta name="full-screen" content="yes">
<!-- QQ强制全屏 -->
<meta name="x5-fullscreen" content="true">
<!-- UC应用模式 -->
<meta name="browsermode" content="application">
<!-- QQ应用模式 -->
<meta name="x5-page-mode" content="app">
<!-- windows phone 点击无高光 -->
<meta name="msapplication-tap-highlight" content="no">
<link href="css/style.css" rel="stylesheet">
<script src="js/javascript.js"></script>
</head>
```


强烈建议阅读扩充资料，了解更全面：

- [http://www.w3cplus.com/html5/meta-tags-and-seo.html](http://www.w3cplus.com/html5/meta-tags-and-seo.html)
- [http://segmentfault.com/a/1190000002407912](http://segmentfault.com/a/1190000002407912)
- [http://segmentfault.com/a/1190000002532413](http://segmentfault.com/a/1190000002532413)
- [http://segmentfault.com/a/1190000000697532](http://segmentfault.com/a/1190000000697532)
- [http://segmentfault.com/a/1190000002586217](http://segmentfault.com/a/1190000002586217)
- [https://github.com/yisibl/blog/issues/1](https://github.com/yisibl/blog/issues/1)
- [360浏览器内核控制Meta标签说明文档](http://se.360.cn/v6/help/meta.html)



