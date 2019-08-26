---
date: "2019-03-15T16:23:38+08:00"
publishdate: ""
lastmod: ""
draft: false
title: "Vuex 摘要"
tags: ["前端"]
series: ["vue"]
categories: ["vue"]
img: ""
toc: true
---

## The difference of Redux and Vuex

React is different from Vue in the way it processes updates: React renders a virtual DOM then calculates optimal DOM operations to make the currently rendered DOM match the new Virtual Dom. But it has no way of knowing whether a particular component needs to re-render or not based on the new data. Vue instances keep track of which bits of data they depend on to render. These instances automatically register what needs to re-render when the data changes.

## Vuex
![](https://vuex.vuejs.org/vuex.png)

- Mutations

  The only way to change state in a Vuex store is by committing a mutation.
  But one thing to remember is that mutations are always synchronous to ensure that the state isn’t dependent on the timing and order of unpredictable events.

- Actions

  Actions are similar to mutations and work like Redux actions. Actions can contain arbitrary asynchronous operations.

- State

  Vuex uses a single state tree. One thing to remember is that the state can only be changed by committing mutations.

- Benefits

  - Mutations are easier to work with then Reducers
  - Asynchronous actions are much more organized in Vuex. There is no need to write ```_ON_LOAD```, ```_SUCCESS``` or ```_FAIL``` middle term state actions.
  - Out of the box dev tools
  - Much easier setup. It is easy as Vue.use(Vuex)
  - Vuex takes advantage of Vue.js uniqueness


https://www.codementor.io/petarvukasinovic/redux-vs-vuex-for-state-management-in-vue-js-n10yd7g2f