---
date: "2019-03-14T21:30:12+08:00"
publishdate: ""
lastmod: ""
draft: false
title: "React-redux(3) 摘要"
tags: ["前端"]
series: ["react"]
categories: ["react"]
img: ""
toc: true
---

React-Redux 将所有组件分成两大类：UI 组件（presentational component）和容器组件（container component）。
<hr>

## UI组件

- 只负责 UI 的呈现，不带有任何业务逻辑
- 没有状态（即不使用this.state这个变量）
- 所有数据都由参数（this.props）提供
- 不使用任何 Redux 的 API

又称为"纯组件"，即它纯函数一样，纯粹由参数决定它的值。

## 容器组件

- 负责管理数据和业务逻辑，不负责 UI 的呈现
- 带有内部状态
- 使用 Redux 的 API

## connect()

将两种组件连起来。

```javascript

import { connect } from 'react-redux'

const VisibleTodoList = connect(
  mapStateToProps,
  mapDispatchToProps
)(TodoList)

```
上面代码中，connect方法接受两个参数：mapStateToProps和mapDispatchToProps。它们定义了 UI 组件的业务逻辑。前者负责输入逻辑，即将state映射到 UI 组件的参数（props），后者负责输出逻辑，即将用户对 UI 组件的操作映射成 Action。

## ```<Provider>``` 组件

connect方法生成容器组件以后，需要让容器组件拿到state对象，才能生成 UI 组件的参数。而 React-Redux 提供Provider组件，可以让容器组件拿到state。
