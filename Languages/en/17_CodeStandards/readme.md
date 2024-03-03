# WTF CSS minimalist tutorial: 17. Code specifications

WTF CSS tutorial, summarized/transported from [MDN CSS tutorial](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Building_blocks/Organizing), to help newcomers get started with CSS quickly.

**Twitter**: [@WTFAcademy_](https://twitter.com/WTFAcademy_) | [@0xAA_Science](https://twitter.com/0xAA_Science)

**WTF Academy Community:** [Official website wtf.academy](https://wtf.academy) | [WTF Solidity Tutorial](https://github.com/AmazingAng/WTFSolidity) | [discord](https: //discord.gg/5akcruXrsk) | [WeChat group application](https://docs.google.com/forms/d/e/1FAIpQLSe4KGT8Sh6sJ7hedQRuIYirOoZK_85miz3dw7vA1-YjodgJ-A/viewform?usp=sf_link)

All codes and tutorials are open source on github: [github.com/WTFAcademy/WTF-CSS](https://github.com/WTFAcademy/WTF-CSS)

---

In this lecture, we introduce how to maintain code standards when writing, so that a larger style sheet and large project will be more readable and maintainable.

## Keep it unified

If you start assigning rules to a project or working alone, the most important thing is to keep everything aligned. Uniformity comes into play all over the place, such as using the same naming convention for classes, choosing a way to describe colors, or maintaining a consistent formatting approach (e.g. do you use tabs or spaces to indent code? If It’s a space, how many should you use?)

By always following a set of rules, you'll save yourself a lot of mental pre-emption when writing CSS because some of the decisions have already been made.

## Format CSS into readable form

You can see a lot of CSS formatting, and some developers put all the rules in one line, like this:

```css
.box { background-color: #567895; }
h2 { background-color: black; color: white; }
```

Other developers prefer to put everything on a new line:

```css
.box {
   background-color: #567895;
}

h2 {
   background-color: black;
   color: white;
}
```

CSS doesn’t care which way you format it, our opinion is that it’s more readable to put each property-value pair on a new line.

## Comment out your CSS

Adding comments to your CSS will not only help any future developers work on your CSS file, but it will also make it easier for you to start over again if you leave the project for a while.

```css
/* This is a CSS comment,
It can be divided into several lines. */
```

It's a good technique to add comments between logical paragraphs in your stylesheet. As you browse quickly, these annotations can help you quickly locate different paragraphs, and even give you keywords to search or jump to that section of CSS. If you use a string that doesn't exist in the code, you can jump from paragraph to paragraph by searching for it. Here we use `||`.

```css
/* || General styles */

...

/* || Typography */

...

/* || Header and Main Navigation */

...

```

You don’t have to comment out everything in your CSS because a lot of it is self-explanatory. What you should annotate are those particular decisions you made for whatever reason.

To maintain compatibility with older browsers, you use a CSS property in a special way, for example:

```css
.box {
   background-color: red; /* fallback for older browsers that don't support gradients */
   background-image: linear-gradient(to right, #ff0000, #aa0000);
}
```

## Add logical paragraphs to your stylesheet

It's a good idea to style the general stuff first in your style sheet. This is all styles that will apply broadly unless you want to do something specific to an element. Typically, you would set rules for the following elements:

- `body`
- `p`
- `h1`,`h2`,`h3`,`h4`,`h5`
- `ul` and `ol`
- `table` attribute
- `a`

In this style sheet, we provide default styles for site types and set up a default style for data tables, lists, etc.

```css
/* || GENERAL STYLES */

body { ... }

h1, h2, h3, h4 { ... }

ul { ... }

blockquote { ... }
```

After this paragraph, we can define some utility classes, such as a class to remove the default list style, which we intend to display as a flexible style or other styles. If you know something you want to apply on a number of different elements, then you can add them here.

```css
/* || UTILITIES */

.nobullets {
   list-style: none;
   margin: 0;
   padding: 0;
}

...

```

Then we can add in all the stuff that will be used throughout the site, which might be things like a base page layout, a header, or a navigation bar style.

```css
/* || SITEWIDE */

.main-nav { ... }

.logo { ... }

```

Finally we can add specific things to CSS, splitting them into contexts, pages and even the components they use.

```css
/* || STORE PAGES */

.product-listing { ... }

.product-box { ... }

```

By laying out the code this way, we can at least get a rough idea of ​​where in the style sheet we can look for what we want to change.

## Avoid selectors that are too specific

If you create a very specific selector, you'll often find that you need to reuse a piece of code in your CSS to apply the same rules to other elements. For example, you might have code like the following selector, which applies a rule to a `<p>` with a `box` class inside a `<article>` with a `main` class.

```css
article.main p.box {
   border: 1px solid #ccc;
}
```

If you later want to apply the same rules somewhere outside `main`, or somewhere else outside `<p>`, you may have to add another selector to these rules, or create a new rule directly. Alternatively, you can create a class called `box` and apply it anywhere.

```css
.box {
   border: 1px solid #ccc;
}
```

Setting things up to be more specific sometimes makes sense, but this is generally more the exception than common practice.


## Summary

In this lecture, we introduced how to maintain code specifications when writing and gave corresponding examples. For a front-end developer, code writing standards are a very important quality.
