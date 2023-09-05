# WTF CSS极简教程: 9. 布局

WTF CSS教程，帮助新人快速入门CSS。

**推特**：[@WTFAcademy_](https://twitter.com/WTFAcademy_)  ｜ [@0xAA_Science](https://twitter.com/0xAA_Science) 

**WTF Academy社群：** [官网 wtf.academy](https://wtf.academy) | [WTF Solidity教程](https://github.com/AmazingAng/WTFSolidity) | [discord](https://discord.gg/5akcruXrsk) | [微信群申请](https://docs.google.com/forms/d/e/1FAIpQLSe4KGT8Sh6sJ7hedQRuIYirOoZK_85miz3dw7vA1-YjodgJ-A/viewform?usp=sf_link)

所有代码和教程开源在github: [github.com/WTFAcademy/WTF-CSS](https://github.com/WTFAcademy/WTF-CSS)

---

这一讲，我们介绍 CSS 布局，涉及浮动和定位的传统布局方法，以及像 flexbox 这样的现代布局工具。每种技术都有它们的用途，各有优缺点，相互辅助。通过理解各个布局方法的设计理念，你能够找到构建你想要的网页需要的布局方案。

## 正常布局

正常布局流 (normal flow) 是指在不对页面进行任何布局控制时，浏览器默认的 HTML 布局方式。让我们快速地看一个 HTML 的例子：

```html
<p>I love my cat.</p>

<ul>
  <li>Buy cat food</li>
  <li>Exercise</li>
  <li>Cheer up friend</li>
</ul>

<p>The end!</p>
```

默认情况下，浏览器的显示如下：

<p>I love my cat.</p>

<ul>
  <li>Buy cat food</li>
  <li>Exercise</li>
  <li>Cheer up friend</li>
</ul>

<p>The end!</p>

注意，HTML 元素完全按照源码中出现的先后次序显示——第一个段落、无序列表、第二个段落。

出现在另一个元素下面的元素被描述为块元素，与出现在另一个元素旁边的内联元素不同，内联元素就像段落中的单个单词一样。

## 浮动布局

把一个元素“浮动”(float) 起来，会改变该元素本身和在正常布局流（normal flow）中跟随它的其他元素的行为。这一元素会浮动到左侧或右侧，并且从正常布局流 (normal flow) 中移除，这时候其他的周围内容就会在这个被设置浮动（[float](https://developer.mozilla.org/zh-CN/docs/Web/CSS/float)）的元素周围环绕。

[float](https://developer.mozilla.org/zh-CN/docs/Web/CSS/float) 属性有四个可能的值：

- `left` — 将元素浮动到左侧。
- `right` — 将元素浮动到右侧。
- `none` — 默认值，不浮动。
- `inherit` — 继承父元素的浮动属性。

在下面这个例子当中，我们把一个 `<div>` 元素浮动到左侧，并且给了他一个右侧的margin，把文字推开。这给了我们文字环绕着这个 `<div>` 元素的效果，在现代网页设计当中，这是你唯一需要学会的事情。

```html
<h1>Simple float example</h1>

<div class="box">Float</div>

<p> Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla luctus aliquam dolor, eu lacinia lorem placerat vulputate. Duis felis orci, pulvinar id metus ut, rutrum luctus orci. Cras porttitor imperdiet nunc, at ultricies tellus laoreet sit amet. Sed auctor cursus massa at porta. Integer ligula ipsum, tristique sit amet orci vel, viverra egestas ligula. Curabitur vehicula tellus neque, ac ornare ex malesuada et. In vitae convallis lacus. Aliquam erat volutpat. Suspendisse ac imperdiet turpis. Aenean finibus sollicitudin eros pharetra congue. Duis ornare egestas augue ut luctus. Proin blandit quam nec lacus varius commodo et a urna. Ut id ornare felis, eget fermentum sapien.</p>
```

```css
.box {
  float: left;
  width: 150px;
  height: 150px;
  margin-right: 30px;
}
```

![](./img/9-5.png)

## 定位布局

定位（Position）是另一个重要的CSS布局工具，它可以控制元素在页面上的精确位置。`position`属性有五个值：`static`（默认），`relative`，`absolute`，`fixed`和`sticky`。

- `static`：元素按照正常的文档流进行定位（即不进行特殊定位）。

- `relative`：元素相对于其正常位置进行定位。

```css
div {
    position: relative;
    top: 20px; /* 向下移动20px */
    left: 20px; /* 向右移动20px */
}
```

- `absolute`：元素相对于最近的非static定位的祖先元素（而不是它在HTML中的父元素）进行定位。如果没有这样的元素，那么它将相对于`<html>`元素进行定位。

```css
div {
    position: absolute;
    top: 20px;
    left: 20px;
}
```

- `fixed`：元素相对于浏览器窗口进行定位，即使页面滚动，它也会停留在相同的位置。

```css
div {
    position: fixed;
    top: 20px;
    left: 20px;
}
```

- `sticky`：元素根据用户的滚动位置进行定位。它的行为就像`position:relative`与`position:fixed`的混合。

```css
div {
    position: sticky;
    top: 0;
}
```

## 弹性盒子

Flexbox 是 CSS 弹性盒子布局模块（[Flexible Box Layout](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Flexible_Box_Layout) Module）的缩写，它被专门设计出来用于创建横向或是纵向的一维页面布局。要使用 flexbox，你只需要在想要进行 flex 布局的父元素上应用 `display: flex` ，所有直接子元素都将会按照 flex 进行布局。我们来看一个例子。

### 设置 `display: flex`

```css
.wrapper {
  display: flex;
}
```

```html
<div class="wrapper">
  <div class="box1">WTF-HTML</div>
  <div class="box2">WTF-CSS</div>
  <div class="box3">WTF-Solidity</div>
</div>
```

![](./img/9-1.png)

### 设置 flex 属性

除了上述可以被应用到 flex 容器的属性以外，还有很多属性可以被应用到 flex 项 (flex items) 上面。这些属性可以改变 flex 项在 flex 布局中占用宽/高的方式，允许它们通过伸缩来适应可用空间。

```css
.wrapper {
  display: flex;
}

.wrapper > div {
  flex: 1;
}
```

```html
<div class="wrapper">
  <div class="box1">WTF-HTML</div>
  <div class="box2">WTF-CSS</div>
  <div class="box3">WTF-Solidity</div>
</div>
```

![](./img/9-2.png)

深入了解 Flex 布局，请看 [Flex 布局](https://github.com/WTFAcademy/WTF-CSS/blob/main/10_Flex/readme.md) 章节。


## Grid 布局

Flexbox 用于设计横向或纵向的布局，而 Grid 布局则被设计用于同时在两个维度上把元素按行和列排列整齐。

### 设置 `display: grid`

同 flex 一样，你可以通过指定 display 的值来转到 grid 布局：`display: grid`。下面的例子使用了与 flex 例子类似的 HTML 标记，描述了一个容器和若干子元素。除了使用 `display: grid`，我们还分别使用 [`grid-template-rows`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/grid-template-rows) 和 [`grid-template-columns`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/grid-template-columns) 两个属性定义了一些行和列的轨道。定义了三个 `1fr` 的列，还有两个 `100px` 的行之后，无需再在子元素上指定任何规则，它们自动地排列到了我们创建的格子当中。

```css
.wrapper {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-template-rows: 100px 100px;
  grid-gap: 10px;
}
```

```html
<div class="wrapper">
  <div class="box1">WTF-HTML</div>
  <div class="box2">WTF-CSS</div>
  <div class="box3">WTF-Solidity</div>
  <div class="box4">WTF-Ethers</div>
  <div class="box5">WTF-gm</div>
  <div class="box6">WTF-ClosedSource</div>
</div>
```

![](./img/9-3.png)

### 在网格内放置元素

一旦你拥有了一个 grid，你也可以显式地将元素摆放在里面，而不是依赖于浏览器进行自动排列。在下面的第二个例子里，我们定义了一个和上面一样的 grid，但是这一次我们只有三个子元素。我们利用 [`grid-column`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/grid-column) 和 [`grid-row`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/grid-row) 两个属性来指定每一个子元素应该从哪一行/列开始，并在哪一行/列结束。这就能够让子元素在多个行/列上展开。

```css
.wrapper {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-template-rows: 100px 100px;
  grid-gap: 10px;
}

.box1 {
  grid-column: 2 / 4;
  grid-row: 1;
}

.box2 {
  grid-column: 1;
  grid-row: 1 / 3;
}

.box3 {
  grid-row: 2;
  grid-column: 3;
}
```

```html
<div class="wrapper">
  <div class="box1">WTF-HTML</div>
  <div class="box2">WTF-CSS</div>
  <div class="box3">WTF-Solidity</div>
</div>
```

![](./img/9-4.png)

为了找到更多关于 Flexbox 的信息，请看 [Flex 布局](https://github.com/WTFAcademy/WTF-CSS/blob/main/10_Flex/readme.md) 章节。

深入了解 Grid 布局，请看 [Grid 布局](https://github.com/WTFAcademy/WTF-CSS/blob/main/11_Grid/readme.md) 章节。


## 多列布局

多列布局模组给了我们 一种把内容按列排序的方式，就像文本在报纸上排列那样。由于在 web 内容里让你的用户在一个列上通过上下滚动来阅读两篇相关的文本是一种非常低效的方式，那么把内容排列成多列可能是一种有用的技术。

要把一个块转变成多列容器 (multicol container)，我们可以使用 [`column-count`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/column-count) 属性来告诉浏览器我们需要多少列，也可以使用 [`column-width`](https://developer.mozilla.org/en-US/docs/Web/CSS/column-width) 来告诉浏览器以至少某个宽度的尽可能多的列来填充容器。

在下面这个例子中，我们从一个 class 为 `container` 的 `<div>` 容器元素里边的一块 HTML 开始。

```html
<div class="container">
  <h1>Multi-column layout</h1>

  <p>Paragraph 1.</p>
  <p>Paragraph 2.</p>
</div>
```

我们指定了该容器的 `column-width` 为 200 像素，这让浏览器创建了尽可能多的 200 像素的列来填充这一容器。接着他们共同使用剩余的空间来伸展自己的宽度。

```css
.container {
  column-width: 200px;
}
```

![](./img/9-6.png)

## 总结

这一讲我们介绍了所有布局技术的简要概述，要深入了解请阅读更多关于每一项技术的信息！
