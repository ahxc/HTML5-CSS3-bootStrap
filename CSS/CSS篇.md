### 伪类/选择器

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
    font-size: 36px;
    color: #ccc;
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

