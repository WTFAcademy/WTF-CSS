# WTF CSS minimalist tutorial: 2. CSS syntax

WTF CSS tutorial to help newcomers get started with CSS quickly.

**Twitter**: [@WTFAcademy_](https://twitter.com/WTFAcademy_) | [@0xAA_Science](https://twitter.com/0xAA_Science)

**WTF Academy Community:** [Official website wtf.academy](https://wtf.academy) | [WTF Solidity Tutorial](https://github.com/AmazingAng/WTFSolidity) | [discord](https: //discord.gg/5akcruXrsk) | [WeChat group application](https://docs.google.com/forms/d/e/1FAIpQLSe4KGT8Sh6sJ7hedQRuIYirOoZK_85miz3dw7vA1-YjodgJ-A/viewform?usp=sf_link)

All codes and tutorials are open source on github: [github.com/WTFAcademy/WTF-CSS](https://github.com/WTFAcademy/WTF-CSS)

---

In this lecture, we introduce CSS syntax and three ways to apply CSS in documents.

## grammar

CSS rule sets consist of selectors and declaration blocks, as shown in the following figure:

![](./img/2-1.png) ![](./img/2-2.png)

The selector points to the element you want to style.

The declaration block starts with `{` and ends with `}`.

A declaration block contains one or more declarations, separated by `;`.

Each declaration contains a CSS property name and a value, separated by `:`.

The code above means: the text color of all `<h1>` elements is red, and the text size is 50 pixels.

## Introduction method

We have three ways of using CSS in HTML:

1. External style
2. Internal style
3. Inline styles

### 1. External style

External styles are the most commonly used CSS method. You can write CSS code in an external `.css` file:

![](./img/2-3.png)

In order to connect `styles.css` and `index.html`, you need to introduce this style file through the `<link>` tag in the `<head>` of the HTML document.

```html
<link rel="stylesheet" href="styles.css" />
```

![](./img/2-4.png)

In the `<link>` tag, we use the attribute `rel` to let the browser know that a CSS document exists, and use the attribute `href` to specify the location of the CSS file.

### 2. Internal style

You can also write CSS code directly in the `<style>` tag of the HTML file. This style is called an internal style.

![](./img/2-5.png)

### 3. Inline styles

If you only want to set the style for an element alone, you can use the `style` attribute in the tag of this element. Such styles are called inline styles.

![](./img/2-6.png)

The above three methods of introducing CSS can achieve the same effect, making the text color of the `<h1>` element in the page red and the text size 50 pixels. As shown below.
![](./img/2-7.png)

We most commonly use external styles, which can separate HTML from CSS and make it more concise.

## Stacking order

Conflicts occur when multiple styles are applied to the same element. CSS cascading rules determine how these conflicts are resolved. Specifically, the factors that determine the priority of style application are:

1. Source: Author style sheet (style written by the developer) > User style sheet (style set by browser user) > Browser default style
2. Selector priority: Inline style > ID selector > Class/pseudo-class/attribute selector > Element/pseudo-element selector
3. Code order: In the case of the same priority, the styles that appear later will override the styles that appear first.
4. `!important` rules: The style with `!important` added has the highest priority, unless other styles also add `!important`, in which case the above three rules are still followed.

Let's look at an example. In this example, we set the text color of the `<h1>` element to blue, green, and red in the external, internal, and inline styles respectively. The effect produced at this time is as shown in the figure below.

![](./img/2-8.png)

![](./img/2-9.png)

As you can see, the text color is red because the inline style has the highest priority.

![](./img/2-10.png)

If we remove the inline styles, the text will turn green (internal styles) because the internal styles are declared further back.

![](./img/2-11.png)

If we adjust the external style declaration to the internal style, the text turns blue (external style).

![](./img/2-12.png)

## Summary

In this lecture, we know how to write CSS styles and the different ways to introduce them. Inline styles have the highest priority and will override external and internal styles as well as browser default styles.
