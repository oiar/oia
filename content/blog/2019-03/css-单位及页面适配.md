---
date: "2019-03-29T11:56:09+08:00"
publishdate: ""
lastmod: ""
draft: false
title: "Css 单位及页面适配"
tags: ["前端"]
series: ["css"]
categories: ["css"]
img: "https://pic2.zhimg.com/80/v2-e1518b6c0b90de95130acfd648c591e5_hd.jpg"
toc: true
---

## px（绝对长度单位）

像素px是相对于显示器屏幕分辨率而言的。px只能用于```固定尺寸```。

## em（相对长度单位）

- 浏览器的默认字体都是16px，那么1em=16px，以此类推计算12px=0.75em，10px=0.625em，2em=32px；
- 为了简化font-size的换算，我们在body中写入以下代码：

```javascript
body {font-size: 62.5%;  } /*  公式16px*62.5%=10px  */
```
- em的值并不是固定的；em会继承父级元素的字体大小（参考物是父元素的```font-size```）；
- em中所有的字体都是相对于父元素的大小决定的；所以如果一个设置了```font-size:1.2em```的元素在另一个设置了```font-size:1.2em```的元素里，而这个元素又在另一个设置了```font-size:1.2em```的元素里，那么最后计算的结果是```1.2*1.2*1.2=1.728em```

## rem(相对长度单位)

与em相似：1rem=16px。特点：

- 和em不同的是rem总是相对于```根元素```(如:root{})，而不像em一样使用级联的方式来计算尺寸。这种相对单位使用起来更简单。
- rem支持IE9及以上，意思是相对于根元素html（网页），不会像em那样，依赖于父元素的字体大小，而造成混乱。使用起来安全了很多。

## 页面适配

页面适配，指的是同样的布局，在不同大小的屏幕上怎么进行缩放、控制间距、宽高、字号等大小。

页面适配的方式：

- 使用```px```，结合Media Query进行阶梯式的适配；
- 使用```%```，按百分比自适应布局；
- 使用```rem```，结合html元素的font-size来根据屏幕宽度适配
- 使用```vw```、```vh```，直接根据视口宽高适配。

## 媒体查询（Media Query）

媒体查询包含一个可选的媒体类型和媒体特性表达式(0或多个)最终会被解析为true或false。如果媒体查询中指定的媒体类型匹配展示文档所使用的设备类型，并且所有的表达式的值都是true，那么该媒体查询的结果为true。

```javascript

<!-- 样式表中的CSS媒体查询 -->
<style>
@media (max-width: 600px) {
  .facet_sidebar {
    display: none;
  }
}
</style>

```

![](https://ws2.sinaimg.cn/large/006tKfTcly1g1jl8lt42uj30nb0edjt1.jpg)

https://developer.mozilla.org/zh-CN/docs/Web/Guide/CSS/Media_queries