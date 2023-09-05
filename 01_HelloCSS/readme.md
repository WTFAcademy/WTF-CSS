# WTF CSS 极简教程: 1. Hello CSS

WTF CSS 教程，帮助新人快速入门 CSS。

**推特**：[@WTFAcademy_](https://twitter.com/WTFAcademy_) ｜ [@0xAA_Science](https://twitter.com/0xAA_Science)

**WTF Academy 社群：** [官网 wtf.academy](https://wtf.academy) | [WTF Solidity 教程](https://github.com/AmazingAng/WTFSolidity) | [discord](https://discord.gg/5akcruXrsk) | [微信群申请](https://docs.google.com/forms/d/e/1FAIpQLSe4KGT8Sh6sJ7hedQRuIYirOoZK_85miz3dw7vA1-YjodgJ-A/viewform?usp=sf_link)

所有代码和教程开源在 github: [github.com/WTFAcademy/WTF-CSS](https://github.com/WTFAcademy/WTF-CSS)

---

这一讲，我们介绍CSS基础，并写第一个HTML+CSS程序：Hello CSS。

## 什么是 CSS ？

CSS（**C**ascading **S**tyle **S**heet，层叠样式表）是为网页添加样式的代码。简单来说，HTML 负责文档的结构，而 CSS 则负责文档的表现样式。通过使用CSS，我们可以控制页面的布局，调整元素的颜色和尺寸，添加背景图像和边框，创建动画效果等。

CSS 被提出的初衷是为了解决内容与表现形式分离的问题。在早期的网页设计中，HTML标签被用来定义文档的结构和样式，这让文档的内容与样式混杂在一起，导致了代码的冗余和维护困难。CSS 的出现，使得我们可以将结构（HTML）和样式（CSS）进行分离，使网页的内容与表现形式得以分离，极大地提高了网页的可维护性和可读性。

## CSS 规则集

在CSS中，样式规则由两个主要的部分构成：选择器，以及一对花括号内的声明块。

```css
selector {
    property: value;
}
```

- **选择器**：用于指定CSS规则应用到哪些元素上。
- **声明块**：包含在花括号（{}）中的一组CSS声明，每个声明由一个属性和一个值组成，属性和值之间用冒号（:）分隔，每个声明的末尾需要加上分号（;）。

例如：

```css
h1 {
    color: blue;
    font-size: 24px;
}
```

这个CSS规则将应用到HTML文档中所有的h1元素上，使得这些h1元素的文字颜色为蓝色，字体大小为24像素。

## Hello CSS

下面，我们要写第一个包含 CSS 的程序：Hello CSS，展示如何在HTML文档中使用CSS。如果你对 HTML 不熟悉，可以阅读 [WTF HTML极简教程](https://github.com/WTFAcademy/WTF-HTML)。

```html
<!DOCTYPE html>
<html>    
    <head>
        <title>This is the head</title>
        <style type="text/css">
            p {
                color: blue;
                text-align: center;
            }
    
            p strong {
                color: green;
                background-color: #d0f0f6;
                padding: 10px;
            }
        </style>    
    </head>
    <body>
        <p>Hello <strong>CSS！</strong></p>
    </body>
</html>
```

![Hello CSS](./img/1-2.png)

在 Hello CSS 中，我们利用内部样式表将 CSS 嵌入到 HTML 中（一般放在 `<head>` 元素中）：

```html
<style type="text/css">
    ...
</style>
```

我们将所有段落元素 `<p>` 中的字体颜色设为蓝色（`color`），并且居中显示（`text-align`）。

```css
p {
    color: blue;
    text-align: center;
}
```

并且，我们将段落元素 `<p>` 中的加粗元素 `<strong>` 中的字体颜色设为绿色（`color`），背景颜色设为浅蓝（`background-color`），并且将内边距设为10像素（`padding`）。

```css
p strong {
    color: green;
    background-color: #d0f0f6;
    padding: 10px;
}
```

## 总结

这一讲我们介绍了什么是 CSS，并且写了第一个包含 CSS 的程序：Hello CSS。你可以阅读[MDN CSS基础](https://developer.mozilla.org/zh-CN/docs/Learn/CSS)学习CSS的更多细节。