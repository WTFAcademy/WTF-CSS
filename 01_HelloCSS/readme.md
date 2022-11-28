# WTF CSS 极简教程: 1. Hello CSS

WTF CSS 教程，总结/搬运自[MDN CSS 教程](https://developer.mozilla.org/zh-CN/docs/Web/CSS)，帮助新人快速入门 CSS。

**推特**：[@WTFAcademy_](https://twitter.com/WTFAcademy_) ｜ [@0xAA_Science](https://twitter.com/0xAA_Science)

**WTF Academy 社群：** [官网 wtf.academy](https://wtf.academy) | [WTF Solidity 教程](https://github.com/AmazingAng/WTFSolidity) | [discord](https://discord.wtf.academy) | [微信群申请](https://docs.google.com/forms/d/e/1FAIpQLSe4KGT8Sh6sJ7hedQRuIYirOoZK_85miz3dw7vA1-YjodgJ-A/viewform?usp=sf_link)

所有代码和教程开源在 github: [github.com/WTFAcademy/WTF-CSS](https://github.com/WTFAcademy/WTF-CSS)

---

这一讲，我们介绍CSS基础，并写第一个HTML+CSS程序：Hello CSS。你也可以直接阅读[MDN CSS基础](https://developer.mozilla.org/zh-CN/docs/Learn/CSS)。

## 什么是 CSS ？

层叠样式表（**C**ascading **S**tyle **S**heet，简称：CSS）是为网页添加样式的代码。本节将介绍 CSS 的基础知识，并解答类似问题：怎样将文本设置为黑色或红色？怎样将内容显示在屏幕的特定位置？怎样用背景图片或颜色来装饰网页？

## CSS 究竟什么来头？

和 HTML 类似，CSS 也不是真正的编程语言，甚至不是标记语言。它是一门样式表语言，这也就是说人们可以用它来选择性地为 HTML 元素添加样式。举个例子，如果你要将 HTML 页面里**所有**的段落元素 `<p>` 中的文本改成红色，可以这样写 CSS：

```css
p {
  color: red;
}
```

### “CSS 规则集”详解

让我们来仔细看一看上述 CSS：

![图解 CSS 声明](./img/1-1.png)

整个结构称为 **规则集**（通常简称“规则”），各部分释义如下：

- 选择器（**Selector**）：HTML 元素的名称位于规则集的开始。它选择了一个或多个需要添加样式的元素（在这个例子中就是 `p` 元素）。开发者要给不同元素添加样式只需要更改选择器。
- 声明（**Declaration**）：一个单独的规则，如 `color: red;` 。指定添加样式元素的**属性**和**属性值**。
- 属性（**Properties**）：改变 HTML 元素样式的途径。本例中 `color` 就是 `p` 元素的属性。CSS 中，由编写人员决定修改哪个属性以改变规则。
- 属性的值（Property value）: 在属性的右边，冒号后面即**属性的值**，它从指定属性的众多外观中选择一个值，我们除了 `red` 之外还有很多属性值可以用于 `color` 。

注意其他重要的语法：

- 每个规则集（除了选择器的部分）都应该包含在成对的大括号里（`{}`）。
- 在每个声明里要用冒号（`:`）将属性与属性值分隔开。
- 在每个规则集里要用分号（`;`）将各个声明分隔开。

如果要同时修改多个属性，只需要将它们用分号隔开，就像这样：

```css
p {
  color: red;
  width: 500px;
  border: 1px solid black;
}
```

## Hello CSS

下面，我们要写第一个包含 CSS 的程序：Hello CSS，看看 CSS 如何给 HTML页面添加更多的样式。如果你对 HTML 不熟悉，可以阅读 [WTF HTML极简教程](https://github.com/WTFAcademy/WTF-HTML)。

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

我们将所有段落元素 `<p>` 中的字体颜色设为蓝色（`color` 属性），并且居中显示（`text-align` 属性）。

```css
p {
    color: blue;
    text-align: center;
}
```

并且，我们将段落元素 `<p>` 中的加粗元素 `<strong>` 中的字体颜色设为绿色（`color` 属性），背景颜色设为浅蓝（`background-color` 属性），并且将内边距设为10像素（`padding` 属性）。

```css
p strong {
    color: green;
    background-color: #d0f0f6;
    padding: 10px;
}
```

## 总结

这一讲我们介绍了什么是 CSS，并且写了第一个包含 CSS 的程序：Hello CSS，下面我们会学习更多 CSS 的细节。