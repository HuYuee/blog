---
title: Zen Coding--如何快速地书写HTML代码
author: 古朋
header-img: post-bg-js-module.jpg
tags:
  - 前端开发
  - JavaScript
date: 2017-04-07 22:58:00
---

# 描述

在本文中我们将展示一种新的使用仿CSS选择器的语法来快速开发HTML的方法。

我使用的是[atom编辑器](https://atom.io/)——由 Github 打造的编程开发利器，他自带这个解析功能。当然其他的如sublime，webstorm等都会自带这个功能，或者使用相关的插件即可。

你在写HTML代码(包括所有标签、属性、引用、大括号等)上花费多少时间？如果你的编辑器有代码提示功能，你编写的时候就会容易些，但即便如此你还是要手动敲入很多代码。



比如，你这么写，按下`tab`键：

```html
div#content>h1+p
```

然后就看到了这样的输出：

```html
<div id="content">  
<h1></h1>  
<p></p>  
</div>
```



# 用法

这里是一个支持的属性和操作符的列表：

- E

  元素名称(`div`, `p`等);

- E#id
  使用id的元素(`div#content`, `p#intro`, `span#error`);

- E.class
  使用类的元素(`div.header`, `p.error.critial`). 你也可以联合使用class和idID: `div#content.column.width`;

- E>N
  子代元素(`div>p`, `div#footer>p>span`);

- E+N
  兄弟元素(`h1+p`, `div#header+div#content+div#footer`);

- E*N
  元素倍增(`ul#nav>li*5>a`);

- E$*N

  条目编号 (`ul#nav>li.item-$*5`);



# 示例

这里就针对于倍增和条目编号来举例子吧。



## 元素倍增

比如你写个`li*4>a`，就会生成以下HTML代码：

```html
<li><a href=""></a></li>  
<li><a href=""></a></li>  
<li><a href=""></a></li>  
<li><a href=""></a></li>  
```



## 条目编号

假设你想生成class为`item1`、`item2`和`item3`的3个`<div>`元素。你可以写成这样的缩写，`div.item$*3`:

```html
<div class="item1"></div>  
<div class="item2"></div>  
<div class="item3"></div>
```



简单吧，赶紧打开你的编辑器操练起来吧！
