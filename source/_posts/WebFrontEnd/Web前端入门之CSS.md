---
title: Web前端入门之CSS
date: 2021-04-19 23:51:35
categories: Web前端
tags: CSS
---

{% folding 参考资料 %}

{% link CSS参考手册, http://css.doyoe.com/, https://cdn.jsdelivr.net/gh/halo-blog/cdn-blog-img-a@main/img/%E7%BD%91%E7%AB%99.svg %}
{% link w3cschool, https://www.w3school.com.cn/, https://cdn.jsdelivr.net/gh/halo-blog/cdn-blog-img-a@main/img/%E7%BD%91%E7%AB%99.svg %}
{% link 黑马程序员Web前端入门教程, https://www.bilibili.com/video/BV1pE411q7FU, https://cdn.jsdelivr.net/gh/halo-blog/cdn-blog-img-a@main/img/%E7%BD%91%E7%AB%99.svg %}

{% endfolding %}

## CSS 简介

1. CSS 是层叠样式表 ( Cascading Style Sheets ) 的简称。有时我们也会称之为 CSS 样式表或级联样式表。
2. CSS 是也是一种标记语言。
3. CSS 主要用于设置 HTML 页面中的文本内容（字体、大小、对齐方式等）、图片的外形（宽高、边框样式、边距等）以及版面的布局和外观显示样式。
4. CSS 让我们的网页更加丰富多彩，布局更加灵活自如。简单理解：CSS 可以美化 HTML , 让 HTML 更漂亮， 让页面布局更简单。
5. CSS 最大价值: 由 HTML 专注去做结构呈现，样式交给 CSS，即 结构 ( HTML ) 与样式( CSS ) 相分离。

### CSS 语法规范

1. 使用 HTML 时，需要遵从一定的规范，CSS 也是如此。要想熟练地使用 CSS 对网页进行修饰，首先需要了解CSS 样式规
2.  CSS 规则由两个主要的部分构成：选择器以及一条或多条声明。

```css
h1{
color:red;
font-size:25px; 
}
```

1. 选择器是用于指定 CSS 样式的 HTML 标签，花括号内是对该对象设置的具体样式
2. 属性和属性值以“键值对”的形式出现
3. 属性是对指定的对象设置的样式属性，例如字体大小、文本颜色等
4. 属性和属性值之间用英文`:`分开
5. 多个“键值对”之间用英文`;`进行区分


所有的样式，都包含在 `<style>` 标签内，表示是样式表。`<style>` 一般写到 `</head>` 上方，例如：

```html
<head>
  <style>
    h4 {
      color: blue;
      font-size: 100px;
    }
  </style>
</head>
```

### CSS代码风格

样式空格风格

```css
/*选择器（标签）和大括号中间保留空格*/
h3 {
  /*属性值前面，冒号后面，保留一个空格*/
  color: pink;    
}
```

样式格式书写

```css
/*紧凑格式*/
h3 { color: deeppink;font-size: 20px;}

/*展开格式(推荐,更直观)*/
h3 {
  color: pink;
  font-size: 20px;    
}
```


样式大小写风格

```css
/*小写格式(推荐)*/
h3 {
  color: pink;
}

/*大写格式*/
H3 {
  COLOR: PINK;   
}
```


## CSS选择器

### 选择器的作用

选择器(选择符)就是根据不同需求把不同的标签选出来这就是选择器的作用。简单来说，就是选择标签用的。

选择器分为基础选择器和复合选择器两个大类。

### CSS 基础选择器

基础选择器又包括：标签选择器、类选择器、id 选择器和通配符选择器

#### 标签选择器

标签选择器（元素选择器）是指用 HTML 标签名称作为选择器，按标签名称分类，为页面中某一类标签指定统一的 CSS 样式。

语法：

```css
标签选择器{
  属性：属性值
  ...
}
```

优点：能快速为页面中同类型的标签统一设置样式。
缺点：不能设计差异化样式,只能选择全部的当前标签。


#### 类选择器

如果想要差异化选择不同的标签，单独选一个或者某几个标签，可以使用类选择器。

结构需要用class属性来调用class类的意思，`<div class="类名"> 变红色 </div>`

语法：

```css
.类名{
  属性：属性值
  ...
}
```

1. 如果想要差异化选择不同的标签，单独选一个或者某几个标签，可以使用类选择器。
2. 类选择器在 HTML 中以 class 属性表示，在 CSS 中，类选择器以一个点“.”号显示。
3. 类选择器使用“.”（英文点号）进行标识，后面紧跟类名（自定义，我们自己命名的）。
4. 可以理解为给这个标签起了一个名字，来表示。
5. 长名称或词组可以使用中横线来为选择器命名。
6. 不要使用纯数字、中文等命名，尽量使用英文字母来表示。
7. 命名要有意义，尽量使别人一眼就知道这个类名的目的。
8. 命名规范：见资料（[Web 前端开发规范手册.doc](https://halo-blog-img.oss-cn-hangzhou.aliyuncs.com/%E8%B5%84%E6%96%99/Web%E5%89%8D%E7%AB%AF%E5%BC%80%E5%8F%91%E8%A7%84%E8%8C%83%E6%89%8B%E5%86%8C.doc)）


#### 多类名选择器

我们可以给一个标签指定多个类名，从而达到更多的选择目的。 这些类名都可以选出这个标签。简单理解就是一个标签有多个名字。

多类名的具体使用，类名之间用空格隔开：

```css
<div class="red font20">嘤嘤嘤</div>
```

注意：
1. 在标签class 属性中写多个类名
2. 多个类名中间必须用空格分开
3. 这个标签就可以分别具有这些类名的样式

多类名开发中使用场景：
1. 可以把一些标签元素相同的样式(共同的部分)放到一个类里面。
2. 这些标签都可以调用这个公共的类然后再调用自己独有的类。
3. 从而节省CSS代码，统一修改也非常方便。


#### ID 选择器

id 选择器可以为标有特定 id 的 HTML 元素指定特定的样式。

HTML 元素以 id 属性来设置 id 选择器，CSS 中 id 选择器以 "#" 来定义。语法：

```csss
#id名 {
  属性1: 属性值1;  
  ...
} 
```

注意：id 属性只能在每个 HTML 文档中出现一次

id 选择器和类选择器的区别：

1. 类选择器（class）好比人的名字，一个人可以有多个名字，同时一个名字也可以被多个人使用。
2. id 选择器好比人的身份证号码，全中国是唯一的，不得重复。
3. id 选择器和类选择器最大的不同在于使用次数上。
4. 类选择器在修改样式中用的最多，id 选择器一般用于页面唯一性的元素上，经常和 JavaScript 搭配使用。


#### 通配符选择器

在 CSS 中，通配符选择器使用 "*" 定义，它表示选取页面中所有元素（标签）。语法：

```css
* {
  属性1: 属性值1;  
  ...
}
```

通配符选择器不需要调用，自动就给所有的元素使用样式，特殊情况才使用(如清除所有的元素标签的内外边距)

```css
* {
  margin: 0;
  padding: 0;
} 
```

#### 基础选择器总结

| 基础选择器   | 作用                    | 特点                                     | 使用情况             | 用法                 |
| ------------ | ----------------------- | ---------------------------------------- | -------------------- | -------------------- |
| 标签选择器   | 可以选出所有相同的标签  | 不能差异化选择                           | 较多                 | `p {color: red;}`    |
| 类选择器     | 可以选出1个或者多个标签 | 可以根据需求选择                         | 非常多               | `.nav {color: red;}` |
| id选择器     | 一次只能选择1个标签     | 相同id属性只能在每一个HTML文档中出现一次 | 一般和JavaScript搭配 | `#nav {color: red;}` |
| 通配符选择器 | 选择所有的标签          | 选择所有                                 | 特殊情况下使用       | `* {color: red;}`    |

### 关系选择器

简单的选择器包括标签选择器、类选择器、ID 选择器和通配符选择器。如果把两个选择器组合在一起，就形成了一个复杂关系的选择器。在 HTML5 文档结构中，通过关系选择器可以精确匹配结构中特定关系元素。

#### 包含选择器

包含选择器通过空格连接两个选择器，前面选择器表示包含的祖先元素，后面选择器表示被包含的后代元素。

+ 优点：可以匹配特定的结构内指定对象，用于缩小匹配范围。
+ 缺点： 匹配范围较大，影响的层级不受限制。

案例：

```html
<!-- 网页模板 -->
<header>
    <h1> 网页标题 </h1>
</header>
<footer>
    <h1> 页脚标题 </h1>
<footer>
```

实现以下目标：
+ 定义网页标题的字体大小为 18px
+ 定义页脚标题的字体大小为 12px

```css
header h1{font-size:18px;}
footer h1{font-size:12px;}
```


#### 子选择器

子选择器使用尖括号（`>`）连接两个选择器，前面选择器表示要匹配的父元素，后面选择器表示被包含的匹配子对象。

+ 优点：比包含选择器匹配的范围更小，从层级结构上来看匹配目标更明确。
+ 缺点：与包含选择器相比，匹配范围优先，用户需要熟悉文档结构。

<iframe width="100%" height="300" src="//jsrun.net/9e3Kp/embedded/html,css,result/dark" allowfullscreen="allowfullscreen" frameborder="0"></iframe>

#### 相邻选择器

相邻选择器使用加号（`+`）连接两个选择器，前面选择器匹配特定元素，后面选择器根据结构关系，指定同级、相邻的匹配元素。

+ 优点：在结构中能够准确找到同级、相邻的元素。
+ 缺点：需要熟悉文档结构。

#### 兄弟选择器

兄弟选择器使用波浪线（`~`）连接两个选择器，前面

<iframe height="400" style="width: 100%;" scrolling="no" title="Swiper.js实现响应式博客卡片滑块轮播" src="https://animpen.com/embed/oMbZtH?tab=rlt,html" frameborder="no"  allowtransparency="true" allowfullscreen="true"></iframe>

## CSS字体属性

CSS Fonts (字体)属性用于定义字体系列、大小、粗细、和文字样式(如斜体)。

### 字体系列

CSS使用`font-family`属性定义文本的字体系列。

```css
div { 
  font- family: Arial, "Microsoft Yahei"; 
}
```

+ 各种字体之间必须使用英文状态下的逗号隔开
+ 般情况下，如果有空格隔开的多个单词组成的字体加引号。
+ 尽量使用系统默认自带字体，保证在任何用户的浏览器中都能正确显示

### 字体大小

CSS 使用 `font-size` 属性定义字体大小。 语法：

```css
p {  
  font-size: 20px; 
}
```
1. px（像素）大小是我们网页的最常用的单位
2. 谷歌浏览器默认的文字大小为16px
3. 不同浏览器可能默认显示的字号大小不一致，我们尽量给一个明确值大小，不要默认大小
4. 可以给 body 指定整个页面文字的大小

### 字体粗细

CSS 使用 `font-weight` 属性设置文本字体的粗细。语法：

```css
p {  
  font-weight: bold; 
}
```

| 属性值  | 描述                                                     |
| ------- | -------------------------------------------------------- |
| normal  | 默认值（不加粗）                                         |
| bold    | 定义加粗                                                 |
| 100-900 | 400等同于normal，700等同于bold，注意这个数字后面不加单位 |

### 字体样式

CSS 使用 `font-style` 属性设置文本的风格。语法：

```css
p {  
  font-style: normal;
}
```

| 属性值 | 作用                                                     |
| ------ | -------------------------------------------------------- |
| normal | 默认值，浏览器会显示标准的字体样式`font- style: normal;` |
| italic | 浏览器会显示斜体的字体样式。                             |

### 字体的综合写法

字体属性可以把以上文字样式综合来写, 这样可以更节约代码：

```css
body { 
  font: font-style  font-weight  font-size/line-height  font-family;
}
```

使用 font 属性时，必须按上面语法格式中的顺序书写，<font color="#FF666">不能更换顺序</font>，并且各个属性间以空格隔开 不需要设置的属性可以省略（取默认值），但必须保留 `font-size` 和 `font-family` 属性，否则 font 属性将不起作用。

### 字体总结

| 属性          | 表示     | 注意点                                                       |
| ------------- | -------- | ------------------------------------------------------------ |
| `font-size`   | 字号     | 通常用的单位是 px 像素，一定要跟上单位                       |
| `font-family` | 字体     | 实际工作中按照团队约定来写字体                               |
| `font-weight` | 字体粗细 | 记住加粗是700或者bold，不加粗是normal或者400记住数字不要跟单位 |
| `font-style`  | 字体样式 | 记住倾斜是italic，不倾斜是normal。工作中我们最常用normal     |
| `font`        | 字体连写 | 字体连写是有顺序的不能随意换位置；其中字号和字体必须同时出现 |


## CSS文本属性

CSS Text (文本)属性可定义文本的外观，比如文本的颜色、对齐文本、装饰文本、文本缩进、行间距等。

### 文本颜色

color 属性用于定义文本的颜色。语法：

```css
div { 
  color: red;
}
```

| 表示         | 属性值                        |
| ------------ | ----------------------------- |
| 预定义的颜色 | red、green、blue等            |
| 十六进制(常用)     | #FF0000、#FF6600等   |
| RGB代码      | rgb(255,0,0)、rgb(100%,0%,0%) |


### 文本对齐

`text-align` 属性用于设置元素内文本内容的<font color="#FF666">水平</font>对齐方式。语法：

```css
div { 
  text-align: center;
}
```

| 属性值 | 解释             |
| ------ | ---------------- |
| left   | 左对齐（默认值） |
| right  | 右对齐           |
| center | 居中对齐         |


### 修饰文本

`text-decoration`属性规定添加到文本的修饰。可以给文本添加下划线、删除线、上划线等。

```css
div { 
  text-decoration：underline；
}
```

| 属性值       | 描述             |
| ------------ | ---------------- |
| none         | 默认，没有装饰线 |
| underline    | 下划线           |
| overline     | 上划线           |
| line-through | 删除线           |

### 文本缩进

`text-indent`属性用来指定文本的第一行的缩进，通常是将段落的首行缩进。语法：

```css
div { 
  text-indent：20px；
}
div { 
  text-indent：2em;
}
```

>   `em` 是一个相对单位，就是当前元素（font-size) 1 个文字的大小，如果当前元素没有设置大小，则会按照父元素的 1 个文字大小。

### 行间距

`line-height` 属性用于设置行间的距离（行高）。可以控制文字行与行之间的距离。语法：

```css
p { 
  line-height: 26px;
}
```

行高的文本分为：上间距、文本高度和下间距，这三者大小之和 = 行间距

### 文本属性总结

| 属性            | 表示     | 注意点               |
| --------------- | -------- | -------------------- |
| color           | 文本颜色 | 常用十六进制表示颜色 |
| text-align      | 文本对齐 | 设定文字水平对齐方式 |
| text-indent     | 文本缩进 | 可以设置首行缩进     |
| text-decoration | 文本修饰 | 添加或去除下划线     |
| line-height     | 行高     | 控制行间距           |


## CSS样式表

按照 CSS 样式书写的位置（或者引入的方式），CSS 样式表可以分为三大类：行内样式表（行内式）、内部样式表（嵌入式）、外部样式表（链接式）。

### 行内样式表（行内式）

行内样式表（内联样式表）是在元素标签内部的 `style` 属性中设定 CSS 样式。适合于修改简单样式。语法：

```css
<div style="color: red; font-size: 12px;">一拳一个嘤嘤怪</div>
```

1. style 其实就是标签的属性，在双引号中间，写法要符合 CSS 规范
2. 可以控制当前的标签设置样式
3. 由于书写繁琐，并且没有体现出结构与样式相分离的思想，所以不推荐大量使用，只有对当前元素添加简单样式的时候，可以考虑使用
4. 使用行内样式表设定 CSS，通常也被称为行内式引入

### 内部样式表（嵌入式）

内部样式表（内嵌样式表）是写到html页面内部. 是将所有的 CSS 代码抽取出来，单独放到一个 `<style>` 标签中，语法：

```css
<style>
  div {
    color: red;
    font-size: 12px;
  }
</style>
```

1. `<style>` 标签理论上可以放在 HTML 文档的任何地方，但一般会放在文档的`<head>`标签中
2. 通过此种方式，可以方便控制当前整个页面中的元素样式设置
3. 代码结构清晰，但是并没有实现结构与样式完全分离
4. 使用内部样式表设定 CSS，通常也被称为嵌入式引入，这种方式是我们练习时常用的方式

### 外部样式表（链接式）

实际开发都是外部样式表. 适合于样式比较多的情况. 核心是:样式单独写到CSS 文件中，之后把CSS文件引入到 HTML 页面中使用.
引入外部样式表分为两步：
1. 新建一个后缀名为 .css 的样式文件，把所有 CSS 代码都放入此文件中。
2. 在 HTML 页面中，使用`<link>` 标签引入这个文件。
语法：
```
<link rel="stylesheet"  href="css文件路径">
```