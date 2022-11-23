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

w	js也有明确的数据类型，但是声明一个变量后它可以接受任何数据类型，并且 会在程序执行过程中根据上下文自动转换

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

   ![image-20221102100343216](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20221102100343216.png)

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
> ![image-20221109155710042](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20221109155710042.png)



Document Object Model文档对象模型

![image-20221109155311523](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20221109155311523.png)

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
> ![image-20221104150907837](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20221104150907837.png)
>
> 标准化的构建流程
>
> ![image-20221104151116664](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20221104151116664.png)
>
> 依赖管理
>
> * 旧方法(手动导入添加)
>
>   ![image-20221104151220470](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20221104151220470.png)
>
> * maven依赖管理
>
>   ![image-20221104151306839](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20221104151306839.png)

>maven模型:
>
>![image-20221104151934307](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20221104151934307.png)
>
>![image-20221104152635682](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20221104152635682.png)

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

  ![image-20221104153815790](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20221104153815790.png)

* <kbd>default</kbd>:核心工作,例如:编译,测试,打包,安装等

  ![image-20221104153903294](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20221104153903294.png)

* <kbd>site</kbd>:产生报告,发布站点等

  ![image-20221104162714055](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20221104162714055.png)

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

![image-20221104165743271](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20221104165743271.png)

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
> ![image-20221107150114571](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20221107150114571.png)
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
>         * 参数传递的时候用#{}
>                 * 表明或者列名不固定的情况下使用${}
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
>    1.转义字符:比较少的情况下使用
>    2.CDATA区:字符比较多的情况下使用
>
>```xml
><!--        例如小于符号,使用转义字符-->
>        select * from tb_brand where id &lt; #{id};
>
><!--        使用cdata区,区内的会当成文本处理-->
><!--大写CD,弹出cd区-->
>        select * from tb_brand where id <![CDATA[  <  ]]> #{id};
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
> ![image-20221108154107638](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20221108154107638.png)
>
> mybatis提供了`chose(when,otherwise)`:选择,类似java中的switch语句
>
> **interface**
>
> ```java
> 
> List<Brand> selectBySingleCondition(Brand brand);
> ```
>
> **mapper**
>
> 注意:#{}内的名字应该与实体类的字段名相同不然没法映射不到
>
> ```xml
> 
> <select id="selectBySingleCondition" resultMap="brandResultMap">
>         select * from tb_brand 
> <!--        where 使用where标签就可以省略以下otherwise标签(只针对本demo) -->
>         <where>
>             <choose><!--类似于switch-->
>                 <when test="status!=null"><!--    类似于case    -->
>                      status = #{status}
>                 </when>
>                 <when test="companyName !=null and companyName!=''">
>                      company_name like #{companyName}
>                 </when>
>                 <when test="randName !=null and randName!=''">
>                      brand_name like #{randName};
>                 </when>
>                 <!--类似于default -->
> <!--                <otherwise>-->
> <!--                    1=1-->
> <!--                </otherwise>-->
>             </choose>
>         </where>
>     </select>
> ```
>
> **测试**
>
> ```java
> public void test4() throws IOException {
>         Brand brand = new Brand();
>         int id=0;
>         String comName="";
>         String brandName="";
> 
> 
>         String resource="mybatis-config.xml";
>         InputStream inputStream = Resources.getResourceAsStream(resource);
>         SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder().build(inputStream);
> 
>         SqlSession sqlSession = sqlSessionFactory.openSession();
>         BrandMapper mapper = sqlSession.getMapper(BrandMapper.class);
> //        brand.setStatus(id);
>         brand.setCompanyName(comName);
>         brand.setRandName(brandName);
> 
>         List<Brand> brands = mapper.selectBySingleCondition(brand);
> 
>         for (Brand brand1 : brands) {
>             System.out.println(brand1.getId()+"\t\t"+brand1.getRandName()+"\t\t"+brand1.getRandName());
>         }
> 
>     }
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
>         insert into tb_brand values(null,#{randName},#{companyName}
>         ,#{ordered},#{description},#{status});
>     </insert>
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
>  默认开启事物,进行增删改操作后需要使用sqlSession.commit();手动提交事物
>
>* openSession(true); 
>
>  可以设置为自动提交事物(关闭事物)
>

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

# WEB核心★

web:全球广域网,能够通过浏览器访问的网站

javaweb:使用java计数来解决相关web互联网领域的技术栈

* B/S架构,browser/server .浏览器架构/服务器.

  ![image-20221110135908475](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20221110135908475.png)

  * 静态资源

    > html、css、JavaScript、图片等。负责页面展示

  * 动态资源

    > Servlet、JSP等。负责逻辑处理

  * 数据库：负责数据存储 

  * HTTP协议：定义通讯规则

  * WEB服务器：负责解析http协议，解析请求数据，并发送响应数据

  

  

* c/s架构,client/Server  客户端架构/服务器

## HTTP

### 介绍:

> <span style="color:red">H</span>yper<span style="color:red">T</span>ext <span style="color:red">T</span>ransfer <span style="color:red">P</span>rotocol,『超文本传输协议』
>
> 规定了浏览器和服务器之间传输的规则
>
> HTTP协议特点:
>
> 1. 基于TCP协议:面向连接,安全
> 2. 基于请求-响应模型的:一次请求对应一次响应
> 3. http协议是无状态的协议:对于事务处理没有记忆能力.每次请求-响应都是独立的
>    * 缺点:多次请求间不能共享数据(会使用会话计数解决)
>    * 优点:速度快

### 请求数据格式

1. <span style="color:red;background:skyblue">请求行</span>: 请求数据的第一行。其中GET表示请求方式，/表示请求资源路径,http/1.1表示协议版本
2. <span style="color:red;background:skyblue">请求头</span>:第二行开始,格式为key:value形式
3. <span style="color:red;background:skyblue">请求体</span>:POST请求的最后一部分,存放请求参数

**常见的HTTP请求头**

* Hsot:表示请求的主机名
* User-Agent:浏览器版本
* Accept:表示浏览器能接收的资源类型
* Accept-Language:表示浏览器偏好的语言,服务器可以据此返回不同语言的网页
* Accept-Encoding:表示浏览器可以支持的压缩类型:比如:gzip,deflate等

**get和post请求**区别

1. get请求请求参数在请求行重工,没有请求体.

   post请求请求参数在请求体中

2. get请求请求参数大小有限制,post没有

 ```
 GET /HTTP/1.1
 Host:www.itccast.cn
 Connection:keep-alive
 Cache-Control:max-age=0 Upgrade-Insecure-Request:1
 User-Agent:Mozilla/5.0 Chrome/91.0.4472.106
 ```

```
POST /HTTP/1.1
Host:www.itccast.cn
Connection:keep-alive
Cache-Control:max-age=0 Upgrade-Insecure-Request:1
User-Agent:Mozilla/5.0 Chrome/91.0.4472.106

Username=superxxx&password=123456
```

### 响应数据格式

1. <span style="color:red;background:skyblue">响应行</span>: 响应数据的第一行。其中http/1.1表示协议版本,200表示响应状态码,OK表示状态码描述
2. <span style="color:red;background:skyblue">响应头</span>:第二行开始,格式为key:value形式
3. <span style="color:red;background:skyblue">响应体</span>:最后一部分,存放相应数据

**常见的HTTP请求头**

* Content-Type:表示响应内容的类型,例如text/html
* Content-length:表示响应内容的长度(字节数)
* Content-Encoding:表示响应压缩算法,例如gzip
* Content-Control:只是客户端应如何缓存,例如max-age=300表示最多可以缓存300秒

![image-20221110143702259](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20221110143702259.png)

[响应状态码参考](#响应状态码)

| 状态码分类 | 说明                                                         |
| ---------- | ------------------------------------------------------------ |
| 1xx        | **响应中**——临时状态码，表示请求已经接受，告诉客户端应该继续请求或者如果它已经完成则忽略它 |
| 2xx        | **成功**——表示请求已经被成功接收，处理已完成                 |
| 3xx        | **重定向**——重定向到其它地方：它让客户端再发起一个请求以完成整个处理。 |
| 4xx        | **客户端错误**——处理发生错误，责任在客户端，如：客户端的请求一个不存在的资源，客户端未被授权，禁止访问等 |
| 5xx        | **服务器端错误**——处理发生错误，责任在服务端，如：服务端抛出异常，路由出错，HTTP版本不支持等 |

## Tomcat

### 简介

web服务器是一个应用程序(软件),对http协议的操作进行封装,使得程序员不比直接对协议进行操作,让web开发更加便捷

* tomcat是apache软件基金会一个核心项目,是一个开元免费的轻量级web服务器,支持servlet/jsp少量javaee规范
  * javaee:java enterprise Edition,java企业版.是指java企业级开发的技术规范总和.
* tomcat也称为web容器,servlet容器.servlet需要依赖tomcat才能运行

### 基本使用

**配置**

修改启动端口号:conf/server.xml

注: http协议默认端口号为80,如果将tomcat端口号改为80,则将来访问tomcat时,将不用输入端口号

启动时可能会出现的问题

1. 端口号冲突:找到对应的程序关掉
2. 启动窗口一闪而过:检查JAVA_HOME环境变量是否配置正确

**Tomcat部署项目**

* 将项目放置到webapps目录下,即部署完成

一般项目会被javaWeb项目会被打成war包,然后讲war包放到webapps目录下,Tomcat会自动解压缩war文件

web**项目结构**

![image-20221110160615029](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20221110160615029.png)

**集成本地tomcat**

maven插件方式

注意:插件只支持到tomcat7版本

1. 在pom.xml添加配置

   ``` xml
   <build>
           <finalName>javawebLearn</finalName>
           <plugins>
               <plugin>
                   <groupId>org.apache.tomcat.maven</groupId>
                   <artifactId>tomcat7-maven-plugin</artifactId>
                   <version>2.2</version>
                 <configuration>
                       <port>80</port><!--访问端口号-->
                       <path>/</path><!--项目访问路径-->
                   </configuration>
               </plugin>
           </plugins>
       </build>
   ```

2. 使用maven Helper插件快速启动项目

   1. 选中项目,右键
   2. run maven
   3. Tomcat7:run

## servlet

### 创建模板

使用模板新建servlet便于开发

![image-20221116222021927](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20221116222021927.png)

创建servlet可以直接选择模板创建

![image-20221116222307177](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20221116222307177.png)

### 简介

servlet是java提供的一门动态web资源开发技术

servlet是javaEE规范之一,其实就是一个接口,将来我们需要定义Servlet类实现Servlet接口,并由web服务器运行Servlet

```java
public class servletDemo implements Servlet{
	...
}
```

### 快速入门

> 1.创建web项目,导入servlet依赖坐标
>
> ```xml
>  <dependency>
>             <groupId>javax.servlet</groupId>
>             <artifactId>javax.servlet-api</artifactId>
>             <version>3.1.0</version>
>    <!--provided编译测试环境有效,运行环境无效-->
>    <!--因为tomcat自带了servlet jar包-->
>             <scope>provided</scope>
>         </dependency>
> ```
>
> 2.创建:定义一个类,实现servlet接口,并重写接口中的所有方法,并在service方法中输入一句话
>
> ```java
> public class ServerDemo01 implements Servlet {
>     @Override
>     public void init(ServletConfig servletConfig) throws ServletException {
> 
>     }
> 
>     @Override
>     public ServletConfig getServletConfig() {
>         return null;
>     }
> 
>     @Override
>     public void service(ServletRequest servletRequest, ServletResponse servletResponse) throws ServletException, IOException {
> 
>     }
> 
>     @Override
>     public String getServletInfo() {
>         return null;
>     }
> 
>     @Override
>     public void destroy() {
> 
>     }
> }
> ```
>
> 3.配置:在类上使用@WebServlet注解,配置改Servlet的访问路径
>
> ```java
> @WebServlet("/demo")
> public class ServerDemo01 implements Servlet {
> ```
>
> 4.访问:启动tomcat,浏览器输入url访问servlet
>
> ```url
> http://localhost:8080/demo
> ```

> Servlet方法介绍
>
> * 初始化方法,在Servlet被创建时执行,只执行一次
>
>   ```
>   void init(ServletConfig config)
>   ```
>
> * 提供服务方法,每次Servlet被访问,都会调用该方法
>
>   ```
>   void service(ServletRequest req,ServletResponse res)
>   ```
>
> * 销毁方法,当Servlet被销毁时,调用该方法.在内存释放或服务器关闭时销毁Servlet
>
>   ```
>   void destroy()
>   ```
>
> * 获取ServletConfig对象
>
>   ```
>   ServletConfig getServletConfig()
>   ```
>
> * 获取Servlet信息
>
>   ```
>   String getServletInfo()
>   ```
>
>   

### Servlet执行流程

![image-20221114141513304](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20221114141513304.png)

### Servlet生命周期

![image-20221114141808980](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20221114141808980.png)

> Servlet运行在Servlet容器(web服务器中),其声明周期由容器来管理,氛围4个阶段
>
> 1. <span style="color:red;background:skyblue">加载和实例化</span> : 默认情况下,当servlet第一次被访问时,由容器创建Servlet对象『默认』
>
>    可以手动更改
>
>    ```java
>    @WebServlet(urlPatterns="/demo",loadOnstartup = 1)
>    ```
>
>    * 负整数:第一次被访问创建Servlet对象
>    * 0或正整数 : 服务器启动时创建Servlet对象,数字越小优先级越高
>
> 2. <span style="color:red;background:skyblue">初始化</span> : 在Servlet实例化之后,容器将调用Servlet的init()方法初始化这个对象,返程一些如加载配置文件,差u过年见链接等初始化的工作,该方法只调用一次
>
> 3. <span style="color:red;background:skyblue">请求处理 </span>: 每次请求Servlet时,Servlet容器都会调用Servlet的service()方法对请求进行处理
>
> 4. <span style="color:red;background:skyblue">服务终止</span>: 当需要释放内存或者容器关闭时,容器就会调用Servlet实例的destroy()方法完成资源的释放.在destroy()方法调用之后,容器会释放设个Servlet实例,该实例随后会被java的垃圾收集器所回收

###  Servlet体系结构

![image-20221114162859072](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20221114162859072.png)



### Servlet urlPattern配置

Servlet要想被访问,必须配置其访问路径(urlPattern)

1. 一个Servlet,可以配置多个urlPattern

   ```java
   @WebServlet(urlPattern={"/demo1","/demo2"})
   ```

2. urlPattern配置规则

   * 精确匹配

     * 配置路径:`@WebServlet("/user/demo")`
     * 访问路径:`localhost:8080/user/demo`

   * 目录匹配

     * 配置路径:`@WebServlet("/user/*")`

     * 访问路径:`localhost:8080/user/aaa`

       ​				` localhost:8080/user/bbb`

   * 扩展名匹配

     * 配置路径:`@WebServlet("*.do")`

     * 访问路径:`localhost:8080/aaa.do`

       ​				` localhost:8080/bbb`.do

   * 任意匹配(`尽量不要使用`)

     * 配置路径:`@WebServlet("/")`

       ​				`@WebServlet("/*")`

     * 访问路径:`localhost:8080/haha`

       ​				` localhost:8080/hehe`

     * /和/*的区别:

       * 当我们项目的Servlet配置了`"/"`,会覆盖掉tomcat中的defaultServlet,当其他的url-pattern都匹配不上时都会走这个servlet
       * 当我们项目配置了`"/*"`,以为匹配任意访问路径

3. 优先级:

   `精确路径>目录路径>扩展名路径> /* > /`

### XML配置方式编写Servlet

从3.0版本之后才使用注解配置,之前都是使用xml配置

步骤:

1. 编写servlet类

2. 在web.xml中配置该Servlet

   ```xml
   <servlet>
       <servlet-name>demo03</servlet-name>
       <servlet-class>org.example.servlet.ServletDemo03</servlet-class>
     </servlet>
     <servlet-mapping>
       <servlet-name>demo03</servlet-name>
       <url-pattern>/demo03</url-pattern>
     </servlet-mapping>
   ```

注意:写地址时`org.example.`需要与项目的\<groupid>保持一致,不然会报错

## Request&Response(请求&响应)

Request:获取请求数据

Response: 设置相应数据

### Request（请求）

#### Request继承体系

![image-20221115154850487](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20221115154850487.png)

1. tomcat需要解析请求数据,封装为request对象,并且创建request对象传递到service方法中
2. 使用request对象,查阅<u>***javaEE API***</u>文档的HttpServletRequest接口

#### Request获取请求数据

请求数据分为3部分:

1. 请求行:`GET/request-demo/req?username=zhangsan HTTP/1.1`

   * String getMethod() : 获取请求方式: GET
   * String getContextPath() : 获取虚拟目录(项目访问路径): /request-demo
   * StringBuffer getRequestURL(): 获取URL(同一资源定位符): http://localhost:8080/request-demo/req1
   * String getRequestURL(): 获取URL(统一资源标识符): request-demo/req1
   * String getQueryString() : 获取请求参数(GET方式): username=zhangsan&password= 123

   ```java 
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
   //        String getMethod(); 获取请求方式: GET
           String method = req.getMethod();
           System.out.println(method);
   //      String getContextPath(); 获取虚拟目录(项目访问路径):/request-demo
           String contextPath = req.getContextPath();
           System.out.println(contextPath);
   //        StringBuffer requestURL:获取url(统一资源定位符):http://localhost:8080/request-demo/xxx
           StringBuffer requestURL = req.getRequestURL();
           System.out.println(requestURL);
   //      String requestURI//获取URL(统一资源标识符): request-demo/req1
           String requestURI = req.getRequestURI();
           System.out.println(requestURI);
   //        String getQueryString() : 获取请求参数(GET方式): username=zhangsan&password= 123
           String queryString = req.getQueryString();
           System.out.println(queryString);
   
       }
   ```

   

2. 请求头: `User-Agent:Mozilla/5.0 Chrome/91.0.4472.106`

   * String getHeader(String name): 根据请求头名称,获取值

3. 请求体: `username=super&password=231`

   * ServletInputStream getInputStream() : 获取字节输入流
   * BufferedReader getReader(): 获取字符输入流

#### 通用的方式获取请求数据

因为doget和dopost的方法实现代码一样,可以直接在dopost方法调用doget()方法`this.doget(req,resp);`

请求参数获取方式

>  GET方式:
>
> ```
> String getQueryString()
> ```

> POST方式
>
> ```
> BufferedReader getReader()
> ```

get和post请求方式区别主要在于获取请求参数的方式不一样,这时需要提供一种统一的获取请求参数的方式,从而统一doget和dopost方法内的代码

理解

```
//        用于接收参数
        String param ="";
        String method = req.getMethod();
        if (method.equals("GET")){ //两种书写方法
            param = req.getQueryString();
        }else if ("POST".equals(method)){
            BufferedReader reader = req.getReader();
            param = reader.readLine();
        }
```

**使用方法**

后两种方法较为常用

* Map<Stirng,String[]> getParameter(): 获取所有参数Map集合
* String[] getParameterValues(String name):根据名称获取参数值(数组)
* String getParameter(String name):根据名称获取参数值

```java
// getParameterMap()方法
        Map<String, String[]> map = req.getParameterMap();
        for (String key: map.keySet()) {
            System.out.print(key+":");
            String[] strings = map.get(key);
            for (String string : strings) {
                System.out.print(string+"");
            }
            System.out.println();
        }
        System.out.println("------------分割线------------");
//        根据key获取参数值,数组
        String[] values = req.getParameterValues("hobby");
        for (String value : values) {
            System.out.println(value);
        }
//        获取单个参数值
        String username = req.getParameter("username");
        System.out.println(username);
        String password = req.getParameter("password");
        System.out.println(password);


```

#### 请求参数中文乱码问题

如果参数如果存在中文数据,则会乱码

解决方案:

* POST:设置输入流的编码

  ```java
  //        post方法解决中文乱码
          req.setCharacterEncoding("UTF-8");
  ```

* GET:

  出现原因:

  因为tomcat进行url解码,默认的字符集为ISO-8859-1

  ![image-20221117161054420](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20221117161054420.png)

  

  ```java
  //        1. 获取username
          String username1 = req.getParameter("username");
  ////        先对乱码数据进行编码,转为字节数组
          byte[] bytes = username1.getBytes(StandardCharsets.ISO_8859_1);
  //        字节数组解码
          String username2 = new String(bytes, StandardCharsets.UTF_8);
          System.out.println("乱码后"+username2);
  
  ```

#### Request请求转发

请求转发(forward):一种在服务器内部的资源跳转方式

![image-20221117165734948](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20221117165734948.png)

实现方式

```java
 req.getRequestDispatcher("资源b").forward(req,resp);
```

```java
//例
request.getRequestDispatcher("/req1").forward(request,response);
```

请求转发资源间共享数据:使用request对象

* void serAttribute(String name , Object o) : 储存数据到request域中
* Object getAttribute(String name) : 根据key,获取值
* void removeAttribute(String name) : 根据key,删除该键值对

请求转发特点

* 浏览器地址栏不发生变化
* 只能转发到当前服务器的内部资源
* 一次请求,可以在转发的资源间使用request共享数据



### Response（响应）

![image-20221118143315919](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20221118143315919.png)

#### Response设置相应数据功能介绍

相应数据分为3部分:

1. 响应行:`HTTP/1.2 200 OK`
   * void setStatus(int sc):设置响应状态码
2. 响应头:`Content-Type:text.html`
   * void setHeader(String name,String value):设置响应头键值对
3. 响应体`<html><head>head<body></body></hmtl>`
   * PrintWriter getWriter():获取字符输出流
   * ServletOutputStream getOutputStream():获取字节输出流

#### Response完成重定向

重定向(Redirect) : 一种资源跳转方式,和请求转发有本质的区别

![image-20221118150806181](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20221118150806181.png)

实现方式

```java
resp.setStatus(302);
resp.setHeader("location","资源b路径");

//例
  response.setStatus(302);
  response.setHeader("location","/resp2");
```

简化方式书写

```java
resp.sendRedirect("资源路径");
//例
 response.sendRedirect("/resp2");
```

重定向特点

* 浏览器地址栏发生变化
* 可以重定向到任意位置的资源,(服务器内部,外部均可)
* 两次请求,不能在多个资源使用request共享数据

#### Response响应字符数据

使用

1. 通过Response对象获取字符输出流

   ```
   PrintWriter writer = resp.getWriter();
   ```

2. 写数据

   ```
   writer.write("aa");
   ```

注意:

* 该流<span style="color:red;">不需要关闭</span>,随着响应结束,response对象销毁,由服务器关闭

* 中文数据乱码:原因通过Response获取的字符流默认编码为iso-8859-1

  ```
  resp.serContentType("text/html;charset=utf-8");
  ```

  

#### Response响应字节数据

使用

1. 通过Response对象获取字节输出流

   ```
   ServletOutputStream outputStream = resp.getOutputStream();
   ```

2. 写数据

   ```
   outputStream(字节数据);
   ```

IOUtils工具类使用

1. 导入坐标

   ```
   <dependency>
   	<groupId>commons-io</groupId>
   	<artifactId>commons-io</artifactId>
   	<version>2.6</version>
   </dependency>
   ```

2. 使用

   ```
   IOUtils.copy(输入流,输出流); 
   ```

### 代码优化

创建SqlSessionFactory代码优化

```java
 String resource = "mybatis-config.xml";
        InputStream inputStream = Resources.getResourceAsStream(resource);
        SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder().build(inputStream);
```

问题

1. 代码重复 : 工具类解决
2. SqlSessionFactory工厂只创建一次,不要重复创建: 静态代码块

```java
public class SqlSessionFactoryUtils {
    private static SqlSessionFactory sqlSessionFactory;
    static {
        String resource = "mybatis-config.xml";
        try {
            InputStream inputStream = Resources.getResourceAsStream(resource);
             sqlSessionFactory = new SqlSessionFactoryBuilder().build(inputStream);
        } catch (IOException e) {
            throw new RuntimeException(e);

        }


    }
    public static SqlSessionFactory getSqlSessionFactory(){

      return sqlSessionFactory;
    }
}
```



## JSP(了解)

### 简介

* 概念: java Server Pages , java服务端页面
* 一种动态的网页技术,其中即可以定义HTML、JS、CSS等静态内容,还可以定义java代码的动态内容
* JSP = HTML + JAVA
* jsp的作用简化开发,避免了Servlet中直接输出html标签

### JSP快速入门

1. 导入JSP坐标

   ```xml
   <dependency>
         <groupId>javax.servlet.jsp</groupId>
         <artifactId>jsp-api</artifactId>
         <version>2.2</version>
       </dependency>
   ```

2. 创建jsp文件

3. 编写HMTL标签和JAVA代码

   ```html
   <body>
           <h1>hellp jsp</h1>
       <%
           System.out.println("hello jsp~~");
       %>
   </body>
   ```

   

### JSP原理

* jsp本质就是一个servlet 
* jsp在被访问时,由jsp容器(tomcat)将其转换为java文件(Servlet),在由jsp容器(tomcat)将其编译,最终提供服务的其实就是这个字节码文件

### JSP脚本

* jsp脚本用于在jsp页面内定义java代码

* jsp脚本分类

  1. `<%.....%>`: 内容会直接放到_jspService()方法之中

  2. `<%=...%>`: 内容会放到out.print()中,作为out.print()的参数

     相当于sout

  3. `<%!....%>`: 内容会放到_jspService()方法之外,被类直接包含

     相当于类中的一个方法

### 缺点

由于jsp页面内,即可以定义html标签,又可以定义java代码,会造成一下问题

1. 书写麻烦:特别是复杂的页面
2. 阅读性差
3. 复杂度高: 运行需要依赖各种环境,jre,jsp容器,javaee...
4. 占内存和磁盘:jsp会自动生成.java和.class文件占磁盘,运行的是class文件占内存
5. 调试困难:出错后,需要找到自动生成的.java文件进行调试
6. 不利于团队写作:前端人员不会java,后端人员不精html

### EL表达式

Expression Language 表达式语言,用于简化jsp页面的内的java代码

主要功能:获取数据

语法:`${expression}`

`${brands}`: 获取域中存储的key为brands的数据

例:

```java
 ArrayList<User> users = new ArrayList<>();
        users.add(new User(1,"usernane1","123321"));
        users.add(new User(1,"usernane2","13321"));
        users.add(new User(1,"usernane3","1321"));

//        储存到request域中
        req.setAttribute("user",users);

//        转发
        req.getRequestDispatcher("/mainView.jsp").forward(req,resp);
```

```html
<body>
    
    ${user}

</body>
```

注意:如果遇到el表达式无效果,在page标签内添加`isELIgnored="false"`取消屏蔽el表达式

javaWeb**种的四大域对象**

* page:当前页面有效
* request:当前请求有效
* session: 当前会话有效
* application: 当前应用有效

![image-20221120180408600](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20221120180408600.png)

<span style="color:red;">el表达式获取数据,会一次从这四个域中寻找,直到找到为止</span>

### JSTL标签

JSP标准标签库(Jsp Standarded Tag Library),使用标签取代JSP页面上的java代码

> 快速入门
>
> 1. 导入坐标
>
>    ```xml
>    <dependency>
>          <groupId>jstl</groupId>
>          <artifactId>jstl</artifactId>
>          <version>1.2</version>
>        </dependency>
>        <dependency>
>          <groupId>taglibs</groupId>
>          <artifactId>standard</artifactId>
>          <version>1.1.2</version>
>        </dependency>
>    
>    ```
>
> 2. 在jsp页面引入jstl标签库
>
>    ```
>    <%@ taglib prefix="c"uri="http://java.sun.com/jsp/jstl/core" %>
>    ```
>
> 3. 使用

语法:

`<c:if>`

```html
<c:if test="${flag==1}">
男
</c:if>
<c:if test="${flag==2}">
</c:if>
```

`<c:forEach>`:相当于for循环

* items:被遍历的容器
* var : 遍历产生的临时变量
* varStatus : 获取序号

```jsp
<c:forEach items="${brands}" var="brand" carStatus="status">
	<tr aligen="center">
		<td>${brand.id}</td>
		<td>${brand.brandName}</td>
		<td>${brand.companyName}</td>
		<td>${brand.description}</td>
    <td>${status.index}</td> //从0开始排序
    <td>${status.count}</td> //从1开始排序
  </tr>
</c:forEach>
```

* begin :开始
* end : 结束
* step : 步长

```jsp
<c:forEach begin="0" end="10" step="1" var="i">
	${i}
</c:forEach>
```

### MVC模式和三层架构

MVC是一种分层开发的模式,其中

`M`: Model,业务模型,处理业务

`V`: View,视图,界面展示 

`C`:Controller,控制器, 处理请求,调用模型和视图

![image-20221120184654852](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20221120184654852.png)

**三层架构**

`表现层`:接收请求,封装数据,调用业务层,相应数据

`业务逻辑层`: 对业务罗技进行封装,组合数据访问层层中基本功能,形成复杂的业务逻辑功能

`数据访问层`:对数据库的CRUD操作

![image-20221120190018284](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20221120190018284.png)

![image-20221120190245581](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20221120190245581.png)





后续对应层级的框架

![image-20221120190201443](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20221120190201443.png)

### 案例



## 会话(Cookie、session)

## Filter(过滤器)

## Listener(监听器)

# 前段进阶(基础)

## Ajax

## VUE

## ElementUI







# 响应状态码

状态码大全：https://cloud.tencent.com/developer/chapter/13553 

## 常见的响应状态码

| 状态码 | 英文描述                               | 解释                                                         |
| ------ | -------------------------------------- | ------------------------------------------------------------ |
| 200    | **`OK`**                               | 客户端请求成功，即**处理成功**，这是我们最想看到的状态码     |
| 302    | **`Found`**                            | 指示所请求的资源已移动到由`Location`响应头给定的 URL，浏览器会自动重新访问到这个页面 |
| 304    | **`Not Modified`**                     | 告诉客户端，你请求的资源至上次取得后，服务端并未更改，你直接用你本地缓存吧。隐式重定向 |
| 400    | **`Bad Request`**                      | 客户端请求有**语法错误**，不能被服务器所理解                 |
| 403    | **`Forbidden`**                        | 服务器收到请求，但是**拒绝提供服务**，比如：没有权限访问相关资源 |
| 404    | **`Not Found`**                        | **请求资源不存在**，一般是URL输入有误，或者网站资源被删除了  |
| 428    | **`Precondition Required`**            | **服务器要求有条件的请求**，告诉客户端要想访问该资源，必须携带特定的请求头 |
| 429    | **`Too Many Requests`**                | **太多请求**，可以限制客户端请求某个资源的数量，配合 Retry-After(多长时间后可以请求)响应头一起使用 |
| 431    | **` Request Header Fields Too Large`** | **请求头太大**，服务器不愿意处理请求，因为它的头部字段太大。请求可以在减少请求头域的大小后重新提交。 |
| 405    | **`Method Not Allowed`**               | 请求方式有误，比如应该用GET请求方式的资源，用了POST          |
| 500    | **`Internal Server Error`**            | **服务器发生不可预期的错误**。服务器出异常了，赶紧看日志去吧 |
| 503    | **`Service Unavailable`**              | **服务器尚未准备好处理请求**，服务器刚刚启动，还未初始化好   |
| 511    | **`Network Authentication Required`**  | **客户端需要进行身份验证才能获得网络访问权限**               |

