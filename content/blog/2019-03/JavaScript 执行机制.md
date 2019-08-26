---
date: "2019-03-26T19:54:38+08:00"
publishdate: ""
lastmod: ""
draft: false
title: "javaScript 执行机制"
tags: ["前端"]
series: ["js"]
categories: ["js"]
img: ""
toc: true
---

## 关于JavaScript

JavaScript 是一门单线程语言

## JavaScript事件循环

为解决任务耗时过长，将任务分为两类：

- 同步任务
- 异步任务

![](https://user-gold-cdn.xitu.io/2017/11/21/15fdd88994142347?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

js引擎存在monitoring process进程，会持续不断的检查主线程执行栈是否为空，一旦为空，就会去Event Queue那里检查是否有等待被调用的函数。

```javascript

let data = [];
$.ajax({
    url:www.javascript.com,
    data:data,
    success:() => {
        console.log('发送成功!');
    }
})
console.log('代码执行结束');

```
上面是一段简易的ajax请求代码：

- ajax进入Event Table，注册回调函数```success```。
- 执行```console.log('代码执行结束')```。
- ajax事件完成，回调函数```success```进入Event Queue。
- 主线程从Event Queue读取回调函数```success```并执行。

## setTimeout

 setTimeout 是异步的，应该先执行同步任务，然后执行它。

- ```setTimeout(fn,0)```的含义是，指定某个任务在主线程最早可得的空闲时间执行，意思就是不用再等多少秒了，只要主线程执行栈内的同步任务全部执行完成，栈为空就马上执行。

## setInterval

 setInterval 是循环的执行， setTimeout 可使异步延迟执行。

- 需要注意的一点是：对于```setInterval(fn,ms)```来说，我们已经知道不是每过ms秒会执行一次fn，而是每过ms秒，会有fn进入Event Queue。一旦```setInterval```的回调函数fn执行时间超过了延迟时间ms，那么就完全看不出来有时间间隔了。

## Promise与process.nextTick(callback)

- ```Promise```是异步编程的一种解决方案。从语法上说，```Promise```是一个对象，从它可以获取异步操作的消息。
- ```process.nextTick(callback)```类似node.js版的"setTimeout"，在事件循环的下一次循环中调用 callback 回调函数。

除了广义的同步任务和异步任务，还可以将任务分为：

- macro-task(宏任务)：包括整体代码script，setTimeout，setInterval。
- micro-task(微任务)：Promise，process.nextTick。

不同类型的任务会进入对应的Event Queue，比如setTimeout和setInterval会进入相同的Event Queue。

![](https://user-gold-cdn.xitu.io/2017/11/21/15fdcea13361a1ec?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

```javascript

setTimeout(function() {
    console.log('setTimeout');
})

new Promise(function(resolve) {
    console.log('promise');
}).then(function() {
    console.log('then');
})

```

- 这段代码作为宏任务，进入主线程。
- 先遇到```setTimeout```，那么将其回调函数注册后分发到宏任务Event Queue。
- 接下来遇到了```Promise```，```new Promise```立即执行，```then```函数分发到微任务Event Queue。遇到```console.log()```，立即执行。
- 整体代码script作为第一个宏任务执行结束，看看有哪些微任务，我们发现了```then```在微任务Event Queue里面，执行。
- 第一轮事件循环结束了，我们开始第二轮循环，当然要从宏任务Event Queue开始。我们发现了宏任务Event Queue中```setTimeout```对应的回调函数，立即执行。
- 结束。


https://juejin.im/post/59e85eebf265da430d571f89