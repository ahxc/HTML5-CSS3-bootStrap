### 什么是盒子模型？

盒子模型包括content+padding+border+margin

标准盒子模型：宽度=内容的宽度（content）

低版本IE盒子模型：宽度=content+border+padding

### CSS常用选择器有哪些？

标签属性：class id 标签名 

样式相关：hover，empty，focus（有焦点的元素）

[菜鸟教程](https://www.runoob.com/cssref/css-selectors.html)

### CSS3新增伪类有哪些？

p:first-of-type 选择属于其父元素的首个元素

p:last-of-type 选择属于其父元素的最后元素

p:only-of-type 选择属于其父元素唯一的元素

p:only-child 选择属于其父元素的唯一子元素

p:nth-child(2) 选择属于其父元素的第二个子元素

:enabled :disabled 表单控件的禁用状态。

:checked 单选框或复选框被选中

### CSS3有哪些新增特性

这个问题贼大，作为一个新闻专业出身的人，这种问题简直是脑残，新特性那么多，难道需要我背一遍文档你听吗？

但是，显然面试官并不care你答不答的全，他自己都不定记得，对吧～

我们完全可以从个人项目经验出发，比如我自己，在做小程序时用过flex布局，就可以以这个为主，再列举三四个其他的就行了。

为了方便大家，这里先列几个出来：

(1)CSS3 弹性盒（ Flexible Box 或 flexbox）

是一种当页面需要适应不同的屏幕大小以及设备类型时确保元素拥有恰当的行为的布局方式。

具体使用参考 [www.jianshu.com/p/5856c4ae9…](https://www.jianshu.com/p/5856c4ae91f2)

(2)伪类选择器，参考上面的第三条，列表渲染修改单个列表样式时，上面的nth-child()超好用

(3)边框圆角：`border-radius：3px`

(4)@font-face，可以引入客户端没有的字体

(5)媒体查询@meida，具体用法：[www.cnblogs.com/yan-ck/p/58…](https://www.cnblogs.com/yan-ck/p/5842771.html)

```css
@media screen and (max-width: 300px) {/* 如果屏幕小于300则修改背景颜色 */
    body {
        background-color:lightblue;
    }
}
```

其他参考：[blog.csdn.net/lxcao/artic…](https://blog.csdn.net/lxcao/article/details/52797914)

### CSS优先级计算规则

important：Infinity

行间样式（行内样式 内联样式style=“”）：1000

id：100

class/属性/伪类：10

标签选择器/伪元素：1

通配：0

### 如何使用自定义字体

@font-face可以实现，

```css
@font-face{
     font-family: '字体名称随便起'; 
     src: url('../font/字体名称.eot');
     src: url('../font/字体名称.woff') format('woff'),
          url('../font/字体名称.ttf') format('truetype'),
          url('../font/字体名称.svg') format('svg');
}

h1{
    font-size: 36px;
    color: #ccc;
    font-family: "字体名称随便起";
}
```

具体使用方法：[www.jianshu.com/p/976d95fb8…](https://www.jianshu.com/p/976d95fb87a7)

### CSS有哪些继承属性

参考：[www.cnblogs.com/thislbq/p/5…](https://www.cnblogs.com/thislbq/p/5882105.html)

### CSS单行省略和多行省略

单行：

```css
overflow: hidden;//隐藏溢出
text-overflow: ellipsis;//省略号
white-space: nowrap;//不换行
flex-wrap: nowrap;//默认不换行
```

### 如何去除inline-block元素间隙？

空隙产生原因：HTML中的换行符、空格符、制表符等空白符，字体大小不为0的情况下，空白符占据一定宽度，使用inline-block会产生元素间的空隙。

**解决办法：**

1. 把所有的子元素写在一行；
2. 子元素设置浮动；
3. 父元素的font-size设置为0，子元素的font-size设置为实际大小；
4. 使用注释：

```html
<div class="parent"> 
&emsp;&emsp;&emsp; <div class="child"></div><!--
&emsp;&emsp;--><div class="child"></div><!--
&emsp;&emsp;--><div class="child"></div><!--
&emsp;&emsp;--><div class="child"></div>
</div>
```

###  display属性？

block: 指定元素为块级元素，可以设宽高，元素前后自带换行符，比如div、p。

 inline：指定元素为内联元素，不能设置宽高，元素不带换行符，会显示在同一行，比如span。 

inline-block：行内块元素，兼具前两者的特点，元素前后不带换行符，但又可以设置宽高，比如input\img。 

none：可以隐藏元素。 常用的还有2个，就是table和table-cell，结合使用在父子元素身上，子元素如果有大段文字，只要再加一个vertical-align:middle，就能轻松将文字垂直居中。

 CSS3新增了一个非常适合移动端使用的flex，能很好的适应不同屏幕大小。

### box-sizing属性

用来控制元素的盒子模型的解析模式，默认为content-box。

context-box：W3C的标准盒子模型，设置元素的height/width属性指的是content部分的高/宽；border-box：IE传统盒子模型。设置元素的height/width属性指的是border + padding + content部分的高/宽。

### display:none与visibility:hidden

很多前端的同学认为visibility: hidden和display: none的区别仅仅在于display: none隐藏后的元素不占据任何空间，而visibility: hidden隐藏后的元素空间依旧保留 ，实际上没那么简单，visibility是一个非常有故事性的属性。

1、visibility具有继承性，给父元素设置visibility:hidden;子元素也会继承这个属性。但是如果重新给子元素设置visibility: visible,则子元素又会显示出来。这个和display: none有着质的区别。

2、visibility: hidden不会影响计数器的计数，如图所示，visibility: hidden虽然让一个元素不见了，但是其计数器仍在运行。这和display: none完全不一样。

### visibility属性的collapse属性值

collapse属性很有意思，当一个元素的 visibility 属性被设置成 collapse 值后，对于一般的元素，它的表现跟 hidden 是一样的。但例外的是，如果这个元素是table相关的元素，例如table行，table group，table列，table column group，它的表现会和浏览器不同而变化。

在谷歌浏览器里，使用 collapse 值和使用 hidden 值没有什么区别。

在火狐浏览器和IE8里，使用 collapse值的效果就如它的字面意思：table的行会消失，它的下面一行会补充它的位置。效果类似于display：none。

### em\px\rem区别

px：绝对单位，页面按精确像素展示。

em：相对单位，基准点为父节点字体font-size的大小，如果自身定义了font-size按自身来计算（浏览器默认字体是16px），整个页面内1em不是一个固定的值。

rem：相对单位，可理解为”root em”, 相对根节点html的字体大小来计算，CSS3新加属性，chrome/firefox/IE9+支持。

PX特点：

1. IE无法调整那些使用px作为单位的字体大小；
2. 国外的大部分网站能够调整的原因在于其使用了em或rem作为字体单位；
3. Firefox能够调整px和em，rem，但是96%以上的中国网民使用IE浏览器(或内核)。

EM特点 ：

1. em的值并不是固定的；
2. em会继承父级元素的字体大小。

rem特点：

rem是CSS3新增的一个相对单位（root em，根em），这个单位引起了广泛关注。区别在于使用rem为元素设定字体大小时，仍然是相对大小，但相对的只是HTML根元素。

这个单位可谓集相对大小和绝对大小的优点于一身，通过它既可以做到只修改根元素就成比例地调整所有字体大小，又可以避免字体大小逐层复合的连锁反应。

目前，除了IE8及更早版本外，所有浏览器均已支持rem。对于不支持它的浏览器，应对方法也很简单，就是多写一个绝对单位的声明。这些浏览器会忽略用rem设定的字体大小。

### position有哪些值？

1、static（静态定位）：默认值。没有定位，元素出现在正常的流中（忽略 top, bottom, left, right 或者 z-index 声明）。

2、relative（相对定位）：生成相对定位的元素，通过top,bottom,left,right的设置相对于其正常（原先本身）位置进行定位。可通过z-index进行层次分级。元素位置变换以后，不会脱离文档流。 

3、absolute（绝对定位）：生成绝对定位的元素，相对于 static 定位以外的第一个父元素进行定位。元素的位置通过 "left", "top", "right" 以及 "bottom" 属性进行规定。可通过z-index进行层次分级，会脱离文档流。

4、fixed（固定定位）：生成绝对定位的元素，相对于浏览器窗口进行定位。元素的位置通过 "left", "top", "right" 以及 "bottom" 属性进行规定。可通过z-index进行层次分级。

### float与display的区别

**float**是元素浮动，页面变化会朝对齐方向重新排列，float定义在子元素上。

**display**是弹性盒子，会根据页面变化伸缩盒子，display定义在父元素上

### 如何清除浮动？

**浮动**会使当前标签脱离文档流，产生上浮的效果。

[www.cnblogs.com/hanqingtao/…](https://www.cnblogs.com/hanqingtao/p/5856103.html)

### 如何让非文字类元素实现水平垂直居中？

**普通div的水平居中**

```
margin: 0 auto;
height: 50px;
width: 80px;
```

**绝对定位的水平居中：**

```css
position:absolute;
left:50%;
top:50%;
margin-left:-50px;
margin-top:-50px;
```

**浮动元素的水平垂直居中：**

```
border: 1px solid red;
float: left;
position:absolute;
width: 200px;
height: 100px;
left: 50%;
top: 50%;
margin: -50px 0 0 -100px;
```

### 利用绝对定位元素的自动伸缩特性水平垂直居中

```css
.father{
    position: relative;
    width: 500px;
    height: 500px;
}
.son{
    position:absolute;
    left: 0;
    right: 0;
    top: 0;
    bottom: 0;
    margin: auto;
}
```

### 利用flex布局水平垂直居中（回答这个显得更高端）

```css
#box{
    display: flex;
    display: -webkit-flex;
    border: 1px solid #0000FF;
    height: 200px;
    width: 400px;
    align-items:center;
    justify-content:center;
}
.item{
    width: 50px;
    height: 40px;
    border: 1px solid #00C1B3;
}
```

### 文字内的垂直居中

```
line-height: 元素高度;
```

### 在不知道图片大小的情况下，如何设置样式让图片不变形？

```
max-width: 100%
```

### 请解释一下CSS3的flexbox（弹性盒布局模型）,以及适用场景？

[flex相关属性与定义](https://www.cnblogs.com/lixuemin/p/6110434.html)

### 用纯CSS创建一个三角形

```css
width: 0;/* 一个80高宽的小方块，内容为0，边框渐变transparent */
height: 0;
border-top: 40px solid transparent;
border-left: 40px solid transparent;
border-right: 40px solid transparent;
border-bottom: 40px solid #ff0000; 
```

### rgba和opacity的透明有何不同？

opacity会继承父元素的opacity 属性，而RGBA设置的元素的后代元素不会继承不透明属性。简单来说就是opacity作用于元素和元素所有内容的透明

rgba相对于opacity还是技高一筹的，当然只要是涉及颜色的，都可以用rgba来设置。

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

### 媒体查询

响应式设计的核心

语法：

```css
@media mediatype and|not|only (media feature) {
    CSS-Code;
}
```

案例:

```css
@media screen and (max-width: 300px) {
    body {
        background-color:lightblue;
    }
}
```

[菜鸟教程](https://www.runoob.com/cssref/css3-pr-mediaquery.html)

### 圣杯布局和双飞翼布局

[掘金](https://juejin.cn/post/6844903763329679368)

### 浏览器解析CSS选择器

[菜鸟教程](https://www.runoob.com/cssref/css-selectors.html)

### 响应式设计

响应式设计就是内容会根据窗口的变化而变化，放大时能伸展，缩小时能收缩，同时内容和布局也会发生适应性的变化。

响应式设计与自适应设计的区别：响应式开发一套界面（比较大），通过检测视口分辨率，针对不同客户端在客户端做代码处理，来展现不同的布局和内容；自适应需要开发多套界面，通过检测视口分辨率，来判断当前访问的设备是pc端、平板、手机，从而请求服务层，返回不同的页面。自适应一般内容不会变。

[掘金](https://juejin.cn/post/6844903814332432397)

### 怎么让浏览器支持小于12px 的文字？

```css
.Num{
    display: inline-block;
    font-size: 14px;
    transform: scale(0.8);/* 缩放 */
 }
```

### link和@import的区别

1. link属于XHTML标签，而@import是CSS提供的。
2. 页面被加载时，link会同时被加载，而@import引用的CSS会等到页面被加载完再加载。
3. import只在IE 5以上才能识别，而link是XHTML标签，无兼容问题。
4. link方式的样式权重高于@import的权重。
5. 使用dom控制样式时的差别。当使用javascript控制dom去改变样式的时候，只能使用link标签，因为@import不是dom可以控制的。

### 重排(reflow)和重绘(repaint)

[掘金](https://juejin.cn/post/6844904083212468238)

**优化方法：**

1、样式集中改变，不要频繁的修改样式，对于元素的样式改变应该更改类名，而不是修改样式属性值。

2、分离读写操作，即要修改样式时，先读取样式属性并赋值为一个变量，如swiper中的style赋值，然后再赋予新的样式值。

第二点原理：当我们修改了元素的几何属性，导致浏览器触发重排或重绘时。它会把该操作放进渲染队列，等到队列中的操作到了一定的数量或者到了一定的时间间隔时，浏览器就会批量执行这些操作。

3、将 DOM 离线，

​	。可通过display:none隐藏节点进行样式修改然后在现实，这样无论多少次重排重绘都实际只两。

​	。复制节点等等修改dom。

4.使用 absolute 或 fixed 脱离文档流

5.优化动画：

​	。gpu加速，一些transform，translate3d属性

### CSS优化与性能提高

简单概括：

css匹配原理：从html中由右向左，从里层到最外层。

css选择器权值

[博客园](https://www.cnblogs.com/xiaoloulan/p/5801663.html)

1，减少css嵌套，最好不要套三层以上，一般情况下块级元素加上类，里面的内联元素不用加，css写的时候块级class套内联tag，这样不仅可以减少css文件大小，还能减少性能浪费。

2，不要在ID选择器前面进行嵌套，ID本来就是唯一的而且人家权值那么大，前方嵌套完全是浪费性能。

3，建立公共样式类，把公共样式部分抽离出来

4，缩写css，其中包括缩写maigin，padding，颜色值等等，即不要分的太细，如margin-top...。

5，减少通配符*或者类似[hidden="true"]这类选择器的使用，它会挨个查找所有。

6，有些人喜欢在类名前面加上标签名：p.ty_p 来进行更加精确的定位，类名全局应该独一，除了公共样式，不要嵌套太多。

7，巧妙运用css的继承机制，在css中很多属性是可以继承的比如颜色字体等等，父节点定义了，子节点就无需定义。

8，不用css表达式，因为结果都是静态的，但是会有性能浪费，因为它并不只是计算一次，一些小的事件可能都会增加它为了有效准确而进行计算求值的次数。

9，少用css reset或者精简，可能你会觉得重置样式是规范，但是其实其中有很多的操作是不必要不友好的，有需求有兴趣的朋友可以选择normolize.css。[css reset](https://www.jianshu.com/p/ef690746ef96)

10，cssSprite，把所有icon图片加成一张图片，用宽高加上bacgroud-position的背景图方式，一个点击部分显示图片一部分，这是一种十分实用的技巧，极大减少了http请求。

11，不同元素最好对应不同标签，如span，h标签等等，能减少很多重复样式声明。

### 如何消除ul和li前面的点？

```css
list-style:none
```
