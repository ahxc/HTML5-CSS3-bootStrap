

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

**自定义字体**

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

**后代（包含）选择器**（重要）：祖先元素1 元素2 省略 {声明;}。

**子选择器**（重要）选择最近一级的元素，可以过滤掉孙子元素：父元素>子元素 {声明;}。

**并集选择器**（重要）集体声明：元素1, 元素2, 省略 {声明;}。

**交集选择器** div.one，标签元素div且类名为one的元素。一般class要有唯一性，所以不太用。

**伪类选择器**，伪类选择器用 : 表示：元素:伪类，更多参考文档。

链接伪类，声明顺序不能变 a:link a:visited a:hover a:active。

focus伪类，有焦点的元素：

```css
input:focus {
	color: red;
}
```

### 元素显示模式

[链接](https://www.cnblogs.com/i969639/p/11201140.html)

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

background-size: x, y; 背景图的尺寸可以是百分比。cover：缩放充满盒子，图片可能溢出。contain：平铺充满盒子，会有空隙。

**背景的复合写法**

```css
background: color image repeat attachment position;
```

**注意**：background-position: 100% 26px;(0%, 0%)表示左上角，(100%, 100%表示右下角)

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

清除内外边距：

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
    display: table;/* 块级且换行，和表格一样 */
}
.clearfix:after {
    clear:both;/* 意思就是清除浮动 */
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

**注意**：1.可以用于解决一些图片底部缝隙的问题（因为默认是以基线base对齐，可以设置为bottom）。2.也可以使用设置为块元素block方法。

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

有多种初始化[方案](https://www.jianshu.com/p/ef690746ef96)。获取方法：1.百度初始化方案，2.大厂网页源码直接找link。

### HTML5新特性

新的标签，新的表单，新的表单属性

div对于搜索引擎来说是没有语义的，

**语义标签**：header头部，nav导航，article内容，section区域（大号div），aside侧边栏，footer尾部。都是针对搜索引擎的标签。

**影音标签**：

[video视频标签](https://www.runoob.com/tags/tag-video.html)（尽量使用MP4，支持大多浏览器）。

[audio音频标签](https://www.runoob.com/tags/tag-audio.html)（规则基本和视频标签一致）。

**[input ](https://www.runoob.com/tags/tag-input.html)type属性**（重要）：email，url，date，time，month，week，number，tel，seach，color。

### CSS3新特性

**1.新增[选择器](https://www.runoob.com/cssref/css-selectors.html)**（重点）详细参看菜鸟教程CSS3，下面只例几个样例。

属性选择器 attribute字样

伪类选择器:

伪元素选择器::

**2.盒子模型**

box-sizing

**3.动画animation**

**4.浏览器私有前缀**

**5.转换transform**

### 属性选择器

```css
div[attribute=value]{};
```

### 伪类选择器:

&：嵌套上一级

an+c：n表示索引a的n整数倍，c表示偏移量，下面则表示从last-child开始4个元素，如果单独一个n则是所有孩子从1开始。n是公式的话从零开始，但零忽略掉了。

```css
&:nth-last-child(-n+4) {
    image {
        height: 33.33vw*386/232/2;
        border-left: 10rpx solid #fff;
    }
    &:nth-child(2),/* 第二个元素 */
    &:nth-child(3) {
        border-bottom: 10rpx solid #fff;
    }
}
```

**注意**：

1.type是child的升级版，不查找所有子元素，而是查找指定元素的第几个元素，如p:nth-of-type(n)查找p元素中的第n个p元素，先查找p，在找第几个p。

2.p:nth-child是查找p元素下的子元素，这个p可以是同级元素。

**常用方法**（重点）

可以将一些同级的浮动元素中的个别子元素设置具有个性的样式，如上代码。

### 伪元素选择器::

可以在指定元素里创建新标签。但是找不到这个盒子，所以称为伪元素。伪元素的权重和标签一样为1。content必须要有。

```css
/* 在p元素内部元素的前面插入span标签，也可以是转义字符，字体码等等。当然也可以定义样式，样式属于before */
p::before{
    content: "span";
};
p::after{};
::selection{};/* 选中的文本 */
```

**注意**：单冒号也是可行，但会转换为双冒号。伪元素样式权重虽然为1，但样式中是复合权重。如上面的p::before;权重是2。

**常用方法**（重点）

```css
p::before{
	content: '';/* content属性必须要有 */
    display: none;
    background: #fff;
}
p:hover::before{
	display: block;/* 显示before */
}
```

如此设置可以在经过某些事件，如上面的鼠标hover，激活一些伪元素创立新样式。比如鼠标hover在视频上时显示播放按钮。当然也可以事先用html写好一个隐藏元素，用hover激活显示。但上面的方法结构代码更少。

### 盒子模型

通过**box-sizing**修改盒子宽度属性。

```css
*{
    box-sizing: content-box;/* content+padding+border 传统每个盒子默认的 */
    box-sizing: border-box;/* content，CSS3盒子模型 */
}
```

**注意**：1.修改了第二个border-box，那padding和border都不会撑大盒子了，只会缩小content（前提padding和border不能超过盒子宽度）。2.有些reset文件会采用第二种来解决兼容性的问题，这种方法可全部用于移动端的盒子模型。

### CSS其他特性（了解）

filter模糊样式。calc()计算。因为这些都是动态属性，十分消耗性能，所以不推荐。

```css
* {
	filter: blur(5px);
    width: calc(100% - 3px);
}
```

### 过度transition（重点）

```css
* {/* 不能重复声明，多个属性要变参照第二行,或则直接写个all，只有声明过的属性有效 */
    width: 100px;
    height: 100px;
	transition: 过度的属性 运行时间 运动曲线 开始时间;
    transition: width .5s, ease .5s;
    transition: all .5s;
}
```

**属性**：可以是高宽，背景颜色，内外边距。

**花费时间**：动画运行时间默认0ms。

**运动曲线**：默认ease。

**何时开始**：默认为0s。

**常用方法**：1.进度条：原理十分简单，白色父盒子里开始位置加入一个绿色子盒子，通过事件，比如鼠标hover和初始化等等，设置子盒子的transition width属性。2.图标切换：原理都是大同小异，父盒子里放一个比父盒子长或宽的子盒子（里面还有两个图标），鼠标hover后，设置子盒子的边距left或top为负或者弹开都可（看如何放置）。

### 2D转换（重点）

**复合写法**

```
transform: translate(x, y) roate(n) scale()...等;
```

**注意**：顺序会影响转换效果，因为**中心点位置**，**坐标轴的变化**（旋转就会改变坐标轴）等等。通常**移动的操作**放最前面，当然具体问题具体分析。

**1.移动**：translate

```css
transform: translate(x, y);
transform: translateX(n);
transform: translateY(n);
```

**注意**：移动的元素不会影响其他元素，其实元素位置是没变化的，如果是百分比，则以元素自身高宽来计算。translate对行内标签没有效果。

**常用方法**：轮播图，选项卡

**2.旋转**：rotate

```css
transform: rotate(度数deg);/* 为正顺时针，负逆时针，默认中心为元素中心点 */
transform-origin: x y;/* 中心点的设置 */
```

**注意**：中心点xy可以用边距left等等，如left bottom表示以左下角为中心点。

**常用方法**：1.图标的切换，鼠标hover后，旋转上来一张图片，可以是伪元素，:hover::before，这个伪元素已经旋转至视野之外并隐藏，用rotate(0deg);回归视野。

**3.缩放**：scale

```
transform: scale(x, y);/* 不带单位，1就是1倍不变。小数就是缩小，可以只写一个，高宽同步缩放。 */
```

**注意**：缩放不会影响其他元素，可以通过修改中心点位置来影响缩放方向。正中心四周缩放。

**常用方法**：1.鼠标hover放大图标或背景。

### 动画

**用keyframes定义动画序列**（类似定义类选择器）

```css
@keyframes name {
    0%{/* 开始状态，也可以写作 from，除了0和100，还有25% 50% 75% */
        transform: translateX(0px);
    }
    100%{/* 结束状态，也可写作 to */
        transform: translateX(100px);
    }
}
div {
    width: 100px;
    height: 100px;
    animation-name: name;/* 调用动画 */
    animation-duration: 300ms;/* 持续时间 */
    animation-timing-function: ease;/* 动画曲线，默认ease */
    animation-delay: 1s;/* 推迟开始时间 */
    animation-iteration-count: 1;/* 动画播放次数，默认1，可以是infinite */
    animation-direction: normal;/* 动画运行方向，默认normal，反方向alternate */
    animation-play-state: running;/* 规定动画状态，paused暂停，hover可用 */
    animation-fill-mode: forwards;/* forwards保持运行后的位置，backwards回到初始位置 */
}
```

**注意**：

1.百分比就是整个过程所持续时间的划分。注意复合写法中没有play-state动画状态。

2.多个动画keyframe用逗号分隔。

**animation复合写法**

```css
animation: name duration timing-function delay iteration-count direction fill-mode, ...;
```

**常用方法**：1.热点雷达，即一个圆点以一种圆环波纹扩大的（width和height设为更大值）形式闪烁。配合box-shadow可实现。

### 动画曲线timing-function细节

**linear**：匀速。

**ease**：默认，低速开始逐步加速。

**ease-in**：低速开始。

**ease-out**：低速结束。

**ease-in-out**：低速开始和结束。

**steps(5)**：指定步数。即分多少步数来完成动画，卡帧效果。

### 3D转换（重点）

3D转换与2D不同的是，加了一个z轴。z轴垂直屏幕，往屏幕外为正，往屏幕内为负。

**1.移动translate3d**

比2d多了个3d和z。

```css
transform: translate3d(x,y,z);
transform: translateX();
transform: translateY();
transform: translateZ();
transform: translateX() translateY() translateZ();/* 可省略 */
```

**2.透视perspective**

在2d平面产生视觉立体，效果是二维。perspective写在观察元素的父元素上面。

```css
perspective: 500px;/* 表示父元素与子元素的Z轴距离，值越大子元素会看起来更大。 */
transform: translateZ(500px);/* 效果一致，区别在于写在子元素上。 */
```

**3.旋转rotate3d**

3d旋转可以是x轴，y轴，z轴。旋转方向遵循**左手法则**：

X轴：大拇指指向x轴正方向，其余手指则是旋转正方向。

Y轴：大拇指指向y轴正方向，其余手指则是旋转正方向。

Z轴：大拇指指向z轴正方向，其余手指则是旋转正方向。和时钟一样。

自定义轴：rotate3d(1, 0, 0, 45deg);x轴。如果不止1个1，则用矢量计算。如(1,1,0)，则是x轴与y轴的中间线。

```css
transform: rotateX(45deg);/* 沿着x轴旋转45度，为负反方向 */
transform: rotateY(45deg);
transform: rotateZ(45deg);
transform: rotate3d(x, y, z, 45deg);/* 沿着自定义轴旋转45度 */
```

**4.呈现 transform-style**

当我们进行3d转换的时候，最终都是以一种2d的视觉效果来实现，因此，在某些情况下没有3d的直观效果，如垂直的两个平面，没有相交效果，而是覆盖效果。

transform-style则是来控制是否开启3d空间呈现3d效果。

```css
transform-style: flat; /* 默认不开启 */
transform-style: preserve-3d;/* 开启3d立体空间 */
```

**常用方法**：1.翻牌子，做两个同级重合的盒子，每个盒子写不同的字体。将父盒子翻过来呈现另一种样式。

### 浏览器私有前缀

因为市面手机浏览器大多基于webkit内核，所以兼容性只考虑添加webkit即可。

```css
-moz-：firefox
-ms-：ie
-webkit-：safari，chrome
-o-：opera

/* 具体写法 */
-moz-border-radius: 10px;
```

### 视口

视口就是显示区域，可分为布局视口，视觉视口和理想视口。

**布局视口layout viewport**

移动设备一般都默认设置了布局视口，将电脑端的页面缩放自适应至手机视口。

**视觉视口visual viewport**

即手机能呈现的网站区域，能缩放，但不会影响布局视口。

**理想视口ideal viewport**

最理想的浏览布局。即布局视口等于理想视口。需要移动端页面meta添加name="viewport"。

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

width：视口宽度

initial-scale：初始缩放比

maximum-scale：最大缩放比

minimum-scale：最小缩放比

user-scalable：用户是否可以缩放，yes或no（1或0）

### 二倍图

**物理像素点**：真是存在的小颗粒，电脑端1px等于1像素，移动端则不尽相同。1px能显示能代表的物理像素个数称为**物理像素比**或**屏幕像素比**。谷歌调试器里的手机尺寸都是**开发尺寸**，即px尺寸，**实际尺寸要尺寸乘以物理像素比**。

retina视网膜屏幕的出现，可以在一块屏幕里面压缩更多的像素。因此一张50×50px的图像放到手机里会放大一定物理像素比的倍数（比如放到iPhone8，就会变成100×100，但他实际没这么多像素），这样会看起来很模糊。这就出现了**倍图**，还有三倍图，四倍图。

所以，**设计稿**通常比手机开发尺寸要大两倍，三倍，以接近手机实际的像素尺寸。

**解决方案**：

```css
/* 原始图片100×100，物理像素比2 */
img {
    width: 50px;
    width: 50px;
}
/* 二倍图 */
.box {
    background-size: 50px 50px;
}
```

### 移动端技术解决方案

```css
box-sizing: border-box;/* 盒子模型 */
-webkit-box-sizing: border-box;
-webkit-tap-highlight-color: transparent;/* 设置透明 */
-webkit-appearance: none;/* ios里加上这个才能给按钮和输入框自定义样式 */
img, a {/* 禁用长按页面弹出菜单 */
	-webkit-touch-callout: none;
}
-webkit-linear-gradient(0deg/可以是top left等, blue, green, 40%, red);可以加入多种颜色
```

### 移动端常见布局

主流布局：流式布局，flex弹性布局（推荐），less+rem+媒体查询布局，混合布局。

响应式布局：bootstrap+媒体查询。

**1.流式布局（百分比布局）**

通过占屏幕百分比来进行盒子的缩放，不受固定像素限制。是移动端常见形式。

**2.flex布局**

兼容性在ie不太行，但操作方便布局简单。传统布局（标准流，浮动）兼容性好多用于pc。即**disply:flex;，flex: n;**的搭配使用。

**注意**：父盒子设置flex后，子盒子的float，clear，vertical-align都将失效。

设立flex后的常用属性：

[flex-direction](https://www.runoob.com/cssref/css3-pr-flex-direction.html)：主轴方向。

[justify-content](https://www.runoob.com/cssref/css3-pr-justify-content.html)：主轴排列方式。

[align-content](https://www.runoob.com/cssref/css3-pr-align-content.html)：多行子元素的主轴的垂直排列方式，单行没有效果。

[align-items](https://www.runoob.com/cssref/css3-pr-align-items.html)：单行主轴的垂直排列方式。

flex-wrap：是否换行。

flex-flow：flex-direction和flex-wrap的复合写法。

[align-self](https://www.runoob.com/cssref/css3-pr-align-self.html)：和上面的align一致，只是用在子项的方法。可覆盖align-item。

### rem布局及其单位rem

流式布局和flex布局主要针对宽度，而rem布局则可针对元素的高度。

**em**是父元素的字体大小。1em则是1倍的字体大小px。

rem则是根元素**html**（网页只有一个html元素）元素的字体大小。元素的rem值就等于实际值除以这个字体大小。可以通过rem设计元素，值为 页面元素/字体大小，因此可以通过修改html的文字大小来修改元素的大小。

**适配方案1：less+媒体查询+rem**：先把设计稿屏幕横竖划分若干相同得等分（多少份看公司），**每一份作为字体的大小**并以此大小的rem设计设计稿。然后，在不同屏幕下，通过媒体查询和等比计算公式来修改html字体大小（屏幕/份数，公式推导如下，），以此达到元素等比缩放得效果。

**不同屏幕下字体公式**

```
p2：设计稿屏幕，f2：设计稿字体，f2=p2/15份（暂且定为15份）
p1/p2 = f1/f2
p1/p2 = f1*15/p2
化简：f1=p1/15;
所以不同屏幕下的字体只要屏幕宽度除以划分的份数即可。
```

**适配方案2：淘宝flexible.js**：其原理类似，先把屏幕划分若干等分，10份，每一份即1rem：字体大小，通过字体大小来设计设计稿。其他的交给flexible.js，flexible会根据屏幕宽度来修改字体大小。相比较第一个方案，不用写很多的媒体查询了。

1.github下载flexble.js。2.要用的页面导入script脚本即可。

**注意**：不同稿件要记得修改CSSrem插件的设计稿基准字体大小。然后重启。

### 媒体查询

```css
@media mediatype and|not|only (medai feature) {
    css-code;
}
```

mediatype：媒体类型，all：用于所有设备，print：打印机和打印预览，screen：屏幕。

关键字：and：多个媒体特性链接在一起（与），not：排除某个媒体类型（非），only：指定某个特性的媒体类型，可以省略。

媒体特性：max-width：小于等于，min-width：大于等于。

### CSS的弊端

CSS是非程序式语言。**没有作用域的概念**，因此CSS是全局的。CSS冗余度比较高，不方便复用维护和扩展。

CSS中最难的部分
1. 如何实现某种效果(cosmetic problems)
2. 如何组织管理CSS(architectural problems)

CSS的副作用主要体现为
* 样式冲突
* 命名冲突

### 解决弊端的工具LESS

leaner style sheets是一门CSS扩展语言。CSS预处理器。他并不是减少CSS的功能或模块式的编码。而是给CSS加入程序式的语言特性，在CSS基础上引入了变量、mixin、运算记忆函数等功能。

**less变量**：@变量名: 值;

less变量命名规范，必须有@为前缀，不能包含特殊字符，不能以数字开头，大小写敏感。

**less嵌套**：

&直接解析为父元素。如果有伪类（a:hover等）、交集选择器、伪元素选择器。可在内层写&:hover。

**less运算**：

less可以直接运算，会转换为静态效果。如果单位不同，直接采用第一个运算值得单位。如果只有一个有单位，则采取该单位。**注意**：运算符需要空格隔开。

**less导入**：

@import "name";不需要后缀名。

### 其他：

order：n; 设置元素在同级元素上的位置，可以为负，数值越小越高前。默认是0，灵活性更高。CSS中@用法小结

[**at-rule**](https://blog.csdn.net/zcy_wxy/article/details/80652247)是一个声明，为CSS提供或执行一些规则。

### SEO优化（搜索引擎优化）

Logo里放一个h1标签，标签里放a标签链接首页，内容为网站名，作为网站标题，a标签设置一个title显示网站名称。美观体验标题可不显示亦可优化，对结构没有什么意义，但这是语义标签，对搜索引擎有提权作用。

**方法1**：缩进标题到月球，淘宝做法。

```css
text-indent: -9999px;
overflow: hidden;
```

**方法2**：

```
font-size: 0;
```
