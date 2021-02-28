# 1、CSS基本信息



## 1.1、CSS概览

cascading Style Sheet 层叠样式表

主要作用是修饰html结构 (美化网页)

字体、颜色、边距、高度、背景图片、浮动、定位





## 1.2、CSS发展史

> CSS1.0	基本html修饰
>
> CSS2.0	DIV(块) + CSS	首次拥有html与css结构分离的思想
>
> CSS2.1	浮动、定位
>
> CSS3.0	圆角边框、阴影、动画	浏览器兼容性





## 1.3、语法基本结构

```css
<!--
语法:
	选择器 {
    	声明;
	}
-->

h1{
    color: red;
}

```





## 1.4、css导入方法

1. style标签中书写css的代码 (不建议与html与css合一)   又称为内部样式表
2. 使用link标签或者import **(建议使用这种规范)**    又称为外部样式表

> 使用css与html分离的优势：
>
> 利用SEO，容易被搜索引擎收录
>
> 网页结构表现统一的，可以实现复用

```html
<!--CSS3.0 与html结构同时渲染加载的方式-->
<link rel="stylesheet" href="css/style.css">
```

```html
<!--CSS2.1 比较大的网页会先展现出html结构再渲染出css 但link标签不会-->
<style>
    @import url("css/style.css");
</style>
```



3. 在标签元素中编写一个style属性编辑属性即可(不建议使用 严重与规范脱节)	又称为行内样式表

**关于导入的样式表的优先级：就近原则(离元素最近的优先级最高)**





# 2、选择器

作用是为css修饰划分作用域

## 2.1、基本选择器

1. 标签选择器

   选择页面上的所有同标签的元素

   ```css
   h1{
       color: black;
   }
   ```

2. 类选择器

   选择自定义的同类标签元素，可以复用

   ```html
   <style>
       .test{
           color: yellow;
       }
   </style>
   
   <h1 class="test">Title</h1>
   <p class="test">paragraph</p>
   ```

3. id选择器

   选择定义的同id标签元素，但是唯一

   ```html
   <style>
       #test{
           color: red;
       }
   </style>
   
   <h1 id="test">Title</h1>
   ```

**选择器的优先级为：id>类>标签**





## 2.2、层次选择器

1. 后代选择器

   某个元素的所有下级含p段落的所有元素

   ```css
   body p{
       background: yellow;
   }
   ```

2. 子类选择器

   选择只在body的下级第一代含p段落的元素

   ```css
   body > p{
       background: green;
   }
   ```

3. 相邻选择器

   选择在指定元素之下相邻的含p段落的元素（牛子选择器？？）

   ```html
   <style>
   	.test + p{
       	background: red;
   	}
   </style>
   
   <p class="test">p1</p>
   <p>p2</p>
   ```

4. 通用选择器

   凡是在指定元素之下所有的含p段落的元素

   ```html
   <style>
   	.test ~ p{
       	background: #ffffff;
   	}
   </style>
   
   <p class="test">p1</p>
   <p>p2</p>
   <p>p3</p>
   ```





## 2.3、结构伪类选择器

> 结构伪类选择器，可以根据元素在文档中所处的位置，来动态的选择元素，从而减少html文档对id或者类选择器的依赖，有助于保持代码干净整洁。

1. E:first-child

   这指的是父元素的第一个子元素E

   ```css
   E:first-child{
       color: #ffffff;
   }
   ```

   类似的还有E:last-child，他们分别等同于E:nth-child(1)和E:nth-last-child(1)

2. E:first-of-type

   这对应指的是父元素的第一个是E的元素

   对应的用法E:nth-of-type(1)





## 2.4、属性选择器

有点类似于正则表达式

```css
a[id=first]{
    background: yellow;
}
```

```css
a[class*="links"]{
    background: red;
}

a[href^=http]{
    background: green;
}
```

> 正则表达式中的通配符：
>
> =为绝对等于
>
> *=为包含
>
> ^=以这个开头
>
> $=以这个结尾





# 3、页面美化元素



## 3.1、包裹标签

1. span标签

   span用于包裹一段文字

2. div标签



## 3.2、字体设置

1. font-family

   字体样式

   ```css
   <!--可以使用多种样式 会根据所有语种自适应-->
   body{
       font-family:"Arial Black","楷体";
   }
   ```

2. font-size

   字体大小

3. font-wight

   字体粗细

4. color

   字体颜色

```css
body{
    font:oblique bold 10px/50px "楷体";
}
<!--
可以按顺序设置如下属性：
font-style
font-variant
font-weight
font-size/line-height
font-family

https://www.w3school.com.cn/css/pr_font_font.asp
-->
```





## 3.3、文本样式

1. 颜色

   单词表示

   RGB表示

   RGBA表示（拥有透明度设定）

   ```css
   /*单词表示*/
   color: red;
   /*RGB表示*/
   color: #00ff00;
   color: rgb(0,255,0);
   /*RGBA表示*/
   color: rgba(0,255,0,0.5);
   ```

2. 文本对齐方式

   text-align :

   插入图片等情况时按水平居中

   ```css
   img,span{
       vertical-align: middle;
   }
   ```

3. 首行缩进

   text-indent :

   一般用em表示，但用px单位缩进也可

4. 行高

   line-height :

   设置字体占高，与块高度相同时可以达到居中

5. 装饰

   text-decoration :

   underline 下划线

   line-through 中划线

   overline 上划线

   ```css
   /*a超链接去下划线*/
   a {
       text-decoration: none;
   }
   ```





## 3.4、文本阴影和超链接伪类

超链接伪类（实测除超链接以外也可以应用）

1. hover 鼠标悬停的状态
2. active 鼠标按住未释放的状态
3. link 未经访问的链接
4. visited 已经访问的链接

example:

```css
a:hover{
    color:red;
    //鼠标悬停时变成红色
}
```



文本阴影

```css
a:hover{
    text-shadow: #000000 10px 10px 10px;
    //阴影颜色 水平偏移 垂直偏移 阴影半径
}
```





## 3.5、背景图片应用和渐变

背景图片（在css中的）

```css
div{
    width: 1000px;
    height: 700px;
    border: 1px solid red;
    background-image: url("img/iamqwq.jpg");
}
```

重复：

1. 横向平铺

   ```css
   background-repeat:repeat-x;
   ```

2. 纵向平铺

   ```css
   background-repeat:repeat-y;
   ```

3. 不重复

   ```css
   background-repeat:no-repeat;
   ```



渐变

```css
div{
    linear-gradient();
    //没有深入研究
}
```



background格式简写

```css
.list{
    background:red url("#") 270px 10px no-repeat;
    //颜色 图片资源位置 图片布局位置 重复方式
}
```





# 4、盒子模型



## 4.1、结构概述

1. margin 外边距
2. padding 内边距
3. border 边框





## 4.2、内外边距

内外边距都有四个属性

```css
margin-top: 0;
margin-bottom: 0;
margin-left: 0;
margin-right: 0;
//有大小时需要单位

margin:0 1px;
//两个参数时 第一个参数是表示上下 第二个参数表示左右

margin:0 0 0 0;
//上下左右

//padding同用法
```

可以用他的特性实现一些奇妙的东西

```css
margin:0 auto
//上下0 左右自动对齐（居中）
```





## 4.3、边框

### border基本格式

```css
div{
    border:1px solid red;
    //粗细 样式 颜色
    //常用样式 实线solid 虚线dashed
}
```



### 圆角边框

```css
border-radius: 0px;
//大小是半径

border-radius: 10px 20px;
//也可以这么写 对应的顺序是10px左上右下 20px右上左下
```





# 5、元素修饰和浮动



## 5.1、行内元素和块级元素

块级元素独占一行

```css
h1-h6 p div ul li table...
```

行内元素则可以并排

```css
span a img strong...
```

行内元素可以被包含在块级元素中，但反之则不行



## 5.2、display

display用于修饰元素改变元素的存在模式

1. block 块元素
2. inline 行内元素
3. inline-block 行内块元素，是块元素但可以内联，可以并排