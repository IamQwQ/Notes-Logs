selenium包是化学元素硒的意思，用于制作电气设备和有色玻璃，人体缺少这种元素会导致抑郁

蛋，谁又能想到这是个web自动化工具的名字..

### 关于selenium

> Selenium是一个用于Web应用程序测试的工具。Selenium测试直接运行在浏览器中，就像真正的用户在操作一样。支持的浏览器包括IE（7, 8, 9, 10, 11），Mozilla Firefox，Safari，Google Chrome，Opera，Edge等。这个工具的主要功能包括：测试与浏览器的兼容性——测试你的应用程序看是否能够很好得工作在不同浏览器和操作系统之上。测试系统功能——创建回归测试检验软件功能和用户需求。支持自动录制动作和自动生成 .Net、Java、Perl等不同语言的测试脚本。

他的作用是为了自动化进行浏览器操作，而与其他测试工具相比较，他的一大优点是，selenium会模仿用户的操作，而且他兼容了许多的浏览器

虽然他的开发最终目的是用于测试，但既然有着自动化操作的特性，就可以单独拎出来写些工具玩

由于是写桌面应用的时候仓促学的，所以没有研究那么深，详细教程请参考文章下方附录的参考资料3

![快乐](C:\Users\HP2020\Desktop\快码阿 怎么不码了\img\img packet\快乐.png)



### 前置准备

既然使用selenium包，那么需要先下载selenium：[传送门](https://www.selenium.dev/downloads/)

需要说的是，这里需要安装的是server版，底下虽然有client版，还细分了各种语言的包，但正如他简介所写的一样：

> The Selenium Server is needed in order to run Remote Selenium WebDriver (Grid)
>
> 为了远程运行selenium浏览器驱动器，你需要selenium server

但需要也仅限于selenium server，实测发现导包并没有用到selenium client里的一堆东西    :D

原理也没有深究，应该是有别的用途     :D

并且selenium在3.X版本以上就不再支持直接打开了，需要安装对应浏览器的驱动：[科学上网传送门](https://www.baidu.com/)



### 开始实验

1. 首先需要设置浏览器驱动：

   此处使用方法`System.setProperty(String prop,String value);`这个方法用于设置键值对的系统属性 (直接拿来复制解释了，没有深入研究)

   ```java
   System.setProperty("Webdriver.chrome.driver","路径");
   ```

   `webdriver.xxx.driver`中间的名字主要取决于驱动器的名字，例如火狐浏览器的名字为geckodriver，在这里则填写`webdriver.gecko.driver`

2. 创建浏览器对象

   ```java
   WebDriver chromeDriver = new ChromeDriver;
   ```

3. 打开网页

   只要调用对应WebDriver下的get方法传入地址参数即可：

   ```java
   chromeDriver.get("https://www.baidu.com/");
   ```
   
4. 选中页面元素

   这个问题稍微熟悉html的都很好解决，selenium提供了很多种查找的方法：

   ```java
   findElement(By.id())
   findElement(By.name())
   findElement(By.className())
   findElement(By.tagName())
   findElement(By.linkText())
   findElement(By.partialLinkText())
   findElement(By.xpath())
   findElement(By.cssSelector())
   ```

   举个栗子：在百度搜索页找到输入元素并进行键入关键字操作

   打开审查元素可以对应找到html语句：

   ```html
   <input id="kw" name="wd" class="s_ipt" value maxlenth="255" autocomplete="off">
   ```

   所以对应使用id获取元素的语句就是：

   ```java
   chromeDriver.findElement(By.id("kw"));
   ```

5. 对元素进行操作

   ```java
   clear()
   sendKeys(value)
   click()
   ```

   sendKeys可以对输入框传入内容

   clear则是清除输入框内容

   click方法可以对元素进行点击

   ```java
   submit()
   ```

   submit可以进行表单的提交

   > 例如，在搜索框输入关键字之后的“回车” 操作， 就可以通过 submit()方法模拟.

   ```java
   WebElement searchText = chromeDriver.findElement(By.id("kw"));
   searchText.sendKeys("Internet");
   searchText.submit();
   ```



### 实例

在csdn搜索关键字"人工智能"

```java
//设置系统变量键值对
System.setProperty("Webdriver.chrome.driver","路径");
//创建对象
WebDriver chromeDriver = new ChromeDriver();
//打开csdn首页
chromeDriver.get("https://www.csdn.net/");
//获取搜索栏元素并输入关键字
chromeDriver.findElement(By.id("toolbar-search-input")).sendKeys("人工智能");
//获取搜素按钮并点击
chromeDriver.findElement(By.id("toolbar-search-button")).click();
```





参考资料：

1. 百度百科 若干名词
2. 一点教程 《Java lang包》 http://www.yiidian.com/java-lang/java-system-setproperty.html
3. *CSDN 《详解介绍Selenium常用API的使用--Java语言（完整版）》 https://blog.csdn.net/qq_22003641/article/details/79137327

