### 如何让非文字类元素实现水平垂直居中？

**普通div的水平居中**

```css
*{margin: 0 auto;}
```

**绝对定位的水平居中：**

```css
* {
    position:absolute;
	left:50%;
	top:50%;
	margin-left:-50px;
	margin-top:-50px;
}
```

**浮动元素的水平垂直居中：**

```css
* {
    border: 1px solid red;/* 防止塌陷 */
	float: left;
	position: absolute;
	width: 200px;
	height: 100px;
	left: 50%;
	top: 50%;
	margin: -50px 0 0 -100px;
}
```

### 利用绝对定位元素的自动伸缩特性水平垂直居中

```css
.father {
    position: relative;
}
.son {
    position:absolute;
    left: 0;
    right: 0;
    top: 0;
    bottom: 0;
    margin: auto;
}
```

### 利用flex布局水平垂直居中

```css
#box {
    display: flex;
    display: -webkit-flex;
    align-items: center;
    justify-content: center;
}
```

### 在不知道图片大小的情况下，如何设置样式让图片不变形？

```css
* {max-width: 100%;}
```

### 对BFC规范(块级格式化上下文：block formatting context)的理解

**BFC有以下特性：**

1、内部的Box会在垂直方向，从顶部开始一个接一个地放置。 2、Box垂直方向的距离由margin决定。属于同一个BFC的两个相邻Box的margin会发生叠加 3、每个元素的margin box的左边， 与包含块border box的左边相接触(对于从左往右的格式化，否则相反)。即使存在浮动也是如此。 4、BFC的区域不会与float box叠加。 5、BFC就是页面上的一个隔离的独立容器，容器里面的子元素不会影响到外面的元素，反之亦然。 6、计算BFC的高度时，浮动元素也参与计算。

**那么我们怎样做就可以触发BFC呢**

- float 除了none以外的值 overflow 除了visible 以外的值（hidden，auto，scroll ）
- display (table-cell，table-caption，inline-block, flex, inline-flex)
- position值为（absolute，fixed） fieldset元素
- fieldset元素 在以上情况下可以创建BFC

**BFC可以解决的问题**

- margin叠加的问题，我们将某个元素放到我们新建的BFC里面就可以避免margin叠加、
- 对于左右布局的元素，我们可以给右侧的元素添加overflow:hidden或者auto，左侧的是float:left
- 可以清除浮动，计算BFC高度，浮动元素不会撑开父元素的高度，我们可以让父元素触发BFC,即使用overflow:hidden

### 圣杯布局和双飞翼布局

[掘金](https://juejin.cn/post/6844903763329679368)

### 怎么让浏览器支持小于12px 的文字？

```css
* {
    display: inline-block;
    font-size: 14px;
    transform: scale(0.8);/* 缩放 */
 }
```

### 如何消除ul和li前面的点？

```css
list-style:none
```
