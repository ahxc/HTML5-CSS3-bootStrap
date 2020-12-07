### html基本信息

```html
<!DOCTYPE html>文档类型声明标签，不是html标签，使用哪种html版本，这里html5
<html lang="zh-CN">语言种类
<meta charset="UTF-8">字符集，重要，utf-8万国码，基本包含了大多国家需要的字符编码规则
```

### 基本结构标签

```html
<html></html>
<head></head>
<text></text>
<body></body>
```

### 语义标签

```html
<h1>标题标签</h1>
<p>段落标签</p><br/>换行标签break
<strong>加粗</strong><b>加粗</b>
<em>倾斜</em><i>倾斜</i>
<del>删除线</del><s>删除线</s>
<ins>下划线</ins><u>下划线</u>
```

### 无语义盒子标签

```html
<div></div>
<span></span>
```

### 图片

```html
<img src="我是必须的" alt="图片显示不出来我出现" title="指针放上去我出现">
```

### 链接

target：目标弹出方式，\_self默认值，_blank新窗口

href：可以是内部链接，外部链接，空连接#，下载链接地址是文件，网页元素链接

锚点链接，文档内部的链接

```html
<a id="zx" href="" target=""></a>
<a href="#zx"></a>
```

### 表格

```html
<table>
    <thead><!-- 表头整体 -->
        <tr>
            <th>表头单元</th>
        	<th>表头单元</th>
        	<th>表头单元</th>
      	</tr>
    </thead>
    <tbody><!-- 表格主体 -->
      	<tr><!-- 行 -->
        	<td colspan="2">单元格</td><!-- colspan列单元合并（横），不是真合并，只是的单元格尺寸变化 -->
        	<td rowspan="2">单元格</td><!-- 行合并 -->
        	<td>单元格</td>
      	</tr>
    </tbody>
</table>
```

### 无序列表（重点）

```html
<ul>
    <li>1</li>
    <li>1</li>
    <li>1</li>
</ul>
```

### 自定义列表

```html
<dl><!-- 表体，结构固定 -->
    <dt>关于</dt><!-- 标题 -->
    <dd>线下</dd><!-- 单元 -->
    <dd>线上</dd>
    <dd>联系我们</dd>
</dl>
```

### 有序列表

```
<ol>
    <li></li>
    <li></li>
    <li></li>
</ol>
```

### 表单（重点）

什么是表单：收集用户信息，由表单域，表单控件（元素），提示信息组成

**1.表单域**

```html
<form action="url地址" method="提交方式get/post" name="表单名"></form>
```

**2.表单元素**

第一大类：input输入表单

```html
<input type="text" value="input的值" placeholder="占位" maxlength="正整数，较少使用"> //文本框
<input type="button"> //按钮
<input type="checkbox" name="必须相同形成作用域" checked="true"> //复选框
<input type="file"> //选择文件
<input type="hidden"> //隐藏的输入字段
<input type="image"> //图片
<input type="password"> //密码
<input type="radio" name="必须相同形成作用域"> //单选框
<input type="reset"> //重置表单到默认状态
<input type="submit" value="提交"> //提交表单
表单标签，用于绑定一个元素id，点击标签能聚焦绑定的元素
<label for="binput"">男</label><input id="binput" type="text">
```

第二大类：select下拉表单

```html
<select name="" id="">
    <option value="">选项</option>
    <option value="">选项</option>
    <option value="" selected="selected">选项</option>默认选中
</select>
```

第三大类：textarea文本域

```html
<textarea name="" id="" cols="30" rows="10"></textarea>行列
```

