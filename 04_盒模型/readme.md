# WTF CSS 极简教程: 4.盒模型

WTF CSS 教程，总结/搬运自[MDN CSS 教程](https://developer.mozilla.org/zh-CN/docs/Web/CSS)，帮助新人快速入门 CSS。

**推特**：[@WTFAcademy\_](https://twitter.com/WTFAcademy_) ｜ [@0xAA_Science](https://twitter.com/0xAA_Science)

**WTF Academy 社群：** [官网 wtf.academy](https://wtf.academy) | [WTF Solidity 教程](https://github.com/AmazingAng/WTFSolidity) | [discord](https://discord.wtf.academy) | [微信群申请](https://docs.google.com/forms/d/e/1FAIpQLSe4KGT8Sh6sJ7hedQRuIYirOoZK_85miz3dw7vA1-YjodgJ-A/viewform?usp=sf_link)

所有代码和教程开源在 github: [github.com/WTFAcademy/WTF-CSS](https://github.com/WTFAcademy/WTF-CSS)

---

这一讲，我们来介绍 CSS 盒模型。在 CSS 中，所有的元素都被一个个的“盒子（box）”包围着，理解这些“盒子”的基本原理，是我们使用 CSS 实现准确布局、处理元素排列的关键。

## 什么是 CSS 盒模型？

完整的 CSS 盒模型应用于块级盒子，内联盒子只使用盒模型中定义的部分内容。模型定义了盒的每个部分 —— margin, border, padding, and content —— 合在一起就可以创建我们在页面上看到的内容。为了增加一些额外的复杂性，有一个标准的和替代（IE）的盒模型。

### 盒模型的各个部分

CSS 中组成一个块级盒子需要：

- Content box: 这个区域是用来显示内容，大小可以通过设置 width 和 height.
- Padding box: 包围在内容区域外部的空白区域；大小通过 padding 相关属性设置。
- Border box: 边框盒包裹内容和内边距。大小通过 border 相关属性设置。
- Margin box: 这是最外面的区域，是盒子和其他元素之间的空白区域。大小通过 margin 相关属性设置。

如下图：

![](./img/4-1.png)

## 标准盒模型

在标准模型中，如果你给盒设置 width 和 height，实际设置的是 content box。padding 和 border 再加上设置的宽高一起决定整个盒子的大小。见下图。

假设定义了 width, height, margin, border, and padding:

```html
.box { width: 350px; height: 150px; margin: 25px; padding: 25px; border: 5px
solid black; }
```

如果使用标准模型宽度 = 410px (350 + 25 + 25 + 5 + 5)，高度 = 210px (150 + 25 + 25 + 5 + 5)，padding 加 border 再加 content box。

![](./img/4-2.png)

> 备注：
>
> margin 不计入实际大小 —— 当然，它会影响盒子在页面所占空间，但是影响的是盒子外部空间。盒子的范围到边框为止 —— 不会延伸到 margin。

## 替代（IE）盒模型

你可能会认为盒子的大小还要加上边框和内边距，这样很麻烦，而且你的想法是对的 ! 因为这个原因，css 还有一个替代盒模型。使用这个模型，所有宽度都是可见宽度，所以内容宽度是该宽度减去边框和填充部分。使用上面相同的样式得到 (width = 350px, height = 150px)。如下图：

![](./img/4-3.png)

也就是说在替代（IE）盒模型下，你设置 `width` 属性，已经不仅仅是 `content` 的宽度，还包含了 `padding` 和 `border` 的大小。

## 改变盒模型

默认浏览器会使用标准模型。如果需要使用替代模型，您可以通过为其设置 box-sizing: border-box 来实现。这样就可以告诉浏览器使用 border-box 来定义区域，从而设定您想要的大小。

```html
.box { box-sizing: border-box; }
```

如果你希望所有元素都使用替代模式，而且确实很常用，设置 box-sizing 在 <html> 元素上，然后设置所有元素继承该属性，正如下面的例子。

```html
html { box-sizing: border-box; } // 使所有元素继承该属性 *, *::before, *::after
{ box-sizing: inherit; }
```

## 总结

这就是你需要了解的关于盒模型的大部分内容。如果以后你发现对于盒模型的布局仍有困惑，你将会回来温故这些内容。
