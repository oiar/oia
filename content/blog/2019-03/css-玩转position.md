---
date: "2019-03-30T10:27:49+08:00"
publishdate: ""
lastmod: ""
draft: false
title: "Css 玩转position"
tags: ["前端"]
series: ["css"]
categories: ["css"]
img: ""
toc: true
---

## 定义和用法

position 属性规定元素的定位类型。

![](https://ws4.sinaimg.cn/large/006tKfTcly1g1km0loqn8j30ml09lgn6.jpg)

## fixed实例

背景图片相对于浏览器窗口进行定位

```html

<div class="image_module" style="background-image: url(https://dynamic.thoughtworks.com/landing_pages/parallax_image-441c058c0a407e96deddd32bd6a00649.jpeg);">
  <div class="full-width-image">
    <div class="vertical_center"></div>
      <div class="module_title_style">
        <h2 class="module_title">准备好加入我们了吗？</h2>
        <el-button class="el_button">让我们开始吧</el-button>
      </div>
  </div>
</div>

```

```css

.image_module {
  background-size: cover; // 保持图像的纵横比并将图像缩放成将完全覆盖背景定位区域的最小大小。
  background-attachment: fixed; // 当页面的其余部分滚动时，背景图像不会移动。
  background-position: center;
  min-height: 500px;
  position: relative;
}
.full-width-image {
  text-align: center;
  display: inline-block;
  position: absolute; // 相对于image_module进行定位
  top: 0;
  right: 0;
  left: 0;
  bottom: 0;
}
.vertical_center {
  height: 100%; // 即height：500px
  display: inline-block;
  vertical-align: middle;
}
.module_title_style {
  display: inline-block;
  vertical-align: middle;
}
.module_title {
  font-size: 48px;
  color: #fff;
  font-weight: 300;
  margin: 0 0 25px 0;
}
.el_button {
  background: #f38a3e;
  color: #fff;
  border: #f38a3e;
  height: 50px;
  font-size: 16px
}

```
