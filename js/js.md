# 1、JavaScript基本信息



## 1.1、JS概览

javascript是世界上最流行的脚本语言，他是一门弱类型的解释型编程语言

而且框架都是基于jsp构建的：

> jQuery
>
> Angular
>
> React
>
> Vue
>
> Axios

UI框架：

> Ant-Desgin
>
> Element-UI、iview、ice
>
> Bootstrap
>
> amaze-UI



## 1.2、JS的发展

[传送门](https://blog.csdn.net/kese7952/article/details/79357868)

> "1994年，网景公司（Netscape）发布了Navigator浏览器0.9版。这是历史上第一个比较成熟的网络浏览器，轰动一时。但是，这个版本的浏览器只能用来浏览，不具备与访问者互动的能力。......网景公司急需一种网页脚本语言，使得浏览器可以与网页互动。"

> 就在这时，发生了另外一件大事：1995年Sun公司将Oak语言改名为Java，正式向市场推出。
>
> Sun公司大肆宣传，许诺这种语言可以"一次编写，到处运行"（Write Once, Run Anywhere），它看上去很可能成为未来的主宰。
>
> 网景公司动了心，决定与Sun公司结成联盟。它不仅允许Java程序以applet（小程序）的形式，直接在浏览器中运行；甚至还考虑直接将Java作为脚本语言嵌入网页，只是因为这样会使HTML网页过于复杂，后来才不得不放弃。
>
> 总之，当时的形势就是，网景公司的整个管理层，都是Java语言的信徒，Sun公司完全介入网页脚本语言的决策。因此，Javascript后来就是网景和Sun两家公司一起携手推向市场的，这种语言被命名为"Java+script"并不是偶然的。

ECMAscript是javascript的一个标准

现在已经发展到了6版本（es6），但现在普遍浏览器都只停留在支持es5上，这会造成一个问题：开发环境和线上环境不一致



## 1.3、导入方式

1. 可以直接在html中嵌入<script></script>标签

   ```html
   <script>
   	alert('hello_world');
   </script>
   ```

2. 按url导入

   ```html
   <script src="url/js.js"></script>
   ```

备注

1. js可以在head和body中使用
2. script标签不能使用自闭合写法





# 2、javascript中的数据和规范



## 2.1、数据类型



### 2.1.0、作用域和常量

1. let 局部，只作用在当前代码块，一般使用他，比较安全
2. var 全局

const 常量



### 2.1.1、Number

js中不区分整数和小数，以下

```javascript
111 //整数
111.11 //小数
1.11e3 //科学记数法
-99 //复数
NaN //非数
Infinity //无限数
```



### 2.1.2、String

#### 2.1.2.1、String定义

三种写法，正常字符使用单引号和双引号包裹，``中可以写多行字符

```javascript
'string'
"string"
`
iamqwq
咸鱼
巨兽
`
```

#### 2.1.2.2、转义

转义使用字符 \

```javascript
console.log('他说:\"我裂开了\"');
```

> \\'
>
> \n
>
> \t
>
> \u4e2d \u####	unicode字符
>
> \x41						ascii字符

#### 2.1.2.3、模板字符串

```javascript
let msg = `hello,${name}`;
```

#### 2.1.2.4、String类型常用的方法和属性

```javascript
let example = 'this is a example';

example.length //字符串长度
example.toUpperCase() //转换为大写
example.toLowerCase() //反之
example.indexOf('i') //获取字符在字符串最先出现的位置

example.substring(subNum) //根据下标截取字符串，如果参数只有一个，则默认截取到最后
example.substring[first,last) //包含第一个下标的写法

student[0] //按下标输出字符串中的字符

```





### 2.1.3、Boolean

```javascript
true
false
```

```javascript
&& //逻辑与
|| //逻辑或
! //逻辑非
```

```javascript
= //赋值
== //等于 但类型不一样值一样也会判断为true
=== //绝对等于
```

一般情况比较时使用绝对等于

注意：

1. NaN六亲不认，NaN与所有数字进行相同比较都是false，包括NaN自己

   只能使用isNaN(NaN)来判断

2. 避免使用浮点数进行运算，存在精度问题，以下

   ```javascript
   console.log((1/3)===(1-2/3))
   ```



### 2.1.4、Null和Undefined

> null：主动释放一个变量引用的对象，表示一个变量不再指向任何对象地址
>
> undefined：是所有没有赋值变量的默认值，自动赋值



### 2.1.5、Array

js的数组可以由任意类型的数据组成

```javascript
var arr = ['a',1,290.1,null,true];
```

```js
let arr = [[1,2],["3","4"]];
```

js的数组大小是可变的，给数组的length赋值就会改变数组大小，且如果赋值过小，元素就会丢失

#### 2.1.5.1、数组常用方法

```js
arr.length //长度
arr.indexOf(元素) //通过元素获得下标索引
arr.slice(下标) //截取arr的一部分 返回新数组
arr.push(元素) //添加元素
arr.pop() //弹出最后一个元素 每弹一次则删除一次最后的元素
arr.unshift() //在头部添加元素
arr.shift() //弹出最后一个 用法相近于pop
arr.sort() //元素排序
arr.reverse() //元素反转（倒序）
arr.concat() //追加元素（不改变原数组 只返回一个追加元素的数组）
arr.join(字符) //打印拼接数组，使用特定的字符串拼接
```



### 2.1.6、Object

js的Object是对象

```javascript
var iamqwq = {
    cnName = ['萌新','咸鱼','巨兽'];
    age = NaN;
}
```

取值的话

```javascript
console.log(iamqwq.cnName[0]);
> '萌新'
```





## 2.2、对象

### 2.2.1、定义

若干个键值对

```js
var person = {
    name : "iamqwq",
    age : "100",
    email : "unknown"
}
```

js对象，大括号表示方法体，用 : 描述属性的值，两个属性之间使用逗号隔开，最后的属性不需加逗号

js当中属性名都为字符串，而值则为任意类型

```js
person["age"]
> 100
"age" in person
> true
```



### 2.2.2、对象操作

#### 2.2.2.1、赋值

```js
person.name = "qwqmai";
```

使用不存在的对象属性会报undefined

#### 2.2.2.2、动态删减属性

且js当中**对象可以动态的删减属性**

```js
delete person.name;
true
```

成功则会返回一个true

#### 2.2.2.3、判断属性是否在对象中

```js
"age" in person
> true
"toString" in person
> true
```

如果是则会返回一个true，这里注意，父类的方法也会判断为正确

#### 2.2.2.4、判断是否是自身对象拥有的方法/对象

```js
person.hasOwnProperty("age")
> true
```



## 2.3、严格检查模式

在script下直接添加

```javascript
'let strict'
```

这可以避免因js过于松散的语法结构导致的各种问题



# 3、流程控制

#### 3.1、forEach

```js
arr.forEach(function(e){
    console.log(e);
})
```

