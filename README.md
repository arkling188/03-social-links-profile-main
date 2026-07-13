# Frontend Mentor - 社交链接个人资料解决方案

这是我完成的 [Frontend Mentor Social links profile 挑战](https://www.frontendmentor.io/challenges/social-links-profile-UG32l9m6dQ)。

## 设计稿

### 桌面版

![社交链接个人资料桌面版设计稿](./design/destkop-design.jpg)

### 在线访问

[查看在线页面](https://arkling188.github.io/03-social-links-profile-main/)

## 概览

这个项目是一个个人资料社交链接卡片。页面中包含头像、姓名、地点、个人简介，以及 5 个社交平台链接。

这个练习重点是纵向 Flexbox 布局、按钮列表、链接语义、hover 状态、`width: 100%` 和父元素 padding 的关系。

## 使用的技术

- HTML5
- CSS
- Flexbox
- 本地图片资源
- `a` 链接标签
- `box-sizing: border-box`
- hover 状态

## 我学到了什么

### 社交按钮应该用 a 标签

一开始可以用 `div` 做视觉按钮，但这些内容本质上是链接，所以更适合用：

```html
<a class="option" href="#">GitHub</a>
```

这样语义更正确，也天然支持键盘聚焦。

### a 标签默认样式需要处理

`a` 标签默认可能有下划线，所以可以加：

```css
.option {
  text-decoration: none;
}
```

### hover 状态

按钮 hover 时背景变绿、文字变黑：

```css
.option:hover {
  background-color: hsl(75, 94%, 57%);
  color: black;
  cursor: pointer;
}
```

如果 HTML 里已经没有 `span`，就不要再写 `.option:hover span`，选择器要和实际结构对应。

### width: 100% 是相对父元素

按钮设置 `width: 100%` 时，它的宽度是相对于父元素 `.options` 的内容区域，不是相对于整个浏览器。

如果父元素在有 padding 的卡片里面，那么最终宽度会受到卡片内容区域影响。

### 重复写同一个属性，后面的覆盖前面的

之前出现过：

```css
.option {
  width: 100%;
  width: 248px;
}
```

最终生效的是后面的 `width: 248px`，所以 `width: 100%` 看起来没有生效。

### 使用 gap 控制按钮间距

按钮列表是一个纵向 flex 容器：

```css
.options {
  display: flex;
  flex-direction: column;
  gap: 14px;
}
```

`gap` 比给每个按钮写 `margin-bottom` 更清楚，因为它表达的是“子元素之间的距离”。

## 遇到的问题

### 按钮左右距离不一致

原因是 `.option` 里重复写了 `width`，后面的固定宽度覆盖了前面的 `100%`。

解决方法是删掉固定宽度，只保留：

```css
.option {
  width: 100%;
}
```

### 卡片上下空间过大

一开始卡片有 `padding`，头像和最后一个按钮又额外设置了 margin，导致上下距离叠加。

更好的思路是让 `.container` 的 `padding` 统一负责卡片内部上下左右留白。

### 少了 LinkedIn

设计稿中有 5 个社交链接：`GitHub`、`Frontend Mentor`、`LinkedIn`、`Twitter`、`Instagram`。

最终补齐了 `LinkedIn`。

## 继续改进

- 可以给 `.option:focus` 添加和 hover 一样的状态，提升键盘可访问性。
- 可以给头像添加更完整的 `alt` 文本。
- 可以把 CSS 拆到单独的样式文件。
- 可以用 `max-width` 和 `width: calc(100% - 32px)` 优化移动端。

## 作者

- arkling

## 核心总结

```text
链接用 a，不只是 div。
width: 100% 是相对父元素。
同一个属性后写的会覆盖先写的。
按钮列表用 flex + gap 很自然。
hover 和 HTML 结构要对应，不能选不存在的子元素。
```
