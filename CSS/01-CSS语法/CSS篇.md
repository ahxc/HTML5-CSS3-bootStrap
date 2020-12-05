

### **伪类**/选择器

&：嵌套上一级

an+c：n表示索引a的n整数倍，c表示偏移量，下面则表示从last-child开始4个元素

```css
&:nth-last-child(-n+4) {
    image {
        height: 33.33vw*386/232/2;
        border-left: 10rpx solid #fff;
    }
    &:nth-child(2),
    &:nth-child(3) {
        border-bottom: 10rpx solid #fff;
    }
}
```

### 自定义字体

```css
@font-face{
     font-family: '字体名称随便起'; 
     src: url('../font/字体名称.eot');
     src: url('../font/字体名称.woff') format('woff'),
          url('../font/字体名称.ttf') format('truetype'),
          url('../font/字体名称.svg') format('svg');
}
h1{
    font-family: "字体名称随便起";
}
```

### CSS3 [attribute*=value] 选择器

设置 class 属性值包含 "test" 的所有 div 元素的背景色：

```css
div[class*="test"]{
	background:#ffff00;
}
```

### CSS中@用法小结

[csdn](https://blog.csdn.net/zcy_wxy/article/details/80652247)

### 媒体查询

[菜鸟教程](https://www.runoob.com/css/css-rwd-mediaqueries.html)

```css
@media screen and (max-width: 300px) {/* 如果屏幕小于300则修改背景颜色 */
    body {
        background-color:lightblue;
    }
}
```

### 常用浏览器以及内核

**ie**：Trident

**firefox**：Gecko

**Safari**：Webkit（常用）

**Chrome/Opera**：Blink（常用）

### 字体font复合写法

font复合写法，font-size和font-family必须保留，否则失效，省略的直接不写，顺序不能变

```
font: font-style font-weight font-size/line-height font-family;
```

**行高的继承特殊性**（重要）：子继承1.5*12px的行距。

父font: 14px/1.5;，子font: 12px;

```html
<style>
    * {
        font: normal 700 16px "Microsoft yahei";
        text-decoration: underline;/* 重点记住下划线和none */
        text-indent:  2em;/* 文本缩进两个字，em表示的就是父元素字体大小 */
        line-height: 1em;/* 行间距，不跟单位就是size的倍数 */
        justify-content: space-between;
    }
</style>
```

### CSS层叠样式表简介，也是一种标记语言

**语法**： 选择器{声明}

选择器包括：标签，类，id，通配符选择器。

id选择常用作唯一标识符，经常和js搭配使用。通配符选择器，*表示所有，不推荐使用消耗性能。

### CSS三种样式表（书写位置）

**1.行内样式表****（行内式）即标签内部style属性，完全嵌入结构，极不推荐

**2.内部样式表**（嵌入式）即head内的style标签，没有与结构完全分离

**3.外部样式表**（链接式）即

```html
<link rel="stylesheet" href="路径">
```

### emmet语法，vscode已集成，用来提高htmlcss语法速度

div{内容}

div.demon$*5

div.name

div#name

### 复合选择器

**后代（包含）选择器**（重要）：祖先元素1 元素2 省略 {声明;}

**子选择器**（重要）选择最近一级的元素，可以过滤掉孙子元素：父元素>子元素 {声明;}

**并集选择器**（重要）集体声明：元素1, 元素2, 省略 {声明;}

**伪类选择器**，伪类选择器用 : 表示：元素:伪类，更多参考文档。

链接伪类，声明顺序不能变 a:link a:visited a:hover a:active

focus伪类，有焦点的元素：

```css
input:focus {
	color: red;
}
```

### 元素显示模式

 **块元素**：div h p ul ol li等

块元素独占一行，高宽边距可控，高宽默认父元素相同，是一个容器，除p h等文字容器以外还可以放块元素。

**行内（内联）元素**：a strong b em i del s ins u span等。

行内元素只能容纳其他行内元素，高宽直接设置无效，内容多大就是多大。

**行内块元素**：img input td等

同行当由间隙，本身多大就是多大，高宽可控。

模式转换：

```
display: block inline inline-block;
```

### 背景一些属性

background-color: 默认transparent;透明 rgb(0,0,0,0.5)半透明，后者css3。

background-image: img | url;

background-repeat repeat|no-repeat|repeat-x|repeat-y;重复和不重复，哪个方向重复。

background-position: center right;中右靠齐，可以只写一个，分别表示x,y，可以写具体数值。

background-attachment: scroll|fixed;设置背景图片是否跟随滚动，这里的滚动是滚走，而fixed固定则一直在视窗内。

**背景的复合写法**

```css
background: color image repeat attachment posiont;
```

### CSS三大特性

**1.层叠性**：即相同的声明属性值如果一样（样式冲突），就近原则：离结构越近则优先级最高

**2.继承性**（重要）：多使用继承可节省性能开销

**3.优先级**，同级的优先级就近原则：

important：Infinity

行间样式（行内样式 内联样式style=""）：1000

id：100

class/属性/伪类：10

标签选择器/伪元素：1

通配：0

**注意**：继承的样式权重都是0

### 复合选择器的权重问题

ul li {}; li{};前者的权重大于后者，比较原理即按上表各元素的权重叠加和。

### 盒子模型

 margin border padding content

border的复合写法：

```
border: width type color;
```

border-collapse: collapse;合并相邻边框

**注意**：根据盒子模型可见，边框会影响盒子实际大小，且不会与其他元素边框重叠，所以要计算实际大小。

### padding的复合写法

一个值四周。

两个值上下，左右。

三个值上，左右，下。

四个值顶部开始顺时针。

padding可以撑大父元素。

### margin的复合写法和padding差不多，不能撑大父元素

外边距可以让块级盒子居中，但必须满足**两个条件**：

1.元素高宽已经指定，外边距设置为auto

2.margin: auto;

父子元素同时设置margin在某些情况下会塌陷，即融合在一起，可以为父元素：定义1边框，2内边距，3添加overflow: hidden;

清楚内外边距：

不同浏览器边距设置不一样所以要事先设置为0，还有很多预设置（CSS reset），有统一文件。

padding:0; margin:0;

**注意**：行内元素尽量不要设置上下内外边距，照顾浏览器兼容性，但转换为块级或者行内块级元素则无此顾虑

### 综合问题（重点）详细的看面试题

1.不同元素最好还是对应不同标签，不要一股脑div，能省下很多样式声明。

2.多用类名，且类名要尽量唯一，除了公共类，而且尽量不要和标签名混合选择器。

### 圆角边框（重点）css3

```
border-radius: 1 2 3 4;
```

一个整数值，表示角上圆的半径，因此如果等于高的一半则为一个半圆。

两个值，即上下，左右，可以设置平行四边型的样式。

四个值可以分别设置，当然这用的少。

### 盒子阴影（重点）css3

```
box-shadow: h-shadow v-shadow blur spread color inset;
```

分别是：水平阴影位置和垂直位置必选，模糊，尺寸，颜色，内部阴影。

可用于一些鼠标悬停设置阴影。

### 文字阴影 css3

```
text-shadow: h-shadow v-shadow blur color;
```

和盒子一样

### 盒子布局

**浮动float**

**标准流**：即元素定义后，按照规定好的方向默认排列

**定位**

标准布局：1.块级元素从上往下，2.行内元素从左往右

### 为什么要浮动（float相关知识点都很重要）

浮动可以把块元素变为行内块元素（伸缩盒子也可以），且能根据屏幕变化换行，标准流是无法实现的，**第一准则：纵向找标准流，横向找浮动**。

**注意**：

1.浮动会脱离文档流（标准流），所以要设置父元素包裹，这点和position:absolute;一样。

2.浮动会具有行内块元素特性，会左上角一行排列；因此像一些如span的行内元素都能设置宽高了。

3.父元素不应该有高度，会溢出，但父元素高度会为0。

**为什么要清除浮动**

浮动会脱离文档流，上面第3点，标准流显示会有问题，父元素下面的元素会占用位置。

**如何清除浮动**

**1.额外标签法**，w3c推荐，但用的少

浮动元素末尾添加一个空的标签（必须是块级元素），如

```html
<style>
	.clear {clear: both};
</style>
或者
<div style="clear:both"></div>
或者
<br/>
```

 **缺点**就是添加了无意义标签，结构化差。

**2.父元素添加overflow**

overflow: hidden auto scroll;三者都可，**缺点**就是无法显示溢出部分。

**3.父元素添加after伪类 class="clearfix"**

```css
.clearfix:after {/* after：在元素后插入一个元素，所以这个是第一个方法的升级版，没有手动创建元素 */
    content: "";
    display: block;
    height: 0;
    clear: both;
    visibility: hidden;
}
.clearfix {/* ie6 7 */
    *zoom:1;
}
```

**4.父元素添加双伪类 class="clearfix"**

```css
.clearfix:before, .clearfix:after{/* 和3同理，比3代码更简洁，样式声明更少 */
    content: "";
    display: table;
}
.clearfix:after {
    clear:both;
}
.clearfix {
    *zoom:1;
}
```

### CSS属性书写顺序（重点）

**1.布局定位属性**：display/position/float/clear/visibility/overflow（关系到模式的最先写）

**2.自身属性**：width/height/margin/padding/border/background

**3.文本属性**：color/font/text-decoration/text-align/vertical-align/white-space/break-word

**4.其他属性**（CSS3）：content/cursor/border-radius/box-shadow/text-shadow/background...

### 页面布局整体思路

1.首先确定可视区域（版区）。

2.根据第一准则，分析页面行模块，再分析每行的列模块。

3.确定行模块内的浮动布局，确定列位置大小。

4.制作html结构，再写样式，**结构**最重要。

5.先布局完成（画出来），再准备代码。

**注意**：

1.包裹a标签最好用ul列表，可使用浮动将其水平排列。

2.搜索框的宽度通常包括一个左padding值（使placeholder文本偏移），所以记住计算实际的宽度。（平时遇到过）

### CSS定位position

**为什么需要定位**

使元素脱离文档流，固定或者游离于视窗，丰富产品功能用户体验。

**定位组成**：定位模式，边偏移

**定位模式**：

static，**静态定位**，（了解）没有脱离文档流，但是可以用到边偏移。

relative，**相对定位**，（重要）相对元素自身位置移动边偏移，不脱标。且一重要特性给绝对定位做基础定位。

absolute，**绝对定位**，（重要）相对祖先元素或者距离最近有定位模式的元素（绝对，相对，固定）进行边偏移。如果没有祖先，则以文档为基准。一般开发要**子绝父相**。

fixed，**固定定位**，（重要）固定定位以视窗为基准，不跟父元素有任何关系，不随滚动而滚动。脱标。

sticky，**粘性定位**，（了解）占有原有位置，必须添加一个边偏距，以视窗为基准，即吸顶效果，但这个功能开发用的少。

**边偏移**（定位使用的属性）：top，bottom，left，right

**注意**：使用定位注意的两大点：1.是否占有位置，2.基准元素

**定位的叠放顺序**

```css
* {
	z-index: 1;
}
```

只有定位盒子才有z-index属性，如果值相同，按顺序后来者居上。

**定位的特殊性**

1.行内元素添加绝对或者固定定位属性，可以设置高宽。2.定位元素不会塌陷，即外边距合并。3绝对定位和固定定位会完全压住盒子，而浮动元素不会压住盒子里的文字或者图片。浮动元素这一特性可以用作文字围绕效果。

### 元素的显示与隐藏

**display**，none隐藏对象，位置不保留。block除了块元素还有显示元素的意思，搭配none使用可以设置光标悬停显示效果。

**visibility**，hidden隐藏元素，visible显示元素，位置保留。

**overflow**，hidden隐藏溢出的元素，scroll不管溢出都显示滚动条，auto溢出时才显示滚动条。 

### CSS精灵图（CSS雪碧，CSS Sprites）

**目的**：为了减少服务器接收和发送请求的次数，提高页面加载速度。

**核心**：主要针对小背景图片使用，如侧边栏一连串的小按钮等，把多个小图片融合到一张大图中，即精灵图。

```css
* {
    background-position: -100px -100px;/* 以图片的父元素左上角对齐为基准 */
}
```

**缺点**：图片文件还是很大的，图片本身放大和缩小会失真，一旦制作完成，后期更换比较复杂。

### 字体图标

即字符转码后的图标，本质属于字体，可用font调节。

优点：轻量级，灵活性，兼容性高。不能完全替换精灵图，毕竟个性化的优化还需自己开发提供。

使用步骤其实和使用自定义字体类似：

1.下载需要的字体图标库。

2.导入字体，自定义字体章节。

3.使用：

```css
* {/* 使用该字体的元素 */
	font-fammily: '自定义字体名称';
}
```

**注意**：现在逐步使用更好的方式svg字体图标。

### vertical-align

**表示行内块元素的对齐方式**，例如图片和文字的对齐方式

```
vertical-align: top/middle/base/bottom;
```

**注意**：1可以用于解决一些图片底部缝隙的问题（因为默认是以基线base对齐，可以设置为bottom）。2也可以使用设置为块元素block方法。

### 文本溢出显示省略号

单行文本溢出省略号必须满足三个条件：

```css
* {
    white-space: nowrap;
	overflow: hidden;
	text-overflow:ellipsis;/* 省略号 */
}
```

**nowrap**，不换行溢出显示。

**normal**，自动换行。

多行文本溢出兼容性问题较大，这里只指出样例，具体问题具体分析：

```css
* {
	text-overflow:ellipsis;/* 省略号 */
	overflow: hidden;
	display: -webkit-box;/* 弹性盒子 */
    -webkit-line-clamp: 2;/* 限定行数 */
    -webkit-box-orient: vertical;/* 排列方向 */
}
```

**注意**：后四项微信小程序用到过。

### 常见布局技巧

1.让并列排列的盒子具有相等的边框，使用 margin-left: -1px; 即让border重叠。

2.在第一条的基础上，如果想加hover悬停后的边框高亮效果，顺便附加一个高索引的z-index，防止border重叠覆盖显示不全。

3.对于多标签的点击能用a不用div，可设置display: inline-block;设为行内块元素。则可设置高宽等属性。

### CSS初始化 reset

参考面试题，有多种初始化方案。获取方法：1.百度初始化方案，2.大厂网页源码直接找link。

### HTML5新特性

新的标签，新的表单，新的表单属性

div对于搜索引擎来说是没有语义的，

**语义标签**：header头部，nav导航，article内容，section区域（大号div），aside侧边栏，footer尾部。都是针对搜索引擎的标签。

**影音标签**：

[video视频标签](https://www.runoob.com/tags/tag-video.html)（尽量使用MP4，支持大多浏览器）。

[audio音频标签](https://www.runoob.com/tags/tag-audio.html)（规则基本和视频标签一致）。

**input type属性**：email，url，date，time，month，week，number，tel，seach，color。

