---
title: javaweb
comments: true
toc: true
date: 2022-11-08 15:16:15
categories:
  - 学习笔记
  - 编程
tags: 编程
pic:
---

# javaWeb

本笔记基于[黑马程序员javaWEB教程](https://www.bilibili.com/video/BV1Qf4y1T7Hx/?spm_id_from=333.999.0.0&vd_source=efe00a256df0c8684bad9315b59f2f1a)

视频参考请进入上述链接

# 前端部分

简单了解

## HTML

html是解释型的超文本标记语言，不区分大小写

html是运行在浏览器上的,是由浏览器解析的

**基础语法**:里面的标签大多都是成对出现的

```
<html>
<tittle></tittle>
<body>
</body>
</html>
```



过于简单，略

各组件标签等信息去直接去看文档



## css

css最基本的分类：标签式样式表、id样式表

css从位置上的分类：嵌入式样式表，内部样式表，外部样式表

### 简单使用

1. 在html标签内使用

   ```html
   <div style="border: 1px solid black;width: 100px; height: 100px;">&nbsp;</div>
   ```

2. 在<head>标签内设置

   对当前页面有效

   ```html
   <head>
       <meta charset="UTF-8">
       <title>Title</title>
       <style type="text/css">
           .one {
               border: 1px solid black;
               width: 100px;
               height: 100px;
               background-color: lightgreen;
               margin-top: 5px;
           }
       </style>
   </head>
   <body>
   
       <div style="border: 1px solid black;width: 100px; height: 100px;">&nbsp;</div>
   
       <div class="one">&nbsp;</div>
       <div class="one">&nbsp;</div>
       <div class="one">&nbsp;</div>
   
   </body>
   ```

3. 引入外部css样式文件

   1. 创建css文件(xxx.css)

   2. 编辑css文件

   3. 在html内引入外部css文件路径

      ```css
      <link rel="stylesheet" type="text/css" href="/aaa/pro01-HTML/style/example.css" />
      ```

### css选择器

（前四个常用）

* 类型

  这个选择器是指向了所有的html的\<h1>元素

  ```css
  h1{}
  ```

* 类

  包含了class的选择器

  ```html
  <div class="box"></div>
  <div class="box"></div>
  ```

  ```css
  .box
  ```

* id

  ```css
  #xxx{}
  ```

  



## js

### 介绍

简介：JavaScript是一门弱类型的语言，不同于java，c等语言先编译后执行，js不会产生编译出来的字节码文件，而是程序的运行过程中对源文件逐行进行解释。

​	js也可以创建对象，也能够使用现有的对象，面向对象的三大特性：『封装』『继承』『多态』，js能够实现封装，可以模拟多态，不支持多态，所以js不是一门面向对象的语言。

​	js也有明确的数据类型，但是声明一个变量后它可以接受任何数据类型，并且 会在程序执行过程中根据上下文自动转换

​	JavaScript是一种采用事件驱动的脚本语言，它不需要经过Web服务器就可以对用户的输入做出响应。

​	JavaScript脚本语言不依赖于操作系统，仅需要浏览器的支持。因此一个JavaScript脚本在编写后可以带到任意机器上使用，前提是机器上的浏览器支持JavaScript脚本语言。目前JavaScript已被大多数的浏览器所支持

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<!--定义一个按钮，设置id-->
<button type="button" id="b">test</button>

</body>

<script type="text/javascript">
<!--    获取按钮的id，并定义一个类型接收-->
 //document对象代表整个html文档
 //document对象调用getElementById（）方法获取id
 var btnelementById = document.getElementById("b");
    //给按钮的元素对象绑定单击响应函数
    btnelementById.onclick = function () {
        //弹窗警告
        alert("demo");
    };
</script>
</html>
```

### 书写语法

> 1. 区分大小写:与java一样,变量名、函数名以及其他一切东西都区分大小写
> 2. 每行结尾的分号可有可无
> 3. 注释
>    * 单行注释：// 注释内容
>    * 多行注释：/\*注释内容\*/
> 4. 大括号表示代码块

### JavaScript嵌入方式

#### 1、HTML文档内

* JavaScript代码要卸载script标签内

* script标签可以卸载文档的任意位置

* 为了方便查询和使用，script标签可以写在body标签后

  ```html
  <script type="text/javascript">
  	document.getElementById("xxx").onclick=function(){
  		alter("hello word");
  		};
  </script>
  ```

#### 2、引入外部JavaScript文档

在script标签内通过src属性指定外部xxx.js文件的路径即可

注意：

* 引用外部JavaScript文件的script标签不能写JavaScript代码

* 先引入，再使用

* script标签不能写成单标签

  ```html
  <html>
  ...
    <body></body>
  <!-- 使用script标签的src属性引用外部的JavaScript文件，和java中的import语句类似-->
   <!-- 引用外部JavaScript文件的script标签不能写JavaScript代码-->
    <!--引用外部的JavaScript文件的script标签不能改成单标签 -->
    <!-- 外部JavaScript文件一定要先引入再使用 -->
  <script src:"xxx/script/xxx.js" type="text/javascript"></script>
    
    
    <script type="text/javascript">
                  
    	//调用外部JavaScript文件中的声明方法
      showMessage();                
    </script>
  </html>
  ```

### JavaScript声明和变量

* 基本数据类型

  * 数值型:js不区分整数，小数

  * 字符串：js不区分字符，字符串；单引号，双引号意思一样

  * 布尔型：true，false

    在JavaScript中，其他类型和布尔类型自动转换。

    true：非零的数值，非空字符，非空对象

    false：零，空字符串，null，undefined

    例如"false放在if判断里"

    ```javascript
    //"false"是一个非空字符串，直接放在if判断中会被当做『真』处理
    if("false"){
    	alter("true");
    	}else{
    	alter("fasle");
    	}
    ```

* 引用类型

  * 所有new出来的对象
  * 用[]声明的数组
  * 用{}声明的对象

* 变量

  * 关键字：var

  * 数据类型：JavaScript变量可以接收任意类型的数据

  * 标识符：严格区分大小写

  * 变量的使用规则：

    * 如果一个没有声明的变量，那么会在运行的时候报错

      `uncaught referenceError: b is not defined`

    * 如果声明一个变量没有初始化，那么这个变量的值就是`undefined`

  * 变量的数据类型由后面赋的值决定

* 使用typeof运算符可以获取数据类型

  ```
  alert(typeof xxx);
  ```

符号`==和===`的区别

> ==
>
> 1. 判断是否一样,如果不一样,则进行类型转换
> 2. 再去比较值
>
> ===
>
> 1. 判断是否一样,如果类型不一样,则直接返回false
> 2. 再去比较其值
>
> 会不会类型转换的区别



### 作用域

>  var: 
>
> * 全局变量
> * 可以重复声明
> * 可以存放不同类型的值
>
> let:
>
> * 相对于var来说,只在所在的代码块有效
> * 不允许重复声明
>
> const:
>
> * 用来声明一个只读的常量,
> * 一旦声明,常量的值就不能改变





### 函数

#### 1、内置函数

系统已经声明好的可以直接使用的函数

1. 单出警告框

   ```javascript
   alter("hello word");
   ```

2. 弹出确认框

   用户点击『确认』返回true，点击『取消』返回false

   ```javascript
   //console.log 控制台输出日志{f12 进去找到浏览器控制台)
   
   var result = confirm("老板，加个钟？");
   if(result){
   	console.log("加钟");
   	}else{
   	console.log("不加");
   	}
   	
   ```

   ![image-20221102100343216](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20221102100343216.png)

#### 2、声明函数

写法1

```javascript
function sum(a,b){
 return a+b;
 }
```

写法2

```javascript
var total = function(){
 return a+b;
 };
```

写法2可以解读：声明一个函数，相当于创建了一个『函数对象』，将整个对象的『引用』赋值给变量total。最后加的（;）分号不是给函数声明加的，而是给整体赋值语句加的

#### 3、调用函数

JavaScript中函数本身就是一种对象，函数名就是这个『对象』的『引用』。而调用函数的格式是：函数引用()

```javascript
function sum(a,b){
 return a+b;
 }
 
 var result = sum(2,3);
 console.log("result"+resule);
```

或

```js
var total = function(){ //应该给a,b初始化, function(a,b)不然会报错
	return a+b;
	};
	var totalresult = total(1,3);
	console.log("totalresult="+totalresult);

```

### 对象

JavaScript种没有『类』的概念，对于系统内置的

1. 使用new关键字创建对象

   ```js
   //创建对象
   var obj = new Object();
   //给对象设置属性和属性值
   obj.stuName="tom";
   obj.setAge=28;
   obj.stuSubject="java";
   
   //在控制台输出对象
   console.log(obj);
   ```

2. 使用{}创建对象

   ```js
   //创建对象
      var obj2={
               "obj2Name":"jack",
               "obj2Age":"12",
               "xxx":"222"
           };
           console.log(obj2)
   ```

3. 给对象设置函数属性

   ```js
   //创建对象
   var obj = new Object();
   //给对象设置属性和属性值
   obj.stuName="tom";
   obj.setAge=28;
   obj.stuSubject="java";
   obj.study=function (){
               console.log(this.stuName+"正在学习");
           }
   
   //在控制台输出对象
   console.log(obj);
   obj.study();
           
         
   ```

   或

   ```js
   var obj2={
               "obj2Name":"jack",
               "obj2Age":"12",
               "xxx":"222",
               "study":function (){
                   console.log(this.obj2Name+"正在拉屎");
               }
           };
           console.log(obj2)
           obj2.study();
   ```

**String对象**

trim()方法:`去除字符换前后的两端字符`



### this**关键字**

this关键字只有两种情况

* 在函数外边：this关键字指向window对象（代表当前窗口）
* 在函数里面：this关键字指向调用函数的对象

```js
//    在函数种的this
    function getname(){
        // console.log(this.name);
        console.log(this);
    }
//    创建对象
    var demo = {
        "name":"nn",
        "age":"12",
        "getname":getname

    };
    var demo2= {
     "name":"22",
     "age2":"12",
     "getname2":getname

    };
    demo.getname();
    demo2.getname2();

```

### 数组

> 分两个格式
>
> 方式一
>
> > var arr = new Array(1,2,3,);
>
> 方式二
>
> ​	var arr =[1,2,33]; 

1. 使用new关键字创建数组

   ```js
   console.log("--------------------数组--------------------");
   //创建数组对象
   var array = new Array();
   array.push("assple");
   array.push("orange");
   array.push("banana");
   array.push("grape");
   
   console.log("数组遍历-----------");
   //遍历数组
   for (var i = 0; i < array.length; i++) {
       console.log(array[i]);
   }
   
   console.log("数组元素反序-----------");
   array.reverse();
   for (let i = 0; i < array.length; i++) {
       console.log(array[i]);
   }
   
   console.log("数组元素拼接成字符串-----------");
   var s = array.join(".");
   console.log(s);
   
   console.log("字符串拆分成数组-----------");
   var strings = s.split(".");
   console.log(strings);
   for (let i = 0; i < strings.length; i++) {
       console.log(strings[i]);
   }
   
   
   console.log("弹出数组的最后一个元素-----------");
   var pop = array.pop();
   console.log(pop);
   
   ```

2. 使用<kbd>[]</kbd>创建数组

   ```js
   var array2 = ["zhangsan","lisi","wangwu"];
   console.log(array2);
   ```

### BOM

Browser Object Model 浏览器对象模型

javaScript将浏览器的各个组成部分封装为对象

组成

* window : 浏览器窗口对象

  > 直接使用window对象,其中window可以省略
  >
  > ``` js
  > window.alert("abc");
  > ```
  >
  > 属性:获取其他BOM对象
  >
  > * history : 对history对象的只读引用
  > * Navigator: 对Navigator对象的只读引用
  > * Screen: 对Screen对象的只读引用
  > * Location :  用于窗口的location对象
  >
  > 方法
  >
  > * `Alert() `警告框
  > * `Confirm()`带有确认和取消的警告框
  > * `setInterval()`在指定的周期(以毫秒计)来调用或计算表达式
  > * `setTimeout()`在指定的毫秒数后调用函数或计算表达式

* Navigator : 浏览器对象

* Screen : 屏幕对象

* History : 历史记录对象

* Location : 地址栏对象



### DOM

> DOM是w3c的标准
>
> DOM定义了访问HTML和XML文档的标准
>
> ![image-20221109155710042](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20221109155710042.png)



Document Object Model文档对象模型

![image-20221109155311523](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20221109155311523.png)

将标记语言的各个组成部分封装为对象

* document:整个文档对象
* Element ; 元素对象
* Attribute : 属性对象
* Text : 文本对虾干
* Comment : 注释对象

js可以通过DOM,对HTML进行操作

* 改变HTML元素内容
* 改变HTML元素的样式(css)
* 对HTML DOM事件作出反应
* 添加和删除HTML元素

获取**Element**

> 获取Element :元素对象
>
> 使用Document对象的方法来获取
>
> 1. getElementById : 根据id属性值来获取,返回一个Element对象
> 2. getElementByTagName : 根据标签名获取,返回Element对象数组
> 3. getElementByName: 根据name属性获取,返回Element对象数组
> 4. getElementByClassName : 根据class属性值获取,返回Element对象数组
>
> 具体对标签操作的属性和方法,[参考文档](https://www.w3school.com.cn/jsref/dom_obj_document.asp)
>
> 通用元素
>
> * style  :设置元素css样式
> * innerHTML : 设置元素内容

### 事件监听

> 事件:HTML事件就是发生在HTML元素上的"事情"
>
> 比如
>
> * 按钮被点击
> * 鼠标移动到元素上
> * 按下键盘按键
>
> JavaScript可以在事件被侦测到时<span style="color:red">执行代码</span>

> **事件绑定**
>
> 方式一: 通过HTML标签中的事件属性进行绑定
>
> ```
> <input type="button" onclick='on()'>
> 
> function on(){
> 	alert("我被点了");
> 	}
> ```
>
> 方式二 : 通过DOM元素属性绑定
>
> ```
> <input type="button" id="btn">
> 
> document.getElementById("btn").onclick = function(){
> alert("我被点了");
> }
> ```
>
> 推荐使用方式二

> [**常见事件**](https://www.w3school.com.cn/js/js_htmldom_events.asp)
>
> 参考文档

# JSON

## 简介

json格式的用途

开发中涉及到『平台传输』，json格式一定是首选

## json格式说明

* json数据两端要么是<kbd>{}</kbd>,要么是<kbd>[]</kbd>

* <kbd>{}</kbd>定义json对象

* <kbd>[]</kbd>定义json数组

* json对象的格式是：

  ```json
  {key:value,key:value,......key:value}
  ```

* json数组格式是：

  ```json
  [value,value,value,....value]
  ```

* key的类型是字符串

* value的类型可以是：

  * 基本数据类型
  * 引用数据类型：json对象或json数组

正因为json格式种的value部分还可以继续用hson对象或数组，所以json格式是可以『多层嵌套』的，所以json格式不论多么复杂的数据类型都可以表达

```json
{
  "stuid":12,
  "stuAge:122",
  "school": {
    "schoolname":"xinshiji",
    "schoolId": 12
  },
  "subjectList": [
    {
      "subjectname": "zhangsan1",
    "subjectStore": "hahaha"
    },{
      "subjectname": "zhangsan1",
      "subjectStore": "hahaha"
    },{
      "subjectname": "zhangsan1",
      "subjectStore": "hahaha"
    }
  ],
  "demo": {
    "demo2": {
      "name1": "name",
      "age1": "age"
    },
    "demo3": {
      "name1": "name",
      "age1": "age"
    }
  }
}
```

## json对象和json字符串互转

1. json对象转json字符串

   ```js
   //json-》字符串
   var json1={"xxx":"xxx","xxx2":"xxx2"};
   var json2= JSON.stringify(json1);
   console.log(json1);//json格式
   console.log(json2);//Strign格式
   ```

2. 字符串转json

   ```js
   // 字符串->json
   var parse1 = JSON.parse(json2);
   console.log(parse1);
   //或
   var str = {"jj":"jj","k":2};
   // console.log(str);
   var parse = JSON.parse(JSON.stringify(str));//这里需要再转一下成字符串，不然会报错
   console.log(parse);
   ```



# MAVEN

## 简介

Apache maven是一个项目管理和构建工具,它基于项目对象模型(pom)的概念,通过一小段描述信息来管理项目的构建、报告和文档。

> MAVEN是专门用于管理和构架java项目的工具,他主要功能有
>
> > 提供了一套标准化的项目结构
> >
> > 提供了一套标准化的构建流程(编译,测试,打包,发布....)
> >
> > 提供了一套依赖管理机制
>
> 标准化的项目结构
>
> ![image-20221104150907837](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20221104150907837.png)
>
> 标准化的构建流程
>
> ![image-20221104151116664](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20221104151116664.png)
>
> 依赖管理
>
> * 旧方法(手动导入添加)
>
>   ![image-20221104151220470](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20221104151220470.png)
>
> * maven依赖管理
>
>   ![image-20221104151306839](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20221104151306839.png)

>maven模型:
>
>![image-20221104151934307](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20221104151934307.png)
>
>![image-20221104152635682](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20221104152635682.png)

## maven常用命令

* <kbd>compile</kbd>:编译
* <kbd>clean</kbd>:清理
* <kbd>test</kbd>:测试
* <kbd>package</kbd>:打包
* <kbd>install</kbd>:安装

## maven的生命周期

maven构建项目生命周期描述的是一次构建过程经历了多少个事件

maven对项目构建的生命周期分为三套

* <kbd>clean</kbd>:清理工作

  ![image-20221104153815790](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20221104153815790.png)

* <kbd>default</kbd>:核心工作,例如:编译,测试,打包,安装等

  ![image-20221104153903294](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20221104153903294.png)

* <kbd>site</kbd>:产生报告,发布站点等

  ![image-20221104162714055](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20221104162714055.png)

  <span style="color:red;background:skyblue">同意生命周期内,执行后面的命令,前面的所有命令都会自动执行</span>

## maven坐标

maven中的坐标是资源的唯一标识

使用坐标来定义项目中需要的依赖

> **坐标的组成**
>
> > <kbd>\<groupId></kbd>:定义当前maven项目隶属组织名称(通常是域名反写,例如:com.alibaba)
> >
> > <kbd>\<artifactId></kbd>:定义当前maven项目名称(通常是模块名称,例如:order-service)
> >
> > <kbd>\<version></kbd>:定义当前项目版本号
> >
> > ```xml
> > <groupId>junit</groupId>
> > <artifactId>junit</artifactId>
> > <version>4.13</version>
> > ```

## 插件推荐

* Maven helper

## 依赖管理

1. 在pom.xml文件编写<kbd>\<dependencies></kbd>标签
2. 在<kbd>\<dependencies></kbd>标签中使用<kbd>\<dependency></kbd>引入坐标
3. 定义坐标的group,artifactId,version
4. 点击刷新,生效

```xml
例如:
<dependencies>
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.13</version>
            <scope>test</scope>
        </dependency>
</dependencies>
```

### 依赖范围

通过坐标点的依赖范围<kbd>\<scope></kbd>,可以设置对应的jar包的作用范围:编译环境,测试环境,运行环境

![image-20221104165743271](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20221104165743271.png)

| 依赖范围 | 编译classpath | 测试classpath | 运行classpath | 例子              |
| -------- | ------------- | ------------- | ------------- | ----------------- |
| compile  | y             | y             | y             | logback           |
| test     | -             | y             | -             | JUnit             |
| provided | y             | y             | -             | servlet-ap        |
| runtime  | -             | y             | y             | jdbc驱动          |
| system   | y             | y             | -             | 储存在本地的jar包 |
| import   | 引入depend    | ency          | Manage        | Ment              |

<kbd>\<scope></kbd>默认值为compile

# WEB

B/S:浏览器服务器架构模式

* 不同安装,浏览器访问,成本低

C/S:客户端服务器架构模式

* 充分利用客户端机器的资源,减轻服务器的负荷

# Mybatis

## 快速入门

> 主要流程
>
> 1. 导入对应的包
>
>    ```xml
>     <dependency>
>                <groupId>org.mybatis</groupId>
>                <artifactId>mybatis</artifactId>
>                <version>3.5.5</version>
>            </dependency>
>            <dependency>
>                <groupId>mysql</groupId>
>                <artifactId>mysql-connector-java</artifactId>
>                <version>8.0.30</version>
>            </dependency>
>    ```
>
> 2. 编写对应的实体类pojo
>
> 3. 编写mybatis-config.xml配置文件
>
>    ```xml
>    <?xml version="1.0" encoding="UTF-8" ?>
>    <!DOCTYPE configuration
>            PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
>            "https://mybatis.org/dtd/mybatis-3-config.dtd">
>    <configuration>
>        <environments default="development">
>            <environment id="development">
>                <transactionManager type="JDBC"/>
>                <dataSource type="POOLED">
>                    <property name="driver" value="com.mysql.jdbc.Driver"/>
>                    <property name="url" value="jdbc:mysql:///java_web?useSSL=false"/>
>                    <property name="username" value="root"/>
>                    <property name="password" value="root"/>
>                </dataSource>
>            </environment>
>        </environments>
>        <mappers>
>    <!--        加载sql映射文件-->
>            <mapper resource="userMapper.xml"/>
>        </mappers>
>    </configuration>
>    ```
>
> 4. 编写sql映射文件
>
>    ```xml
>    <?xml version="1.0" encoding="UTF-8" ?>
>    <!DOCTYPE mapper
>            PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
>            "https://mybatis.org/dtd/mybatis-3-mapper.dtd">
>    <mapper namespace="test">
>        <select id="selectAll" resultType="com.jwb.pojo.user">
>            select * from tb_user;
>        </select>
>    </mapper>
>    ```
>
> 5. 调用并测试
>
>    ```java
>    public class test {
>        public static void main(String[] args) throws IOException {
>    //        加载mybatis核心配置文件
>            String resource = "mybatis-config.xml";
>            InputStream inputStream = Resources.getResourceAsStream(resource);
>            SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder().build(inputStream);
>    
>    //        获取sqlsession对象
>            SqlSession sqlSession = sqlSessionFactory.openSession();
>            List<user> user = sqlSession.selectList("test.selectAll");
>            System.out.println(user);
>        }
>    }
>    
>    ```
>
> 

## mapper代理开发

> 规则
>
> 1. 定义与sql映射文件相同名的mapper接口,并且将mapper接口和sql映射文件放置在同一目录下
> 2. 设置sql映射文件的namespace属性为mapper接口全限定名
> 3. 在mapper接口中定义方法,方法名就是sql映射文件中sql语句的id,并且保持参数类型和返回值类型一致
> 4. 编码
>    1. 通过sqlseeion的getMapper方法获取Mapper接口的代理对象
>    2. 调用对应方法完成sql的执行
>
> 注意:如果mapper接口名称和sql映射文件名称相同,并且咋同一目录下,则可以使用包扫描的方式简化sql映射文件的加载
>
> ![image-20221107150114571](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20221107150114571.png)
>
> ```xml
> <mappers>
> <!--        加载sql映射文件-->
> <!--        <mapper resource="com/jwb/mapper/userMapper.xml"/>-->
> <!--        mapper代理方式,直接进行包扫描-->
>         <package name="com.jwb.mapper"/>
>     </mappers>
> ```
>
> 

1. 在`com.jwb.mapper`文件夹下创建对应的接口`userMapper.xml`

2. 可以在resource文件夹下建立相同的文件结构`com.jwb.mapper`将对应的mapper文件放入其中

   ```xml
   //注意:namespace要写对应结构下的interface
   <mapper namespace="com.jwb.mapper.UserMapper">
       <select id="selectAll" resultType="com.jwb.pojo.User">
           select * from tb_user;
       </select>
   ```

3. 在接口定义与sql相对应的方法,方法名尽量和和id相同

   ```java
   public interface UserMapper {
       List<User> selectAll();
   }
   ```

4. 修改mybatis-config.xml文件的sql映射文件路径是否正确

5. 测试

   ```java
   public static void main(String[] args) throws IOException {
   //        加载mybatis核心配置文件
           String resource = "mybatis-config.xml";
           InputStream inputStream = Resources.getResourceAsStream(resource);
           SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder().build(inputStream);
   
   //        获取sqlsession对象,然后执行sql
           SqlSession sqlSession = sqlSessionFactory.openSession();
   //        List<User> user = sqlSession.selectList("test.selectAll");
   //        System.out.println(user);
   
   //        读取userMapper接口的代理对象
           UserMapper userMapper = sqlSession.getMapper(UserMapper.class);
           List<User> users = userMapper.selectAll();
           System.out.println(users);
   
           sqlSession.close();
       }
   ```

   

## mybatis核心配置文件

### 环境配置（environments）

mybatis可以配置多钟数据库,在不同的场景下可以通过`default="xxx"`切换不同的数据库环境

尽管可以配置多个环境,但每个sqlSessionFactory实例,每个数据库对应一个,如果是三个数据库,就需要三个实例.

注意:default种设置的id是<kbd>\<environment></kbd>的id

```xml
<environments default="development">
  <environment id="development">
    <transactionManager type="JDBC">
      <property name="..." value="..."/>
    </transactionManager>
    <dataSource type="POOLED">
      <property name="driver" value="${driver}"/>
      <property name="url" value="${url}"/>
      <property name="username" value="${username}"/>
      <property name="password" value="${password}"/>
    </dataSource>
  </environment>
  <!--数据库2-->
  <environment id="development2">
    <transactionManager type="JDBC">
      <property name="..." value="..."/>
    </transactionManager>
    <dataSource type="POOLED">
      <property name="driver" value="${driver}"/>
      <property name="url" value="${url}"/>
      <property name="username" value="${username}"/>
      <property name="password" value="${password}"/>
    </dataSource>
  </environment>
</environments>
```

### **事务管理器（transactionManager）**

在 MyBatis 中有两种类型的事务管理器（也就是 type="[JDBC|MANAGED]"）：

提示:可以不用管,当spring和mybatis一起使用时此功能会被spring接管

### 类型别名（typeAliases）

可以给java类起一个别名

```xml
<typeAliases>
  <typeAlias alias="Author" type="domain.blog.Author"/>
  <typeAlias alias="Blog" type="domain.blog.Blog"/>
  <typeAlias alias="Comment" type="domain.blog.Comment"/>
  <typeAlias alias="Post" type="domain.blog.Post"/>
  <typeAlias alias="Section" type="domain.blog.Section"/>
  <typeAlias alias="Tag" type="domain.blog.Tag"/>
</typeAliases>
```

也可以指定一个包为别名

```xml
<typeAliases>
  <package name="domain.blog"/>
</typeAliases>
```

每一个在包 `domain.blog` 中的 Java Bean，在没有注解的情况下，会使用 Bean 的首字母小写的非限定类名来作为它的别名。 比如 `domain.blog.Author` 的别名为 `author`；若有注解，则别名为其注解值。见下面的例子：

```java
@Alias("author")
public class Author {
    ...
}
```

### 其他

> 参数占位符
>  1.#{}: 相当于preparestatement里sql的?,会替换成为?
>  2.${}:  拼接sql,会存在sql注入问题
>  使用时机:
>
>    * 参数传递的时候用#{}
>      或者列名不固定的情况下使用${}
>
>     参数类型:设置传参的类型
>         parameterTypt :可以省略
>
> ```xml
>     <select id="SelevtById"parameterType="int" resultMap="brandResultMap">
>         select * from tb_brand where id=#{id};
>     </select>
> ```

>特殊字符的处理
>1.转义字符:比较少的情况下使用
>2.CDATA区:字符比较多的情况下使用
>
>```xml
><!--        例如小于符号,使用转义字符-->
>   select * from tb_brand where id &lt; #{id};
>
><!--        使用cdata区,区内的会当成文本处理-->
><!--大写CD,弹出cd区-->
>   select * from tb_brand where id <![CDATA[  <  ]]> #{id};
>```

>多条件查询
>
>需要将传的参数和占位符相对应,不然会报错,以下有三种方法
>
>如果是模糊搜索,需要吧传入的参数进行处理后传参比如:
>
>a=`"%"+xxx+"%"`;
>
>1.使用param注解表示穿的参数和占位符对应的值
>
>​	@param("『占位符名称』")
>
>```java
>List<Brand> selectProductByinfo(@Param("states") int states, @Param("companyName") String companyName, @Param("brandName") String brandName);
>```
>
>2.直接传对应的实体类,mybatis会自动的进去找对应的字段
>
>```java
>List<Brand> selectProductByinfo(Brand barnd);
>```
>
>3.传map集合,写入对应的key和value
>
>```java
>List<Brand> selectProductByinfo(Map map);
>```



## 插件推荐

mybaitsX

## 配置文件完成增删改

## 动态sql

### 查询

**1、多条件动态查询**

> 标签:if用于判断参数是否有值,使用test属性进行条件判断
>
> * 存在问题:第一个条件不需要逻辑运算符
> * 解决方法:
>   1. 使用恒等式`1=1`让所有条件格式都一样
>   2. <kbd>\<where></kbd>标签替换where关键字
>
> ```xml
> <select id="selectProductByinfo" resultMap="brandResultMap">
> <!--        select * from tb_brand where status = #{states} and company_name like #{companyName} and brand_name like #{brandName};-->
> <!--   动态条件查询-->
> <!--        问题1:出现where后面和and中间缺少条件爆粗-->
> <!--            解决1:在where条件后面价格恒等式1=1-->
> <!--
>             select * from tb_brand where 1=1
>         <if test="states != null">
>             and status = #{states}
>         </if>
>         <if test="companyName !=null and companyName!=''">
>             and company_name like #{companyName}
>         </if>
>         <if test="brandName !=null and brandName!=''">
>             and brand_name like #{brandName};
>         </if>
> -->
> <!--     解决2:使用mybatis提供的<where>标签-->
> <!--         where标签会自动识别并去掉and -->
>         select * from tb_brand
>         <where>
>             <if test="states != null">
>                 and status = #{states}
>             </if>
>             <if test="companyName !=null and companyName!=''">
>                 and company_name like #{companyName}
>             </if>
>             <if test="brandName !=null and brandName!=''">
>                 and brand_name like #{brandName};
>             </if>
>         </where>
>     </select>
> ```

**2、单条件动态查询**

> 从多条件中选择一个
>
> ![image-20221108154107638](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20221108154107638.png)
>
> mybatis提供了`chose(when,otherwise)`:选择,类似java中的switch语句
>
> **interface**
>
> ```java
> List<Brand> selectBySingleCondition(Brand brand);
> ```
>
> **mapper**
>
> 注意:#{}内的名字应该与实体类的字段名相同不然没法映射不到
>
> ```xml
> <select id="selectBySingleCondition" resultMap="brandResultMap">
>      select * from tb_brand 
> <!--        where 使用where标签就可以省略以下otherwise标签(只针对本demo) -->
>      <where>
>          <choose><!--类似于switch-->
>              <when test="status!=null"><!--    类似于case    -->
>                   status = #{status}
>              </when>
>              <when test="companyName !=null and companyName!=''">
>                   company_name like #{companyName}
>              </when>
>              <when test="randName !=null and randName!=''">
>                   brand_name like #{randName};
>              </when>
>              <!--类似于default -->
> <!--                <otherwise>-->
> <!--                    1=1-->
> <!--                </otherwise>-->
>          </choose>
>      </where>
>  </select>
> ```
>
> **测试**
>
> ```java
> public void test4() throws IOException {
>      Brand brand = new Brand();
>      int id=0;
>      String comName="";
>      String brandName="";
> 
> 
>      String resource="mybatis-config.xml";
>      InputStream inputStream = Resources.getResourceAsStream(resource);
>      SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder().build(inputStream);
> 
>      SqlSession sqlSession = sqlSessionFactory.openSession();
>      BrandMapper mapper = sqlSession.getMapper(BrandMapper.class);
> //        brand.setStatus(id);
>      brand.setCompanyName(comName);
>      brand.setRandName(brandName);
> 
>      List<Brand> brands = mapper.selectBySingleCondition(brand);
> 
>      for (Brand brand1 : brands) {
>          System.out.println(brand1.getId()+"\t\t"+brand1.getRandName()+"\t\t"+brand1.getRandName());
>      }
> 
>  }
> ```

### 添加

**主键返回**

案例:在数据添加成功后,需要插入数据库数据的主键

注意事物提交

> 实际需求比如:添加订单和订单项
>
> 1.添加订单
>
> 2.添加订单项,订单项种需要设置所属订单的id
>
> > 添加 void add(Brand brand);
> >
> > 参数:除了id的所有数据
> >
> > 结果:void
> >
> > 添加成功后返回主键id

> 操作:
>
> 在insert标签种添加两项属性<kbd>useGeneratedKeys</kbd>和<kbd>keyColumn</kbd>
>
> 将设置为<kbd>useGeneratedKeys="true"</kbd>和<kbd>keyColumn="要返回的列名"</kbd>
>
> ```xml
> <insert id="add" useGeneratedKeys="true" keyColumn="id">
>      insert into tb_brand values(null,#{randName},#{companyName}
>      ,#{ordered},#{description},#{status});
>  </insert>
> ```
>
> 此时执行该添加方法后会返回主键id

### 修改

**修改静态字段**

```java
 int update(Brand brand);
```

```xml
<update id="update">

        update tb_brand set brand_name=#{randName},company_name=#{companyName},ordered=#{ordered},description=#{description},status=#{status} where id=#{id};
    </update>
```

**修改动态字段**

> 参数:部分数据,封装在对象中
>
> 结果:void
>
> \<set>标签

```xml
<update id="update2">
        update tb_brand
        <set>
            <if test="randName!=null and randName!=''">
                brand_name=#{randName},
            </if>
            <if test="companyName!=null and companyName!=''">
                company_name=#{companyName},
            </if>
            <if test="ordered!=null and ordered!=''">
                ordered=#{ordered},
            </if>
            <if test="description!=null and description!=''">
                description=#{description},
            </if>
            <if test="status!=null and status!=''">
                status=#{status}
            </if>
        </set>
        where  id =#{id};
    </update>
```

### 删除

**单数据删除**

> 参数:id
>
> 结果:viod

```xml
<delete id="deleteById">
        delete from tb_brand where id=#{id};
    </delete>
```

**批量删除**

> ``` java
>  void deleteMoreById(@Param("ids")int[] ids);
> ```
>
> ```xml
> <delete id="deleteMoreById">
> <!--        delete from tb_brand where id in(?,?,?)-->
>         delete from tb_brand where
>         id in
> <!--        myabtis会将数组 封装成为一个map集合
>              *默认:key为array = 数组
>              * 使用@Param注解改变map集合的默认key的名称
>             -->
> <!--     collection要遍历的数组,item:对应的字段 separator分隔符多个id时中间用separator分隔
>            open开始时前面拼, close结束后拼接-->
>         <foreach collection="ids" item="id" separator="," open="(" close= ")">
>             #{id}
>         </foreach>
> ```
>
> 

## mybatis参数传递

> mybatis接口方法中可以接收各种各样的参数,Mybatis底层对这些参数进行不同的封装处理方式
>
> 单个参数
>
> * **pojo类型**:直接使用,属性名和参数占位符名称一致
>
> * **Map集合**: 直接使用, 键名和参数占位符一致
>
> * **Collection**: 封装为map集合
>
>   map.put("arg0",collection集合);
>
>   map.put("Collection",collection集合);
>
> * **List**:封装为map集合
>
>   map.put("arg0",list集合);
>
>   map.put("collection",list集合);
>
>   map.put("list",list集合);
>
> * **Array**:封装为map集合
>
>   map.put("arg0",数组);
>
>   map.put("array",数组);
>
> * 其他:直接使用
>
> 多个参数
>
> ```java
> //这里的param需要个xml中#{}的名字相同,不然会映射不到
> User select(@Param("username")String username,@Param("password")String password);
> ```
>
> ```xml
> <select id="select" resultType="user">
> select * from tb_brand where
> username=#{username} and password=#{password};
> </select>
> ```
>
> * 封装为Map集合
>
>   ```java
>   map.put("arg0",参数值1);
>   map.put("param1",参数值1);
>   map.put("arg1",参数值2);
>   map.put("param2",参数值2);
>   ```
>
> Mybatis提供了ParamNameResolver类来进行封装
>
> > mybatis会将多个参数封装为map集合,默认的key为arg或param,所以不使用@param注解来修改key的名字的话,需要吧#{}内的名字改写成arg0或param.可读性低
> >
> > 建议:将来都使用@Param注解来修改Map集合中的默认键名,并使用修改后的名称来获取值.这样可读性更高
> >
> > 



## 注意事项

>mybatis事物
>
>* openSession();
>
> 默认开启事物,进行增删改操作后需要使用sqlSession.commit();手动提交事物
>
>* openSession(true); 
>
> 可以设置为自动提交事物(关闭事物)

> 增删改可以设置返回int类型(影响到行数)

## 注解完成增删改

使用注解开发会比配置文件更方便

```java
    @Select("select * from tb_brand where id=#{id}")
    @ResultMap("brandResultMap") //配置文件里配置的brandResultMap
    Brand selectIdBrand(int id);
```

> * 查询:@(Select)
> * 添加:@(Insert)
> * 修改:@(Update)
> * 删除:@(Delete)
>
> 提示:
>
> * 注解完成简单的功能
> * 配置文件完成复杂的功能

# servlet

