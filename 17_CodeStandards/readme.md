# WTF CSS极简教程: 17. 代码规范

WTF CSS教程，总结/搬运自[MDN CSS教程](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Building_blocks/Organizing)，帮助新人快速入门CSS。

**推特**：[@WTFAcademy_](https://twitter.com/WTFAcademy_)  ｜ [@0xAA_Science](https://twitter.com/0xAA_Science) 

**WTF Academy社群：** [官网 wtf.academy](https://wtf.academy) | [WTF Solidity教程](https://github.com/AmazingAng/WTFSolidity) | [discord](https://discord.gg/5akcruXrsk) | [微信群申请](https://docs.google.com/forms/d/e/1FAIpQLSe4KGT8Sh6sJ7hedQRuIYirOoZK_85miz3dw7vA1-YjodgJ-A/viewform?usp=sf_link)

所有代码和教程开源在github: [github.com/WTFAcademy/WTF-CSS](https://github.com/WTFAcademy/WTF-CSS)

---

这一讲，我们介绍如何在编写时保持代码规范，从而使一个更大的样式表和大项目具有更强的可读性和可维护性。

## 保持统一

如果你开始为项目指定规则或者独自工作，那么最重要的事情是让各方面都保持统一。统一在所有的地方都会起到实际作用，例如对类使用相同的命名常规，选择一种描述颜色的方式，或者维护一个统一的格式化方式（例如你是使用Tab还是空格来缩进代码？如果是空格，用多少个？）

一直遵守一系列规则，你会在编写 CSS 的时候省去不少精神上的预负担，因为一些决定已经定型了。

## 将CSS格式化成可读的形式

你可以看到很多 CSS 格式化的方式，一些开发者将所有的规则放在一行里面，像是这样：

```css
.box { background-color: #567895; }
h2 { background-color: black; color: white; }
```

还有的开发者更喜欢将所有的东西放在新的一行：

```css
.box {
  background-color: #567895;
}

h2 {
  background-color: black;
  color: white;
}
```

CSS 不会管你使用哪种方式来进行格式化，我们的看法是，将每个属性值对放在新的一行会更好读。

## 为你的CSS加注释

在你的 CSS 里加入注释，不仅可以帮任何未来的开发者处理你的CSS文件，也可以在你离开项目一段时间后，帮你在回来时更轻松地重新上手。

```css
/* 这是一条 CSS 注释，
它可以分成好几行。*/
```

在你的样式表里面的逻辑段落之间，加入一块注释，是个好技巧。在你快速掠过的时候，这些注释可以帮你快速定位不同的段落，甚至给了你搜索或者跳转到那段 CSS 的关键词。如果你使用了一个不存在于代码里面的字符串，你可以从段落到段落间跳转，只需要搜索一下，下面我们用的是`||`。

```css
/* || General styles */

...

/* || Typography */

...

/* || Header and Main Navigation */

...

```

你不必在你的 CSS 中给每个东西都加上注释，因为它们很多都是自解释的。你应该加上注释的是那些你因为某些原因做的特殊决定。

为了对旧浏览器保持兼容，你用某种特殊方法使用了一种 CSS 属性，示例：

```css
.box {
  background-color: red; /* fallback for older browsers that don't support gradients */
  background-image: linear-gradient(to right, #ff0000, #aa0000);
}
```

## 在你的样式表里面加入逻辑段落

在样式表里面先给一般的东西加上样式是个好想法。这也就是除了你想特定对某个元素做点什么以外，所有将会广泛生效的样式。典型地，你可以为以下的元素设定规则：

- `body`
- `p`
- `h1`,`h2`,`h3`,`h4`,`h5`
- `ul`和`ol`
- `table`属性
- `a`

在这段样式表里面，我们提供了用于站点类型的默认样式，为数据表格、列表等设立了一份默认的样式。

```css
/* || GENERAL STYLES */

body { ... }

h1, h2, h3, h4 { ... }

ul { ... }

blockquote { ... }
```

在这段之后，我们可以定义一些实用类，例如一个用来移除默认列表样式的类，我们打算将其展示为灵活样式或者其他样式。如果你知道你想要在许多不同的元素上应用的东西，那么你可以把它们加到这里。

```css
/* || UTILITIES */

.nobullets {
  list-style: none;
  margin: 0;
  padding: 0;
}

...

```

然后我们可以加上在整个站点都会用到的所有东西，这可能是像基础页面布局、抬头或者导航栏样式之类的东西。

```css
/* || SITEWIDE */

.main-nav { ... }

.logo { ... }

```

最后我们可以在 CSS 里面加上特指的东西，将它们分成上下文、页面甚至它们使用的组件。

```css
/* || STORE PAGES */

.product-listing { ... }

.product-box { ... }

```

通过使用这种方式排布代码，我们至少能大致了解，我们能在样式表的哪个部分寻找想要更改的东西。

## 避免太特定的选择器

如果你创建了很特定的选择器，你经常会发现，你需要在你的 CSS 中复用一块代码，以将同样的规则应用到其他元素上。例如，你也许会有像是下面的选择器那样的代码，它在带有`main`类的`<article>`里面的带有`box`类的`<p>`上应用了规则。

```css
article.main p.box {
  border: 1px solid #ccc;
}
```

如果你之后想要在`main`外的什么地方上应用相同的规则，或者在`<p>`外的其他地方，你可能必须在这些规则中加入另一个选择器，或者直接新建个规则。或者，你也可以建立一个名为`box`的类，在任何地方应用。

```css
.box {
  border: 1px solid #ccc;
}
```

将东西设置的更为特定，有时也有意义，但是这一般与其说是通常实践，倒不如说是例外。


## 总结

这一讲我们介绍了在编写时如何保持代码规范，并给出了相应的示例。对一个前端开发人员而言，代码编写规范是一个十分重要的素养。
