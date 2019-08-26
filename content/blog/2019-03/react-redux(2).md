---
date: "2019-03-14T21:20:45+08:00"
publishdate: ""
lastmod: ""
draft: false
title: "React-redux(2) 摘要"
tags: ["前端"]
series: ["react"]
categories: ["react"]
img: ""
toc: true
---

## 同步与异步

Action 发出以后，Reducer 立即算出 State，叫做同步；Action 发出以后，过一段时间再执行 Reducer，就是异步。
怎么才能 Reducer 在异步操作结束后自动执行呢？这就要用到新的工具：中间件（middleware）。

## 中间件（middleware）
![](http://www.ruanyifeng.com/blogimg/asset/2016/bg2016092002.jpg)

applyMiddlewares() 方法是 Redux 的原生方法，作用是将所有中间件组成一个数组，依次执行。下面是它的源码。
```javascript

export default function applyMiddleware(...middlewares) {
  return (createStore) => (reducer, preloadedState, enhancer) => {
    var store = createStore(reducer, preloadedState, enhancer);
    var dispatch = store.dispatch;
    var chain = [];

    var middlewareAPI = {
      getState: store.getState,
      dispatch: (action) => dispatch(action)
    };
    chain = middlewares.map(middleware => middleware(middlewareAPI));
    dispatch = compose(...chain)(store.dispatch);

    return {...store, dispatch}
  }
}

```
上面代码中，所有中间件被放进了一个数组 chain，然后嵌套执行，最后执行 store.dispatch。可以看到，中间件内部（middlewareAPI）可以拿到 getState 和 dispatch 这两个方法。

## 异步操作

同步操作只要发出一种 Action 即可，异步操作的差别是它要发出三种 Action。

- 操作发起时的 Action
- 操作成功时的 Action
- 操作失败时的 Action

三种 Action 有两种不同的写法。

```javascript

// 写法一：名称相同，参数不同
{ type: 'FETCH_POSTS' }
{ type: 'FETCH_POSTS', status: 'error', error: 'Oops' }
{ type: 'FETCH_POSTS', status: 'success', response: { ... } }

// 写法二：名称不同
{ type: 'FETCH_POSTS_REQUEST' }
{ type: 'FETCH_POSTS_FAILURE', error: 'Oops' }
{ type: 'FETCH_POSTS_SUCCESS', response: { ... } }

```

State 也要反应不同的操作状态。

```javascript

let state = {
  // ... 
  isFetching: true,//表示是否在抓取数据
  didInvalidate: true,//表示数据是否过时
  lastUpdated: 'xxxxxxx'//表示上一次更新时间
};

```
异步操作思路：

- 操作开始时，送出一个 Action，触发 State 更新为"正在操作"状态，View 重新渲染
- 操作结束后，再送出一个 Action，触发 State 更新为"操作结束"状态，View 再一次重新渲染

## redux-thunk 中间件

Action Creator 解决异步操作结束后，系统自动无法送出第二个 Action 的问题。但由于 Action 是由 store.dispatch 方法发送的。而 store.dispatch 方法正常情况下，参数只能是对象，不能是函数。这时需要用到中间件 redux-thunk 改造 store.dispatch ，使得后者可以接受函数作为参数。

## redux-promise 中间件

这个中间件使得 store.dispatch 方法可以接受 Promise 对象作为参数。

http://www.ruanyifeng.com/blog/2016/09/redux_tutorial_part_two_async_operations.html