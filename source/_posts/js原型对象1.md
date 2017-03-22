---
title: js原型对象1
date: 2017-03-20 19:28:35
author:     "古朋"
tags:
    - 前端开发
    - JavaScript
---
## 为什么要写原型对象？

原型，其实已经是前端知识中老生常谈的内容了。很多初学者和工作者其实都觉得这个概念其实跟你使用JavaScript没有太大的联系（因为我刚开始其实就是这样）。但是当你深入到代码中，一些架构中的时候，你就会发现巧妙的运用原型，能让你的代码写的既简洁又优美



## 什么是原型对象

无论什么时候，**只要创建了一个新函数，就会根据一组特定的规则为该函数创建一个prototype属性**，这个**属性**指向**函数**的**原型对象**

举个栗子：

```javascript
function Person{
}
Person.prototype.name = "Nicholas";
Person.prototype.age = 29;
Person.prototype.job = "Software Engineer";
Person.prototype.sayName = function(){
	alert(this.name);
};

var person1 = new Person();
person1.sayName(); //"Nicholas"

var person2 = new Person();
person2.sayName(); //"Nicholas"

alert(person1.sayName == person2.sayName); //true
```

如下图图一所示，针对于上面的“栗子”，`Person`是一个函数，那么在 JavaScript中就会为这个函数创建一个prototype的属性，这个prototype属性指向该函数的原型对象。在默认情况下，所有原型对象都会自动获得一个constructor属性，这个属性指向该函数。


![图一](http://upload-images.jianshu.io/upload_images/5099107-8d025db6f9977c21.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


如上图图一所示：当调用构造函数创建一个新实例（person1和person2）后，该实例的内部将包含一个指针，指向构造函数的原型对象（Person Prototype）。



## 原型对象的属性查找机制

查找机制是这样的：**首先会先在实例上面搜索属性，如果找到了直接返回，否则就继续去原型上面寻找**。

说个**形象一点的故事**，这样好理解一点。假设：实例就是你，原型就是你的父亲。你的有些东西是继承自你的父亲。比如你父亲在北京有一套价值1000W的别墅，他作为不动产留给了你。你自己也通过自己的努力，积攒了300W的积蓄。这个时候，你急需要用钱，你改怎么办？**首先你会看你自己有没有这个符合条件的积蓄，如果有，那么就用掉自己的积蓄，如果没有，那么就只能用父亲的房子作抵押给别人了。**

先来个栗子：

```javascript
function Person(){
}

Person.prototype.money = "1000W";

var person1 = new Person();
var person2 = new Person();

person1.money = "300W";
alert(person1.money); //"300W"----来自实例，是自己的钱
alert(person2.money); //"1000W"----来自原型，是父亲的钱
```

从上面的例子我们能发现，当在alert()中访问person1.money时，他就会去实例上面搜索一个名为money的属性。这个属性在person1实例中找到了，直接返回。同理在person2的实例中寻找money属性时，没有找到，这时就需要继续去原型寻找，这个时候找到了，于是返回原型上面的值。



## 如何判断属性值是来自实例还是原型？

在了解完上面的知识之后，有的人就会问了，那我在写代码的时候，如何去判断属性值是来自实例的，还是来自原型对象上面的？就是说我想知道那个钱，到底我自己的积蓄，还是用的我父亲的房子。这个时候我就可以借助方法hasOwnProperty()，**当属性值是来自实例，也就是说是自己的钱，那么返回true，否则返回false**

来段代码来看看：

```javascript
function Person(){
}

Person.prototype.money = "1000W";

var person1 = new Person();
var person2 = new Person();

person1.money = "300W";
alert(person1.hasOwnProperty(money)); //true----来自实例，是自己的钱
alert(person2.hasOwnProperty(money)); //false----来自原型，是父亲的钱
```
这一部分讲完了，可以前往观看[js原型对象（二)](http://www.jianshu.com/p/a14db8fc6509)
