---
date: "2019-03-27T17:12:24+08:00"
publishdate: ""
lastmod: ""
draft: false
title: "JavaScript 代码风格"
tags: ["前端"]
series: ["js"]
categories: ["js"]
img: ""
toc: true
---

## 解构赋值

```javascript

function bar() { return {a: 1, b: 2, c: 3}; }
let { a, c } = bar();
console.log(a); // 1
console.log(c); // 3
console.log(b); // undefined

```

```javascript

function baz() { 
    return {
        x: 'car',
        y: 'London',
        z: { name: 'John', age: 21}
    }; 
}
let { x: vehicle, y: city, z: { name: driver } } = baz();
console.log(
    `I'm going to ${city} with ${driver} in their ${vehicle}.`
); // I'm going to London with John in their car. 

```

## 箭头函数

箭头函数一个最重要的用途之一就是应用在数组的相关函数中，像```.map```，```.forEach```，```.sort```等等。

```javascript

let arr = [ 5, 6, 7, 8, 'a' ];
let b = arr.map( item => item + 3 );
console.log(b); // [ 8, 9, 10, 11, 'a3' ]

```

## for...of 循环

```javascript

let a = ['a', 'b', 'c', 'd' ];
// ES6 
for ( var val of a ) {
    console.log( val );
} // "a" "b" "c" "d"
// pre-ES6 
for ( var idx in a ) {
    console.log( idx );
}  // 0 1 2 3

```