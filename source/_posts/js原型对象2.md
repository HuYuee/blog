---
title: js原型对象2
date: 2017-03-21 19:28:43
author:     "古朋"
tags:
    - 前端开发
    - JavaScript
---
在看下面的内容之前，建议先看我写的[js原型对象（一)](http://www.jianshu.com/p/541051e2ffda)

## 更简单的原型语法

在看了前面栗子之后，你们可能注意到了，每添加一个属性和方法就要敲一遍Person.prototype。为了使代码简洁美观，最常见的做法是用一个包含所有属性的方法的对象字面量来重写整个原型对象。

来看个栗子：

```javascript
function Person(){
}
Person.prototype = {
  name : "Lee",
  age : 20
}
```

但是上面的这种更简单的写法有几个问题：

**1.上面的写法本质上完全重写了默认的prototype对象，因此使得原型中的constructor属性不再指向Person了**。这种情况的时候如果constructor属性很重要，可以像下面这样特意将他设置回适当的值

```javascript
function Person(){
}
Person.prototype = {
  constructor : Person,//设置回适当的值
  name : "Lee",
  age : 20
}
```

**2.上面的写法在重写了默认的prototype对象，切断了现有原型与任何之前已经存在的对象实例之间的联系，他们引用的仍然是最初的原型**。

下面两个栗子来对比这个问题：

1）没有重写原型对象的栗子：

```javascript
function Person(){
}
var lee = new Person();
Person.prototype.name = 'Lee';
alert(lee.name);//'Lee'
```

2）重写原型对象的栗子

```javascript
function Person(){
}
var lee = new Person();
Person.prototype = {
  constructor : Person,//设置回适当的值
  name : "Lee",
  age : 20
}
alert(lee.name);//undefined
```



## 原型对象的问题

原型中所有属性是被很多实例共享的，这种共享对于函数非常合适。对于那些包含基本值的属性也说得过去，毕竟（上面一篇文章中所示），通过在实例上添加一个同名属性，可以隐藏原型中的对应属性。然而，**对于包含引用类型值的属性就有问题了**。

举个栗子：

```javascript
function Person(){
}

Person.prototype = {
  constructor : Person,//设置回适当的值
  name : "Lee",
  age : 20,
  friends : ["Wang","Tang"]
}
var p1 = new Person();
var p2 = new Person();

p1.friends.push("Zhang");

alert(p1.friends);//"Wang,Tang,Zhang"
alert(p2.friends);//"Wang,Tang,Zhang"
alert(p1.friends === p2.friends);//true
```

在上面的例子中，Person.prototype对象有一个名为friends的属性，该属性包含一个字符串数组。这个属性就是包含引用类型值属性。因为该属性是保存的对这个数组的引用，相当于就是说所有的实例都是公用的同一个这个数组，只要一个人对这个数组进行了修改，其他实例就都会改变。
