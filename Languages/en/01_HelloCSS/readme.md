# WTF CSS minimalist tutorial: 1. Hello CSS

WTF CSS tutorial to help newcomers get started with CSS quickly.

**Twitter**: [@WTFAcademy_](https://twitter.com/WTFAcademy_) | [@0xAA_Science](https://twitter.com/0xAA_Science)

**WTF Academy Community:** [Official website wtf.academy](https://wtf.academy) | [WTF Solidity Tutorial](https://github.com/AmazingAng/WTFSolidity) | [discord](https: //discord.gg/5akcruXrsk) | [WeChat group application](https://docs.google.com/forms/d/e/1FAIpQLSe4KGT8Sh6sJ7hedQRuIYirOoZK_85miz3dw7vA1-YjodgJ-A/viewform?usp=sf_link)

All codes and tutorials are open source on github: [github.com/WTFAcademy/WTF-CSS](https://github.com/WTFAcademy/WTF-CSS)

---

In this lecture, we introduce the basics of CSS and write the first HTML+CSS program: Hello CSS.

## What is CSS?

CSS (**C**ascading **S**tyle **S**sheet, Cascading Style Sheet) is the code that adds styles to web pages. Simply put, HTML is responsible for the structure of the document, while CSS is responsible for the presentation style of the document. By using CSS, we can control the layout of the page, adjust the color and size of elements, add background images and borders, create animation effects, and more.

The original intention of CSS was to solve the problem of separation of content and presentation. In early web design, HTML tags were used to define the structure and style of the document, which mixed the content and style of the document, resulting in redundant code and difficulty in maintenance. The emergence of CSS allows us to separate structure (HTML) and style (CSS), so that the content and presentation of web pages can be separated, which greatly improves the maintainability and readability of web pages.

## CSS ruleset

In CSS, style rules consist of two main parts: selectors, and a declaration block within a pair of curly braces.

```css
selector {
     property: value;
}
```

- **Selector**: used to specify which elements CSS rules apply to.
- **Declaration block**: A set of CSS declarations enclosed in curly braces ({}). Each declaration consists of a property and a value. The property and value are separated by a colon (:). Each declaration A semicolon (;) is required at the end.

For example:

```css
h1 {
     color: blue;
     font-size: 24px;
}
```

This CSS rule will be applied to all h1 elements in the HTML document, making the text color of these h1 elements blue and the font size 24 pixels.

## Hello CSS

Next, we will write our first program that contains CSS: Hello CSS, showing how to use CSS in HTML documents. If you are not familiar with HTML, you can read [WTF HTML Minimalist Tutorial](https://github.com/WTFAcademy/WTF-HTML).

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
         <p>Hello <strong>CSS! </strong></p>
     </body>
</html>
```

![Hello CSS](./img/1-2.png)

In Hello CSS, we use internal style sheets to embed CSS into HTML (usually in the `<head>` element):

```html
<style type="text/css">
     ...
</style>
```

We set the font color in all paragraph elements `<p>` to blue (`color`) and center them (`text-align`).

```css
p {
     color: blue;
     text-align: center;
}
```

Moreover, we set the font color in the bold element `<strong>` in the paragraph element `<p>` to green (`color`), the background color to light blue (`background-color`), and set Padding is set to 10 pixels (`padding`).

```css
p strong {
     color: green;
     background-color: #d0f0f6;
     padding: 10px;
}
```

## Summary

In this lecture we introduced what CSS is and wrote the first program containing CSS: Hello CSS. You can read [MDN CSS Basics](https://developer.mozilla.org/zh-CN/docs/Learn/CSS) to learn more details about CSS.
