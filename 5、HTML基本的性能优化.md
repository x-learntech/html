# HTML基本的性能优化

前端性能与浏览器的运作方式密切相关，故想要优化性能就要从了解浏览器是如何渲染界面的。

### 浏览器显示页面的原理

#### 基本流程：

- 获取 HTML 文档及样式表文件
- 解析成对应的树形数据结构
	- DOM tree
	- CSSOM tree
- 计算可见节点形成 render tree
- 计算 DOM 的形状及位置进行布局
- 将每个节点转化为实际像素绘制到视口上（栅格化）

render tree（页面上所显示的最终结果）是由 DOM tree（开发工具中所显示的 HTML 所定义的内容结构）与 CSSOM tree（样式表所定义的规则结构）合并并剔除不可见的节点所形成的，其中不包含如下节点：

- 本身不可见的：`<html><head><meta><link><style><script>`
- 设置了 `display: none;` 样式的

资源加载：

- 执行 JavaScript 会阻止 DOM tree 构建
- 加载 CSS 会阻止 render tree 构建

**无论是否为阻止呈现的 CSS，都会被浏览器下载**

默认情况下，JavaScript 脚本会在引入它的位置执行（如果是外联脚本则还需要等待加载完毕），这时会阻断 DOM tree 的构建；如果在运行脚本时浏览器尚未完成 CSS 的下载和 CSSOM tree 的构建，浏览器会将脚本执行延迟到这些操作结束之后。

#### 影响性能的因素：

- 白屏
	- HTML 和 CSS 的加载及解析速度
	- <head> 内的脚本加载及执行
- 首屏
	- 图片加载
	- <body> 内的脚本加载及执行
- render tree 的构建
	- HTML 的复杂度
	- CSS 的复杂度
- render tree 的绘制（栅格化）
	- 颜色的复杂度
	- 形状的复杂度

### 怎么提高前端性能？

提高以下几个方面，总体性能就会得到大幅度提升：

- 缩短白屏时间；
- 加快首屏显示；
- 尽快监听主要操作的事件。

所要达到的理想指标：60 f/s。

**优化关键呈现路径**

为了在首次渲染时尽可能快，我们需要优化以下三个变量：
- 最小化关键资源数
- 最小化关键字节数
- 最小化关键路径长度

常规步骤：

- 分析并描述关键路径：资源数、字节数和长度；
- 减少关键资源的数量：删掉、延迟下载或标记为异步等等；
- 优化剩余关键资源的加载顺序：尽早下载所有关键资源以缩短关键路径长度；
- 优化关键字节数以减少下载时间（往返次数）。

搜集性能数据

通过 [Navigation Timing API](https://www.w3.org/TR/navigation-timing-2/#processing-model) 可以获取浏览器在处理网页的关键步骤的时间戳。

其中，各步骤的意义如下：

- domLoading 表示开始解析第一批收到的 HTML 文档的字节
- domInteractive 表示完成全部 HTML 的解析并且 DOM 构建完毕
- domContentLoaded 表示 DOM 与 CSSOM 皆已准备就绪
	- 如果没有解析器阻塞 JavaScript，DOMContentLoaded 事件会在 domInteractive 之后立即触发
	- 很多 JavaScript 框架会在执行它们自己的逻辑前等待这个事件的触发
- domComplete 表示所有的处理都已完成并且所有的附属资源都已经下载完毕
- loadEvent 作为网页加载的最后一步以便触发附加的应用逻辑

**PageSpeed 规则和建议**

- 排除阻止呈现的 JavaScript 和 CSS
- 优化 JavaScript 的用法
	- 推荐使用异步 JavaScript 资源
	- Avoid synchronous server calls
	- 延迟解析 JavaScript
	- 避免运行时间长的 JavaScript
-优化 CSS 的用法
	- 将 CSS 放到文档头部
	- 避免使用 CSS import
	- 内联阻止呈现的 CSS






**资源阅读：**

- [网站性能优化·前端篇](http://segmentfault.com/a/1190000002589116)
- [影响网页渲染的关键](http://segmentfault.com/a/1190000002786584)


**强烈推荐：**

- [从输入URL到页面加载完成的过程中都发生了什么事情？](http://fex.baidu.com/blog/2014/05/what-happen/)
- [有关网页渲染，每个前端开发者都该知道的那点事](http://segmentfault.com/a/1190000002907021)
- [网页性能管理详解](http://div.io/topic/1420)
- [前端工程与性能优化](http://div.io/topic/371)