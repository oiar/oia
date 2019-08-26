---
date: "2019-03-27T11:26:38+08:00"
publishdate: ""
lastmod: ""
draft: false
title: "JavaScript 值类型和引用类型"
tags: ["前端"]
series: ["js"]
categories: ["js"]
img: ""
toc: true
---

## 值类型

值类型（基本类型）：字符串（String）、数值（Number）、布尔值（Boolean）、Undefined、Null  （这5种基本数据类型是按值访问的，因为可以操作保存在变量中的实际的值

## 引用类型

引用类型：对象（Object）、数组（Array）、函数（Function）

## 两者区别

（1）值类型

- 占用空间固定，保存在栈中（栈：当一个方法执行时，每个方法都会建立自己的内存栈，随着方法执行结束后，内存栈自然销毁。）
- 保存与复制的是值的本身
- 使用typeof检测数据的类型
- 基本类型数据是值类型

（2）引用类型

- 占用空间不固定，保存在堆中（堆：当我们在程序中创建一个对象时，这个对象将被保存到运行时数据区（堆内存）中，堆内存中的对象不会随方法结束而销毁，即使方法结束后，这个对象还可被其他引用变量所引用。只有当没有任何引用变量引用这个对象时，系统的垃圾回收机制才会回收它。）
- 保存与复制的是指向对象的一个指针
- 使用instanceof检测数据类型
- 使用new()方法构造出的是引用类型

## 区别举例

- 引用类型

```javascript

var obj1 = new Object(); 
var obj2 = obj1; 
obj1.name = "Nicholas"; 
alert(obj2.name); //"Nicholas" 

```
图解：
![](https://img2018.cnblogs.com/blog/1207871/201901/1207871-20190102110222496-978852296.png)
