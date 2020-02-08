# HTML+CSS笔记

## 文档结构

### 基本结构

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
  <!-- CSS的外部样式表 -->
  <link rel="stylesheet" type="text/css" href="./xx.css">
  <style>
  	@import "xx.css";
    @import url(xx.css);
  </style>
</head>
<body>

</body>
</html>
```

### 实体字符&amp;

实体字符大小写敏感。

| 实体字符   | 含义              |
| ---------- | ----------------- |
| &amp;amp;  | &                 |
| &amp;nbsp; | 空格              |
| &amp;lt;   | < less than       |
| &amp;gt;   | &gt; greater than |
| &amp;quot; | &quot;双引号      |



## &lt;标签>

### &lt;常用标签>

| <常用标签>     | 含义             | 常用属性                  |
| :------------- | ---------------- | ------------------------- |
| div            | 分区标签，无样式 |                           |
| p              | 段落标签，有样式 |                           |
| span           | 范围标签，无样式 |                           |
| br             | 换行             |                           |
| hr             | 水平线           | color、size、width、align |
| h1-h6          | 标题             |                           |
| img            | 图片             | src、alt、title           |
| ol/ul、li      | 有序/无序列表    | type                      |
| select、option | 下拉菜单         |                           |
| i、em          | italic、斜体     |                           |
| b、strong      | bold、强调加粗   |                           |
| del            | 删除线           |                           |
| ins            | 下划线           |                           |
| a              | 超链接           | herf、target、name        |
| iframe         | 内嵌框架         |                           |



### &lt;其他标签>

| <其他标签> | 含义           | 常用属性 |
| ---------- | -------------- | -------- |
| dl、dt、dd | 描述定义的列表 |          |
| pre        | 预格式化       |          |
| address    | 地址           |          |
| sup、sub   | 上标、下标     |          |
| small、big | 字号减小、增加 |          |

### 常用属性

| <标签>  | 属性名                               | 含义                           |
| ------- | ------------------------------------ | ------------------------------ |
| ol、li  | type = "1、a、A、i、I"               | 列表前的标记                   |
| ul、li  | type = "disc、circle、square、none"  | 实心圆、空心圆、正方形、不显示 |
| hr      | color = "red、#FF0000"               | 颜色                           |
| hr      | size = "10"                          | 粗细                           |
| hr      | width = "100px、80%""                | 宽度：绝对值、相对父容器百分比 |
| hr      | align = "center、left、right"        | 对齐                           |
| img     | src = "./xxx.jpg"                    | 来源                           |
| img     | alt = "图片加载失败"                 | 图片无法显示时的提示信息       |
| img     | title = "标题"                       | 鼠标停留时的提示               |
| bdo     | dir = "rtl"                          | 文本从右向左显示               |
| abbr    | tltle = "提示信息"                   | 停留在文字上时的提示           |
| a       | href = "http://baidu.com、../d.html" | 链接地址、路径                 |
| a、form | **target = "_self、blank"**          | 链接打开位置为自身、新标签页   |
| a       | name = "锚点名称"                    | href="#锚点名称"进行锚链       |
| option  | value = " "                          |                                |



### 锚链接、&lt;iframe>实例

```html
<!-- 锚链接 -->
<ol>
	<li><a href="#first">详细介绍</a></li>
</ol>	
<a name="first">详细介绍编辑</a>

<!-- 内嵌框架 -->
<iframe src="top.html" width="100%" height="200px" frameborder="no" scrolling="auto" name="nav">
	您的浏览器不支持iframe
</iframe>
```



### 头部&lt;meta>等标签

```html
<head>
	<!-- 设置字符编码 -->
	<meta charset="UTF-8">
	<!-- 设置关键字 -->
	<meta name="keywords" content="IT教育,Java开发">
	<!-- 设置作者 -->
	<meta name="author" content="汤小洋">
	<!-- 实现刷新跳转 -->
	 <meta http-equiv="refresh" content="2;url=http://www.baidu.com">
  
	<title>Document</title>
	
	<!-- 定义内部CSS样式 -->
	<style>
		body{
			color:red;
		}
	</style>

	<!-- 引用外部CSS样式文件 -->
	<link rel="stylesheet" href="CSS样式文件的路径">

	<!-- 定义或引用脚本 -->
	<script>
		alert("嘿嘿");
	</script>

	<!-- 定义基础路径 -->
  <!-- 默认以当前页面文件所在位置为相对路径的参照 -->
	<base href="images/">
</head>
```

## 表格

### &lt;表格标签>

| <标签名> | 含义       |
| -------- | ---------- |
| table    | 表格       |
| caption  | 标题       |
| thead    | 页眉       |
| tbody    | 表格主题   |
| tfoot    | 页眉       |
| tr       | 行         |
| th       | 表头单元格 |
| td       | 单元格     |

快速创建表格`table>(tr>td{hello$}*4)*4`

### 表格属性

| 属性                   | 含义                 |
| ---------------------- | -------------------- |
| border = "0"           | 边框                 |
| bordercolor = "red"    | 边框颜色             |
| bgcolor = "cyan"       | 背景颜色             |
| background = "./p.jpg" | 背景图片             |
| cellspacing = "0"      | 单元格与单元格的间距 |
| cellpadding = "0"      | 单元格与边界距离     |
| rowspan = "2"          | 单元格横跨的行数     |
| colspan = "4"          | 单元格横跨的列数     |

### 表格实例

```html
<table border="1" width="600px" height="300px" align="center" cellspacing="0">
  <caption><h2>学生信息表</h2></caption>
  <thead bgcolor="cyan">
    <tr>
      <th>学号</th>
      <th>姓名</th>
      <th>年龄</th>
      <th>性别</th>
    </tr>
  </thead>
  <tbody bgcolor="#cccccc">
    <tr>
      <td>1001</td>
      <td>唐伯虎</td>
      <td>25</td>
      <td>男</td>
    </tr>
    <tr>
      <td>1002</td>
      <td>秋香</td>
      <td>21</td>
      <td>女</td>
    </tr>
  </tbody>
  <tfoot bgcolor="yellow">
    <tr>
      <td width="25%">总计人数</td>
      <td colspan="3">5</td>
    </tr>
  </tfoot>
</table>
```



## 表单

### form标签的属性

| 属性                             | 含义                     |
| -------------------------------- | ------------------------ |
| autocomplete = "on、off"         | 自动完成之前输入过的内容 |
| novalidate                       | 提交时不进行校验         |
| action = "https://www.baidu.com" | 提交表单时向何处提交     |

```html
<input type="表单元素类型" name="名称" value="初始值" size="宽度">
```

### input表单元素类型 type="?"

| type="?"   | 含义                       | 包含属性            |
| ---------- | -------------------------- | ------------------- |
| text       | 单行文本框                 | name、value、size等 |
| password   | 密码框                     | 同text              |
| radio      | 单选按钮，几个中选一       | name、value         |
| checkbox   | 多选按钮                   | name、value         |
| **submit** | 提交按钮                   | value               |
| reset      | 重置按钮                   | value               |
| image      | 图像按钮                   | src                 |
| button     | 普通按钮                   | value               |
| file       | 文件选择器，选择上传的文件 | name、accept        |
| hidden     | 隐藏域，但会提交           |                     |

-   表单元素类型(H5新增)

| type="?"     | 含义           | 包含属性       |
| ------------ | -------------- | -------------- |
| email        | 邮箱           |                |
| url          | 接收url        |                |
| tel          | 电话号码       |                |
| search       | 搜索文本框     |                |
| number/range | 数字、数字滑块 | min、max、step |
| color        | 颜色拾取       |                |

### 常用属性

| 属性                 | 含义                                                |
| -------------------- | --------------------------------------------------- |
| name = "age"         | 名称，单选框的name必须相同；有name时才能提交        |
| id = " "             | label标签的for属性与input标签的id值相同             |
| value= "18"          | 初始值                                              |
| size= "10"           | 宽度                                                |
| maxlength = "6"      | text的最大字符数                                    |
| readonly             | text的只读                                          |
| disable              | text的禁用，不提交                                  |
| checked              | 是否选中                                            |
| accept = "text/html" | file的可选文件类型，MINE格式如text/html、image/jpeg |
| onclick = "Fn()"     | 点击时触发JavaScript函数                            |



-   表单元素属性(H5新增)

&lt;input>、&lt;select>、&lt;textarea>等的属性

| 属性                       | 含义                         |
| -------------------------- | ---------------------------- |
| **placeholder** = "请输入" | 提示文字                     |
| required                   | 是否必填                     |
| autocomplete = "on、off"   | 自动完成                     |
| pattern                    | 正则表达式，进行数据校验     |
| list                       | 使文本元素具有下拉列表功能   |
| form                       | 在<form>外的表单元素进行关联 |

-   &lt;list&gt;和form属性实例

```html
<form action="" id="myform">
	<label for="city">城市：</label>
  <input type="text" name="city" id="city" list="cityList">
  <datalist id="cityList">
    <option value="nanjing">南京</option>
    <option value="beijing">北京</option>
    <option value="shanghai">上海</option>
    <option value="guangdong">广东</option>
  </datalist>
</form>

<input type="submit" value="外部的提交按钮" form="myForm">
```



-   表单元素常用属性实例

```html
<form action="" method="get" enctype="multipart/form-data">
  用户名：<input type="text" name="username" value="tom" size="10" maxlength="6" readonly> <br>
  密码：<input type="password" name="password"> <br>
  年龄：<input type="text" name="age" disabled value="18"> <br>
  性别：<input type="radio" name="sex" value="male" checked> 
  <img src="images/male.gif" alt="">
  <input type="radio" name="sex" value="female"> 
  <img src="images/female.gif" alt="">
  <br>
  爱好：<input type="checkbox" name="hobby" value="eat" checked> 吃饭	  
  <input type="checkbox" name="hobby" value="sleep"> 睡觉
  <input type="checkbox" name="hobby" value="doudou"> 打豆豆 <br>
  <br>
  头像：<input type="file" name="head" accept="image/jpeg">	  <br>
  <input type="hidden" name="id" value="9527">

  <input type="submit" value="注  册">
  <input type="reset" value="重  置">
  <input type="image" src="images/submit.gif">
  <input type="image" src="images/reset.gif">
  <input type="button" value="普通按钮">
</form>
```

### &lt;其他表单标签>

| <标签名> | 含义               | 常用属性                       |
| -------- | ------------------ | ------------------------------ |
| select   | 下拉列表           | name = "city"                  |
| optgroup | 选项组             | label = "Jiangsu"              |
| option   | 列表选项           | value = "Nanjing" selected     |
| textarea | 多行文本框         | readonly                       |
| label    | 为表单元素提供标签 | for = "对应input的id值"        |
| button   | 按钮，与input类似  | type = "submit、reset、button" |
| fieldset | 对表单元素进行分组 |                                |
| legend   | 对分组添加标题     |                                |

-   实例

```html
<select name="city">
  <optgroup label="江苏">
    <option value="nanjing" selected>南京</option>
    <option value="yangzhou">扬州</option>
  </optgroup>
  <optgroup label="山东">
    <option value="qingdao">青岛</option>
    <option value="rizhao">日照</option>
  </optgroup>
</select>

<textarea name="intro" rows="10" cols="50" readonly>
  请遵守本网站的相关协议和国家的法规。。。。
</textarea>

<label for="name">用户名：</label> 
<input type="text" name="username" id="name">

<fieldset>
  <legend>院校信息</legend>
  学校：<input type="text" name="stuSchool"> <br>
  专业：<input type="text" name="stuMajor"> <br>
</fieldset>
```

## HTML5

### &lt;结构标签>

只表明角色，更好地语义化，无外观样式，与普通的div相同

| <标签名>   | 含义               |
| ---------- | ------------------ |
| article    | 文章               |
| section    | 章节、段落         |
| header     | 头部               |
| footer     | 底部               |
| aside      | 侧边栏             |
| figure     | 图片区域           |
| figcaption | 在figure内用作标题 |
| nav        | 导航               |

### &lt;语义相关标签>

| <标签名>        | 含义                              |
| --------------- | --------------------------------- |
| mark            | 标注，添加黄色背景                |
| time            | 日期和时间，便于搜索引擎查找      |
| summary、detail | 默认显示summary，点击后显示detail |
| meter           | 计数器                            |
| progress        | 进度条                            |

#### 实例

```html
我在<time datetime="2019-2-14">情人节</time>有个约会。

<details>
  <summary>HTML简介</summary>
  <p>HTML是一门用来制作网页的标签语言</p>
</details>

<meter max="100" min="1" value="70" high="60" low="20" optimum="50"></meter>

<progress value="40" max="50"></progress>
```

### &lt;多媒体标签>

#### &lt;audio&gt;

| 常用属性                         | 含义                       |
| -------------------------------- | -------------------------- |
| src = ""                         | 来源，可以指定多个音频文件 |
| controls                         | 显示控制面板               |
| autoplay                         | 自动播放                   |
| loop                             | 循环播放                   |
| muted                            | 静音                       |
| preload = "none、auto、metadata" | 预加载，若autoplay则无意义 |

#### &lt;video&gt;

| 属性         | 含义                   |
| ------------ | ---------------------- |
| width/height | 视频播放器的尺寸       |
| poster       | 在视频加载前显示的图片 |



# CSS笔记

## 应用方式

| 应用方式         | 含义                                 |
| ---------------- | ------------------------------------ |
| 内部（内嵌）样式 | <head>内通过<style>定义              |
| 行内（嵌入）样式 | 使用标签的style属性                  |
| 外部样式         | 使用<link>或在style标签内@inport导入 |



## 选择器

| 选择器类型             | 使用方法                                                | 含义                             |
| ---------------------- | ------------------------------------------------------- | -------------------------------- |
| 标签（元素）选择器     | p{color:red;}                                           | 以标签名作为选择器名称           |
| 类选择器               | .aaa{font-size:10px;}                                   | 以.class属性为选择器             |
| ID选择器               | #bbb{color:blue;}                                       | 以#ID属性值为名称                |
| 复合选择器             | h1.aaa{}、p#bbb{}                                       |                                  |
| 组合选择器（集体声明） | h1,p,.ccc{}                                             | 用逗号隔开                       |
| 嵌套选择器             | dip p{}                                                 | 用空格隔开，有层次关系           |
| 伪类选择器             | a:link{}、a:visited{}、a:hover{}、a:active{}            | 多用于<a>标签，                  |
| 伪元素选择器           | p:first-letter{}、p:first-line{}、p:before{}、p:after{} | before和after需要配合content使用 |

### 选择器优先级

-   行内样式>ID选择器>类选择器>标签选择器
-   同优先级时，后加载的覆盖先加载的
-   使用**!important**使某个样式有最高优先级

## 常用CSS属性

### 字体属性

| 属性                                  | 含义                             |
| ------------------------------------- | -------------------------------- |
| font-style: normal, italic;           | 样式                             |
| font-weight: normal, bold;            | 粗细                             |
| font-size: inherit, 16px, 72.5%, 2em; | 大小                             |
| font-family: 黑体, 楷体, Arial;       | 字体                             |
| font: italic bold 20px Arial;         | 简写，必须按顺序，后两项不可省略 |

### 文本属性

| 文本属性                                                  | 含义             |
| --------------------------------------------------------- | ---------------- |
| color: red, #9032e6, rgb(0,255,0), rgba(0,255,0,0.7);     | 颜色             |
| line-height: 50px;                                        | 行之间的高度     |
| text-align: left, center, right;                          | 水平对齐方式     |
| vertical-align: left, center, right;                      | 垂直对齐方式     |
| text-indent: 60px;                                        | 首行缩进         |
| text-decoration: underline, overline, line-through, none; | 文本修饰         |
| text-transform: capitalize, lowercase, uppercase;         | 字母大小写       |
| letter-spacing: 3px;                                      | 字母间距         |
| word-spacing: 8px;                                        | 单词间距（英文） |
| white-space: nowrap;                                      | 文本超出后不换行 |
| overflow: hidden;                                         | 隐藏超出的内容   |

### 背景属性

| 背景属性                                                  | 含义               |
| --------------------------------------------------------- | ------------------ |
| background-color: transparent;                            | 背景颜色           |
| background-image: url(photo.gif);                         | 背景图片           |
| background-repeat: repeat, repeat-x, repeat-y, no-repeat; | 图片重复方式       |
| background-position: top, botton,center, left, (0,0);     | 图片位置，原点左上 |
| background-attachment: scroll, fixed;                     | 图片跟随滚动       |
| background                                                | 简写，无顺序要求   |

### 列表属性

| 列表属性                                             | 含义             |
| ---------------------------------------------------- | ---------------- |
| list-style-type: none, disc, circle, square, decimal | 列表前的标记     |
| list-style-image: url(xxx.png)                       | 图片作为标记     |
| list-style-position: outside, inside;                | 标记的位置       |
| list-style                                           | 简写，无顺序要求 |

### 表格属性

| 表格属性                             | 含义           |
| ------------------------------------ | -------------- |
| border-collapse: seperate, collapse; | 相邻的边框合并 |
| border-spacing: 0;                   | 间距           |
| border: 1px solid #ccc;              | 边框           |
| padding                              | 单元格的内边距 |

## 盒子模型

### 盒子模型的属性

| 属性           | 含义   | 解释                     |
| -------------- | ------ | ------------------------ |
| width          | 宽     | 只有尺寸                 |
| height         | 高     | 只有尺寸                 |
| padding        | 内边距 | 有方向                   |
| border         | 边框   | 有方向、颜色、粗细、样式 |
| maigin:0 auto; | 外边距 | 有方向                   |



### border的属性

| border属性                                                 | 含义 |
| ---------------------------------------------------------- | ---- |
| border-top, right, bottom, left                            | 方向 |
| border-width: 2px 4px;                                     | 粗细 |
| border-style:solid, dashed, dotted, double, inset, outset; | 样式 |
| border-color                                               | 颜色 |
| border: width style color;                                 | 简写 |



## 定位方式

| 定位方式            | 含义                                                   |
| ------------------- | ------------------------------------------------------ |
| position: static;   | 默认值，常规文档流显示                                 |
| position: relative; | 相对定位，相对于标签原来的位置                         |
| position: absolute; | 绝对定位，相对于第一个非static的父标签，元素浮在页面上 |
| position: fixed;    | 固定定位，相对于浏览器窗口，元素浮在页面上             |
| top: 50px;          | 设置偏移量：top、right、bottom、left                   |
| z-index: 0, -3;     | 设置优先级，控制堆叠方式，只能给非static设置           |

## 浮动及其他CSS属性

| 属性                                              | 含义                                                         |
| ------------------------------------------------- | ------------------------------------------------------------ |
| float: left;                                      | 浮动，在同一行显示                                           |
| clear: left, both;                                | 设置元素的某一侧不允许浮动元素                               |
| display: none, inline, block, inline-block;       | 设置元素不显示（不保留位置）、行级元素（不独占一行）、块级元素、行级元素（可设置宽高） |
| visibility: visiable, hidden;                     | 显示、隐藏（保留位置）                                       |
| outline                                           | 在border外围的轮廓，不影响元素的尺寸和位置，获得焦点时显示。有width、color、style或者简写的方式可设置 |
| overflow: visiable, hidden, scroll, auto;         | 元素内容溢出时的处理                                         |
| cursor: default, pointer, move, text, wait, help; | 光标形状                                                     |

























