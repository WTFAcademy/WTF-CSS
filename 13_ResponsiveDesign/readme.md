# WTF CSS 极简教程: 13. 响应式设计

WTF CSS 教程，帮助新人快速入门 CSS。

**推特**：[@WTFAcademy_](https://twitter.com/WTFAcademy_) ｜ [@0xAA_Science](https://twitter.com/0xAA_Science)

**WTF Academy 社群：** [官网 wtf.academy](https://wtf.academy) | [WTF Solidity 教程](https://github.com/AmazingAng/WTFSolidity) | [discord](https://discord.gg/5akcruXrsk) | [微信群申请](https://docs.google.com/forms/d/e/1FAIpQLSe4KGT8Sh6sJ7hedQRuIYirOoZK_85miz3dw7vA1-YjodgJ-A/viewform?usp=sf_link)

所有代码和教程开源在 github: [github.com/WTFAcademy/WTF-CSS](https://github.com/WTFAcademy/WTF-CSS)

---

这一讲，我们介绍如何使用浏览器响应式设计来使页面即使在不同尺寸下也展现完好的方案。

早年设计 Web 时，页面是以适配特定的屏幕大小为考量创建的。如果用户正在使用比设计者考虑到的更小或者更大的屏幕，那么结果从多余的滚动条，到过长的行和没有被合理利用的空间，不一而足。随着人们使用的屏幕尺寸的种类越来越多，出现了响应式网页设计的概念（responsive web design，RWD）。

## 响应式设计

“响应式设计”这个词是[Ethan Marcotte 在 2010 年首度提出的](https://alistapart.com/article/responsive-web-design/)，他将其描述为三种技术的混合使用。

1. 第一个是液态网格，这早先已由 Gillenwater 进行探讨，可以在 Marcotte 的文章《[Fluid Grids](https://alistapart.com/article/fluidgrids/)》（出版于 2009 年的《A List Apart》上）中读到。
2. 第二个是[液态图像](https://unstoppablerobotninja.com/entry/fluid-images)的理念。通过使用相当简单的将设置 max-width 属性设置为 100%的技术，图像可以在包含它们的列变得比图像原始尺寸窄的时候，缩放得更小，但总不会变得更大。这使得图像可以被缩放，以被放到一个灵活尺寸的列，而不是溢出出去，同时也不会在列宽于图像的时候，使图像变得太大以至于画质变得粗糙。
3. 第三个关键的组件是[媒体查询](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Media_Queries)。媒体查询使以往 Cameron Adams 探讨过的、由 JavaScript 实现的布局类型切换，可以只使用 CSS 实现。和所有尺寸的屏幕都使用一种布局不同的是，布局是可以改变的：侧栏可以在小屏幕上重新布局，而替代用的导航栏也可以显示出来。

## 媒介查询

媒介查询允许我们运行一系列测试，例如用户的屏幕是否大于某个宽度或者某个分辨率，并将CSS选择性地适应用户的需要应用在样式化页面上。

例如，下面的媒体查询进行测试，以知晓当前的Web页面是否被展示为屏幕媒体（也就是说不是印刷文档），且视口至少有`800`像素宽。用于`.container`选择器的 CSS 将只会在这两件前提存在的情况下应用。

```css
@media screen and (min-width: 800px) {
  .container {
    margin: 1em 2em;
  }
}
```

你可以在一张样式表上加入多条媒体查询，调整整个页面或者部分页面以达到适应各式屏幕尺寸的最佳效果。媒体查询，以及样式改变时的点，被叫做断点（breakpoints）。

使用媒体查询时的一种通用方式是，为窄屏设备（例如移动设备）创建一个简单的单栏布局，然后检查是否是大些的屏幕，在你知道你有足够容纳的屏幕宽度的时候，开始采用一种多栏的布局。这经常被描述为移动优先设计。

## 灵活网格

响应式站点不只是在断点之间改变它们的布局，它们是建立在灵活网格上的。一个灵活网格意味着你不需要适配每个可能使用的设备尺寸，然后为其建立一个精确到像素级的适配布局。

使用灵活网格，你只需要加进去一个断点，在内容看起来不齐整的时候改变设计。

例如如果我们的预期栏尺寸为 60 像素，而且它所在的上下文（或者容器）为 960 像素，我们在将零点二的空间移动到右边以后，用 960 去除 60，得到我们能够使用在我们的 CSS 上的值。

```css
.col {
  width: 6.25%; /* 60 / 960 = 0.0625 */
}
```

下面的例子阐释了一个使用媒体查询和灵活网格的简单响应式设计。在窄屏幕上，布局将盒子堆叠在另一个的上面：

![](./img/mdn-rwd-mobile.png)

在宽些的屏幕上，它们变成了两列：

![](./img/mdn-rwd-desktop.png)

> 备注：你可以在 GitHub 上找到此[示例](https://mdn.github.io/css-examples/learn/rwd/float-based-rwd.html)的实时示例和[源代码](https://github.com/mdn/css-examples/blob/main/learn/rwd/float-based-rwd.html)。

## 现代布局技术

现代布局方式，例如[多栏布局](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/CSS_layout/Multiple-column_Layout)、[伸缩盒](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/CSS_layout/Flexbox)和[网格](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/CSS_layout/Grids)默认是响应式的。它们都假设你在尽力创建一个可伸缩网格，而且给了你更容易这样做的方式。

### 多个列

这些布局方式中最老的一个是多个列，即当你指定一个`column-count`的时候，这意指你希望把你的内容分成多少列。浏览器之后会算出这些列的大小，这是一个随着屏幕尺寸变化的尺寸。

```css
.container {
  column-count: 3;
}
```

如果你却去指定`column-width` 话，你是在指定一个最小宽度。浏览器会尽可能多数量地创建这一宽度的列，只要它们可以恰当地放进容器里面，然后将所有列之间的剩余空间共享出去。因而列的数量会随着空间的多少而改变。

```css
.container {
  column-width: 10em;
}
```

### 伸缩盒

在伸缩盒中，初始的行为是，弹性的物件将参照容器里面的空间的大小，缩小和分布物件之间的空间。通过更改`flex-grow`和`flex-shrink`的值，你可以指示在物件遇到周围有更多或者更少的空间的情况下，你所期望的物件表现。

在下面的示例中，和布局专题的[Flexbox: Flexible sizing of flex items](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/CSS_layout/Flexbox#flexible_sizing_of_flex_items)中所描述的那样，使用了`flex: 1`的简写，可伸缩物件每个将会占据一份可伸缩容器中相等大小的空间。

```css
.container {
  display: flex;
}

.item {
  flex: 1;
}
```

> 备注：作为一个示例，我们已经重构了上面的简单响应式布局，这次我们用了伸缩盒。你可以看看我们是怎么样才不再需要使用奇怪的百分数值来计算列的尺寸的：[示例](https://mdn.github.io/css-examples/learn/rwd/flex-based-rwd.html)、[源代码](https://github.com/mdn/css-examples/blob/main/learn/rwd/flex-based-rwd.html)。

### CSS网格

在CSS网格布局中，`fr`单位许可了跨网格轨道可用空间的分布。下面的示例创建了一个有着`3`个大小为`1fr`的轨道的网格容器。这会创建三个列轨道，每个占据了容器中可用空间的一部分。你可以在 [Flexible grids with the fr unit](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/CSS_layout/Grids#flexible_grids_with_the_fr_unit) 下的学习布局网格专题了解更多和这一方式相关的信息。

```css
.container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
}
```

> 备注：网格布局版本的代码要更简单，因为我们可以在.wrapper 上定义列：[示例](https://mdn.github.io/css-examples/learn/rwd/grid-based-rwd.html)，[源代码](https://github.com/mdn/css-examples/blob/main/learn/rwd/grid-based-rwd.html)。

![](./img/grid.png)

## 响应式图像

最简单的处理响应式图像的方式是在 Marcotte 的早年的关于响应式设计的文章上所描述的那样。基本来说，你可以用一张有着所需最大尺寸的图像。然后缩放它。这仍然是今日所使用的一种方式，而且在大多数样式表里面，你在某些地方可以找到下面的 CSS：

```css
img {
  max-width: 100%;
}
```

这种方式有显然的弊端。图像有可能会显示得比它的原始尺寸小很多，以至于浪费带宽——一个移动端用户会下载几倍于他们在浏览器窗口中实际看到的大小的图像。此外，你可能不想在移动端和桌面端有相同的图像宽高比例。

响应式图像，使用了`<picture>`元素和`<img>`的`srcset`和`sizes`特性，解决了这两个问题。你可以提供附带着“提示”（描述图像最适合的屏幕尺寸和分辨率的元数据）的多种尺寸，浏览器将会选择对设备最合适的图像，以确保用户下载尺寸适合他们使用的设备的图像。

## 响应式排版

在早期的工作没有考虑的一个响应式设计的元素是响应式排版的理念。本质上讲，这描述了根据屏幕真实使用范围的多少，在媒体查询的同时改变字体大小。

在本例子中，我们想讲我们的一级标题设置为 4rem，也就是说它将会有我们的基础字体的四倍大。这真的是个很大的标题！我们只想在大些的屏幕上有这么个超大的标题，那我们先弄个小点的标题，再使用媒体查询，在我们知道用户使用至少 1200px 的屏幕的时候，拿大些的尺寸覆写它。

```css
html {
  font-size: 1em;
}

h1 {
  font-size: 2rem;
}

@media (min-width: 1200px) {
  h1 {
    font-size: 4rem;
  }
}
```

我们已经编辑了我们在上面的响应式网格示例，让它同时包含了使用了圈出方式的响应式类型。你也可以看下随着布局变为两栏，标题是怎样转换大小的。

移动端，标题变小了：

![](./img/mdn-rwd-font-mobile.png)

但在桌面端，我们看到了大点的标题：

![](./img/mdn-rwd-font-desktop.png)

> 备注： 查看这个编排好的示例：[示例](https://mdn.github.io/css-examples/learn/rwd/type-rwd.html)，[源代码](https://github.com/mdn/css-examples/blob/main/learn/rwd/type-rwd.html)。

正如这种排版方式展示的这样，你不需要让媒介查询只能改变页面的布局。它们也能用来调节每个元素，让它们在别的大小的屏幕上更加可用或者更具吸引力。

### 使用视口单位实现响应式排版

一个有趣的方式是使用视口单位 vw 来实现响应式排版。1vw 等同于视口宽度的百分之一，即如果你用 vw 来设定字体大小的话，字体的大小将总是随视口的大小进行改变。

```css
h1 {
  font-size: 6vw;
}
```

问题在于，当做上面的事情的时候，因为文本总是随着视口的大小改变大小，用户失去了放缩任何使用 vw 单位的文本的能力。所以你永远都不要只用 viewport 单位设定文本。

这里有一个解决方法，它使用了 [calc()](https://developer.mozilla.org/zh-CN/docs/Web/CSS/calc)，如果你将 vw 单位加到了使用固定大小（例如 em 或者 rem）的值组，那么文本仍然是可放缩的。基本来说，是 vw 加在了放缩后的值上。

```css
h1 {
  font-size: calc(1.5rem + 3vw);
}
```

这就是说，我们只需要指定标题的字体大小一次，而不是为移动端设定它，然后再在媒介查询中重新定义它。字体会在你增加视口大小的时候逐渐增大。

> 备注： 查看这种情况的一个编排好的示例： [示例](https://mdn.github.io/css-examples/learn/rwd/type-vw.html)，[源代码](https://github.com/mdn/css-examples/blob/main/learn/rwd/type-vw.html)。

## 视口元标签

如果你看看一张响应式页面的 HTML 源代码，你通常将会在文档的`<head>`看到下面的`<meta>`标签。

```html
<meta name="viewport" content="width=device-width,initial-scale=1" />
```

这个元标签告诉移动端浏览器，它们应该将视口宽度设定为设备的宽度，将文档放大到其预期大小的 100%，在移动端以你所希望的为移动优化的大小展示文档。

和视口元标签一起，你可以使用另外几个设定，但大体说来，上面那行就是你想要使用的。

- `initial-scale`：设定了页面的初始缩放，我们设定为 1。
- `height`：特别为视口设定一个高度。
- `minimum-scale`：设定最小缩放级别。
- `maximum-scale`：设定最大缩放级别。
- `user-scalable`：如果设为 no 的话阻止缩放。

你应该避免使用`minimum-scale`、`maximum-scale`，尤其是将 `user-scalable`设为`no`。用户应该有权力尽可能大或小地进行缩放，阻止这种做法会引起访问性问题。

> 备注： CSS`@`规则是被设计用来替换掉视口元标签的——[`@viewport`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/@viewport)——但是浏览器对它的支持太差了。它是在 IE 和 Edge 中引入的，但自从 Chromium 内核的 Edge 发布以后，它就不再受到 Edge 浏览器支持了。

## 小结

本节我们学习了很多方法来实现网站页面的响应式设计，它涵盖了很多CSS和HTML的功能和技术，现在基本上就是我们默认建设网站的方式。
