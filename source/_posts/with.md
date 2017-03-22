---
title:      "with语句详解"
date:       2017-03-15 23:21:00
author:     "古朋"
header-img: "post-bg-2015.jpg"
tags:
    - 前端开发
    - JavaScript
---

with这种语法现如今应该已经无人问津了，但是还是想来说说这个在JavaScript中的用法和缺点

## 介绍

with语句的作用是将代码的作用域设置到一个特定的对象中。

利：with语句可以在不造成性能损失的情况下，减少变量的长度。很多情况下，也可以不使用with语句，而是使用一个临时变量来保存指针，来达到同样的效果。

弊：with语句使得程序在查找该语句块中的所有的变量值时，都是先在该with语句指定的对象下面先寻找一遍，然后再去外面的作用域去寻找。所以尽量不要在该语句块中去使用一些不属于该对象中的变量

## 用法

```javascript
var x = {
  name : "古朋",
  nick_name : "gupeng"
};
with(x){
  console.log(name+'的小名是'+nick_name);
}
```
可以替换为:

```
var x = {
  name : "古朋",
  nick_name : "gupeng"
};
/*
 *这里将x对象赋值到当前局部变量中，减少不必要的指针路径解析运算
 *一般用于在在方法中将this对象局部化，比如：var this_ = this;
 */
var x_ = x;
console.log(x_.name+'的小名是'+x_nick_name);
```
