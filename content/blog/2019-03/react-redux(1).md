---
date: "2019-03-14T21:02:38+08:00"
publishdate: ""
lastmod: ""
draft: false
title: "React-redux(1) 摘要"
tags: ["前端"]
series: ["react"]
categories: ["react"]
img: "http://www.ruanyifeng.com/blogimg/asset/2016/bg2016091802.jpg"
toc: true
---

## 首先

用户发出 Action。

```javascript
store.dispatch(action);
```

## 然后

Store 自动调用 Reducer，并且传入两个参数：当前 State 和收到的 Action。 Reducer 会返回新的 State 。
```javascript
let nextState = todoApp(previousState, action);
```

## 调用

State 一旦有变化，Store 就会调用监听函数。
```javascript
// 设置监听函数
store.subscribe(listener);
```

## 渲染

listener可以通过store.getState()得到当前状态。如果使用的是 React，这时可以触发重新渲染 View。
```javascript
function listerner() {
  let newState = store.getState();
  component.setState(newState);   
}
```