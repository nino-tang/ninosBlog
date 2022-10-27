---
title: java基础笔记
comments: true
toc: true
date: 2022-10-27 12:40:00
categories:
  - 学习笔记
  - java
tags: java
pic:
---

[TOC]



#   java基础

这是快速复习java基础的笔记

## 重要编程思想

**化繁为简**：现将复杂的功能转变成简单的需求。

先死后活：有限考虑固定的值，再考虑变量。







# java概述

知识点：

## [快速练习](##快速入门部分)

1. 使用黑窗口编译.java文件时，注意要把需要编译的java文件编码设置与cmd黑窗口编码相同

2. ```java
   javac hello.java //编译指令			
   ```

3. ```java
   java hello //运行指令	
   //注意不要带文件后缀，否则报错
   ```

4. java执行流程分析

   1. ![image-20220204113338135](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220204113338135.png)

## [制表符](##制表符部分)

1. ```
   \t 一个制表位，实现对其功能
   \n 换行符，
   \\ 第一个斜杠代表转义，第二个代表结果 所以要输入\\两个斜杠
   \	\将""：号输出显示出来，在前面添加\" \" 也可转义其他符号例如'
   // \r 表示一个回车 例如：System.out.println("韩顺平教育\r北京");
   		// 执行步骤：
   		// 	1. 先输出韩顺平教育
   		//  2. 执行回车后，相当于光标来到了最开头
   		//  3. 再输出北京
   		//  4. 最终输出的结果是“北京平教育”  ，相当于北京把前面的韩顺覆盖掉了
           可以加个\n换行防止覆盖
   
   ```

2. ````java
   class ChangeChar{
   	public static void main(String[] args){
   		// \t 一个制表位，实现对其功能
   		System.out.println("beijing\tshanghai\tguangzhou");
   		// \n换行
   		System.out.println("jack\nlisa\nnino");
   		// \\ 输出一个斜杠\ 
   		// 第一个斜杠代表转义，第二个代表结果 所以要输入\\两个斜杠
   		System.out.println("c\\a\\v\\b.exe");
   		// \将""：号输出显示出来，在前面添加\" \"
   		System.out.println("老王说：\"hello\"");
   		// \r 表示一个回车 System.out.println("韩顺平教育\r北京");
   		// 执行步骤：
   		// 	1. 先输出韩顺平教育
   		//  2. 执行回车后，相当于光标来到了最开头
   		//  3. 再输出北京
   		//  4. 最终输出的结果是“北京平教育”  ，相当于北京把前面的韩顺覆盖掉了
   		System.out.println("韩顺平教育\r\n北京");
   
   	}
   }
   ````

# 注释

1. 文档注释

   1. ```
      javadoc -d 路径文件 -xx -yy xxx.java
      生成文档命令
      xx yy 分别代码javadoc标签命令 例如-auther -version等
      ```

   2. ```java
      @author 标明开发该类模块的作者 
      @version 标明该类模块的版本 
      @see 参考转向，也就是相关主题 
      @param 对方法中某参数的说明 
      @return 对方法返回值的说明 
      @exception 对方法可能抛出的异常进行说明 
      
      @author 作者名 
      @version 版本号
      其中，@author 可以多次使用，以指明多个作者，生成的文档中每个作者之间使用逗号 (,) 隔开。@version 也可以使用多次，只有第一次有效 
      
      使用 @param、@return 和 @exception 说明方法 
      这三个标记都是只用于方法的。@param 描述方法的参数，@return 描述方法的返回值，@exception 描述方法可能抛出的异常。它们的句法如下： 
      @param 参数名 参数说明 
      @return 返回值说明 
      @exception 异常类名 说明 
      
      ```

# 变量

## 数据类型

### 变量

1. 变量本质就是一个变化的值。

2. 变量有三个基本要素

   1. 类型
   2. 名称
   3. 值

3. ```java
   public static void main(String[] args){
   	int a=1;
   	//定义了一个变量，类型为int，名称为a，值为1
   	a=89;
       //把89这个值赋给了a变量
   }
   ```

4. 注意事项：

   * 变量表示内存中的一个储存区域，[不同的变量，类型不同，占用的空间大小不同，比如：int 4个字节，double 8个字节]
   * 该区域有自己的名称[变量名]和类型[数据类型]
   * 变量必须先声明，后使用，有着自身的顺序
   * 该区域的数据可以在同一类型范围内不断变化
   * 变量在同一个作用域内不能重名
   * 变量=变量名+值+数据类型，变量三要素

### 运算符

1. +号的使用
   * 当左右两边为数值类型的时候，做加法运算
   * 当左右两边有一方为字符串类型时，做拼接运算

### 数据类型

java数据类型

1. 基本数据类型

   * 数值型
     * 整数类型，存放整数（byte[1],short[2],int[4],long[8])
     * 浮点（小数）类型（float[4]，double[8])
   * 字符型（char[2]），存放单个字符'a'
   * 布尔型（Boolean[1]），存放true，false

2. 引用数据类型（面向对象部分讲解）

   * 类（class）
   * 接口（interface）
   * 数组（[]）

3. 八大基本数据类型

   【byte，short，int，long，float，double】，char，Boolean

4. 浮点数据类型

   1. 默认情况下输入的字符默认是double类型的

   2. 如果想改成float类型需要在数值后面加上f或F

   3. ```java
      float a = 1.1 //错误
      float a = 1.1F //正确
      double b = 1.1	//正确
      double b = 1.1F	//正确
      ```

   4. 平时使用默认的double类型就行，因为更为精确

   5. 浮点数使用陷阱

      * ```java
        //例如
        //2.7和8.1/3 比较
        double a = 2.7 ;
        double b = 8.1/3 ;//理论上数学得数是2.7
        System.out.println(a);//2.7
        System.out.println(b);//得数是一个接近2.7的一个小数，而不是2.7
        //因为计算机计算机制的问题，不是数学的问题。
        所以在做相等判断时需要小新
        ```

      * ```java
        //类似问题的解决方法
        double a = 2.7 ;
        double b = 8.1/3 ;//理论上数学得数是2.7
        System.out.println(a);//2.7
        System.out.println(b);
        
        if(a == b){
        //这样的写法会出问题
        	System.out.println("相等");
        }
        
        //可以使用计算其差值
        if(Math.abs(a-b)<0.001){
        	System.out.println("差值非常小，到我规定的精度内，认为相等");
            
           // Math方法调用java API
           
        }
        ```

5. 字符类型

   1. char的本质就是一个整数，默认用的是Unicode编码
   2. 字符常量用单引号引出来，
      * 例：char a = 'a';
      * char b = '/n';
   3. 不能输入双引号，否则会认成字符串，会报错。
   4. char类型时可以运算的。

   字符型的本质

   * 字符型储存到计算机中，需要将对应的码值（整数）找出来

   * 字符和码值的对应关系是通过字符编码表决定的（是规定死的）

   * ![image-20220205221255475](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220205221255475.png)

6. 布尔类型

   1. 只占一个字节，只允许true和false
   2. 用于判断操作
   3. 不可用0或非0 来代替true或false，c语言可以

## 数据类型转换

### 1、自动类型转换

* 精度小的类型自动转换为精度大的数据类型，反之就会报错。

* char < int < long < float < double 

* byte < short < int < long < float < double

* ```java
  //例：
  int num = 'a';
  ```

1. 注意事项

   1. 多重类型的数据混合运算时，系统首先自动将所有数据转换成容量最大的哪种数据类型，然后再进行计算

    ```java
     //例
     int n1 = 10;
     float d1 = n1+1.1;
     //这是错误的，因为转换成最大单位，1.1默认的类型是double类型的，如果是n1＋1.1f 的话就是正确的
     double d1 = n1+1.1;
     // 这是正确的；
    ```

   2. （ byte , short ) 和 char之间不会相互转换，当把一个具体的数赋给byte时。

      1. 先判断该数是否在byte范围内，如果是就可以

   3. byte，short，char 三者可以进行计算，在计算时都会先转换成int类型

      * ```java
        byte b1 = 1;
        byte a1 = 1;
        short b2 = 1;
        short s2 = b1 + b2//错误
        //因为计算时会转换成int类型，int不能再赋给比它小的类型short
        int s2 = b1 + b2 //正确
        byte s3 = a1 + b1//错误
        //byte，short，char,只要涉及计算都会转换为int类型，所以错误
        ```

   4. 布尔类型 ( boolean ) 不参与类型转换

   5. 自动提升原则：表达式结果的类型自动提升为 操作数中最大的类型。

### 2、强制类型转换

1. 简介

   1. 大的数据类型转换为小的数据类型
   2. 使用时要加上强制转换字符（类型）
   3. 可能会出现精度降低和溢出问题

2. 注意细节

   1. 将数据从大到小转换，需要强制转换

   2. ```java
      //强制转换符只对最近的操作数有效，也就是只对下边的10数字有效，转换后再进行计算又会转换成double类型。
      int x = (int)10*3.5+6*1.5;//提示编译错误，类型是double ->
      
      int x = (int)(10*3.5+6*1.5);//用小括号括起来即可完美解决上述问题
      ```

3、基本数据类型和String类型的转换

1. 介绍

   1. 在程序开发中，我们经常需要吧基本数据类型转换成String类型，或String转基本数据类型

2. 方式

   * 基本转String

     * 基本数据类型的值+" " 

     * ```java
       //例
       int n1 = 123;
       float f = 2.3f;
       double b = 4.5;
       String str1 = n1 +" ";
       String str2 = f +"";
       String str3 = b +"";
       
       ```

   * String 转基本

     * 调用基本类型的包装类方法parseXXX 方法即可

     * ```java
       String s5= "123";
       integer.parseInt(s5);
       Double.parseDouble(s5);
       Float.parseFloat(s5);
       //怎么吧字符串转成字符char，含义是指吧字符串的第一个字符得到
       system.out.println(s5.charAt(0));//获取字符串的第一个字符
       //所以这个输出的值为1
       ```

3. 注意事项

   1. string转换基本类型时，要确保string类型能够转成有效数据，可以吧'123'转换成一个整数，但不能吧"hello"转换成一个整数

# 运算符

## 运算符

### 1.简介

1. 是一种特殊符号，表示数据的运算、赋值和比较等
2. 种类
   * 算数运算符
   * 赋值运算符
   * 关系运算符(比较运算符)
   * 逻辑运算符
   * 位运算符 [ 需要二进制基础 ]
   * 三元运算符

### 2.算数运算符

1. 对数值类型的变量进行运算的
2. 预览：![image-20220211161920431](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220211161920431.png)
3. 注意事项
   * 取模
   * <span style="color:white;background:red;font-size:文字大小;font-family:字体;">再%的本质，看一个公式 a % b = a-a / b * b</span>
4. 面试题
   1. ![image-20220213151013682](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220213151013682.png)
      1. 答案为 1
         * 运行步骤为
         * (1)先把 i 的值赋给一个临时变量tmp
         * (2)再进行计算i++，结果为i=2
         * (3)tmp的值重新赋给i，此时i =1
      2. 答案为2
         * 运行步骤为
         * (1)再进行计算i++，结果为i=2
         * (2)再将2移到临时变量tmp
         * (3)tmp赋给 i

### 3.关系运算符（比较运算符）

1. 介绍
   * 关系运算符的结果都是boolean型，
   * 通常用在if条件语句结构条件中
   * 关系运算符组成的表达式成为关系表达式
2. 预览图

![image-20220213162614379](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220213162614379.png)



### 4.逻辑运算符

预览：

1. ![image-20220213170452994](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220213170452994.png)

2. ![image-20220213170753311](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220213170753311.png)

3. ![image-20220213170926798](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220213170926798.png)

4. ```
   &&（短路与）	只有两个条件都为true ，才为true	//如果第一个条件为false，则后面的条件不执行，直接输出flase，效率高
   
   &	（逻辑与）	只有两个条件都为true ，才为true	//两个条件都执行，效率低
   ```

5. ![image-20220214140501385](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220214140501385.png)

6. ```java
   取反
   真变假，假变真
   //a^b :叫逻辑异或，当a和b不同时，结果为true，否侧为false
   例：
   	boolean b = (10>1) ^ (3<5);
   	System.out.println("b="+b);//f
   ```

### 5.赋值运算符（=）、

分类：

* 基本赋值运算符 = 	int a = 10；

* 复合赋值运算符

  ```
  +=，-=，*=，/=，%=等等，
  例：a += b;[等价 a=a+b;]
  	a -=b;[等价 a = a-b;]
  一般情况加复合赋值运算符，前边都有基本赋值运算符
  ```

* 复合运算符会进行类型转换

  ```java
  byte a =3;
  a += 2; //此时计算结果为int类型
  //不会报错，因为会自动进行类型转换
  
  //不能直接写成
  a=a+2; //会报错
  
  // 像a++，++a这种会都进行自动的类型转换
  ```

### 6.三元运算符

* 语法：条件表达式？ 表达式1: 表达式2；

* 运算规则：

  1. 如果条件表达式为true，运算后的结果是表达式1；

  2. 如果条件表达式为false，运算后的结果是表达式2；

     口诀：【一灯大师：一真大师（如果为真，返回1）】

  3. 例：

     ```java
     int a = 10 ;
     int b = 99 ;
     // 1.如果 结果为false
     // 2.返回b--，先返回b，再进行b-1。依旧按照之前的a++,++a的计算形式
     // 3.结果为99
     int result = a > b ? a++; b--;
     //如果a>b 为真，返回a++，如果为false返回b--;
     
     ```

  4. 本质就是if，else语句

### 7.运算符优先级

* ![image-20220215150928654](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220215150928654.png)
* 小结：优先级排名
  1. () ，{}等优先级最高
  2. 单目运算==a ，--a等；
  3. 算术运算符+-
  4. 位移运算符
  5. 比较运算符
  6. 逻辑运算符
  7. 三元运算符
  8. 赋值运算符

## 标识符

**标识符的规则和规范**

1. java中对各种变量、方法和类的命名使用的字符成为标识符。

* ```java
  int num =1;
  // num就是标识符
  ```

2. 标识符的命名规则必须遵守
   * 标识符由26个字母的大小写，0-9，_或$符组成。
   * 不可以用数字开头
   * 不可以使用关键字和保留至，但能包含关键字和保留字
   * 标识符不能包含空格
3. 标识符命名规范
   * 包名：多单词组成时，所有字母都小写。例：aaa.bbb.ccc
   * 类名、接口名：多单词组成是，所有单词首字母大写，驼峰命名法
   * 变量名、方法名：多单词组成时，第一个单词首字母小写，后面单词的首字母大写。例：aaBbCc
   * 常量名：所有字母都大写。多单词时用下划线隔开。例：A_B_C

##   键盘输入语句

### 1.介绍

在编程过程中需要接受用户的输入数据，可以使用键盘输入语句来获取。input.java，需要一个扫描器（对象），就是Scanner

### 2.步骤

1）导入该类所在的包，java.utill.*

2）创建该类对象（声明变量）

3）调用里面的功能

### 3.案例

```java
public class KeyboardInput {
    public static void main(String[] args) {
//        创建Scanner对象
        Scanner scanner = new Scanner(System.in);

        System.out.println("请输入文本1");
//        z字符串类型
        scanner.next();
        System.out.println("请输入age");
//        nextint 代表接收一个int类型的输入
        scanner.nextInt();
//        接收double类型的
        scanner.nextDouble();

    }

```





## 进制

### 介绍

对于整数，有四种表达方式

* 二进制（Bin/B）：0,1，满2进1，以0b或0B开头

* 八进制（OCT/O）：0-7，满8进1。以数字0开头表示

* 十进制（DEC/D）：0-9，满10进1

* 十六进制（HEX/H）：0-9及A(10)-F(15)，满16进1.以0x或0X开头表示。此处的A-F不区分大小写

* ```java
  int n1 = 0b1010;
  int n2 = 01010;
  int n3 = 1010;
  int n4 = 0x10101;
  ```

  

### 进制转换（基本功）*

第一组

1. 二进制转十进制

   * 规则：从最低位（右边）开始，将每个位上的数提取出来，乘以2的（位数-1）次方，然后求和

   * ```
     例
     0b 1011  =1*2^0+1*2^1+0*2^2+1*2^
     = 1+2+0+8
     =11
     
     ```

2. 八进制转十进制

   * 规则：从最低位（右边）开始，将每个位上的数提取出来，乘以8的（位数-1）次方，然后求和。

   * ```
     例：0234转成十进制
     0 234
     =4*8^0 + 3*8^1 + 2*8^2 
     =4+24+128
     =156
     ```

3. 十六进制转十进制

   * 规则：从最低位（右边）开始，将每个位上的数提取出来，乘以16的（位数-1）次方，然后求和

   * ```
     例：0x 23A转成十六进制
     =10*16^0 + 3*16^1 + 2*16^2
     =10 + 48 + 512
     =570
     A(10),B(11),C(12),D(13),E(14),F(15)
     ```

[第一部分练习](###进制部分)

第二组

1. 十进制转二进制

   * 规则：将该数不断除2，直到商为0为止，然后将每步得到的余数倒过来，就是对应的二进制

   * ```
     将34转换成二进制
     34%2	余0
     17%2  余1
     8%2		余0
     4%2		余0
     2%2		余0
     1%2		余1
     反着读
     结果：0b100010 //前缀0b的意思为二进制
     正确答案为：0b00100010
     因为一个字节二进制的是八位，34的出的结果是六位所以前面需要多加两个0
     ```

2. 十进制转八进制

   * 规则：将该数不断除8，直到商为0为止，然后将每步得到的余数倒过来，就是对应的八进制

   * ```
     例：将131转为八进制
     131%8		余3
     16%8		余0
     2%8			2
     结果为0203前面的0代表的意思是八进制
     ```

3. 十进制转十六进制

   * 规则：将该数不断除16，直到商为0为止，然后将每步得到的余数倒过来，就是对应的十六进制

   * ```
     例：237
     答案为 ED
     ```

   * ![image-20220216221217568](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220216221217568.png)

第三组

1. 二进制转八进制

   * 规则：从低位开始，将二进制数的每三位一组，转成对应的八进制数即可

   * ```
     例：0b 11010101 每三个转成十进制再拼起来
     =325
     11100101
     =345
     ```

2. 二进制转十六进制

   * 从低位开始，将二进制数的每四位一组，转成对应的十六进制即可

   * ```
     11010101
     =0xD5
     1110010110
     =0x396	每四个转成十进制再拼起来
     ```

第四组

1. 八进制转二进制

   * 规则：将八进制数每一位，转成对应的3位的二进制数

   * ```
     237  每位以十进制转二进制转成对应的3位二进制数再连起来
     2（010）3（011）7（111）
     =010011111
     
     1230
     =1(001)2(010)3(011)0(000)
     =001010011000
     ```

2. 十六进制转二进制

   * 规则：将八进制数每一位，转成对应的4位的二进制数

   * ```
     23B
     =2(0010)3(0011)B(1011)
     =001000111011
     AB29
     =A(1010)B(1011)2(0010)9(1001)
     =1010101100101001
     ```

源码，反码，补码（重点）

对于有符号的数而言（八个规则）：

1. 二进制的最高位是符号位：0表示正数，1表示负数（口诀：0 - >0   1-> -）
2. 正数的原码，反码，补码都一样（三码合一）
3. 负数的反码 = 它的原码符号位不变，其他位取反（0->1,1->0）0变1,1变0.
4. 负数的补码 = 它的反码+1，负数的反码 = 负数的补码-1
5. 0的反码，补码都是0
6. java没有无符号的数，换而言之，java中的数都是有符号的
7. 计算机运算的时候，都是以 <span style="color:white;background:red;font-size:文字大小;font-family:字体;">补码的方式来运算的</span>
8. <span style="color:white;background:red;font-size:文字大小;font-family:字体;">当我们看运算结果的时候，要看它的原码（！！！）</span>



## 位运算

* java中有七个位运算符（&，|，^，~，>>，<<和>>>）

* 分别是：

  * &：按位与

    * 规则：两位全为1，结果为1，否则为0

    * ```
      例：
         10011010
        &11011101
      -------------
        =10011000// 两个都1结果才为1
      ```

  * |：按位或

    * 规则：两位有一个为1，结果为1，否则为0

    * ```
          10011010
        &11011101
      -------------
        =11011111// 两个有一个1结果才为1
      ```

  * ^：按位异或

    * 规则：两位一个为0，一个为1，结果为1，否则为0

    * ```
      10011010
      &11011101
      ```

    -------------

        =01000111// 两位一个为0，一个为1，结果为1，否则为0

      ```
    
      ```

  * ~：按位取反

    * 规则：0为1,1为0

```
//位移运算
int a = 1>>2; // 1 向右位移2位
int b = -1>>2;
int c = 1<<2; //左移 2位
int d = -1<<2;
int e = 3>>>2;//无符号右移


```

[练习部分](##位运算练习)

```
2&3计算机计算流程（计算机是按照补码进行计算的）
因为一个字节是八位，一个int类型有4个字节
1.先得到2的补码 ===>* 源码00000000 00000000 00000000 00000010 //得到原码
* 转成补码（正数的三码都一样）
00000000 00000000 00000000 00000010
2. 得到3的补码 ====>先获得原码00000000 00000000 00000000 00000011
得到3的补码
00000000 00000000 00000000 00000011

3.计算2&3
补码结果为：00000000 00000000 00000000 00000010
原码也为：00000000 00000000 00000000 00000010
最终结果为：2
```

````
~-2计算过程
1. 得到-2的原码10000000 00000000 00000000 00000010
2. 算出-2的反码11111111 11111111 11111111 11111101（原符号位保持不变，其他取反）
3. 算出-2的补码11111111 11111111 11111111 11111110
4.再进行~-2操作00000000 00000000 00000000 00000001//运算后的补码
5.转为原码00000000 00000000 00000000 00000001
6.结果为1
````

```
~2的计算过程
1.得到2的原码00000000 00000000 00000000 00000010
2.获取补码：00000000 00000000 00000000 00000010
3.计算~2:11111111 11111111 11111111 11111101
3.转为反码（）负数的反码=补码-1
11111111 11111111 11111111 11111100
4.转为原码：10000000 00000000 00000000 00000011
5.结果为-3
```

* 运算符>>，<<和>>>运算规则

  * 算数右移>>；低位溢出，符号位不变，并用符号位补溢出的高位

    * ```
      int a = 1>>2;
      1:00000000 00000000 00000000 00000001
      1 >>2 //相当于把最后边的01去掉用符号位补上
      结果：00000000 00000000 00000000 00000000
      最后结果为0
      
      简便的方法
      1>>2 = 1/2/2= 0
      15>>2 = 15/2/2=3  //取整
      ```

  * 算数左移<<; 符号位不变，低位补0

    * ```
      int a =1<<2;
      1:00000000 00000000 00000000 00000001
      1<<2
      00000000 00000000 00000000 00000100
      结果为4
      
      简便的方法
      1<<2 =1*2*2 = 4
      4<<3 = 4*2*2*2 = 32
      
      ```

  * 3.>>>逻辑右移，也叫无符号右移，运算规则是：低位溢出，高位补0

# 程序控制结构

## 顺序控制（if,else,switch）

### 介绍

程序从上到下逐行执行，中间没有任何判断和跳转

### 分支控制

### **1）单分支**

基本语法：

```java
if(条件表达式){
	执行代码块;
}
```

说明：当条件表达式为true时，则执行{}内的代码。false就不执行。如果只有一条执行语句，可以省略{}。但不建议省略

### **2）双分支**

基本语法：

```java
if(条件表达式){
	执行代码块1;
}else{
	执行代码块2;
}
```



### **3）多分支**

基本语法：

```java
if(条件表达式){
	执行代码块1;
}else if(条件表达式){
	执行代码块2;
}else{
	执行代码块....;
}.....
```

流程图：

else只能有一个执行入口

![image-20220222162201564](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220222162201564.png)

特别说明：

1. 多分支可以没有else，如果所有条件都不成立，则一个执行入口都没有
2. 如果有else，如果所有的条件表达式都不成立，则默认执行else代码块。

练习：

```java
public class ifChapter {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("请输入0-100的数字");
        int num = scanner.nextInt();
        if (num<1 && num>100){
            if (num==100){
                System.out.println("信用极好");
            }else if (num>80 && num <= 99){
                System.out.println("信用优秀");
            }else if (num >= 60 && num <= 80){
                System.out.println("信用一般");
            }else if (num <60){//或直接不写这个条件语句，但这个会有bug
                System.out.println("不及格");
            }else{
                System.out.println("请输入合法数字");
            }
        }else{
            System.out.println("输入不合法");
        }
    }
}
```

### **4）嵌套分支**

介绍：

一个分支完整的嵌套了另一个分支结构，里面的分支结构称为内层分支，外面的分支结构称为外层分支。

规范：不建议超过三层（可读性不好）

基本语法：

```java
if(){
	if(){
	
	}else{
		if.....
	}
}
```

### 5）switch分支

基本语法：

```java
switch(表达式){ //表达式为具体的一个值
    case 常量1:
语句块1;
break;
    case 常量2:
语句块2;
break;
    case ······:
break;
 ...........
       
default :
default语句块
break;
}
```

1. switch 关键字,表示swtich分支
2. 表达式   对应一个值
3. case常量1：当表达式的值等于常量1，就执行语句块1
4. break：表示退出switch
5. 如果case 常量1 匹配，就执行语句块1，如果没有则继续case 常量2；
6. 如果一个都没有匹配上，就执行default

Switch流程图：

![image-20220224155515378](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220224155515378.png)

 注意：

* 穿透
  1. 如果case1 没有break
  2. 则case不进行判断直接执行case2 的语句块

```java
public static void main(String[] args) {
        char week;
        Scanner scanner = new Scanner(System.in);
        System.out.println("请输入字母");
        week = scanner.next().charAt(0);
        switch (week){
            case 'a':
                System.out.println("Monday");
                break;
            case 'b':
                System.out.println("Tuesday");
                break;
            case 'c':
                System.out.println("Wednesday");
            case 'd':
                System.out.println("Thursday");
                break;
            case 'e':
                System.out.println("Friday");
                break;
            case 'f':
                System.out.println("Saturday");
                break;
            case 'g':
                System.out.println("sunday");
                break;
            default:
                System.out.println("输入有误，请输入a-g的字母");
        }
    }
```

注意事项和细节

1. 表达式数据类型，应和case后的常量类型一致，或者是可以自动转换成可以相互比较的类型，比如输入的是字符，而常量是int

2. Switch(表达式)中表达式的返回值必须是：（byte，short，int，char，enum，String）

   ```java
   //比如下列例子，是不可以的
   double a = 1.1;
   switch(a){//错误
   	case 1.1://case后面不可以有变量
   		System.out.println("···");
   		break;
   }
   ```

3. case子句中的值必须是常量，不能是变量

4. default子句是可选的，当没有匹配的case时，执行default。default语句是可选的，当没有匹配的任何常量，则没有任何输出。

5. break语句用来执行完一个case分支后使程序跳出switch语句块；如果没有则会出现穿透现象，使程序执行后面所有的case语句块，除非遇到break；

6. [练习](##switch练习)

**switch 和if的比较**

1. 如果判断的具体数值不多，而且符合byte，short，int，char，enum，string类型虽然这两个语句都可以用，建议用switch
2. 其他情况，对区间判断，对结果为boolean配型判断，使用if，if的使用范围更广

## 循环控制（for,while,dowhile,多重循环[重点]）

### 1）for循环

1. 基本语法

   ```java
   for(循环变量初始化；循环条件；循环变量迭代){
   	循环操作；(可多条语句)
   }
   
   ```

   

2. 说明

   1. for关键字，表示循环控制
   2. for有四要素，1）循环变量初始化，2）循环条件，3）循环操作，4）循环变量迭代
   3. 循环操作，这里可以有很多条语句，也就是我们要执行的代码块
   4. 如果 循环操作(语句)只有一条语句，可以省略{}，建议不要省略

例子：

```java
public static void main(String[] args) {

        //练习： 打印100句“韩顺平教育”
        for (int i = 0; i < 10; i++) {
            System.out.println("韩顺平教育" +i);
        }


    }
```

* for循环流程图
  * ![image-20220227123857620](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220227123857620.png)

#### 注意事项：

* 循环条件返回一个布尔值(Boolean)

* for（；循环条件；）中的初始化和变量迭代可以写到其他地方，但两边的分号不能省略

  * ```java
    //演示
    int i = 0;
    for (i; i < 10;) {
                System.out.println("韩顺平教育" +i);
                 i++;
            }
    
    //补充
    for(;;){//表示一个无限循环
       System.out.println("韩顺平教育" +i);
    }
    ```

* 循环初始值，可以有多条初始化语句，但要求类型一样，并且中间用逗号隔开，循环变量迭代也可以有多条变量迭代语句，中间用逗号隔开

  * ```java
    //例
    int count =3;
    for (i =0 ,j = 0 ;i<count; i++, j+=2){
    	System.out.println("i="+i "j=" +j);
    }
    输出 ：00 12 24
    ```

  * 00 12 24 

#### **编程技巧**

* 化繁为简：将复杂的需求拆解成简单的需求
* 先死后活：先考虑固定的值，然后转成可以灵活变化的值

**练习**

1. 打印1-100之间所有9的倍数的整数，统计个数以及总和。[化繁为简，先死后活]

   * ```
     
     ```

   * ```java
     //打印1-100之间所有9的倍数的整数，统计个数以及总和。[化繁为简，先死后活]
           //1、先输出1-100循环
           //2、在输出的过程中过滤9的倍数
           //3、定义一个变量来累计计算个数
           //4、定义一个变量来累计计算总和
     public static void main(String[] args) {
             int count= 0;
             int sum =0;
             for (int i = 1; i <=100 ; i++) {
                 if (i%9==0){
                     System.out.println("i="+i);
                     count++;
                     System.out.println("数量"+count);
                     sum+=i;// = sum + i
                     System.out.println("sum="+sum);
                 }
     
             }
     ```

### 2）while循环

基础语法：

```java
while（循环条件）{
	循环体（语句）；
	循环变量迭代；
}
```

说明：

1. while循环也有四要素
2. 只是四要素放的位置，和for不一样

**流程图**

![image-20220227143009846](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220227143009846.png)

#### 注意事项：

1. 循环条件是返回布尔值
2. while循环是先判断再执行语句



### 3）do...while循环控制

基础语法：

```java
do{
	循环体(语句);
	循环变量迭代;
}while(循环条件);

```

 说明:

1. do  while 是关键字

2. 也有循环四要素，只是位置不一样

3. 先执行，在判断，也就是说，一定会执行一次

4. 最后有一个分号

5. while和do... while区别

   * while是先判断再执行

   * do .. while是先执行再判断

```java
public static void main(String[] args) {

       int i = 1;
        do {
            System.out.println("阿巴阿巴");
            i++;//不要忘记加上，否则容易死循环
        }while (i<=10);

        System.out.println("exit dowhile");
    }
```



流程图：

![image-20220227163555197](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220227163555197.png)

#### 注意事项：

1. 循环条件是返回一个布尔值的表达式
2. do...while 循环是先执行后判断，因此它至少执行一次



### 4）多重循环

#### 介绍

1. 讲一个循环放在另一个循环体内，就形成了嵌套循环。其中，for,while,do ...while均可以作为外层循环和内层循环 。【建议一般使用两层，最多不超过三层，否则代码可读性很差】

2. 实质上，嵌套循环就是把内层循环当成外层循环的循环体，当只有内层循环的条件为false时，才会完全跳出内层循环，才可结束外层的当次循环，开始下一次的循环

3. 例：设外层循环次数为m次，内层为n次。则内层循环体实际上需要执行m*n次

   ```java
   for (int i = 0; i < 2; i++) {
               for (int j = 0; j < 3; j++) {
                   System.out.println("i = "+i+ ","+"j = "+j);
               }
           }
   
   ------------------------输出------------------------
   i = 0 , j =0
   i = 0 , j =1
   i = 0 , j =2
   i = 1 , j =0
   i = 1 , j =1
   i = 1 , j =2
   ```

   

#### 练习

1. 统计3个班成绩情况，每个班有5名同学，求出各个班的平均成绩和所有班级的平均分【学生的成绩从键盘输入】

   * ```java
     Scanner scanner = new Scanner(System.in);
     //        int clss = 1;
                 int stu =0;
                 double sum = 0;
             for (int i = 1; i <=3 ; i++) {
                 for ( int j = 1;j<=5;j++){
     
                     System.out.println("请输入"+i+"班"+j+"成绩");
                     int s = scanner.nextInt();
                     sum = sum + s;
                 }
                 System.out.println(i+"班的平均分为："+(sum / 5));
                 sum =0;
             }
     ```

     

2. 打印99乘法表

   * ```java
     for (int i = 1; i <=9 ; i++) {
        
                 for (int j = 1; j <=i ; j++) {
                     System.out.print(i+"*"+j+"="+(i*j)+"  ");
     
     
                 }
                 System.out.println("");
             }
     ```

3. 打印空心金字塔

   * ```java
     //        实心金字塔
             for (int i = 1; i <=5 ; i++) {
                 for (int k = 1; k <=5-i ; k++) {
     //                在输出*之前，先输出对应的空格 = 总层数 - 当前层数
                     System.out.print(" ");
                 }
     //            控制每个打印的*的层数
                 for (int j = 1; j <=2*i-1 ; j++) {
     
                     System.out.print("*");
                 }
                 System.out.println(" ");
             }
     ```

   * ```java
     空心金字塔 【难点】
             for (int i = 1; i <=5 ; i++) {
                 for (int k = 1; k <=5-i ; k++) {
     //                在输出*之前，先输出对应的空格 = 总层数 - 当前层数
                     System.out.print(" ");
                 }
                 
                 
     //            控制每个打印的*的层数
                 for (int j = 1; j <=2*i-1 ; j++) {
                 
                 
     				//1.空心金字塔的第一层和最后一层的*全部输出
     				//2.用if（j == 1 || j == 2*i-1）条件语句过滤掉，此时会出现最后一层不显示
     				//3.再加一个条件 i == 5
     				if(j == 1 || j == 2*i-1 || i==5 ){
     					 System.out.print("*");
     				}else{
     					 System.out.print(" ");
     				}
     
     //可以将其中的5 提出来换成变量，实时控制金字塔的层数
     
                    
                 }
                 System.out.println(" ");
             }
     ```

     

   * ```java
     //可手动修改的
     
           Scanner scanner = new Scanner(System.in);
           System.out.println("请输入层数");
           int layer = scanner.nextInt();
     ```


             for (int i = 1; i <=layer ; i++) {
                 for (int k = 1; k <=layer-i ; k++) {
    
     //                在输出*之前，先输出对应的空格 = 总层数 - 当前层数
                     System.out.print(" ");
                 }
     //            控制每个打印的*的层数
                 for (int j = 1; j <=2*i-1 ; j++) {
    
                     //1.空心金字塔的第一层和最后一层的*全部输出
                     //2.用if（j == 1 || j == 2*i-1）条件语句过滤掉，此时会出现最后一层不显示
                     //3.再加一个条件 i == 5
                     if(j == 1 || j == 2*i-1 || i==layer ){
                         System.out.print("*");
                     }else{
                         System.out.print(" ");
                     }
                 }
                 System.out.println(" ");
             }
    
     ```
   * 改为菱形
     ```



## break

介绍

1. 跳转控制语句----->break
2. 当某个条件满足时，终止循环
3. break语句用于终止某个语句块的执行，一般用于switch或者循环中

基本语法：

```java
{
......
break;
......
```

以while循环为例流程图：

![image-20220228111326348](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220228111326348.png)

#### 注意事项

1. break语句出现在多层嵌套语句块时，可以通过标签指明要终止的是哪一层语句块

2. 标签的基本使用

   ```java
   label1:{.....
   label2:		{.....
   label3:			{.....
   				break label2;
   		
   }
   	
   }
   
   }
   ```

   1. break语句可以指定退出哪层
   2. label1是标签，由程序员决定
   3. break后指定到哪个label就退出到哪里
   4. 在实际开发中，尽量不要使用标签
   5. 如果没有指定break，默认退出最近的循环体

## continue-跳转控制语句

介绍：

1. <u>**continue语句用于结束本次循环，继续执行下次循环**。</u>
2. continue语句多出现在多层嵌套的循环语句中时，可以用过标签指明要跳过的是哪一环，这个和前面的标签使用一样

基本语法

```java
{
....
continue;
....
}
```

流程图：

![image-20220228153036178](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220228153036178.png)



## return-跳转控制语句

介绍：

return使用在方法，表示跳出所在的方法

注意：

1. 如果吧return放在main方法中会退出程序

# 数组【重点】

## 数组

**介绍**

数组可以存放 <u>多个</u>*<u>同一类型</u>* 的数据。数组也是一种数据类型，是引用数据类型。

即：数（数据）组（一组）就是一组数据

<span id = "数组案例01">案例</span>（快速入门）：

```java
public static void main(String[] args) {
   			double totalWeght =0;
        double[] hen = {1,2,3,4,5,6};
  //可以通过 for循环访问数组的元素
        for (int i = 0; i <hen.length ; i++) {
          //可以通过下标来访问数组的元素 hen[下标]
          //下标是从0开始的，比如【0，1，2，3】
          //第二个元素是hen[1]
    
            System.out.println("第"+(i+1)+"个元素的值为"+hen[i]);
          totalWeght+=hen[i];
        }
  		System.out.println("总体重为"+totalWeght+"平均体重为="+(totalWeght/hen.length));
    }
```

### 动态初始化

#### 使用方式1

先new出一个数组，再动态的给它赋值。

数组的定义：

数据类型	数组名[] = new 数据类型[大小]

数据类型[]	数组名 = new 数据类型[大小]

以上两种写法的效果都是等价的

例：

```java
int a[] = new int[5];

//创建一个数组，名字为a，长度为5个int
```

内存图：

![image-20220302092916369](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220302092916369.png)

例：

```java
package com.smms.demo;

import java.util.Scanner;

public class chapterArray01 {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        //new数组类型时，记得加上数组的长度
        double[] doubles = new double[5];
        for (int i = 0; i < doubles.length; i++) {
            System.out.println("请输入第"+(i+1)+"个数");
            doubles[i] = scanner.nextDouble();
        }
        System.out.println("========================================");
        for (int i = 0; i <doubles.length ; i++) {
            System.out.println("输入的数为"+doubles[i]);

        }
    }
}

```

#### 使用方式2

1. ***<u>先声明数组</u>***

语法：

* 数据类型 数组名[];	或		数据类型[] 	数组名;

* int a[]  / int[]  a;

2. ***<u>创建数组</u>***

语法：

* 数组名 = new 数据类型 [ 大小 ];
* a = new int[5];

```java
//        double[] doubles = new double[5];
//相当于吧使用方法1给拆分成两个
//	1.先声明
        double doubles[];
        //2.再创建
        doubles = new double[5];
```

解释：1.先声明，在内存中相当于创建了一个空的变量，这时没有任何左右

2.再创建，才使得这个数组有意义。不写的话会报空指针异常

### 静态初始化

语法：

数据类型	数组名[] = {元素值，元素值，元素值，......}

[案例](#数组案例01)跳转

### 注意事项和细节

1. 数组是多核相同的数据类型的组合，实现对这些数据的统一管理
2. 数组中的元素可以使任何数据类型，包括基本数据类型和引用数据类型，但不能混用
3. 数组创建后，如果没有赋值，会有默认值：int 0 , short 0 , byte 0 ,long 0, float 0 ,double 0.0 , char \u0000, boolean false , String null;
4. 使用数组的步骤：
   1. 声明数组并开辟空间
   2. 给数组各个元素赋值
   3. 使用数组
5. 数组的下表是从0开始的 
6. 数组下表必须在指定范围内使用，否则报：下标越界异常，比如: int[] arr = new int [5] ; 则有效下标为0-4
7. 数组属于引用数据类型，数组行数据是对象（object）
8. boolean 类型没有赋值的情况下默认false

### 数组赋值机制

1. 基本数据类型赋值，这个值就是具体的数据，而且相互不影响

   ```java
   //基本数据类型赋值，复制方式为值拷贝
   int n1 = 2 ; 
   int n2 = n1 ;
   
   n2的变化不会影响n1
       
   ```

2. 数组再默认情况下是引用传递，赋的值是地址。赋值方式为引用传递

   ```java
   int[] array1 = {1,2,3}
   int[] array2 = array1; 
   
   array2[0] = 10;
   //此时运行的结果 array1的第0个元素会变成10
   
   ```

   

 ![image-20220302141207302](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220302141207302.png)

### 数组拷贝

案例：

```java
int[] arr1 = {1,2,3}
//1. 创建一个新的数组arr2,开辟一个新的数据空间
//2. 大小 = arr1.length
int arr2[] = new int[arr1.length];

//遍历arr1到对应的位置
for( i = 0; i < arr1.length; i++){
    arr2[i] = arr1[i];
}

```

jvm内存图分析:

![image-20220302142048498](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220302142048498.png)

![image-20220302142253236](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220302142253236.png)

### 数组翻转

案例：

要求：需要把数组的元素内容反转。

arr { 1 , 2 , 3 , 4 , 5 }-->{5 , 4 , 3 , 2 , 1}

方式1：

```java
int[] arr = {11 , 22 , 33 , 44 , 55 , 66};

//1. 把 arr[0] 和 arr[5] 进行交换
//2. 把 arr[1] 和 arr[4] 进行交换
//3. 把 arr[2] 和 arr[3] 进行交换
//4. 一共要交换 3 次 = arr.length
//5. 每次交换时，对应的下标 是 arr[i] 和 arr[arr.length - 1 -i]
  int temp = 0;
        int len = arr.length;
        for (int i = 0; i <len/2 ; i++) {
            temp = arr[len-1-i];
            arr[len-1-i] = arr[i];
            arr[i] = temp;
        }
     
     
 }
```

方式2

```java
int[] arr = {11 , 22 , 33 , 44 , 55 , 66};
//1. 先创建一个arr2
        //2. 逆序遍历arr，再将每个元素赋给arr2的元素中
        //3. 增加一个循环变量j
        int[] arr2 = new int[arr.length];

        for (int i = 0,j=arr.length-1 ; j>=0; i++,j--) {
            arr2[j] =arr[i];

        }
//4.当for循环结束，arr2就是一个逆序数组，{66 , 55 , 44 , 33 , 22 , 11}
//5. 让arr指向arr2数据空间,此时arr原来的数据空间就没有变量引用
//会被当做垃圾处理
arr = arr2
    //6. 遍历输出
  
        for (int i = 0; i <arr.length ; i++) {
            System.out.println(arr[i]);
        }
```



### 数组扩容

数组缩减同理

数组添加

要求：实现动态的给数组添加元素效果，实现对数组扩容

1）原始数组使用静态分配int[] arr = {1,2,3}

2）增加的元素4，直接放在数组的最后 arr = {1,2,3,4}

3）用户可以通过如下方法来决定是否继续添加，添加成功，是否继续？y/n

```java
package com.smms.demo;

import java.util.Scanner;

public class chapterArrayAdd {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        char key ;
        int[] arr1 = {1,2,3};


        do {
            int[] arr2 = new int[arr1.length+1];
                for (int i = 0; i < arr1.length; i++) {
                    arr2[i] = arr1[i];
                }
                System.out.println("请输入一个要添加的值");
                arr2[arr2.length - 1] = scanner.nextInt();

            arr1 = arr2;

            System.out.println("是否继续添加？请输入y/n");
            key = scanner.next().charAt(0);

            if (key=='y'){
                System.out.println("继续增加");
            }else if (key== 'n'){
                System.out.println("跳出");
                break ;
            }else {
                System.out.println("输入不合法");
            }
//            将arry1的地址指定到arry2的地址，此时原arry1的地址被没有变量引用，所以被jvm销毁

        }while (true);

        for (int i = 0; i < arr1.length ; i++) {
            System.out.println("arr1 = "+arr1[i]);
        }

    }

}

```







## 排序

介绍

排序的分类：

1. 内部排序：

* 指将需要处理的所有数据都加载到内部存储中进行排序。包括（交换式排序法，选择时排序法和插入式排序法）

2. 外部排序法：
   * 数据量过大，无法全部加载到内存中，需要借助外部存储进行排序。包括（合并排序法和直接合并排序法）。

### 冒泡排序

基本思想：通过对待排序序列从后向前（从下标较大的元素开始），一次比较相邻元素的值若发现逆序则交换，使值较大的元素从前移向后部。像水下的气泡一样逐渐向上冒。

![image-20220303105607719](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220303105607719.png)

特点：

1. 一共有五个元素

2. 一共进行了四轮排序，可以看成外层循环

3. 每1轮排序可以确定一个数的位置，比如第一轮排序确最大数，第二轮确定第二大的数 的位置，依次类推

4. 当进行比较时，如果前面的数大于后面的数，就交换

   

案例说明:

将五个无序：24,69,80,57,13使用冒泡排序，从小到大排序

```java
package com.smms.demo;

public class chapterBall {
    public static void main(String[] args) {
        int tmp = 0;
        int[] a  = {24,69,80,57,13};
       
        for (int i = 0; i < a.length-1; i++) {
            for (int j = 0; j < a.length; j++) {
                if (j>=a.length-1){
                    break;
                } else if (a[j]<a[j+1]){
                    System.out.println("不做交换");
                }else {

                    tmp = a[j];
                    a[j]  = a[j+1];
                    a[j+1] = tmp;
                    System.out.println("交换第"+j+"个数为"+a[j]);
                }
            }
        }
        for (int i = 0; i <a.length ; i++) {
            System.out.println(a[i]);
        }

    }
}

```



## 查找

### 1）顺序查找：

```java
package com.smms.demo;

import java.util.Scanner;

public class exercisesSequence {
    public static void main(String[] args) {
        /*有一个数列：
        * 白眉鹰王，金毛狮王，紫衫龙王，青翼蝠王猜数游戏
        * 从键盘任意输入一个名称，判断数列中是否包含此名称（顺序查找）
        * 要求：如果找到了，就提示找到，并给出下标
        */
        String[] a ={"白眉鹰王","金毛狮王","紫衫龙王","青翼蝠王"};
        Scanner scanner = new Scanner(System.in);
        System.out.println("请输入");
        String next = scanner.next();
        //用于判断是否没找到
        int nub =-1;
        for (int i = 0; i <a.length ; i++) {
            if (next.equals(a[i])){
                System.out.println("找到了");
                //如果找到了就把i的值赋给sub
                nub = i;
                break;
                //如果nub==-1就代表没找到
            }else if (nub == -1){
                System.out.println("没找到");
            }
        }
    }
}

```



### 2）二分查找：



算法部分讲解补充



## 二维数组

介绍：一个数组内，还有数组

要理解的点：

1. 看到定义形式就可知道是不是二维数组
2. 二维数组的每一个元素都是一维数组
3. 二维数组的每个元素是一维数组，所以如果需要得到每个一维数组的值，需要再次遍历
4. 

```java
如果需要访问第（i+1)个一维数组，第（j+1)个值。arr2d[i][j]
 或需要访问第i个一维数组，第j个值。arr2d[i-1][j-1]   
```



案例：

```java
public static void main(String[] args) {
        /*
        * 请用二维数组输入如下图形
         0 0 0 0 0 0
         0 0 1 0 0 0
         0 2 0 3 0 0
         0 0 0 0 0 0
         */

//        1. 定义形式 int[][]
//        2.可以理解为一个数组内的每个元素都是一个数组
        int[][] arr2d= {{0,0,0,0,0,0},{0,0,1,0,0,0},
                        {0,2,0,3,0,0},{0,0,0,0,0,0}};
   System.out.println("二维数组的元素个数"+arr2d.length);
//	二维数组的每个元素是一维数组，所以如果需要得到每个一维数组的值，需要再次遍历
    
    
    
//        获取多个少个一维数组
        for (int i = 0; i < arr2d.length; i++) {
//            遍历二维数组的每一个元素（数组）,
//            arr2d[i].length  获取二维数组内对应的每一个一维数组的长度
            for (int j = 0; j < arr2d[i].length; j++) {
                System.out.print(arr2d[i][j]+"\t");

            }
            System.out.println();
        }
    }
```

### 二维数组内存原理图：

![image-20220304165024843](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220304165024843.png)



### 二维数组的使用方式

方式1：动态初始化

```
1.语法：类型[][] 数组名 = new 类型[大小][大小];
例如： int[][] = new int[2][3];

```

方式2：动态初始化

```
1. 先声明：类型 数组名[][];
2. 再定义（开辟空间）： 数组名 = new 类型[大小][大小];
3. 赋值（有默认值，比如int 类型默认值就是0）
```

方式3：动态初始化

1. 列数不确定
2. java不强制每个数组的长度都一样
3. 例：![image-20220304165929272](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220304165929272.png)

```java
public static void main(String[] args) {
        /*
            动态创建下面二维数组，并输出
            i = 0 : 1
            i = 1 : 2 2
            i = 2 : 3 3 3
         */
        //1. 创建一个二维数组，因为数组内的每一堆数组的元素都是不确定的，所以不填。
        // 填了的话相当于固定了长度
        int[][] arr= new int[3][];
        for (int i = 0; i <arr.length ; i++) {
//            给数组内的一维数组开辟空间
//            如果没有给一堆数组开辟空间，那么这个空间的就是null
            arr[i] = new int[i+1];
//            遍历一维数组，给一堆数组的每个元素赋值
            for (int j = 0; j < arr[i].length ; j++) {
                arr[i][j]= i+1;
            }
        }

//        遍历出这个二维数组
        for (int i = 0; i <arr.length ; i++) {
            for (int j = 0; j <arr[i].length ; j++) {
                System.out.print(arr[i][j]);
            }
            System.out.println();
        }
    }
```

杨辉三角形

![image-20220305143151743](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220305143151743.png)

提示：

1. 第一行有一个元素，第n行有n个元素

2. 第一行的第一个元素和最后一个元素都是1

3. 从第三行开始，对于非第一个元素和最后一个元素的元素的值，arr[i],[j]

4. ```java
   中间的数为：
   arr[i][j]  = arr[i-1][j]+ arr[i-1][j-1]
     
     
     
   ```

   ```java
   package basics.chapterArray;
   
   public class exerciseArrayYangHuiTriangle {
       public static void main(String[] args) {
           int[][] arr =  new int[10][];
           for (int i = 0; i <10 ; i++) {
               arr[i] = new int[i+1];
               for (int j = 0; j < arr[i].length; j++) {
                   if (j==0 || j == arr[i].length-1){
                       arr[i][j] = 1;
                   }else {
                       arr[i][j] = arr[i-1][j]+arr[i-1][j-1];
                   }
   
               }
   
           }
           for (int i = 0; i <arr.length ; i++) {
               for (int j = 0; j <arr[i].length ; j++) {
                   System.out.print(arr[i][j]);
               }
               System.out.println();
           }
       }
   }
   
   
   ```


# 面向对象

## 类与对象

1）类是抽象的，概念的。代表一类事物，比如人类，猫类，狗类。。。。，即它是实例

```java
例：
class cat{
    //属性/也叫成员变量
   // 成员变量 =属性 = field(字段)
	String name;
	int age;
}
//实例
cat c = new ca();
```

2） 对象是具体的，实际的，代表一个具体事务，即是实例

3） 类是对象的模板，对象是类的一个个体，对应一个实例

属性可以使基本数据类型，也可以是引用数据类型(对象，数组)

### 对象在内存中存在的形式（重要）

java内存的结构分析：

1. 栈：一般存放基本数据类型（局部变量）
2. 堆：存放对象（Cat cat ，数组等）
3. 方法区：常量池（常量，比如字符串），类加载信息
4. 示意图：[Cat(name,age,price)]

```java
Person p = new Person();
p.name = "jack";
p.age = 12;

1.先加载Person类信息（属性和方法信息，只会加载一次）
2.在堆中分配空间，进行默认初始化（看规则），
3.把堆中的地址返回给p，p就指向对象
4.进行指定初始化，比如：p.name = "jack",p.age = 12;

    
```





对象和数组都是引用类型

![image-20220307112129768](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220307112129768.png)

如果存放的数据，类型是基本数据类型则存放在堆中，引用的数据类型则存放在方法区

###  注意事项

1） 属性的定义语法同变量，示例：<span style="color:blue">访问修饰符</span><span style= "color:red" > 属性类型  属性名;</span>

2） 属性的定义类型可以为任意类型，包含基本类型或引用类型

3） 属性如果不赋值，有默认值，规则和数组一致

### 创建对象

1. 先声明在创建

   ```java
   CAT cat;
   cat  = new CAT();
   ```

2. 直接创建

   ```java
   CAT cat  = new CAT();
   ```

   

访问属性

```
对象名.属性名；
cat.xxx;
```

### 类对象的内存分配机制

![image-20220307145803905](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220307145803905.png)

## 成员方法

介绍：

用于描述对象的行为，成为方法

案例：

![image-20220307161842380](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220307161842380.png)

```java
package com.smms.demo.method;

public class exercisesMethod01 {
    public static void main(String[] args) {
        Person person = new Person();
        person.speal();
        person.cal01();
        person.cal02(3);
//        调用getSum方法，并给了1,3的值
//        用returnsum接收getSum返回的值
        double returnsum = person.getSum(1,3);

        System.out.println("returnsum="+returnsum);

    }
}
class Person{
    public  void speal(){
        System.out.println("我是一个好人");
    }

    public  void cal01(){
        int sum = 0;
        for (int i = 0; i <= 1000; i++) {
            sum+=i;
        }
        System.out.println("1+~+1000="+sum);
    }
    public  void cal02(int n){
        int sum =0;
        for (int i = 1; i <=n ; i++) {
            sum = sum+i;
        }
        System.out.println("1+n="+sum);
    }

    public double getSum(double a, double b){
        double sum=0;
        sum = a+b;
        System.out.println("a+b="+sum);
//        表示返回sum
        return sum;
    }
}
```

### 内存分析流程图

![image-20220308162432089](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220308162432089.png)

方法的优点：

1. 提高了代码的复用性
2. 可将实现的细节封装起来，然后提供其他用户来调用



### 成员方法的定义

```java
public 返回数据类型\void（表示没有返回值）	方法名(形参列表...){//方法体
语句;
return；//返回值
}
```

1. 参数列表：表示成员方法输入cal(int n)
2. 数据类型(返回类型)：表示成员方法输出，void表示没有返回值
3. 方法主体:表示为了实现某一功能代码块
4. return语句不是必须的



### 注意事项

1. 访问修饰符

2. ``` java
   访问修饰符 返回数据类型\void（表示没有返回值）	方法名(形参列表...){//方法体
   语句;
   return；//返回值
   }
   
   1. 访问修饰符（作用是控制 方法的适用范围）
       如果不写默认访问，[有四种：public protected 默认]
   
   ```

   

3. 返回数据类型

```
1. 一个方法最多有一个返回值
	返回多个结果，返回数组
2. 返回类型可以为任意类型，包含基本类型和引用类型(数组，对象)
3. 如果方法要求有返回数据类型，则方法体中最后执行的语句必须为return值；而且要求返回值类型必须和return的值的类型一致或兼容
4. 如果方法是void，则方法体照片那个可以没有return语句，或者 只写 return；


方法命名；使用驼峰命名法，最好见名知意
```

4. 一个方法可以有0个参数，也可以有多个参数，中间用逗号隔开。例：getSum(int a,int b)

5. 参数类型可以为任意类型，包含基本类型或引用类型。

6. 调用带参数的方法时，一定对应着参数列表传入相同类型或兼容类型的参数

7. 方法定义时的参数成为形式参数（形参）；方法调用时的参数成为实际参数，简称实参。实参和形参的类型要一致或兼容、个数、顺序必须一致

   * ```java
     public static void main(){
     	Method a = new Method();
     	a.input(123,345//这里成为实参);
     }
     
     class Method{
     	public int input(int a,int b//这里成为形参){
     	system.out.print("xxx");
     	return xxx;
     	}
     }
     ```

方法体

​	里面写完成功能的具体语句，可以为输入、输出、变量、运算、分支、循环、方法调用，但里面不能再定义方法！即：方法不能嵌套定义

调用细节

1. 同一类中的方法调用：直接调用即可

   * 直接输入：方法名（参数）即可

2. 跨类中的方法A类调用B类方法：需要通过对象名调用。比如：对象名.方法名(参数)


## 成员方法传参（重要）

基本数据类型

1. ![image-20220310134944831](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220310134944831.png)
2. <span style = "color:red">基本数据类型</span>，传递的值（拷贝），形参的任何改变不影响实参！

引用数据类型

1. ![image-20220310140041330](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220310140041330.png)
2. 引用类型传递的是地址（传递也是值，但值是地址），可以通过形参影响实参。

## 递归机制（recursion）

递归调用的本质，是方法的调用

1. ![image-20220310164428690](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220310164428690.png)
2. 栈是先进后出，先出后进（所以图中的test栈2先输出，然后是3，4）
3. 每次这个栈内的方法执行完成后，外边的方法（图中test方法）都会执行一边
4. 哪里调用就返回给哪里

### 阶乘（factorial）

![image-20220310203253490](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220310203253490.png)

###   递归调用的规则

1. 执行一个方法时，就创建一个新的受保护的独立空间（栈空间）
2. 方法的局部变量是独立的，不会相互影响，比如n变量
3. 如果方法中使用的是引用类型变量（比如数组，或者对象），就会共享该引用类型的数据。
4. 递归必须像退出递归的条件逼近，否则就是无限递归，出现StackOverflowError，死龟了:)
5. 当一个方法执行完毕，或者遇到return，就会执行完毕或者返回时，该方法也就执行

### 斐波拉契数练习

```java
package basics;

public class exerciseRecursion {
    public static void main(String[] args) {
        T t = new T();
        int i = t.racursionNum(4);
        System.out.println(i);

    }

}

class T{
    public int racursionNum(int n1) {
        if (n1 == 1 || n1 == 2) {
            return 1;
        } else {
            return racursionNum(n1 - 1) + racursionNum(n1 - 2);
        }
    }
}

```

解析图

![image-20220310225335626](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220310225335626.png)





## 重载（overload）

介绍：java允许同一个类中，多个同名方法的存在，但要求形参列表不一致！！！

好处：

1. 减轻了起名的麻烦
2. 减轻了记名的麻烦

注意细节：

1. 方法名：必须相同
2. 形参参列表：必须不同（参数类型或个数或顺序，至少有一样不同）
3. 返回类型：无要求

## 可变参数

介绍：

java允许将同一类中多个同名同功能但参数个数不同的方法，封装成一个方法。

基本语法：

```java
访问修饰符	 返回类型	方法名（数据类型 .... 参数名）{
}
```

案例

```java
class hasMestod{
/*
    public int sum(int a,int b){
        return a+b;
    }
    public int sum(int a,int b,int c){
        return a+b+c;
    }
    public int sum(int a,int b,int c,int d){
        return a+b+c+d;
    }
//    ........以此类推
*/

//    可变参数优化
//    上面三个方法名称相同，功能相同，只是参数个数不同---->使用可变参数优化
//    1.int...表示接收的是可变参数，类型时int，即可以接收多个int（0-多）
//    2.使用可变参数时，可以当做数组；来使用，即nums 可以当做数组使用
    public  int sum1(int... nums){
        System.out.println("接收的个数为"+nums.length);
        int sum = 0;
        for (int i = 0; i < nums.length ; i++) {
            sum=sum+nums[i];
        }
        return sum;
    }

}
```

注意事项：

1. 可变参数的实参可以为0或任意多个

2. 可变参数的实参可以为数组

3. 可变参数的本质就是数组

   

4. 可变参数可以和普通类型的参数<u>*一起放在形参列表*</u>，但必须保证可变参数在最后

5. 一个形参列表中只能出现一个可变参数



## 作用域

1. 在java中，主要的变量就是属性（成员变量）和局部变量
2. 我们说的局部变量一般是指在成员方法中定义的变量
3. 作用域的分类
   1. 全局变量：也就是属性，作用域为整个整体
   2. 局部变量：也就是除了属性以外的其他变量，作用域为定义它的代码块中
4. 全局变量可以不赋值，直接使用，因为有默认值（也可指定值），局部变量必须赋值后，才能使用，因为没有默认值。    、   

注意事项和细节

1. 属性和局部变量可以重名，访问时遵循就近原则
2. 在一个作用域中，比如在同一个成员方法中，两个局部变量，不能重
3. 属性生命周期较长，伴随对象的创建而创建，伴随对象的死亡而死亡。局部变量，生命周期较短，伴随它的代码块的执行而创建，伴随代码块的结束而死亡
4. 作用域范围不同：
   1. 全集变量/属性：可以被本类使用，或其他类使用（通过对象调用）
   2. 局部变量：智能在本类中对应的方法中使用
5. 修饰符不同
   1. 全局变量/属性可以加修饰符
   2. 局部变量不可以加修饰符

## 构造器(constructor)

基本介绍：构造方法又称构造器(constructor)，是类的一种特殊方法，它的主要作用是完成对<span style = "color:red">新的对象初始化。</span>



特点：

1. 方法和类名相同
2. 没有返回值
3. 在创建对象时，系统会自动调用该类的构造器完成对对象的初始化



需求案例：

案例1:创建一个人类的对象，显示把一个对象创建好后，再给他的年龄姓名等属性赋值，如果现在我要求，在创建人类对象的时候，就直接指定这个对象的年龄和姓名。 此时可以使用构造器

基本语法：

```java
[修饰符] 方法名(形参列){

	方法体;

}
```

1. 构造器的修饰符可以默认，也可是public，protected，private
2. 构造器没有返回值,也不能写void
3. 方法名和类名必须一样
4. 参数列表和成员方法一样的规则
5. 构造器的调用<span style = "color:red">系统完成</span>



细节：

1. 一个类可以定义多个不同的构造器，即构造器的重载
   * 比如：我们可以再给Person类定义一个构造器，用来创建对象的时候，只指定人名，不需要指定年龄
   * ![image-20220314163037454](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220314163037454.png)
2. 构造器是完成对象的初始化，并不是创建对象
3. 如果程序员没有定义构造器，系统会自动生成一个默认的无参构造器(也叫默认构造方法),比如Person(){ }
4. 一旦定义了自己的构造器，默认的构造器就覆盖了，就不能再使用默认的午餐构造器，除非显示的定义一下，即自己再手写一边Person(){ }







对象创建流程

```java
class Person{
	int age =90;
	String name;
	Person(String n , int a){
	name = n;
	age = a;
	}
}


Person p = new Person("zhangsan" , 20);
```

![image-20220314215432778](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220314215432778.png)

```
1. 先在方法区加载Person类
2. 在堆中开辟一个空间，内部存放形参
   1. 先初始化默认值，0和null，然后再将值赋进去
   2. 当执行到构造器的时候，值才会赋进去
   3. 引用类型的话，会将数据存放在常量池，在堆中放入地址。此时堆中的空间才会有赋值
3. 最后再把堆的地址，赋给栈中的p对象引用 (xxx p = new  xxx;)
```

1. 加载Person.class，只会加载一次。

2. 在堆中分配空间(地址)

3. 完成对象初始化

   3.1 默认初始化 age=0	name = null	

   3.2 显示初始化 age=90,name=null,

   3.3 构造器的初始化 age=20，name=zhangsan

4. 在对象堆中的地址，返回给p(也可理解成对象的引用)

   













## this

案例：

```java
class Person{
	String name;
	int age;
/*
	旧方法：
		int age =90;
		String name;
		Person(String n , int a){ //此时形参的起名不能与属性名一致
		name = n;
		age = a;
     1.如果可以将构造器的形参，直接写成属性名就好了
     2.但是会出现一个问题，根据变量的作用域原则
     3.构造器的name 是局部变量，而不是属性。相当于自己赋给自己
     4.构造器的age 是局部变量，而不是属性、
     5.==>此时使用this关键字	
*/
    public Person(String name,int age){
        this.name/*表示当前对象的属性*/ = name;/*表示当前构造器的局部变量*/
        this.age = age;
    }
	 
}
```

介绍：

java虚拟机会给每个对象分配this，代表当前对象。

分析图：

每一个对象都有一个隐藏的属性this

这个this它指向自己

![image-20220314222909415](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220314222909415.png)

简单说，哪个对象调用this就指向哪个对象





注意事项：

1. this关键字可以用来访问本类的属性，方法，构造器

2. this用于区分当前类的属性和局部变量

3. 访问成员方法的语法：this.方法名(参数列表)；

4. 访问构造器语法：this(参数列表);//注意，只能在构造器中访问另外一个构造器(当有访问构造器的语法this时，必须放在构造器语句里的第一行 )

   * ```java
     class T{
         String name;
         int age;
     	//无参构造器
     	public T(){
             //当执行无参构造器时，我们想去访问有参构造器
             this("zhangsan",12);//这样访问有参构造器
            //当有访问构造器的语法this时，必须放在构造器语句里的第一行 
            
     		System.out.println("T() 构造器");
             
             
             
     	}
     	
     	//有参构造器
     	public T(String name,int age){
             System.out.println("T(String name,int age) 构造器");
         }
     }
     ```

5. this不能再类定义的外部使用，只能在类定义的范围中使用

```java
package chapterObject;
/*
* 创建一个employee类
* 属性有（名字，性别，年龄，职位，薪水）
* 提供三个构造器
* 1.名字，性别，年龄，职位，薪水
* 2.名字，性别，年龄
* 3.职位，薪水*/
public class ObjectHomeWork06 {
}
class Employee{
    String name;
    char sex;
    int age;
    String post;
    double salary;

    public Employee(String name,char sex,int age){
        this.name = name;
        this.sex = sex;
        this.age = age;
    }
    public Employee(String post,double salary){

        this.post = post;
        this.salary = salary;
    }
    public Employee(String name,char sex,int age,String post,double salary){
        this(name, sex, age);
//        因为构造器调用只能放在第一行，所以最多只能调用一个构造器
        this.post = post;
        this.salary = salary;
    }

//    public Employee(String name,char sex,int age,String post,double salary){
//        this.name = name;
//        this.sex = sex;
//        this.age = age;
//        this.post = post;
//        this.salary = salary;
//
//    }
}


```



# 面向对象（中级）

## idea

### 快捷键

```
自定义快捷键
settings - - > Keymap
删除当前行 ctrl+y  自定义 alt+D
复制当前行 ctrl+d

快速格式化代码 ctrl + alt + L
快速运行程序  自定义alt + R

查看类的层级关系 ctrl + H
将光标放在一个方法上，输入ctrl+b，可以定位到该方法的上
自动分配变量名   在后面添加.var
例：new Scanner(System.in).var+回车
会生成Scanner scanner = new Scanner(System.in);
```

### 模板

 设置路径

file -> settings -> editor -> live templates->

可以自己自定义，也可查看预设的模板









## 包

三大作用：

1. 区分相同名字的类
2. 当类不同的时候，可以很好的管理
3. 控制访问范围

基本语法：

package com.xxx;

1. package 关键字，表示打包
2. com.xxx:表示包名

包的本质

就是创建不同的文件/目录保存文件



### 包的命名

规则：

智能包含数字，字母，下划线，小圆点，但不能用数字开头，不能是关键字或保留字

```java
demo.class.exec1 //falsee不允许有关键字class
demo.12		//false,不能数字开头
demo.ad12.oa //true
```

规范

一般是小写字母+小圆点

com.公司名.项目名.业务模块名

例：com.alibaba.taobao.login

```java
com.sina.crm.user
等等
```

### java常用的包

```java
java.lang // lang包是基础包，默认引入，不用手动输入

java.util //系统提供的工具包，工具类，例如Scanner类

java.net // 网络包，网络开发

java.awt  // 是做java的界面开发，GUI
```



包的引入

建议需要什么类就引入什么类，不建议(java.util.* )全部引入







## 访问修饰符

介绍

java提供了四种访问控制修饰符号控制方法和属性(成员变量)的访问权限(范围)

1. 公开级别：public 修饰，对外公开
2. 受保护级别：用protected修饰，对子类和统一包中的类公开
3. 默认级别：没有修饰符号，向同一包的内公开
4. 私有级别：用private修饰，只有类本身可以访问，不对外公开

![image-20220317140746725](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220317140746725.png)

注意事项：

1. 修饰符可以用修饰类中的属性，成员方法以及类
2. 只有默认的和public才能修饰类，并且遵循上述访问权限的特点
3. 成员方法访问规则和属性完全一样













## <u>*封装*</u>（重要）

封装（encapsulation）就是把抽象出来的数据[**属性**]和对数据的操作[**方法**]封装在一起，数据被保护在内部，程序的其他部分只有通过被授权的操作[**方法**]，才能对数据进行操作。

**封装的好处**

1. 隐藏实现细节  方法(连接数据库)<----调用(传入参数)
2. 可对数据进行验证，保证安全合理



封装的实现步骤 ( 三 步 ) 

1. 将属性进行私有化，private

2. 提供一个公共的set方法，对属性进行判断并赋值

   ```java
   public void setXXX(类型	参数名){
   //加入数据验证的业务逻辑
   属性 = 参数名；
   }
   ```

3. 提供一个公共的get方法，用于获取属性的值

   ```java
   public void getXXX(类型	参数名){
   	return xx;
   }
   ```

   



## <u>*继承*</u>（重要）extends

### 继承作用：

解决代码复用性

### 介绍：

相当多个类存在相同的属性（变量）  和方法时，可以从这些类中抽象出父类，在父类中定义这些相同的属性和方法，所有子类不需要重新定义这些属性和方法，只需通过extend来声明继承父类即可

###  基本语法

```java
class 子类 extends 父类{

}
1. 子类会自动拥有父类定义的方法
2. 父类又叫超类，基类
3. 子类又叫派生类

```

示意图

![image-20220318104942566](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220318104942566.png)



### 注意事项

1. 子类继承了所有的属性和方法，但是私有属性不能再子类直接访问，需要通过公共方法访问

2. 子类必须调用父类的构造器，完成父类的初始化

3. 当创建子类对象时，不管使用子类的哪个构造器，默认情况下总会去调用父类的无参构造器，如果父类没有提供无参构造器，则必须在子类的构造器中调用super去指定使用父类的那个构造器完成对父类的初始化工作，否则编译不通过

4. 如果希望指定去调用父类的某个构造器，则显式的调用一下{super ( 参数 ) }

5. super在使用时，需要放在第一行。super只能在构造器中使用

6. super()和this()都只能放在构造器的第一行，因此这两个方法不能共存在一个构造器

7. java所有类都是Object的子类，是所有类的基类   Ctrl+H可以看到类的继承关系

   ![image-20220318165601997](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220318165601997.png)

8. 父类构造器的调用不限于直接父类！将一直往上追溯直到Object类(顶级父类)

9. 子类对多只能继承一个父类(指直接传承)，即java中是单继承机制。

10. 不能滥用继承，子类和父类之间必须满足is-a的逻辑关系

    1. person is a music
    2. person music
    3. music extends  person 



### 继承的本质（分析）

当子类创建号对象以后，建立查找关系

```java
//案例：
class Grandpa{
	String name = "爷爷";
	String hobby = "旅游";
}

class Father extends GrandPa{
	String name = "大头爸爸";
	int age = 30;
}
 class Son extends Father{
 	String name = "儿子";
 }
 
 
 Son son = new Son();
 son.name=?      //儿子
 son.age = ?	 //30	
 son.hobby = ?	 // 旅游
 //		1. 此时请注意，要按照查找关系返回信息
 /*     2. 首先看子类是否有该属性
 		3. 如果子类有这个属性，并且可以访问，则返回信息
 		4. 如果子类没有这个属性，就看父类有没有这个属性(如果父类有该属性，并且可以访问，就返回)
 		5. 如果父类没有4的规则，继续找上级，直到object
   */  
```

### 内存原理图：

 ![image-20220320170828664](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220320170828664.png)

## Super

### 基本介绍

super代表父类的构造器，用于访问父类的属性，方法，构造器

### 基本语法

1. 访问父类的属性，但不能访问父类的private属性[案例]
   * super.属性名；
2. 访问父类的方法名，不能访问父类的private方法
   * super.方法名(参数列表);
3. 访问父类的构造器(这点前面用过);
   * super(参数列表);
   * 只能放在构造器的第一句并只能出现一句

### 细节和注意事项

1. 调用父类的构造器的好处（分工明确，弗雷属性由父类初始化，子类的属性由子类初始化）

2. 当子类中有和父类中成员（属性和方法）重名时，为了访问父类的成员，必须通过super。如果没有重名，使用super、this、直接访问是一样的效果

   * ```java
     案例
     class A{
     	public void cal(){
     		System.out.println("a类的cal方法");
     	}
     }
     class B{
     	public void sum(){
     		System.out.println("b类的sum方法");
     	/*	
     		此时有三种方法调用cal
     		1. 找cal方法时，顺序是：先找本类，如果有，开始调用。
     		2. 如果没有。则找父类（如果有则调用）
     		3. 如果父类没有则继续找父类的父类。以此类推。直到Object类‘
     		
     		提示：如果查找的过程中找到了，但不能访问，则报错
     			 如果查找的过程中没找到。则提示没找到
     	*/
         	cal();
             
            
             this.cal();//等价cal（）；
             
              /*
             跳过本类直接查找父类
             其他规则一样
             */
             super.cal();
             
     	}
     }
     ```

3. super的访问不限于直接父类，如果爷爷类和本类中有同名的成员，也可以使用super去访问爷爷类的成员；如果多个基类（上级类）中都有同名的成员，使用super访问遵循就近原则。（相当于跳过本类，从父类开始按规则找。父类找不到找爷爷类·····）

### super和this的比较

![image-20220320190806497](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220320190806497.png)

![image-20220320190935663](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220320190935663.png)

## 重写（overwrite）

### 基本介绍

简单地说：方法覆盖(重写)就是子类有一个方法，和父类的某个方法的名称、返回类型、参数一样，那么我们就说子类的这方法覆盖了父类的方法。

### 案例

```java
class Animal{
	public void cry(){
		System.out.println("叫");
	}
}
/*
	1. 因为dog是Animal的子类
    2. Dog的cry方法和Animal的cry方法定义形式一样(名称，返回类型，参数)
    3. 这时我们就说Dog的cry方法，重写了Animal的cry方法
  */      
class dog extends Animal{
	public void cry(){
		System.out.println("汪汪汪");
	}
}
```

### 注意事项和使用细节

1. 子类的方法的形参列表，方法名称，要和父类的方法的参数，方法名称完全一样。

2. 子类方法的返回类型和父类方法返回类型一样，或者父类返回类型的子类

   比如 父类返回类型是Object，子类方法返回类型是String

   ```java
   public Object getInfo(){}
   ```

   ```java
   public String getInfo(){}
   ```

3. 子类方法不能缩小父类方法的访问权限public > protected > 默认(default ) > private 

   ```java
   void sayOk(){}
   ```

   ```java
   public void sayOk(){}//这样是可以的，但不能缩小
   ```

### 重写与重载的区别

![image-20220320211941817](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220320211941817.png)

练习

```java
package seatWork;

public class override {
    /*
    * 1. 编写一个Person类，包括属性/private（name,age），
    * 构造器，方法say（返回组我介绍的字符串）
    * 2. 编写一个student类，继承Person类，增加id，score属性/private，
    * 以及构造器，定义say方法（返回自我介绍信息）
    * 3. 在main方法中，分别创建Person和Student对象，调用say方法输出自我介绍*/

    public static void main(String[] args) {
        Person person = new Person("lisi", 123);
        String say1 = person.say();
        System.out.println(say1);

        Student student = new Student("zhangsan",12,12345,100);
        String say = student.say();
        System.out.println(say);
    }
}
class Person{
    private String name;
    private int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public String say(){
        System.out.println("我是父类");
//        System.out.println("name"+getName()+"\t"+"age"+getAge()+"\t");
        return "name"+getName()+"\t"+"age"+getAge()+"\t";
    }
}

class Student extends Person{
    private int id;
    private double score;

    public Student(String name, int age, int id, double score) {
        super(name, age);
        this.id = id;
        this.score = score;
    }
    public int getId() {
        return id;
    }
    public void setId(int id) {
        this.id = id;
    }
    public double getScore() {
        return score;
    }
    public void setScore(double score) {
        this.score = score;
    }

    public String say(){
        return super.say()+"id"+getId()+"\t"+"score"+getScore()+"\t";
//        System.out.println("name"+getName()+"\t"+"age"+getAge()+"\t"
//        +"id"+getId()+"\t"+"score"+getScore()+"\t");
    }
}
```

## <u>*多态*</u>（重要）

 多态可以提高代码的复用性

### 基本介绍

多态(多种)（状态）

1. 方法或对象具有多种形态，是面向对象的第三大特征，多态是建立在封装和继承的基础之上的额

### 多态的具体体现

#### 方法上体现

1. 方法的多态

   重写和重载就体现多态

2. 案例说明

3. 重载上体现

   1. 对某一方法，传入不同的参数，调用不同的方法
   2. ![image-20220320215939959](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220320215939959.png)





### 对象的多态（核心，难点，重点）

要记住几点：

1. 一个对象的编译类型和运行类型可以不一致

   * ```
     例如：
     Animal animal = new Dog();【animal编译类型时Animal，运行类型是Dog】
     animal  = new Cat(); 	【animal的运行类型变成了Cat，编译类型仍然是Animal】
     ```

2. 编译类型在定义对象时，就确定了，不能改变

   * ```
     Animal animal = new Dog()   编译类型在定以后就不能改变，所以可以直接用引用接收其他的运行类型
     animal  = new Cat();
     animal  = new PIG();`````
     ```

3. 运行类型是可以变化的

4. 编译类型看定义时 = 号的左边，运行类型看 = 号的右边

   * ```
     Animal animal = new Dog()  animal就是变异类型，dog就是运行类型
     ```

```java
//编译类型和运行类型的体现
class Animal{
	public void say(){
		System.out.println("动物在叫");
	}
}
class Cat extends Animal{
	public void say(){
		System.out.println("猫在叫");
	}
}

class Dog extends Animal{
	public void say(){
		System.out.println("狗在叫");
	}
}

class test{
	public static void main(String[] args){
		//animal编译类型就是Animal，运行类型Dog
		Animal animal = new Dog();
		animal.say();//因为运行类型是dog，animal的运行类型是dog，所以输出dog类的say方法。
		
        animal = new Cat();
        animal.say();//此时animal的运行类型是cat，所以输出cat类的say方法；
    }
}
```



### 注意事项和细节

多态的前提是：两个对象(类)存在继承关系

#### 多态的向上转型

1. 本质：父类的引用指向了子类的对象

2. 语法：父类类型    引用名 = new    子类类型()；

   ```java
   Father father = new Son();
   //此时可称为向上转型
   ```

3. 特点：编译类型看左边，运行类型看右边

   <span style="color:red;">可以调用父类中的所有成员(需要遵循访问权限),</span>

   <span style="color:red;">不能调用子类中特有成员</span>

   （<span style="color:red;">因为在编译阶段，不能调用那些成员，是由编译类型来决定的。</span>）

   最终运行效果按子类(运行类型)的具体实现，即调用方法时，按照从子类(运行类型)开始查找方法

   然后调用，与前面的方法调用规则一致

#### 多态的向下转型

语法：子类类型   引用名 = (子类类型) 父类引用;

1. 只能强转父类的引用，不能强转父类的对象

   ```java
   //此时的向上转型
   Animal animal = new Cat();
   adimal.a();
   //等等方法，这些方法只能调用父类子类的共同拥有的方法，不能调用子类的特殊方法
   
   //此时这样写
   //强转一下，上述父类的引用
   Cat cat =  (Cat)animal；
       cat.catchMouse();
   ```

   

2. 要求父类的引用必须指向的是当前目标类型的对象

   ```java
   //也就是说animal必须是指向对应的子类
   Animal animal = new Cat();//必须有这句话
   Cat cat =  (Cat)animal；//才能强转成cat类型
   
   ```

   

3. 可以调用子类类型中所有的成员



#### 属性没有重写之说

属性的值看编译类型

```java
例:
class A{
	int count = 1;
}
class B extends A{
	int count = 2;
}

public class test{
	public static void main(String[] atgs){
		A a = new B();
		public.out.print(a.count);
            
        //此时输入的值为1
        //因为属性的值是看编译类型
            
        B b = new B();
        public.out.print(a.count);
        //此时输出2
	}
}
```



#### instanceOf比较操作符，

用于判断对象的类型是否为xx类型或xx类型的子类型

判断对象的运行类型是否为xx类型，或这个xx类型的子类型

```java
class A{
	int count = 1;
}
class B extends A{
	 count = 2;
}
public class test{
	public static void main(String[] atgs){
	BB bb = new BB();
	public.out.print(bb instanceof BB);//true
	public.out.print(bb instanceof AA);//true
       
        
        //编译类型AA ，运行类型BB
     AA aa = new AA();
        public.out.print(aa instanceof AA);//true
       public.out.print(aa instanceof BB);//true 
        	
     Object obj   = new Object();
        public.out.print(obj instanceof AA);//false,因为obj不是AA类，也不是AA的子类
        
}}	
```

#### java动态绑定机制(重要) 

1. 当调用对象方法的时候，该方法会和该对象的内存地址/运行类型绑定
2. 当调用对象属性时，没有动态绑定机制，哪里声明，那里使用

```java
class A{
	public int i =10;
	//2
	public int sum(){
        //3  
		return geti()+10;//5
	}
	
	public int sum1(){
	return i+10;
	}
	public int geti(){
	return i;
	}
}

class B{
	public int i =10;
	
	public int sum1(){
	return i+10;
	}
    //4
	public int geti(){
	return i;
	}
}


A a  = new B()
   //1
a.sum //40
    
   
//因为执行到sum方法，开始准备执行geti方法时，因为有java动态绑定的机制，会跳到b类的geti方法执行
    //再根据继承跳回去
```



####  多态的应用

1）多态数组

数组的定义类型为父类类型，里面保存的实际元素类型为子类型

```java
package seatWork;
import java.security.PrivateKey;

public class polySeatwork {
    public static void main(String[] args) {
        /*
        * 要求创建一个person对象name ，age
        * 两个student 对象和2个teacher对象，统一放在数组中，
        * 并调用每个对象的say方法
        * */
        Person1[] person1s = new Person1[5];
        person1s[0] = new Person1("human",00);
        person1s[1] = new Student1("tom1",12,150);
        person1s[2] = new Student1("tom2",13,143);
        person1s[3] = new teacher("zhangsan",30,4000);
        person1s[4] = new teacher("lisi",28,5000);

        //循环遍历多态数组，调用say方法
        for (int i = 0; i < person1s.length ; i++) {
            //老韩提示， person1s[i]的编译类型是Person，
            // 运行类型是根据实际情况而变化
            System.out.println(person1s[i].say());
        }
    }
}
class Person1{
    private String name;
    private int age;

    public Person1(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
    public int getAge() {
        return age;
    }
    public void setAge(int age) {
        this.age = age;
    }
    public String say(){
        return "name = "+name+"age = "+age;
    }
}

class Student1 extends Person1{

    private double score;

    public Student1(String name, int age, double score) {
        super(name, age);
        this.score = score;
    }
    public double getScore() {
        return score;
    }
    public void setScore(double score) {
        this.score = score;
    }

    @Override
    public String say() {
        return super.say()+"score = "+score;
    }
    public void study(){
        System.out.println(getName()+"学习······");
    }
}

class teacher extends Person1{
    private double salary;

    public teacher(String name, int age, double salary) {
        super(name, age);
        this.salary = salary;
    }
    public double getSalary() {
        return salary;
    }
    public void setSalary(double salary) {
        this.salary = salary;
    }

    @Override
    public String say() {
        return super.say()+"salary = "+salary;
    }
    public void teach(){
        System.out.println(getName()+"教书·············");
    }
}
```

案例升级：如何调用子类的特有方法，比如Teacher 有一个teach，Student有一个study方法。如何调用?

```java
//循环遍历多态数组，调用say方法
        for (int i = 0; i < person1s.length ; i++) {
            //老韩提示， person1s[i]的编译类型是Person，
            // 运行类型是根据实际情况而变化

            //判断person1s[i]的运行类型
            if ( person1s[i] instanceof Student1){
               Student1 student1 =  (Student1)person1s[i];
               student1.say();
               //也可以写成一条语句
               ((Student1)person1s[i]).study();
            }else if (person1s[i] instanceof teacher){
                ((teacher)person1s[i]).teach();
            }else{
                System.out.println("============类型有误==============");
            }
            System.out.println(person1s[i].say());
        }
```

#### 多态参数

方法定义的形参类型为父类型，实参类型允许为子类类型

* polyParameter.java

* ```java
  package seatWork;
  
  public class polyParameter {
      /*
      * 定义员工类Employee，包含姓名和月工资[private]，以及计算年工资getAnnual的方法。
      * 普通员工和经理继承了员工，经理类多了奖金bonus属性和管理manage方法，
      * 普通员工类多了work方法，普通员工和经理类要求分别重写getAnnual方法
      *
      *
      * 测试类中添加一个方法showEmployAnnual（Employee e ),
      * 实现获取任何员工对象的年工资，
      * 并在main方法中调用该方法[e.getAnnual()]
      *
      * 测试类中添加一个方法，testWork，如果是普通员工，
      * 则调用work方法，如果是经理，则调用manage方法
  */
      public static void main(String[] args) {
          GeneralStaff staff = new GeneralStaff("zhangsan", 5000);
          Manager manager = new Manager("lisi", 5000, 10000);
          polyParameter polyParameter = new polyParameter();
          polyParameter.showEmployAnnual(staff);
          polyParameter.showEmployAnnual(manager);
  
          polyParameter.testWork(staff);
          polyParameter.testWork(manager);
  
      }
      public void showEmployAnnual(Emplyee e){
  
          System.out.println(e.getAnnual());
      }
      /*
      * 添加一个方法，testwork
      * 如果是普通员工，则调用work方法
      * 如果是经理则调用manage方法
      * */
      public void testWork(Emplyee e){
          if (e instanceof GeneralStaff){
              ((GeneralStaff) e).work();//向下转型
          }else if (e instanceof Manager){
              ((Manager) e).manage();//向下转型
          }
      }
  
  
  }
  class Emplyee {
      private String name;
      private double salary;
  
      public Emplyee(String name, double salary) {
          this.name = name;
          this.salary = salary;
      }
  
      public String getName() {
          return name;
      }
  
      public void setName(String name) {
          this.name = name;
      }
  
      public double getSalary() {
          return salary;
      }
  
      public void setSalary(double salary) {
          this.salary = salary;
      }
  
      public double getAnnual(){
          double tmp = 12*salary;
  
          return tmp;
      }
  }
  
  class GeneralStaff extends Emplyee{
  
      public GeneralStaff(String name, double salary) {
          super(name, salary);
      }
  
      @Override
      public double getAnnual() {
          return super.getAnnual();
      }
  
      public void work(){
          System.out.println("work method");
      }
  }
  class Manager extends Emplyee{
      private double bonus;
  
      public Manager(String name, double salary,double bonus) {
          super(name, salary);
          this.bonus = bonus;
      }
  
      public void manage(){
          System.out.println("manage method");
      }
  
      @Override
      public double getAnnual() {
          return super.getAnnual()+bonus;
      }
  }
  
  ```


## Obeject类详解

类Object是类的层次结构的根类，每个类都使用Object作为超类，所有对象(包括数组)都实现了这个类的方法

#### equals

==和equals的对比

==是一个比较运算符

1. 既可以判断基本类型，又可以判断引用类型
2. 如果判断基本类型，判断值是否相等。例如：int i = 10; double b = 10.0;
3. 如果判断引用类型，判断的是地址是否相等，即判断是不是同一个对象



 

equals：是Object类中的方法，只能判断引用类型，

判断的是地址是否相等，子类中往往重写该方法，用于判断内容是否相等

案例：

```java
package seatWork;

public class equalsExercise {
    public static void main(String[] args) {
        Person02 person02 = new Person02("zhangsan", 123, '男');
        Person02 person03 = new Person02("zhangsan", 123, '男');
        //在没有重写equals方法时是不相等，此时的方法时比对是否指向同一对象
        System.out.println(person02.equals(person03));
    }
}
class Person02{
//    判断两个Person是否相等
    private String name;
    private int age;
    private char gender;

    public Person02(String name, int age, char gender) {
        this.name = name;
        this.age = age;
        this.gender = gender;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public char getGender() {
        return gender;
    }

    public void setGender(char gender) {
        this.gender = gender;
    }

    public boolean equals(Object obj) {
//        1. 先判断两个是否指向同一对象
        if (this == obj){
            return true;
        }
//        2.进行类型判断
        if (obj instanceof Person02) {
//            3.向下转型，得到所有的属性信息进行比对
            Person02 person02 = (Person02) obj;
            return this.name.equals(person02.name)&&this.age== person02.age&&this.gender==person02.gender;
        }
//        如果不是Person类型，则直接返回false
        return false;
    }

}

```

#### hashCode

介绍：

返回对象的哈希码值，支持此方法是为了提高哈希表的性能

实际上，由object类定义的hashCode方法确定会针对不同的对象返回不同的证书，(这一般是通过将该对象的内部地址转移换成一个整数来实现的，但是java编程语言不需要这种实现技巧)

老韩六小结：

1. 提高具有哈希结构容器的效率

2. 两个引用，如果指向的是同一个对象，则哈希值肯定是一样的

3. 两个引用，如果指向的是不同的对象，则哈希值是不一样的（极大概率不一样）

4. 哈希值主要根据地址号来的！，不能完全将哈希值等价于地址

5. 案例演示obj.hashCode() [测试 A obj1 = new A(); A obj2 = new A(); A obj3 = obj1]

   ```java
   package seatWork;
   
   public class hashCodeExcise {
       public static void main(String[] args) {
           A a = new A();
           A a1 = new A();
           A a3 = a;
           System.out.println("a.hashCode() = "+a.hashCode());       System.out.println("a1.hashCode() = "+a1.hashCode());       System.out.println("a3.hashCode() = "+a3.hashCode());
       }
   }
   class A{
   }
   
   ```

   ![image-20220323164744164](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220323164744164.png)

6. 后面在集合，中hashCode如果需要的话，也会重写

#### toString

介绍：

默认返回：全类名+@+哈希值的十六进制，[查看object的tostring方法]

子类往往会重写toString方法，用于<span style="color:red;background:yellow">返回对象的属性信息</span>

重写toString方法，打印对象或拼接对象时，都会自动调用该对象的toString形式。



当直接输出一个对象时，toString方法会被默认的调用

```
System.out.print(xxx);
等价于System.out.print(xxx.toString);
```



#### finalize()

介绍：

当垃圾回收器确定不存在对该对象的更多引用时，由对象的垃圾回收器调用此方法

1. 当对象被回收时，系统自动调用该对象的finalize方法。子类可以重写该方法，做一些释放资源的操作
2. 什么时候被回收：当某个对象没有任何引用时，则jvm就认为这个对象是一个垃圾对象，就会使用垃圾回收机制销毁该对象，在销毁该对象前，会先调用finalize方法
3. 垃圾回收机制的调用，是由系统来决定的(即有自己的GC算法 )，也可以通过System.gc()主动触犯垃圾回收机制

## 断点调试（debug）

#### 提示：

在断点调试的过程中，是运行状态，是以对象运行类型来执行的

#### 介绍：

​	断点调试是指程序在的某一行设置一个断点，调试时，程序运行到这一行就会停住，然后可以一步一步往下调，调试过程中可以看到各个变量当前的值，出错的话，调试到出错的代码行即显示错误，停下。进行分析从而找到这个bug。

#### 快捷键

* F7（跳入）
  * 跳入方法内
* F8（跳过）
  * 逐行执行代码
* shift+F8（跳出）
  * 跳出方法
* F9（resume，执行到下一个断点）

![image-20220324141333874](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220324141333874.png)



# 面向对象（高级）

## 类变量和类方法

### 一、类变量

案例理解：

```java
public Child{
private String name;

    
//定义一个变量count，是一个类变量（静态变量）static静态
    //该变量最大的特点就是会被Child类的所有的对象实例共享
public static int count = 0;

public Child （String name）{
     this.name = name;
}
    public void join(){
        System.out.println(name+"加入了游戏····")
    }
}



main(){
    //定义一个变量count，统计多少小孩加入了游戏
    //传统方法，定义一个count然后统计
    //int count  = 0;
    
    Child child0 = new Child("xiaoming")；
        child0.join();
    	//count++;
    
    //改进后
    	child0.count++;
    
    Child child1 = new Child("xiaoming")；
        child1.join();
    	child1.count++;
    
    Child child2 = new Child("xiaoming")；
        child2.join();
    	child2.count++;
    
    //类变量可以通过类名来访问
    System.out.println("共有"+child.count+"小孩加入了游戏")
}
```

static变量会开辟一个独立的空间，所以new的对象空间不会再单独创建一个static变量的空间。所以这个static变量空间对于这个类的所有实例是共享的

#### 内存分析

![image-20220402161426676](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220402161426676.png)

1. static变量是对象共享的
2. 不管static变量在哪
   1. static变量是同一个类，所有对象共享
   2. static类变量，在类加载的时候就生成了

#### 定义语法

访问修饰符	static	数据类型	变量名；【推荐】

static	访问修饰符	数据类型	变量名；

#### 类变量访问

类名.类变量名【推荐】

或者	

对象名.类变量名 [静态变量的访问修饰符的访问权限和范围和普通属性是一样的]

推荐使用第一种



#### 使用细节

1. 什么时候使用类变量？
   * 当我们需要让某个类的所有对象都共享一个变量时，就可以使用类变量（静态变量）：比如上述的统计人数的案例
2. 类变量与实际变量的区别
   * 变量是该类的所有对象共享的
   * 实例变量是每个对象独享的
3. 加上static成为类变量或静态变量，否则称为实例变量/普通变量/非静态变量
4. 类变量可以通过<span style="color:red">类名.类变量名</span>或者<span style="color:red">对象名.类变量名</span>来访问。推荐第一种方式访问（前提是得满足访问权限）
5. 实例变量不能通过<span style="color:red">类名.类变量名</span>方式访问
6. 类变量是在类加载时就初始化了，也就是说，及时没有创建对象，只要加载类了，就可使用类变量了
7. 类变量的声明周期是随类的加载开始，随着类的消亡而销毁

### 二、类方法

#### 介绍

类方法也称静态方法

### 格式

````java
访问修饰符	static	数据源返回类型	方法名(){}	【推荐】
static	访问修饰符	数据返回类型	方法名(){}
````



#### 类方法调用

使用方式：

<span style="color:red">类名.类方法名</span>

或

<span style="color:red">对象名.类方法名</span>

#### 使用场景

当方法中不涉及到任何和对象相关的成员，则可以将方法设计成静态方法，提高开发效率。

比如：工具类中的方法utils

Math类、Arrays类、Collections集合类

#### 使用细节

1. 类方法和普通方法都是随着类的加载而加载，将结构信息储存在方法区：
   * 类方法中无this的参数
   * 普通方法中隐含this参数
2. 类方法可以通过类名调用，也可以通过对象名调用
3. 普通方法和对象有关，需要通过对象名调用，比如对象名.方法名（参数），不能通过类名调用
4. 类方法中不允许使用和对象有关的关键字，比如this和super。普通方法(成员方法)可以
5. 类方法(静态方法)中，只能访问 静态变量和静态方法
6. 普通成员方法，既可以访问静态的成员，非静态的方法。可以访问静态成员和非静态成员

#### 总结：

静态方法，只能访问静态的成员，

非静态方法，可以访问静态的 成员和非静态的成员

（前提是必须遵守访问权限规则）

## 理解main方法语法

#### 深入理解main方法

解释main方法的形式：public static void main(String[] args){}

main方法是java虚拟机调用的

1. java虚拟机需要调用类的main()方法，所以该方法的访问权限必须是public

2. java虚拟机在执行main()方法是不必创建对象，所有该方法必须是static

3. 该方法接收String类型的数组参数，该数组中保存执行java命令时传递给所运行的类的参数

4. java执行的程序 参数1 参数2  参数3

   ![image-20220403184106869](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220403184106869.png)

#### 提示

1. 在main（）方法中我们可以直接调用main方法所在类的静态方法或静态属性

2. 但是，不能直接访问该类中的非静态成员，必须创建该类的一个实例对象后，再能通过这个对象去访问类中的非静态成员

3. 例：

   * ```java
     class A{
     	private int a;
     	private static int b;
     	
     	private void a(){
     		System.out.println("非静态方法a");
     	}
     	private static void b(){
     		System.out.println("静态方法a");
     	}
     	
     	
     	
     	public static void main(String[] args){
     		System.out.println("id = " +a);//错误 a是非静态变量，得实例一个对象才能调用
             System.out.println("id = " +new A().a);//这样是正确的，创建了个匿名对象调用
             System.out.println("id = " +b);//正确， 因为b是静态变量，可以直接调用
             System.out.println("id = " +a());//错误，和上述a的非静态变量的原因相同
             System.out.println("id = " +new A().a());//改成这样就是正确的，因为a()是非静态的方法
             
             A a = new A();
             System.out.println("id = " +a.a());//同理
     	}
     }
     ```

   * 



## 代码块

#### 介绍

代码块又称初始化块，属于类中的成员【即 是类的一部分】。类似于方法，将罗技语句封装在方法体中，通过{}包围起来

和方法不同，没有方法名，没有返回，没有参数，只有方法体。而且不用通过对象或类显式调用，而是在家类是，或创建对象时隐式调用。

#### 基本语法

```java
[修饰符]{
	代码
};
```

#### 注意：

1. 修饰符 可选，要写的话，也只能写static
2. 代码块分为两类，使用static修饰的叫静态代码块，没有static修饰的，叫普通代码块
3. 逻辑语句可以为任何罗技语句（输入，输出，方法调用，循环，判断等）
4. ; 号可以写上，也可以省略。

#### 优点

1. 相当于另一种形式的构造器（对构造器的补充机制），可以做初始化的操作
2. 如果多个构造器中都有重复的语句，可以抽取到初始化块中，提高代码的重用性

#### 案例

```java
class Movie{
	private String name;
	private double price;
	pricate String director;
    /*
    使用场景
    1. 下面三个构造器都有相同的语句
    2. 这样重写大量的代码
    3. 可以吧相同语句提取出来，放到一个代码块中
    4. 我们不管调用哪个构造器，创建对象，都会先执行代码块
    5. 代码块调用的顺序都是优先于构造器
    
    */
	
	{
		System.out.println("电影屏幕打开···");
		System.out.println("广告···");
		System.out.println("开始播放电影···");
	
	}
    
    public Movie(String name){
       /* 
        System.out.println("电影屏幕打开···");
		System.out.println("广告···");
		System.out.println("开始播放电影···");
        */
        this.name = name;
    }
    public Movie(String name,double price){
       /* 
        System.out.println("电影屏幕打开···");
		System.out.println("广告···");
		System.out.println("开始播放电影···");
        */
        this.name = name;
        this.price = price;
    }
    public Movie(String name,double price,String director){
       /* 
        System.out.println("电影屏幕打开···");
		System.out.println("广告···");
		System.out.println("开始播放电影···");
        */
        this.name = name;
        this.price = price;
        this.director = director;
    }
}
```

#### 使用细节

1. static代码块也叫静态代码块，作用就是对类进行初始化，

   而且它随着类的加载而执行

   并且只会执行一次。

   如果是普通代码块，每创建一个对象，就执行

   ```java
   //静态代码块
   static{
   	xxxx;
   }
   
   //普通代码块
   {
   	xxxx;
   }
   ```

2. 类什么时候被加载？[重要]

   1. 创建对象实例时（new xxx)
   2. 创建子类对象实例，父类也会被加载
      1. 先在家父类的代码块，再执行子类的
   3. 使用类的静态成员时（静态属性，静态方法）

   案例：A类 extends B类的静态块

   ​			先执行a的静态块，然后再执行b的

   ![image-20220404151232983](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220404151232983.png)

3. 普通代码块，在创建对象实例时，会被隐式调用。

   被创建一次，就会调用一次

   如果只是使用类的静态成员时，普通代码块并不会执行

   

4. 创建一个对象时，在一个类 调用顺序是（重点，难点）

   1. 调用静态代码块和静态属性初始化

      （注意：静态代码块和静态属性初始化调用的优先级一样，如果有多个静态代码块和多个静态变量初始化，则按他们定义的顺序调用

      ```java
      案例理解
          
          因为static的优先级一样，
          所以哪个写在前面，哪个就先执行
      class A{
          
          private static  int n1 = getn1();
          static {
              System.out.println("A's static codeBlock");
          }
      
          public static int getn1(){
              System.out.println("use getn1");
              return 100;
          }
      }
      
      ============================================
      输出结果：
      ============================================
      use getn1
      A's static codeBlock
          
          
      =========================分割线=========================
      //如果更换顺序
      class A{
          static {
              System.out.println("A's static codeBlock");
          }
          
          private static  int n1 = getn1();
          
      
          public static int getn1(){
              System.out.println("use getn1");
              return 100;
          }
      }   
      ============================================
      输出结果：
      ============================================
       A's static codeBlock
      use getn1
         
      ```

      

   2. 调用普通代码块和普通属性的初始化

      （注意：普通代码块和普通属性初始化调用的优先级一样，如果有多个普通代码块和多个普通属性初始化，则按定义的顺序调用） 

      ```java
      //先执行静态的，和上述的一样，
      //然后再执行非静态的，规则也是和上述一样，谁写前面先执行谁
      class A{
          private int b = getn2();
      
          {
              System.out.println("普通代码块被执行");
          }
          static {
              System.out.println("A's static codeBlock");
          }
          private static  int n1 = getn1();
      
          public static int getn1(){
              System.out.println("use getn1");
              return 100;
          }
          public int getn2(){
              System.out.println("getn2 被调用");
              return 1;
          }
      }
      ============================================
      输出结果：
      ============================================
      A's static codeBlock
      use getn1
      getn2 被调用
      普通代码块被执行
          
          
      =========================分割线=========================
      class A{
          {
              System.out.println("普通代码块被执行");
          }
          private int b = getn2();
      
          static {
              System.out.println("A's static codeBlock");
          }
          private static  int n1 = getn1();
      
          public static int getn1(){
              System.out.println("use getn1");
              return 100;
          }
          public int getn2(){
              System.out.println("getn2 被调用");
              return 1;
          }
      }    
      ============================================
      输出结果：
      ============================================
      A's static codeBlock
      use getn1
      普通代码块被执行
      getn2 被调用
      ```

        

   3. 调用构造器

      构造器优先级最低，上述的两个规则执行完成后
      才会执行构造器

      ```java
      class A{
          public A() {
              System.out.println("构造器被执行");
          }
      
          {
              System.out.println("普通代码块被执行");
          }
          private int b = getn2();
      
          static {
              System.out.println("A's static codeBlock");
          }
          private static  int n1 = getn1();
      
          public static int getn1(){
              System.out.println("use getn1");
              return 100;
          }
          public int getn2(){
              System.out.println("getn2 被调用");
              return 1;
          }
      }
      
      ============================================
      输出结果：
      ============================================
      A's static codeBlock
      use getn1
      普通代码块被执行
      getn2 被调用
      构造器被执行
      
      ```

5. 构造器 的最前面其实隐含了super() 和调用普通代码块

   静态相关的代码块，属性初始化，在类加载时，就执行完毕。因此是优先于 构造器和普通代码块执行的

   演示：

   ```java
   class A{
   	public A(){
   		//这里存在隐藏的调用
   			//(1) super();
   			//(2) 调用普通代码块
   			
   		 System.out.println("xxxx");	
   	}
   }
   ```

   ```java
   class AAA{
       public AAA() {
           //这里存在隐藏的调用
           //(1) super();
           //(2) 调用普通代码块
           //因为Object的代码块没有输出
           
           //1.先输出
           System.out.println("AAA的构造器被调用");
       }
   }
   class BBB extends AAA{
       {
   //        根据规则父类的输出完毕后，再调用方法区
   //        2. 再执行普通代码块
           System.out.println("bbb的普通代码块执行");
       }
   
       public BBB() {
           //这里存在隐藏的调用
           //(1) super();
           //(2) 调用普通代码块
   //        等上述执行完毕后，最后执行该语句
           System.out.println("BBB的无参构造被执行");
       }
   }
   ```

6. 创建一个子类对象时(继承关系),他们的静态代码块，静态属性初始化，普通代码块，普通属性初始化，构造方法的调用顺序如下：

   1. 父类的静态代码块和静态属性（优先级一样，按定义的顺序执行）
   2. 子类的静态代码块和静态属性（优先级一样，按定义的顺序执行）
   3. 父类的普通代码块和普通属性初始化（优先级一样，按定义的顺序执行）
   4. 父类的构造器
   5. 子类的普通代码块和普通属性初始化（优先级一样，按定义的顺序执行）
   6. 子类的构造器

7. 静态代码块只能直接调用静态成员(静态属性和静态方法)，普通代码块可以调用任何成员



## 单例设计模式

#### 介绍

1. 所谓单例设计模式，就是采取一定的方法保证在整个的软件系统中，对某个类只能存在一个对象实例，并且只提供一个取得对象实例的方法
2. 单例模式有两种方式：1）饿汉式 2）懒汉式
   1. 二者最主要的区别在于创建对象的时机不同，饿汉式是在类加载就创建了对象实例,而懒汉式在使用时才创建
   2. 饿汉式不存在线程安全问题，懒汉式存在线程安全问题
   3. 饿汉式存在浪费资源的可能。（因为如果程序员一个对象实例都没使用，那么饿汉式创建的对象就是浪费了，懒汉式是使用时才创建，就不存在这个问题
   4. 在javaSE标准类中，java.lang.Runtim就是经典的单例设计模式

演示：

1. 恶汉式

   类加载的时候，对象就被创建实例对象，可能会出现创建了，但是没有使用

   步骤：

   1. 构造器私有化 => 防止直接new

   2. 类的内部创建对象

   3. 向外露出一个静态的公共方法。

   4. 代码实现

   5. ```java
      public class singleDesign {
          public static void main(String[] args) {
              System.out.println(GirlFriend.info());
          }
      
      }
      //有一个女朋友类
      //只能有一个女朋友
      class GirlFriend{
          private String name;
      
      
      //    2.创建一个对象
      //    3.为了能够接收静态方法，需要修饰为static
          private static GirlFriend girl = new GirlFriend(info());
      
      
      
      //    如何保证只能有一个对象实例
      //    public girlFriend(String name) {
      //        this.name = name;
      //    }
      //    1. 改成私有的构造器
          private GirlFriend(String name) {
              this.name = name;
          }
      //    4.创建一个静态方法，用于接收实例对象
          public static String info(){
              return "g";
          }
      
      ```

2. 懒汉式

   使用时才创建实例

   1. 构造器私有化=> 防止直接new

   2. 类的内部创建对象

   3. 向外暴露一个静态的公共方法

   4. ```java
      public class SingleDesign01 {
          public static void main(String[] args) {
              System.out.println(Cat.i);
      //        此时只是初始化了cat ，但没有创建对象，其他的静态参数可以直接调用
              System.out.println(Cat.getCat());
      //        当只有调用了这个方法时，才会创建对象(通过判断发现没有cat类，此时创建后返回)
          }
      }
      //懒汉式
      //希望在程序运行中，只创建一个cat
      
      class Cat{
          private String name;
          public static int i =1;
      //    2.定义一个静态属性static
          private  static Cat cat;
      
      //    3.提供一个公共的static方法 可以返回一个Cat对象
          public  static  Cat getCat(){
              if (cat == null){ //如果还没创建对象
                  cat = new Cat("little cute");
              }
              return cat;
          }
      
      //    1.创建私有构造器
          private Cat(String name){
              this.name = name;
          }
      }
      ```

      

## final关键字

#### 介绍

final / 最后的，最终的

fianl 可以修饰类、属性、方法和局部变量

某些情况下，程序员可能有以下需求，就会使用到final：

1. 当不希望类被继承时，可以用final修饰
2. 当不希望父类的某个方法可以被子类覆盖/重写（override）时，可以用final关键字修饰
3. 当不希望类的某个属性的值被修改，可以使用final修饰
4. 当不希望某个局部变量被修改，可以使用final修饰



#### 使用细节

1. final修饰的属性又叫常量，一般用XX_XX_XX来命名

2. final修饰的属性在定义时，必须赋初始值，并且以后都不能修改，赋值可以在如下位置之一（选择一个位置赋初始值即可）

   1. 定义时：例如  public final double TAX_PATE=0.09;

   2. 在构造器中

   3. 在代码块中

   4. ```java
      class A{
      //定义时赋值
      	public final double ATX_A = 0.9;
      	//在构造器中赋值
      	public final double ATX_B；
      	public A{
      		ATX_B=0.8；
      	}
      	//在代码块中赋值
      	public final double ATX_C；
      	{
      		ATX_C=0.2；
      	}
      }
      ```

3. 如果final修饰的属性是静态的，则初始化的位置只能是

   1. 定义时
   2. 在静态代码块 
   3. 不能再构造器中赋值

4. final类不能被继承，但是可以实例化对象

5. 如果类不是final类，但是含有final方法，则该方法虽然不能重写，但是可以被继承

6. 一般来说，如果一个类已经是final类，就没有必要再将方法修饰成final方法。

7. final不能修饰构造方法（即构造器）

8. final和static 往往搭配使用，效率更高，不会导致类的加载。底层编译器做了优化处理

9. 包装类(integer,Double,Float,Boolean等等都是final),String 也是final类



## 抽象类

```java
编写一个父类
//class Animal{
abstract Animal{
	String name;
	public Animal(String name){
	 this.name = name;
	}
	/*
	这里的eat方法 实现了，没有什么意义
	即父类中的方法不确定性的问题
	
	1.考虑将该方法设计为抽象(abstract)方法
	2.所谓抽象方法就是没有实现的方法
	3.所谓的没有实现就是没有方法体
	4.当一个类存在抽象方法时，就需要将该类声明为abstract类
	
	一般来说，抽象类会被继承，有其子类来实现抽象方法
	*/
    
	//public void eat(){
	//	System.out.println("这个是一个吃方法，但不知道吃啥");
	//}
    
	public abstract void eat();
}
```



#### 介绍

1. 用abstract 关键字修饰的类时，这个类就是抽象类

   1. ```java
      访问修饰符 abstract 类名{
      }
      ```

2. 用abstract 关键字来修饰一个方法时，这个方法就是抽象方法

   1. ```java
      访问修饰符 abstract 返回类型 方法名(参数列表);//没有方法体
      ```

3. 抽象类的价值更多作用是在于设计，是设计者设计好后，让子类继承并实现抽象类()

#### 细节

1. 抽象类不能被实例化
2. 抽象类不一定包含abstract方法。也就是说，抽象类可以没有abstract方法
3. 一旦包含了abstract方法，则这个类必须声明为abstract 
4. abstract 只能修饰类和方法，不能修饰属性和其他的
5. 抽象类可以有任意成员【抽象类的本质还是类】，比如：非抽象方法、构造器、静态属性等等
6. 抽象方法不能有主体，即不能实现。例如：abstract void method()；不能有{}
7. 如果一个类继承了抽象类，则它必须实现抽象类的所有抽象方法，除非它自己也声明为abstract 类（所谓实现就是有那个{}就可，具体内容不管）
8. 抽象方法不能使用private、final和static来修饰，因为这些关键字都是和重写相违背的

#### 抽象类实践-模板设计模式

现有个需求

1. 有多个类，完成不同的任务job
2. 要求能得到各自完成任务的时间

```java
package seatWork;

public class Template {
    public static void main(String[] args) {
        son1 son1 = new son1();
        son1.getCurrentTime();
        son2 son2 = new son2();
        son2.getCurrentTime();
    }

}

abstract class Father{
//在抽象类中定义一个抽象方法，这个方法后期会填入不同子类的不同不同方法
    public abstract void job();
//创建一个子类中的公共部分，在其中添加 不同的部分抽象类(方法)，
// 由于动态绑定机制，当调用该方法时，根据实例不同的子类实现不同的输出结果
//    也就是说相当于创建了个模板，不同的类用填不同的内容
    public void getCurrentTime(){
        long start = System.currentTimeMillis();
        job();
        long end = System.currentTimeMillis();
        System.out.println("用时："+(end-start));
    }
}
class son1 extends Father{
    @Override
    public void job() {
        int sum=0;
        for (int i = 0; i < 10000; i++) {
            sum+=i;
        }
    }
}
class son2 extends Father{

    @Override
    public void job() {
        int sum=0;
        for (int i = 0; i < 60000; i++) {
            sum+=i;
        }
    }
} 
```

## 接口（重要）

#### 介绍

接口就是给出一些没有实现的方法，封装到一起，起到某个类要使用的时候，在根据具体情况吧这些方法写出来

#### 语法

```java
interface 类名 implements 接口{
 自己的属性；
 自己的方法；
 必须实现的接口的抽象方法；
}
```

小结:

1. jdk7之前，接口中所有方法否是抽象方法
2. jdk8之后，接口中可以有实现方法，但需要使用default关键字修饰
3. jdk8之后可以有静态方法
4. abstract关键字可以省略

#### 注意事项

1. 接口不能被实例化

2. 接口中所有的方法是public方法，接口中抽象方法，可以不用填写abstract，因为默认修饰的就是public abstract xxx。

3. 一个普通类实现接口，就必须将该接口的所有方法都实现

4. 抽象类实现接口，可以不用实现接口的方法

5. 一个类同时可以实现多个接口

6. 接口的属性，只能是final的，而且public static final 修饰符，比如：int a =1; 实际上是public static final int a =1；（必须）初始化

7. 接口中属性的访问形式：接口名.属性名

8. 一个接口不能继承其他的类，但是可以继承多个别的接口

   ```java
   interface A extend B,c,d...{}
   ```

9. 接口的修饰符只能是public和默认，这点和类的修饰符是一样的。

小结：

继承vs接口

1. 当子类继承了父类，就自动拥有了父类的功能
2. 如果子类需要拓展功能，可以通过实现接口的方式扩展
3. 可以理解，接口是对java单继承机制的一个补充

继承的价值：解决代码的复用性和可维护性

接口的价值主要在于：设计，设计好各种规范（方法），让其他类去实现这些方法。更加的灵活

## 内部类（重点）

#### 介绍：

一个类的内部又完整的嵌套了另一个类结构。被嵌套的类成为内部类（inner class)，嵌套其他类的类成为外部类(out class)。是我们类的第五大成员

类的五大成员：

1. 属性
2. 方法
3. 构造器
4. 代码块
5. 内部类

#### 基本语法

```java
class Outer{//外部类
	class inner{//内部类
	}
}

class other{//外部其他类
}
```

 

#### 内部类的分类

定义在外部类局部位置上（比如方法内）

##### 1）局部内部类（有类名）

​		说明：局部内部类是定义在外部类的局部位置，比如方法中，并且有类名

```java
//例
class outclass{
  private int n = 100;
  //局部内部类师是定义在外部类的局部位置，通常在方法内
 // 1.第一种在局部位置
 	class innerClass{}
  //2. 在方法内，（局部内部类）
  public void mehtod(){//局部内部类（本质仍然是一个类）
    	class innerClass{
        System.out.print("n="+n);
      }    
  }
}
```

1. 可以直接访问外部类的所有成员，包括私有的

2. 不能添加访问修饰符，因为它的地位就是一个局部变量。局部变量是不能使用修饰符的。但可以使用final修饰，因为局部变量也可以使用final修饰符的

3. 作用域：仅仅在定义它的方法或代码块中

4. 局部内部类---访问---->外部类的成员【访问方式：直接访问】

5. 外部类----访问---->局部内部类的成员

   访问方式：创建对象，再访问（注意：必须在作用域内）

6. 外部其它类---->不能访问---->局部内部类（因为 局部内部类地位是一个局部变量）

7. 如果外部类和局部内部类的成员重名时，默认遵循就近原则，如果想访问外部类的成员，则可以使用（外部类名.this.成员）去访问

8. ```java
   class Outer{
   	private int n1 = 10;
   	private static String name = "张三";
   	public void say(){
   		int n3 = 30;
         //局部内部类是定义在外部类的局部位置，通常在方法  
           //不能添加访问修饰符，可以使用final修饰
     class localInner{//局部内部类（本质仍然是一个类）
       int n1 = 100;
      int n2 = 40;
           //可以直接访问外部类的所有成员，包括私有的    
         public void show(){
         //默认输入内部类的n1的值 100
   	    System.out.print("n1="+n1);
         //输入outer.this.n1 输出的才是外部类的n1
         System.out.print("n1="+outer.this.n1);
           
         }
   	}
   }
     //外部类使用内部类
     localInner inner = new localInner();
     inner.show();
    }
   
   
   
   //外部其他类
   
   ```

9. 

##### 2）匿名内部类（没有类名，重点！！！！）

###### 介绍：

1. 本质是类
2. 是一个内部类
3. 该类没有名字
4. 同时还是一个对象

匿名内部类是定义在外部类的局部位置

比如在方法中，并且没有类名

###### 基本语法

```java
new 类 或 接口（参数列表）{
	类体
};

anonymous
```

###### 演示 

```java
package chapterObjectHeightLevel;

public class AnonymousClass {
    public static void main(String[] args) {
        outer outer = new outer();
        outer.method();
    }
}

class outer{//外部类
    private  int n1 =10;
    public  void method(){
        //现有一个需求，使用IA接口，并创建对象

//        传统方法：新建一个类tiger 实现IA接口，并new tiger调用
//        IA tiger = new Tiger();
//        tiger.cry();
//        当此时的需求是只需要这个Tiger类使用一次，并且以后再也不使用
//        如果再用传统方法的话，会造成资源浪费，而且没有必要再去新建一个类
//        此时就需要匿名内部类来简化开发，如下
        IA tiger = new IA(){
            /**
             *此时底层是这样的
             * class xxx(该类名是系统自动创建的) implements IA{
             *     @Override
             *     public void cry() {
             *         System.out.println("老虎叫`````");
             *     }
             * }
             *
             * 之后在让tiger指向xxx的地址
             */
            @Override
            public void cry() {
                System.out.println("老虎叫`````");
            }
        };
        tiger.cry();



        //演示基于类的匿名内部类
//        1. father的编译类型 Father(不加{}号)
//        2. father的编译类型 xxx$2(加{}号）
//        2.1 底层会创建匿名内部类
        Father father = new Father("tiger"){
            @Override
            public void test() {
                System.out.println("override test method");
            }
            /**
            * 相当于创建了哥匿名内部类重写了test方法
            * class xxx implement test{
             *      @Override
             *      public void test() {
             *          System.out.println("override test method");
             *       }
             * }
             * 然后再将father指向xxx的地址
            * */
        };
        father.test();

    }

}

interface IA{
    public void cry();
}

//class Tiger implements IA{
//
//    @Override
//    public void cry() {
//        System.out.println("老虎叫`````");
//    }
//}

class Father{
    public Father(String name) {

    }
    public void test(){

    }
}

```



###### 注意细节

1. 匿名内部类既是一个类的定义，同事它也是一个对象，因此从语法上来看，它既有定义类的特征，也有创建对象的特征，对前面的代码分析可以看出这个特点，因此调用匿名内部类方法有两种

   ```java
   //1.第一种方式
   new A{
   @override
   	public void cry(){
   	System.out.print("hello");
   	}
   }.cry();
   
   //2.第二种方式
   A a=new A{
   @override
   	public void cry(){
   	System.out.print("hello");
   	}
   }
   a.cry();
   ```

2. 可以访问外部类的所有成员，包括私有的

3. 不能添加访问修饰符，因为它的地位就是一个局部变量

4. 作用域：方法或代码块中

5. 匿名内部类--->范围跟--->外部类成员

6. 外部其他类--->不能访问--->匿名内部类（因为 匿名内部类地位是一个局部变量）

7. 如果外部类和内部类的成员变量重名时，内部类访问的话，默认就是就近原则，如果想访问外部，可以使用（外部类名.this.成员）去访问





定义在外部类的成员位置上

##### 1）成员内部类（没用static修饰）

介绍：

1. 成员内部类是定义在外部类的成员位置，并且没有static修饰

   ```java
   class outer{
   	private int n1 =10;
   	public String name = "zhangsan";
   	
   	class inner{
   		public void say(){
   			System.out.print("outer n1 = "+n1+"outer name = "+name);
   		}
   	}
   }
   ```

2. 可以添加任意访问修饰符（public、protected、默认、private），因为它的地位是一个成员

3. 作用域

   和外部类的其他成员一样，为整个类体比如前面的案例，在外部类的成员方法中创建成员内部类对象，再调用方法

4. 成员内部类-->访问--->外部类成员

   (比如属性)【访问方式：直接访问】

5. 外部类 ---访问---内部类

   访问方式：创建对象，再访问

6. 外部其他类-----访问-----成员内部类

   ```java
   //三种方式:
   //1
   outer.inner class = new outer.new inner;
   
   // 第二种方式
    1.定义一个方法，用于创建内部类并返回内部类的实例
      public inner getInner(){
      Inner inner  = new Inner();
      return inner;
    }
   2. 在需要的地方new一个外部类.这个方法
     Outer.Inner inner = new Outer.getInner();
   
   //3这个方法不建议使用
     
     new Outer().new Inner();
   
   ```

7. 如果外部类和内部类的成员重名时，内部类访问的话，默认遵循就近原则，如果想访问外部类的成员，则可以使用（外部类名.this.成员）去访问

   ![image-20220409142725630](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220409142725630.png)

##### 2）静态内部类（使用static修饰）

###### 介绍

静态内部类定义在外部类的成员位置，并且有static修饰

1. 可以直接访问外部的所有静态成员，包含私有的，但不能直接访问非静态成员
2. 可以添加任意访问修饰符（public、protected、默认、private），因为它的地位就是一个成员
3. 作用域：同其他的成员，为整个类体

```java
class outer{
private int n1=10;
private static String name = "zhangsan";

//inner就是静态内部类
  //1. 放在外部类的成员位置
  //2. 使用static修饰
  //3. 不能直接访问非静态成员
  //4. 可以添加修饰符
	static class Inner{
		public void say(){
      	System.out.println(name);
    }
	}
}
```

4. 静态内部类---访问----外部类

   （比如：静态属性）[访问方式：直接访问所有静态成员]

5. 外部类--访问---静态内部类 

   访问方式：创建对象，再访问

6. 外部其他类 --访问 --内部类

   访问方式：

   ```java
   //访问方式1
   //因为静态内部类，是可以通过类名直接访问（前提是满足访问权限）
   Outer.Inner inner = new Outer.Inner();
   inner.xxx();
   //访问方式2
   //写一个方法，返回静态内部类的实例
   public Inner getInner(){
     return new Inner();
   }
   Outer.Inner inner = Outer.getInner();
   
   inner.xxx();
   
   //或者将方法换成静态
   public static Inner getInner(){
     return new Inner();
   }
   
   
   
   ```

7. 如果外部类和静态内部类的成员重名时，静态内部访问的时候，默认遵循就近原则，如果想访问外部类的成员，则可以使用（外部类名.成员）去访问



# 枚举和注解

## 枚举（enum）

### 介绍

1）枚举对应的英文（enumeration,简写enum）

2）枚举是一组常量的集合

3）可以理解：枚举属于一种特殊的类，里面只包含一组有限的特定对象（比如一年只有四个季节，建一个季节类的话只能有四个，而且有被添加其他季节的风险）



### 实现方式

#### 1）自定义枚举

1. 不需要提供set方法，因为枚举对象通常为只读
2. 对枚举对象/属性使用final +static共同修饰，实现底层优化
3. 枚举对象通常使用大写，常量的命名规范
4. 枚举对象根据需要，也可以有多个属性

```java
package chapterEnum;

public class understandForEnum {
    public static void main(String[] args) {
        season autumn = season.AUTUMN;
        System.out.println(autumn.getSeasonName()+autumn.getSeasonDescription());

    }
}
//定义一个季节类
class season{
    private String seasonName;//季节名称
    private String seasonDescription;//季节描述
  //1.将构造器私有化
  //2.去掉setxx方法，防止属性被修改
  //3.在season内部，直接创建固定的对象
  //4.优化，添加final

    public String getSeasonName() {
        return seasonName;
    }

    public String getSeasonDescription() {
        return seasonDescription;
    }

    private season(String seasonName, String seasonDescription) {
        this.seasonName = seasonName;
        this.seasonDescription = seasonDescription;
    }
//定义了四个对象
    public final static season SPRING = new season("春天","温暖");
    public final static season SUMMER = new season("夏天","炎热");
    public final static season AUTUMN = new season("秋天","凉爽");
    public final static season WINTER = new season("冬天","寒冷");
}

```

总结：定义枚举类型有一下几个特点

1. 构造器私有化
2. 本类内部创建一组对象
3. 对外暴露对象（添加public final static 修饰）
4. 可以提供get方法，但不需要提供set方法

#### 2）使用enum关键字实现

```java
package chapterEnum;

public class understandForEnum02 {
    public static void main(String[] args) {
        System.out.println(season02.SPRING);
    }
}
enum season02{
    /**
     * 实现步骤
     * 1.使用enum代替class
     * 2.直接使用 常量名(实参列表)
     *   SPRING("春天","温暖"),
     *   如果有多个常量则用,号隔开
     *
     * enum修饰必须将常量对象写在第一行
     *  必须写在定义的变量和方法前面
     *
     * 3.编写常量，私有构造器和get方法
     * */

    SPRING("春天","温暖"),
    SUMMER("夏天","炎热"),
    AUTUMN("秋天","凉爽"),
    WINTER("冬天","寒冷");


    private String seasonName;//季节名称
    private String seasonDescription;//季节描述

    public String getSeasonName() {
        return seasonName;
    }

    public String getSeasonDescription() {
        return seasonDescription;
    }

    private season02(String seasonName, String seasonDescription) {
        this.seasonName = seasonName;
        this.seasonDescription = seasonDescription;
    }

    @Override
    public String toString() {
        return "season02{" +
                "seasonName='" + seasonName + '\'' +
                ", seasonDescription='" + seasonDescription + '\'' +
                '}';
    }
    //定义四个固定对象
    /*
    public final static season02 SPRING = new season02("春天","温暖");
    public final static season02 SUMMER = new season02("夏天","炎热");
    public final static season02 AUTUMN = new season02("秋天","凉爽");
    public final static season02 WINTER = new season02("冬天","寒冷");
*/


}
```

##### 注意事项

1. 当我们使用enum关键字开发一个枚举类时，默认会继承Enum类
2. 传统的public static final SPRING = new season("春天","温暖");简化成SPRING("春天","温暖"),这里必须知道，它调用的是哪个构造器
3. 如果使用无参构造器 创建枚举对象，则实参列表和小括号都可以省略
4. 当有多个枚举对象时，使用，号间隔，最后一个分号结尾
5. 枚举对象必须放在枚举的行首



### enum常用方法说明

使用关键字enum时，会隐式继承Enum类，这样我们就可以使用Enum类的相关方法

![image-20220409204654918](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220409204654918.png)

```java
    public static void main(String[] args) {
//        使用season02 枚举类，演示各个方法
        season02 summer = season02.SUMMER;
//        输出枚举对象的名字
//        summer.name();
        System.out.println(summer.name());

//        ordinal()输出的是该枚举对象的次序/编号，按枚举的顺序从0开始编号
//        summer枚举对象时第二个，因此返回 1
        System.out.println(summer.ordinal());

//        从反编译可以看出values方法，返货season02[]
//        含有定义所有的枚举对象
        season02[] values = season02.values();
        for (int i = 0; i <values.length ; i++) {
            System.out.println(values[i].name());
        }
//        增强for循环演示
//        每执行一次values就会扔一个对象给season、
//        简单来说就是依次取出数组赋给season
        System.out.println("==========增强for=========");
        for(season02 season:values){
            System.out.println(season.name());
        }

//        valueOf:将字符串转换成枚举对象，要求字符串必须VT为己有的常量名，否则会报错
//        1.根据输入的"xia"到season02中的枚举对象去查找
//        2.如果找到了，就返回，如果没有找到就报错，如下这个例子
        /*season02 vaof = chapterEnum.season02.valueOf("xia");
        System.out.println("vaof = "+ vaof);*/
//        3.只要valueOf()中的参数和枚举对象一致才能正常返回，如下
        season02 xia = chapterEnum.season02.valueOf("SUMMER");
        System.out.println("xia = " +xia);

//        compareTo:比较两个枚举常量，比较的是编号
//        就是把season02.SPRING和season02.SUMMER的编号进行比较
//        底层是第一个的编号减去第二的编号，
//        如果=0则是相等的，
//        如果大于1，则代表前面那个编号大于后面一个编号
//        如果小于1，则反之
        System.out.println(season02.SPRING.compareTo(season02.SUMMER));//= -1
        System.out.println(season02.SPRING.compareTo(season02.WINTER));//= -3

    }
```

### 使用细节

1. enum修饰的类不能在继承其他父类，因为enum会隐式继承一个Enum类
2. enum实现的类，仍然是一个类，所以还是可以实现接口的



### Switch中使用枚举

案例

1. ![image-20220410224921752](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220410224921752.png)

2. ```java
   package homeWork.Annotation;
   
   public class AnnotationHomeWork08 {
       public static void main(String[] args) {
   //        Color.BLACK.show();
   //        Color.RED.show();
       Color red = Color.RED;
   //    在小（）内放入枚举对象
   //        在每个case后，直接写上枚举类，定义枚举对象即可
           switch (red){
               case RED:
                   System.out.println("红色");
                   break;
               case BLUE:
                   System.out.println("蓝色");
                   break;
               case BLACK:
                   System.out.println("黑色");
                   break;
               case YELLOW:
                   System.out.println("黄色");
                   break;
               case GREEN:
                   System.out.println("绿色");
                   break;
               default:
                   System.out.println("没匹配到");
   
           }
       }
   }
   interface Tint{
       public void show();
   }
   enum Color implements Tint{
       RED(255,0,0),
       BLUE(0,0,255),
       BLACK(0,0,0),
       YELLOW(255,255,0),
       GREEN(0,255,0);
   
       private int redValue;
       private int greenValue;
       private int blueValue;
   
       Color(int redValue, int greenValue, int blueValue) {
           this.redValue = redValue;
           this.greenValue = greenValue;
           this.blueValue = blueValue;
       }
   
       @Override
       public void show() {
           System.out.println(redValue+"\t"+greenValue+"\t"+blueValue);
       }
   }
   
   ```



## 注解

#### 介绍

1. 注解(Annotation)也被称为元数据(Metadata)，用于修饰解释包、类、方法、属性、构造器、局部变量等数据信息
2. 和注解一样，注解不影响程序逻辑，但注解可以被编译或运行，相当于嵌入在代码中的补充信息
3. 在javaSE中，注解的使用目的比较简单，例如标记过时的功能，忽略警告等，在javase中注解占据了更重要的角色，例如用来配置应用程序的任何切面，代替javaee旧版中所遗留 的繁冗代码和xml配置等

使用Annotation时，前面要加@符号，并把Annotation当成一个修饰符使用。用于修饰它支持的程序元素

1. @Override：限定某个方法，是重写父类方法，该注解只能用于方法

   ```java
   class son extends father{
   //1.@Override注解方法fly方法上，表示子类fly方法重写了父类的fly
   //2.如果这里没有写@Override ，还是重写了fly
   //3.如果写了@Override注解，编译器就会去检查该方法是否真的重写了fly方法，
   	如果的确重写了，则编译通过。如果没有构成重写，则编译错误
   @Override
   public void fly(){
    System.out.println("son fly...");
   }
   }
   ```

   @Override只能修饰方法，不能修饰其他类

2. @Deprecated：用于表示某个程序元素(类、方法等)已过时

3. @SuppressWarnings：抑制编译器警告

   1. 当写一些方法时，会出现一些无关不影响运行的警告。

      可以使用@SuppressWarnings来抑制警告信息

   2. 可以在@SuppressWarnings{""}中写入希望抑制的警告信息

   3. ![image-20220410190809537](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220410190809537.png)

   4. 位置在哪就屏蔽哪里 



### 元注解（了解）

@Target是修饰注解的注解，称为元注解  （了解）

元注解的种类（使用不多，要求看到直到是干啥的）

#### 1）Retention //指定注解的作用范围，三种SOURCE,CLASS,RUNTIME

说明：

只能用于修饰一个Annotation定义，用于指定该Annotation可以保留多长时间，

@Rentention包含一个RententionPolicy类型的成员变量，使用@Rentention时必须为该value成员变量指定值

@Rentention的三种值：

RententionPolicy.SOURCE //编译器使用后，直接丢弃这种策略的注释

RententionPolicy.CLASS // 编译器将把注释记录在class文件中，当运行java程序时，JVM不会保留注释，这是默认值

RententionPolicy.RUNTIME  //编译器将把注解记录在class文件中，当运行java程序时，JVM会保留注释，程序可以通过反射获取该注释

示意图：

![image-20220410203107921](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220410203107921.png)

#### 2）Target     //指定注解可以在哪些地方使用

用于修饰Annotation定义，用于指定被修饰的Annotation能用于修饰哪些程序元素

简单来说就是在哪些元素上使用

@Target   也包含一个名为value的成员变量	

Target(value = CONSTRUCTOR（构造器）, FIELD（field） , LOACL_VARIABLE（局部变量）, METHOD（方法）,PACKAGE（包）,PARAMETER ,TYPE )

#### 3）Documented    //指定该注解是否会在javadoc中体现

@Documented   用于指定该元注解修饰的Annotation类将被Javadoc 工具提取成文档，即在生成文档时，可以看到注解

定义Documented  注解必须设置Retention 值为RUNTIME

#### 4）Inherited    //子类会继承父类注解



# 异常

## 异常的概念

### 介绍

java语言中，将程序执行中发生的不正常情况成为“异常”。（开发过程中的语法错误和逻辑错误不属于异常）

执行过程中所发生的异常事件可分为两类

1. Error（错误）：java虚拟机无法解决的严重问题。例如：JVM系统内部错误，资源耗尽等严重情况。例：StackOverflowError[栈溢出]和OOM（out of memory),Error是严重错误，程序会崩溃。
2. Exception：因为，其他因编程错误或偶然的外在因素导致的一般性问题，可以使用针对想的代码进行处理，例如空指针访问，视图读取不存在的文件，网络连接中断等等，Exception分为两大类，运行时异常[程序运行发生的异常]和编译时异常[编译时，编译器查出的异常]



## 异常体系图（重要）

![image-20220411214601035](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220411214601035.png)

![image-20220411215335526](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220411215335526.png)

小结：

1. 异常分为两大类，运行时异常和编译时异常

2. 运行时异常，编译器不要求强制处置的异常，一般是指编程时的逻辑错误，是程序员应该避免出现的异常。java.lang.RuntimeException类及它的子类都是运行程序

3. 对于运行时异常，可以不做处理，因为这类异常很普遍，若全处理可能会对程序的可读性和运行效率产生影像

4. 编译时异常，是编译器要求必须处置的异常

    

## 常见的异常

### 常见的运行异常

#### 1）NullPoniterException 空指针异常

1. 当程序试图在需要对象的地方使用 null时，抛出该异常

#### 2 ) ArithmeticException	数字运算异常

1. 当出现异常的运行条件时，抛出此异常
2. 例如 一个整数"除以零"时，抛出此类的一个实例

#### 3）ArrayIndexOutOfBoundsException	数组下标异常

1. 用非法索引访问数组时抛出的异常，如果索引为负或者大于等于数组大小，则该索引为非法索引

#### 4）ClassCastException	类型转换异常

1. 当试图将对象强制转换为不是实例的子类时，抛出该异常

#### 5）NumberFormatException	数字格式不正确异常[]

1. 当应用程序试图将字符串转换成一种数值类型，但该字符不能转换为适当格式时，抛出该异常
2. 使用该异常我们可以确保输入的是满足条件的数字

### 常见的编译异常

#### 介绍

编译异常是指在编译期间。就必须处理的异常，否则代码不能通过编译

#### 常见的编译异常

1. SQLException	//操作数据库时，查询表可能发生的异常
2. IOException		//操作文件时，发生的异常
3. FileNotFoundException	//当操作一个不存在的文件时，发生异常
4. ClassNotFoundException	//加载类，该类不存在时，异常
5. EOFException		//操作文件，到文件末尾，发生异常
6. IIIegalArguementException	//参数异常



## 异常处理概念

### 基本介绍

异常处理就是当异常发生时，对异常处理的方式

### 异常处理方式

#### 1）try-catch-finally

程序员在代码中捕获发生的异常，自行处理

```java
try{
	代码/可能有异常
}catch(Exception e){
//捕获的异常，传给e
//1.当异常发生时
//2.系统将异常封装成Exception对象e，传递给catch
//3.得到异常对象后，程序员自己处理
//4.如果没有发生异常，则catch代码块不执行
}finally{
    //不管try代码块是否有异常发生，始终都要执行finally
    //通常将释放资源的代码方法finally代码块中
}
```



#### 2）throws

将发生的异常抛出，交给调用者（方法）来处理，最顶级的处理者就是JVM

##### 处理机制图

![image-20220411224543192](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220411224543192.png)



throws处理机制

1. try-catch-finally和throws二选一
2. 如果程序员，没有显示是处理异常，默认throws

## 异常处理分类

### try-catch方式处理异常说明

#### 1）java提供try和catch块来处理异常。

try块用于包含可能出错的代码块。catch用于处理try块中发生的异常，可以根据需要在程序中有多个数量的try...catch块

#### 2）基本语法

```java
try{
//可疑代码
//将异常生成对应的异常对象，传递给catch块
}catch(异常){
//对异常的处理
}
//没有finally是可以通过的
```

```java
//使用案例
try{
String str = "糖";
int a  = Integer.parseInt(str);
System.out.println("数字="+a);
}catch(Exception e){
System.out.println("异常信息="+e.getMessage());
}
```

#### 注意事项

1. 如果异常发生了，则异常发生后面的代码不会执行，直接进入到catch块

2. 如果异常没有发生，则顺序执行try代码块，不会进入到catch块

3. 如果希望不管是否能发生异常，都执行某段代码块（比如关闭链接，释放资源等）、

4. 可以有多个catch语句，捕获不同的异常（进行不同的业务处理），要求是父类异异常在后，子类异常在前，比如（Exception 在后，NullPointerException 在前）如果发生异常，只会匹配一个catch

   1. ```java
      例:
      try{
      
      }catch(NullPointerException e){
      
      }catch(Exception e){
      
      }finally{
      
      }
      
      ```

5. 可以记性try-finally配合使用，这种方法相当于没有捕获异常，因此程序会直接崩掉

   1. 应用场景：就是执行一段代码，不论是否发生异常，都必须执行某个业务逻辑

#### 小结

1. 如果没有出现异常，则执行try块中所有语句，不执行catch块中的语句，如果有finally，最后还要执行finally语句
2. 如果出现异常，则try块异常发生后，剩下的语句不在执行，将执行catch块中的语句，如果有finally，最后还要执行finally里面的语句



### throws异常处理

#### 介绍：

1）如果一个方法（中的语句执行时）可能生成某种异常，但是并不能确定如何处理异常，则此方法应显示的声明抛出异常，表明该方法将不对这些异常进行处理，而且由该方法的调用者负责处理

2）在方法声明throws语句可以声明排除异常的列表，throws后面的异常类型可以是方法产生的异常类型，也可以是它的父类

#### 注意事项

1. 对于编译异常，程 序必须处理，比如try-catch或者throws
2. 对于运行时异常，程序中如果没有处理，默认就是throws的方式处理
3. 子类重写父类的方法是，对抛出异常的规定：子类重写的方法，所抛出的异常类型要么和父类抛出的异常一直，要么为父类抛出的异常的类型和子类型
4. 在throws过程中，如果有try-catch，就相当于处理异常，就可以不必throws
5. ![image-20220412135104986](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220412135104986.png)
6. 

## 自定义异常  

### 介绍：

当程序中出现了某些“错误”，但该错误信息并没有在Throwable子类中描述处理，这个时候可以自己设计异常类，用于描述错误信息。

### 自定义异常的步骤

1. 定义类：自定义异常类名（程序员自己写）继承Exceotion或RuntimeException
2. 如果继承Ecxeption，属于编译异常
3. 如果继承RuntimeException，属于运行异常（一般来说，继承RuntimeException）

```java
//当我们接受Person对象年龄时，要求范围在18-120之间，否则抛出一个自定义异常（要求继承RuntimeException），并提示
public class CustomException {
    public static void main(String[] args) {
        int age =30;
//        结果取反
        if (!(age>=18&&age<=120)){
//            通过构造器设置输出信息
            throw new AgeException("年龄需要在18-120之间");
        }
        System.out.println("你的年龄为"+age);
    }
}
//定义一个异常类继承RuntimeException
//一般情况下，我们自定义异常都继承RuntimeException
//也就是说大都是定义为运行时异常，好处是我们可以使用默认处理机制
//即比较方便
class AgeException extends RuntimeException{
//    定义一个构造器
    public AgeException(String message) {
        super(message);
    }
}
```



## throw和throws的对比

|        | 意义                     | 位置       | 后面跟的东西 |
| ------ | ------------------------ | ---------- | :----------: |
| throws | 异常处理的一种方式       | 方法声明处 |   异常类型   |
| throw  | 手动生成异常对象的关键字 | 方法体中   |   异常对象   |

throws

```java
public void xxx() throws Exception{
    //throws通常放在定义方法的末尾
} 
```

throw

```java
//throw后面跟的是异常对象
throw new AgeException("年龄需要在18-120之间");
```



# 常用类

## 包装类

### 包装类的分类   Wrapper

1、针对八种基本数据类型相应类型的引用类型---包装类

2、有了类的特点，就可以调用类中的方法

| 基本数据类型 |  包装类   |
| :----------: | :-------: |
|   boolean    |  Boolean  |
|     char     | Character |
|     byte     |  `Byte`   |
|    short     |  `Short`  |
|     int      | `Integer` |
|     long     |  `Long`   |
|    float     |  `Float`  |
|    double    |  `Doble`  |

上述标出来的6个数据类型父类均为Number

![image-20220412164154544](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220412164154544.png)

### 包装类和基本数据的转换

#### 案例

演示包装类和基本数据类型的相互转换，以int和integer演示

1）jdk5前的手动装箱和拆箱方式，装箱：基本类型->包装类型,反之拆箱

2）jdk5以后（包括jdk5）的自动装箱和拆箱方式

3）自动装箱底层调用的是valueOf方法，比如integer.valueOf();

4）其他类型同理

```java
//基本类型——————>包装类型[手动装箱]
int i =10;
integer i1 = new Integer(i);
integer i2 = Integer.value(i);

//包装类型————————>基本类型[手动拆箱]
Integer j = new Integer(99);
int j1 = j.intValue();
```

```java
//jdk5.0之后的方式
int m =10;
Integer m2 =m;
Integer n = new Integer(99);
int n2 = n;
System.out.println("n+100");
System.out.println("n*2");
if(n>10){

}
```

### 包装类型和String类型的相互转换

#### 案例

以integer和String转为例

```java
//包装类型---->String类型
integer i =10;
//方式1
String s1 = i.toString();
//方式2
String s2 = String.valueOf(i);
//方式3
String s3 = i+""; 
System.out.println(s3);

//String --->包装类
//方式1
Integer j =new Integer(s1);
//方式2
Integer j2 = Integer.valueOf(s2);
//
Integer.parseInt(s3);
```

### Integer类和Character类常方法

```java
Integer.MIN_VALUE //返回最小值
Integer.MAX_VALUE //返回最大值

Character.isDigit('a');//判断是不是数字
Character.isLetter('a');//判断是不是字母
Character.isUpperCase('a');//判断是不是大写
Character.inLowerCase('a');//判断是不是小写

Character.isWhitespace('a')；//判断是不是空格
Character.toUpperCase('a');//转成大写
Character.toLowerCase('a');//转成小写

```

### Integer面试题

1.看代码输出什么，为啥

1. ![image-20220413164815801](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220413164815801.png)

2. 因为integer的原码定义好了从-128-127之间不返回一个对象

   ![image-20220413164729185](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220413164729185.png)

   2.integer面试题总结

   看下列代码输出什么结果

   <span style="color:red;background:yellow " >只要有基本数据类型会自动拆箱，比对的是数值。判断的是值是否相等</span>

   如下的示例六和七，比对的是

   ![image-20220413205739995](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220413205739995.png)

   

   

## String(重要)

![image-20220413213320195](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220413213320195.png)

String实现了三个接口并继承了Object类

* Serializable接口：说明String可以串行化。（可以在网络传输）
* Comparable接口：说明String对象可以相互比较
* CharSequence接口：字符序列

<span style="color:blue;background:pink">String类是final类，String类不能被其他类继承</span>

<span style="color:blue;background:pink">String 有属性，private final char value[];用于存放字符串内容（字符串的本质就是char数组）</span>

<span style="color:red;background:pink">(注意：value是一个final类型，不可修改（即：value不能指向新的地址，但是单个字符内容时可以变化的）)</span>





### 理解

1）String对象用于保存字符串，也就是一组字符序列

2）字符串常量对象时用双引号括起来的字符序列。例如："你好"，"21.213"，"boy"等等

3）字符串的字符使用Unicode字符编码，一个字符（不区分字幕还是汉字）占两个字节

4）String类较常用的构造方法（其他手册）

* String s1 = new String();
* String s2 = new String(String original);
* String s3 = new String(char[] a);
* String s4 = new String(char[] a,int startIndex, int count)

### 创建方式

#### 1）方式一：直接赋值String s = "xxx";

创建流程：

先从常量池查看是否有"xxx"数据空间，如果有，直接指向；如果没有则重新创建，然后指向。s最终指向的是常量池的空间地址

#### 2）方式二：调用构造器 String s = new String("xxx")；

流程：现在堆中创建空间，里面维护了value属性，指向常量池的xxx空间。如果常量池没有"xxx"，重新创建，如果有，直接通过value指向。最终指向的是堆中的空间地址

![image-20220414101904944](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220414101904944.png)

### String字符串的特性

1）String是一个final类，代表不可变的字符序列

2）字符串是不可变的。一个字符串对象一旦被分配，其内容是不可变的 



#### 面试题、

1）String a = "hello"+"abc";创建了几个对象

```java
编译器会在后台会进行优化，判断创建的常量池对象，是否有引用指向
优化等价于String a = "helloabc"；

所以答案是创建了一个对象
不是创建了三个
```

2）String a = "hello";

String b = "abc";

String c = a+b;

总共创建了几个对象

所以只创建了一个

```java
执行流程
1. 先创建了一个StringBuilder sb = StringBuilder();
2.执行sb.append("hello");
3.sb.append("abc");
4.String c = sb.toString();
最后其实是c指向了堆中的对象（String）value[],堆中的对象指向了池中的“helloabc”
```

![image-20220414140922725](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220414140922725.png)

小结:底层是StringBuilder sb = new StringBuilder();sb.append(a);sb.append(b);sb是在堆中，并append是在原来的字符串的基础上追加的。

重要规则：String c1 = "sb"+"cd";常量相加，看的是池。String c1 = a+b;变量相加，是在堆中

### String类的常见方法

#### 说明：

​	String类是保存字符串常量的。每次更新都需要重新开辟空间，效率低，因此java设计者还提供StringBuilder和StringBuffer来增强String的功能，并提高效率。

#### Strng常见的方法

![image-20220414145929644](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220414145929644.png)

* equals		//区分大小写，判断是否相等

* equalsIgnoreCase   //忽略大小写，判断内容是否相等

* length  //获取字符的个数，字符窜长度                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            

* indexOf  //获取字符在字符串中第一次出现的索引，索引从0开始，如果找不到返回-1

* lastIndexOf   //获取字符在字符串中最后一次出现的索引，索引从0开始，如果找不到，返回-1

* substring //截取指定范围字符串

* trim  //去前后空格

* charAt //获取某索引处的字符，之一不能使用Str[index]这种方式

* toUpperCase  //字符串转换成大写

* toLowerCase  //字符串转换成小写

* concat  //拼接字符串

* replace  替换字符串中字符

* split 分割字符串，罪域某些分割字符，我们需要转义

  案例：

  ```java
  String poem ="锄禾日当午，汗滴禾下土，谁知盘中餐，粒粒皆辛苦";
  String[] split = poem.split(",");
  //以，号为标准，分割上述整个字符串
  //上述字符串被分割为4个部分用数组接收
  
  //在堆字符串进行分割时，如f
  poem = "E:\\aaa\\bbb";
  split  = poem.split("\\\\");
  ```

  和 文件路径

* compareTo //比较两个字符串的大小，如果前者大则返回正数，如果后者大则返回负数，

  如果相等（

  1.如果长度相同，并且字符串也相同返回0。

  2.如果长度相同或者不相同，但是在进行比较时，可以区分大小就返回if(c1 != c2）{

  ​		return c1 - c2;

  }

  3.如果前面的部分都相同，就返回str1.len - str2.len）

* toCharArray //字符串转成字符数组

* format//格式化字符串，%s字符串，%c字符，%d 整型，%.2f 浮点型

  ```java
  //  %s%d%.2f%c成为占位符
  //  这些占位符由后面的变量来替换
  //  %s表示后面由字符串替换
  //  %d表示整数替换
  //  %.2f表示使用小数来替换，替换后，只会保留小数两位，并且会进行四舍五入的处理
  //  %c是char类型替换
      
  String name ="jack";
  int age = 10;
  double score = 98.3 /3;
  char gender ='男';
  
  //传统方法拼接
  String info = "名字是"+name+"年龄是"+age+"成绩是"+score+"性别："+gender";
  
  
  //使用format拼接
  String info2 =String.format("姓名是%s年龄是%d成绩是%d性别时%c",name,age,score,gender);
  
  //可以做成一个模板后面直接调用
  String formatstr = "姓名是%s年龄是%d成绩是%d性别时%c";
  
  String info2 =String.format(formatstr,name,age,score,gender);
  
  System.out.println("info2 ="+info2);
  ```

  

## StringBuffer(重要)

<span style="color:red;background:pink">串行化（对象可以网络传输，可以保存到文件）</span>

### 基本介绍

java.lang.StringBuffer代表可变字符序列，可以对字符串内容进行增删

很多方法与String相同，但StringBuffer是可变长度的

StringBuffer是一个容器

![image-20220415090614911](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220415090614911.png)

```java
StringBuffer stringBuffer = new StringBuffer("hello");
//1.StringBuffer 的直接父类是 AbstractStringBuilder
//2.StringBuffer 实现了Serializable，即StringBuffer的对象可以串行化
//3.在父类中，AbstractStringBuilder 有属性 char[] value ，不是final
	该value 数组存放祖父穿内容，因数存放在堆中的
//4.StringBuffer是一个final类， 不能被继承
```

### String 对比StringBuffer

1）String保存的是字符串常量，里面的值不能更改，每次String类的更新实际是更改地址，效率较低//private final char value[]；

2）StringBuffer保存的是字符串变量，里面的值可以更改，每次StringBuffer的更新实际上可以更新内容，不用更新地址，效率较高//char[] value //这个放在堆



### StringBuffer构造器

StringBuffer()

* 构造一个其中不带字符的字符串缓冲区，其初始容量为16个字符

* ```java
  //创建一个大小为16的char[]，用于存放字符串内容
  StringBuffer stringBuffer = new StringBuffer();
  ```

StringBuffer(CharSequence seq)

* public java.lang.StringBuffer(CharSequence seq)构造一个字符串缓冲区，它包含与指定的CharSequence 相同的字符

StringBuffer(int capacity)//capacity[容量]

* 构造一个不带字符，但具有指定初始容量的字符串缓冲区，即对char[]大小进行指定

* ```java
  //通过构造器指定 char[]大小
  StringBuffer stringBuffer = new StringBuffer(100);
  ```

StringBuffer(String str)

* 构造一个字符串缓冲器，并将其内容初始化为指定的字符串内容

* ```java
  //通过给一个String 创建StringBuffer,char[] 大小就是str.length()+16
  StringBuffer stringBuffer = new StringBuffer("hello");
  ```

### String和StringBuffer

#### String->StringBuffer

```java
//        String->StringBuffer
//        方式一
        String str ="xxx";
//        注意：返回的是StringBuffer对象，对str本身是没有影响的
        StringBuffer stringBuffer = new StringBuffer(str);


//        方式二，使用append方法
        StringBuffer stringBuffer1 = new StringBuffer();
        stringBuffer1 = stringBuffer1.append(str);
```

#### StringBuffer->String

```java

//        StringBuffer->String
        StringBuffer stringBuffer2 = new StringBuffer("xxxxxx");
//        方式一,使用StringBuffer提供的 toString方法;
        String s = stringBuffer2.toString();

//        方式二,使用构造器搞定
        String s1 = new String(stringBuffer2);

```



### StirngBuffer类常见方法

1. 增 append
2. 删 delete(start,end)
3. 改 replace(start,end,string)//将start---end间的内容替换掉，不含end
4. 查 indexOf //查询字符串第1次出现的索引，如果找不回返回-1
5. 插 insert
6. 获取长度 length

```java
       StringBuffer stringBuffer = new StringBuffer("zhangsan");

        stringBuffer.append('x');
        stringBuffer.append("张三");
        stringBuffer.append("wangwu").append(true).append(10.2);
        System.out.println(stringBuffer);

//        删除
        /*
        * 删除索引为>=start && <end 处的字符
        * 解读：删除11~14的字符[11,14)
        * */
        stringBuffer.delete(11,14);
        System.out.println(stringBuffer);

        //    改
//        修改本质就是替换
//        使用fff替换索引11-14的字符
        stringBuffer.replace(11,14,"fff");
        System.out.println(stringBuffer);

//        查
//        查找指定的子串在字符串出现的索引.如果找不到返回-1
        int index = stringBuffer.indexOf("zhang");
        System.out.println(index);

//        插入
//        指定一个位置插入
//        在索引为9的位置插入"老王"，原来索引为9的内容自动后移
        stringBuffer.insert(9,"老王");
        System.out.println(stringBuffer);

//        获取长度
        System.out.println(stringBuffer.length());
    }

```





```java
 public static void main(String[] args) {
        /**
         * 输入商品名称和商品价格，要求打印效果示例，实用前面学习的方法完成
         * 商品名  商品价格
         * 手机123，456.56  //比如 价格价格1,456,786.5
         * 要求：价格的小数点前面每三位用,号隔开，再输出
        * */

        String prices;
        Scanner scanner = new Scanner(System.in);
        String price = scanner.next();
        StringBuffer stringBuffer = new StringBuffer(price);


//        先完成最简单的实现21,312,412.32
//        找到小数点的索引,然后再该位置的前三位插入,

        for (int j = stringBuffer.lastIndexOf(".")-3; j >0 ; j-=3) {

            stringBuffer = stringBuffer.insert(j, ",");
        }

        System.out.println(stringBuffer);

    }
```





## StringBuilder(重要)

### 基本介绍

1）一个可变的字符序列。此类提供一个与StringBuffer兼容的API，但不保证同步(StringBuilder 不是线程安全)。该类被设计用作StringBuffer的一个简易替换，用在字符串缓冲区被单个线程使用的时候。如果可能，建议优先采用该类，因为在大多数实现中，它比StringBuffer要快（单线程的情况下，优先使用StringBuilder）

2）在StringBuilder上主要操作是append和insert方法，可重载这些方法，以接受任意类型的数据



### StringBuilder常用方法

StringBuilder和StringBuffer均代表可变字符序列，方法是一样的，所以使用和StringBuffer一样。

1. StringBuilder是final类，不能被继承
2. StringBuilder对象可以串行化
3. 继承了AbstractStringBuilder属性 char[] value，内容存到value
4. 实现了Serializable接口，序列化（所谓系列化既可以保存类型和数据本身）

## String、StringBuffer、StringBuilder的比较☆

1）StringBuilder和StringBuffer非常类似，均代表可变字符序列，而且方法也一样

2）String：不可变字符序列，效率低，但是复用率高。

3）StringBuffer：可变字符序列、效率较高（增删）、线程安全

4）StringBuilder：可变字符序列、效率最高、线程不安全

5）String使用注意事项：

```java
String s="a"; //创建了一个字符串
s+= "b";   //实际上原来的"a"字符串对象已经丢弃了，现在又产生了一个转字符串s+"b"（也就是"ab").如果多次执行这些改变串内容的操作，会导致大量副本字符串对象存留在内存中，降低效率。如果这样的操作放到循环中，会极大影响程序的性能=》
//结论：如果我们对Stirng做大量修改，不要使用String
```

### 效率

StringBuilder  > StringBuffer >String 



### 使用原则，结论

1. 如果字符串存在大量的修改操作，一般使用StringBuffer或StringBuilder
2. 如果字符串存在大量的修改操作，并且在单线程的情况下使用StringBuilder
3. 如果字符串存在大量的修改操作，并且在多线程的情况下使用StringBuffer
4. 如果我们字符串很少修改，被多个对象引用，使用String，比如配置信息等

StringBuffer和StringBuilder的方法使用一样

## Math

### 基本介绍

Math类包含用于执行基本数学运算方法，如初等指数，对数，平方根和三角函数

方法一览（均为静态方法）![image-20220415145338171](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220415145338171.png)

### Match常用的方法

1. abs  绝对值

2. pow  求幂

3. ceil   向上取整  (返回>=该参数的最小整数)

4. floor   向下取整  (返回<=该参数的最大整数)

5. round   四舍五入

6. sqrt  求开方

7. random  求随机数

   ```java
   public static void main(String[] args) {
           /*
           random随机数
           random默认返回 0<= x <1之间的一个随机小数
           请写出a-b之间的一个随机整数，a,b均为整数比如a=2,b=7
           即返回一个2 - 7 之间的随机数
           * */
           
           /**
           * random返回的是0<=x <1之间的一个随机小数
            * Math.random()*(b-a)返回的就是0<= 数 <=b-a
            * (1)(int)(a)<= x <(int)(a+Math.random() * (b-a +1))
           * (2)集体使用解析
            * (int)(a+Math.random() * (b-a +1))
            *  = (int)(2+Math.random() * 6)
            *  Math.random() * 6返回的就是0<= x <6小数
            *  2+Math.random() * 6返回的就是2<= x <8小数
            *  (int)(2+Math.random() * 6) = 2 <=x <=7
           * */
           
   
   
   //      公式就是：(int)(a+Math.random() * (b-a +1))
           for (int i = 0; i < 5; i++) {
               System.out.println((int) (2 +Math.random()*(7-2+1)));
           }
       }
   ```

   

8. max   求两个数的最大值

9. min    求两个数的最小值





## Date,Calender,LoaclDate.

### Date[知道怎么查，怎么用即可]

#### 第一代日期类

Date：精确到毫秒，代表特定的瞬间

SimpleDateFormat：格式和解析日期的类SimpleDateFormat 格式化和解析日期的具体类。它允许进行格式（日期->文本、解析（文本->日期）和规范化

![image-20220420110144786](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220420110144786.png)

```java
//获取当前时间
//默认输出的格式是国外的格式
Date d1 = new Date();、
//因此需要对格式进行转换
SimpleDateFormat simpleDateFormat = new SimpleDateFormat("yyyy年MM月dd日 hh:mm:ss E");
//其他格式的字母意思，查看手册
String foramt = d1.format(d1);

//获取某个时间对应的毫秒数
Date d2 = new Date(23123);

//可以吧一个格式化的字符串转成对应的date
String s = "2000年7月五日 20:12:20 星期一";
Date pares = simpleDateFormat.parse(s);
//接收的格式必须个定义的格式一样
```

### Calendar(日历)

#### 第二代日期类

主要就是Calendar类（日历）

1）public abstract class Calendar extends Object implements Serializable,Cloneable,Comparable<Calendar

2)calendar类是一个抽象类，他为特定瞬间为一组诸如YEAR、MONTH、DAY_OF_MONTH、HOUR等，日历字段之间的转换提供了一些方法，并为操作日历字段（例如获得下星期的日期）提供了一些方法。

```java
//创建日历对象，
Calendar c =Calendar.getInstance();
System.out.print("年"+c.get(Calendar.YEAR))；
System.out.print("月"+c.get(Calendar.MONTH)+1)；
System.out.print("日"+c.get(Calendar.DAY_OF_MONTH))；
System.out.print("小时"+c.get(Calendar.HOUR))；
System.out.print("分钟"+c.get(Calendar.MINUTE))；
System.out.print("秒"+c.get(Calendar.SECOND))；
//Calendar没有专门的格式化方法，所以程序员自己组合
System.out.print(c.get(Calendar.SECOND)+"年"+(c.get(Calendar.MONTH)+1)+"月"+c.get(Calendar.DAY_OF_MONTH)+"日")；
```

### 第三代日期类

前面两代的不足分析

（jdk1.0中包含了一个java.Util.Date类，但是他的大多数方法已经存在JDK1.1引入Calendar类之后被弃用。Calendar也存在着很多问题

1. 可变性：像日期和时间这样的类应该是不可变的。
2. 偏移性：Date中年份是从1900开始的，而月份是从0开始的
3. 格式化：格式化只对Date有用，Calendar则不行
4. 此外，他们不是线程安全的，不能处理闰秒等（每隔两天多出1s）

#### 第三代日期类

1）LoaclDate（日期）、localTime（时间）、loacalDateTime（日期和时间内）

JDK8

LoaclDate：只包含日期，可以获取日期字段

localTime：包含时间，可以获取时间字段

loacalDateTime包含日期和时间，

```java
loacalDateTime ln = loacalDateTime.now();
ln.getYear();
ln.getMonth();
ln.getMonthValue();//输出数字版的月份
```

##### 2）DateTimeFormatter格式日期类

类似于SimpleDateFormat

```java
DateTimeFormatter dtf = DateTimeFormatter.ofPattern(格式);//(yyyyMMdd....)

String srt = dtf.format(日期对象);
```

#### Instant 时间戳

类似于Date

提供了一系列和Date类转换的方式

Instant---->Date;

Date date = Date.from(instant);

Date --->Instant;

Instant instant = date.toInstant();

案例演示

```java
Instant now = Instant.now();
System.out.print(now);
Date date = Date.from(now);
Instant instant = date.toInstant();
```













## System

### 常见方法

1）exit 退出当前程序

```
System.exit(0);表示退出
//0代表一个正常状态状态  。
```

2）Arraycopy：复制数组元素，比较合适底层调用，一般使用Arrays.copyOf完成数组复制。

```java
int[] src = {1,2,3};
int[] dest = new int[3];
System.arraycopy(src,0,dest,0,3)
 	src:源数组
    srcpos：从原数组的哪个索引位置开始开始拷贝
    dest:目标数组，即吧原数组的数据拷贝到哪个数组
    destpos：把原数组的数据拷贝到 目标数组的哪个索引
    length:从原数组拷贝多少个数据到目标数组
```

3）currentTimeMillens：返回当前时间距离1970-1-1(1970年1月1日到现在) 的毫秒数

4）gc：运行垃圾回收机制System.gc();

## Arrays类

### 介绍

Arrays里面包含了一系列静态方法，用于管理或操作数组（比如排序和搜索）

### 方法

#### 1） toString返回数组的字符串形式，将数组拼接成字符串返回

```java
Arrays.ToString(arr)
```

#### 2)sort排序（自然排序和定制排序）	

```java
Integer arr[] = {1,-1,7,0,89};
//可以直接使用该方法进行排序。不用再动手去敲方法
//因为数组时引用类型，所以通过sort排序后，会影响到实参arr
Arrays.sort(arr);//正序排序
//sort重载的，也可以通过传入一个接口Comparator实现定制排序

1、调用定制排序时，传入两个参数
    (1)排序数组的参数
    (2)实现Comparator接口的匿名内部类。要求实现Compare方法

    
    
//      这里体现了接口编程的方式
//
//        倒序排序
        Arrays.sort(a, new Comparator() {
            @Override
            public int compare(Object o1, Object o2) {
                Integer i1 = (Integer) o1;
                Integer i2 = (Integer) o2;
//                return大于0 就是正序排序，小于0就是倒序
                return i2 -i1;
            }
        });
        System.out.println(Arrays.toString(a));

    }
```

```java
       bubble(a,new Comparator() {
            @Override
            public int compare(Object o1, Object o2) {
                Integer i1 = (Integer) o1;
                Integer i2 = (Integer) o2;
                return i1 -i2 ;
            }
        });

        System.out.println("定制类"+Arrays.toString(a));

    }


//    定制排序
    public static void bubble(Integer[] arr,Comparator c){
        int temp;
        for (int i = 0; i < arr.length-1 ; i++) {
            for (int j = 0; j <arr.length-1-i; j++) {
                if (c.compare(arr[j],arr[j+1])>0){
                    temp =arr[j];
                    arr[j] = arr[j+1];
                    arr[j+1] = temp;
                }
            }
        }
    }
```



#### 3）binarySearch 二分搜索

binarySearch 通过二分搜索法进行查找，要求必须排好序

```java
 //如果这个数组是有序的，可以通过该方法查找知否有这个数
 int[] arr = {1,23,45,65,78};
//如果不存在该元素就返回，return -(low +1)//意思就是返回负的他该出现的位置的下标+1
 int index = Arrays.binarySearch(arr,3);//返回-2
```

#### 4）copyOf数组元素的复制

```java
//表示从arr数组中拷贝arr.length个长度的元素到新的arr数组中
Integer[] newArr = Arrays.copyOf(arr,arr.length);
Integer[] newArr = Arrays.copyOf(arr,arr.length-1);就是拷贝原数组长度-1
Integer[] newArr = Arrays.copyOf(arr,arr.length+1);
//如果长度超出原数组的长度，则多出来的部分元素为null   
```

#### 5)fill数组元素的填充

```java
Integer[] num = new Integer[]{9,2,1};
//使用99去填充num数组
//可以理解成替换原来的元素
Arrays.fill(num,99);

==========运行结果======
    [99,99,99]
```

#### 6)equals 比较两个数组元素内容是否完全一致

```java
boolean equals  = Arrays.equals(arr,arr2);
//如果两个数组元素一样，则返回true。不一样返回false
```

#### 7)asList 将一组值，转换成list

```java
List<Integer> asList = Arrays.asList(2,3,4,5,6,1);
System.out.println("asList"+asList);
```





## Integer和BigDecimal类

### 应用场景

1）BigInteger适合保存比较大的整型(整数)

```java
//当编程中需要处理很大的整数。long不够用可以使用BigInteger类
//使用
BigInteger bigInteger = new BigInteger("2222222222222222222222222222222222222222");

//运算
//在对BigInteger进行加减乘除的时候，需要使用对应的方法，不能直接使用符号（+-*/）
    
BigInteger bigInteger 2=bigInteger.add(10)；//加
    //也可再创建一个BigInteger相加
```



2）BigDecimal适合保存精度高的浮点型(小数)

```java
//当我们需要保存一个精度很高的值时，double不够用
//可以使用BigDecimal
BigDecimal bigDecimal = new BigDecimal("22.22222222222222222222222222");
//运算
//在对BigDecimal进行加减乘除的时候，需要使用对应的方法，不能直接使用符号（+-*/）
//需要创建一个需要操作的BigDecimal，然后调用即可

BigDecimal bigDecimal=bigDecimal.add(2.3);
    //使用删除方法时，可能会出现除不尽的情况，会抛出异常
//解决办法：在调用divede(删除)方法是，指定精度即可
bigDecimal.divide(1.11,BigDecimal.ROUND_CEILING)
//如果有无限循环小数，就会保留到分子的精度

```

# 集合

## 集合框架体系

### 集合体系图

背下来

1）单例集合（在集合里面放单个的对象）

![image-20220420163040446](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220420163040446.png)

![image-20220420163624872](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220420163624872.png)

2）双列集合（存放键值对形式的）

![image-20220420163100945](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220420163100945.png)

![image-20220420163609594](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220420163609594.png)

```java
//存放单个数据的成为单例
ArrayList  arrayList = new ArrayList();
arrayList.add("zhangsan");
arrayList.add("lisi");

//存放双列数据的成为双例集合
HashMap hashMap = new HashMap();
hashMap.put("no1","zhangsan");
//key,value
hashMap.put("no2","李四");
```

## Collection

Collection接口

#### Collection接口实现类的特点

```java
Public interface Collection<E> extends Iterable<E>
```

1. Collection实现子类可以存放多个元素，每个元素可以是 Object
2. 有些Collection的实现类，可以存放重复的元素，有些不可以
3. 有些Collection的实现类，有些是有序的（List），有些不是有序（Set）
4. Collection接口没有直接实现子类，是通过它的子接口Set和List来实现的

#### Collection接口和常用方法

![image-20220420165341922](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220420165341922.png)

常用方法

```java
1)add :添加单个元素
2)remove:删除指定元素
3)contains:查找元素是否存在
4）size：获取元素个数
5）isEempty：判断是否为空
6）clear：清空
7）addAll：添加多个元素
8）containsAll：查找多个元素是否都存在
9）removeAll：删除多个元素
说明：以ArrayList实现类演示
```

```java
public static void main(String[] args) {
        ArrayList list = new ArrayList();
//        1.添加单个元素
        list.add("zhangsan");
        list.add("hahah");
        list.add("lisi");
        list.add(123);//等价于list.add(new Integer(123);
        System.out.println("数组增加"+list);
//      remove：删除指定元素
        list.remove(0);//删除第一个元素,下标从0开始
        list.remove("123");//删除指定元素
        System.out.println("数组删除"+list);

//       contains 查找元素是否存在
        System.out.println(list.contains("zhangsan"));//F
//        size,显示元素的个数
        System.out.println(list.size());
//      isEmpty判断是否为空
        System.out.println(list.isEmpty());
//        clear清空
        list.clear();//清空集合
        System.out.println("list清空="+list);

        ArrayList list1 = new ArrayList();
//        addAll:添加多个元素
        list1.add("xxx");
        list1.add("xxxxxx");

        list.addAll(list1);
        System.out.println("addAll"+list);
//        containsAll:查找多个元素知否存在
        System.out.println(list.containsAll(list1));
//        removeAll：删除多个元素
        list.removeAll(list1);
        System.out.println(list);

    }
```

#### 使用Iterator（迭代器）

Collection接口遍历元素的方式1-使用Iterator（迭代器）

##### 基本介绍

1）Iterator对象成为迭代器，主要用于遍历Collection集合中的元素

2）所有实现了Collection接口的集合类都有一个iterator()方法，用以返回一个实现了Iterator接口的对象，即可返回一个迭代器

3）Iterator的结构![image-20220420231917444](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220420231917444.png)

4）Iterator仅用于遍历集合，Iterator本身并不存放对象

###### 迭代器的运行原

![image-20220421160914060](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220421160914060.png)

hasNext用于判断

next（）；下移，并返回指向的元素

```java
public class Iteraor {
    public static void main(String[] args) {
        Collection list = new ArrayList();
        list.add(new HomeWork("zhansgan",12313));
        list.add(new HomeWork("haha",231));

//        使用迭代器遍历
        Iterator iterator = list.iterator();
//        while循环  快捷方式输入 itit
//        ctrl+j提示所有快捷键
     while (iterator.hasNext()) {
//            返回下一个元素，是Object类型
            Object next =  iterator.next();
            System.out.println(next);
        }
//      当退出while循环后，这是iterator迭代器，指向最后一个元素
//        iterator.next()  ，此时再让往下移指针会报异常：NuSuchElementException
//        如果希望再次遍历，需要我们重置迭代器
        iterator = list.iterator();//相当于指向了第一个元素

    }
}

class HomeWork{
    String name;
    Integer phoneNum;

    public HomeWork() {
    }

    public HomeWork(String name, Integer phoneNum) {
        this.name = name;
        this.phoneNum = phoneNum;
    }

    @Override
    public String toString() {
        return "HomeWork{" +
                "name='" + name + '\'' +
                ", phoneNum=" + phoneNum +
                '}';
    }
}
```

#### for循环增强

Collection接口遍历元素的方式2-

增强for循环，可以代替iterator迭代器

特点：增强for就是简化版的iterator，本质一样。只能用于<span style="color:red">遍历集合或数组</span>

###### 基本语法

```java
for(元素类型 元素名 : 集合名或数组){
	访问元素
}
```

案例

```java
 for (Object homeWork:list) {
            System.out.println(homeWork);
        }

//        增强也可以在数组中使用
        int[] a = {1,2,3,45,6};
        for (int i: a){
            System.out.println(i);
        }
```

1. 增强for底层是迭代器
2. 可以理解成增强for是简化版的迭代器

## List

基本介绍：

List接口是Collection接口的子接口

1）list集合类中元素有序（即添加顺序和取出顺序一致）、且可重复

2）list集合中的每个元素都有其对应的顺序索引，即支持索引

3）list容器中的元素都对应一个整数型的序号记载其在容器中的位置，可以根据序号存取容器中的元素

4）JDK API中的List接口实现类有：ArrayList、LinkedList和Vector

```java
public static void main(String[] args) {
//        list集合类中元素有序（即添加顺序和取出顺序一致）、且可重复
        List list = new ArrayList();
        list.add("jack");
        list.add("tom");
        list.add("zhangsan");
//        此时不会有冲突，相当于会认为有两个tom
        list.add("tom");
//        此时输出的顺序就是存进去的顺序
        System.out.println("list"+list);

//        2）list集合中的每个元素都有其对应的顺序索引，即支持索引
//        索引从0开始
        System.out.println(list.get(3));
    }
```

##### List接口的常用方法

1. void add（int index,Object ele）在index位置插入ele元素
2. boolean addAll(int index,Collection eles):从index位置开始将eles中的所有元素添加进来
3. Object get (int index)获取固定index位置的元素
4. int indexOf(Object obj)  返回obj在几个中首次出现的位置
5. int lastIndexOf(Object obj) 返回obj在当前集合末次出现的位置
6. Object remove(int index) 移除指定index位置的元素，并返回此元素
7. Object set(int index ,Object ele) 设置指定index位置的元素为ele，相当于替换
8. List subList (int fromIndex,int toIndex) 返回从fromIndex到toIndex位置的子集合

```java
public static void main(String[] args) {

        List list = new ArrayList();
        list.add("no1");
        list.add("no2");
//        1. void add（int index,Object ele）在index位置插入ele元素
//        在index=1的位置插入一个对象
        list.add(1,"add(index,ele)");
        System.out.println(list);
//        2. boolean addAll(int index,Collection eles):从index位置开始将eles中的所有元素添加进来
        List list2 = new ArrayList();
        list2.add("lno2");
        list2.add("lno3");
        list2.add("lno3");
//        在1的位置插入list2的集合
        list.addAll(1,list2);
        System.out.println(list);
//        3. Object get (int index)获取固定index位置的元素
//        4. int indexOf(Object obj)  返回obj在几个中首次出现的位置
        System.out.println(list.indexOf("no1"));
//        5. int lastIndexOf(Object obj) 返回obj在当前集合末次出现的位置
        System.out.println(list.lastIndexOf("lno3"));
//        6. Object remove(int index) 移除指定index位置的元素，并返回此元素
        list.remove(1);
        System.out.println( list);
//        7. Object set(int index ,Object ele) 设置指定index位置的元素为ele，相当于替换
//        将索引为1的改为尼诺
        list.set(1,"尼诺");
//        8. List subList (int fromIndex,int toIndex) 返回从fromIndex到toIndex位置的子集合
        List result = list.subList(0, 2);//相当于选择了下标为0的和下标为2-1之间的元素
        System.out.println("result"+result);
}
```

##### 注意事项

1. permits all elements,including null , ArrayList 可以加入null，并且多个
2. ArrayList 是由数组来实现数据存储的
3. ArrayList基本等同于Vector，除了ArrayList是线程不安全（执行效率高）看源码，在多线程情况下，不建议使用ArrayList

#### ArrayList

#####  ArrayList底层机制和源码分析（重点）

1）ArrayList中维护了一个Object类型的数组elementData

​		transient Object[] elementData 

```
transient 表示瞬间，短暂的，表示该属性不会被序列化
```



2）当创建对象ArrayList时，如果使用的是无参构造器，则初始elementData容量为0

3）当添加元素时，先判断是否需要扩容，则调用grow方法，否则直接添加元素到合适位置

4）如果使用的是无参构造器，如果第一次添加，需要扩容的话，则扩容elementData为10，如果需要再次扩容的话，则扩容elementData为1.5倍

5）如果使用的是指定容量capacity的构造器，则初始elementData容量为capacity

6）如果使用的是指定容量capacity的构造器，如果需要扩容，则直接扩容elementData为1.5倍



#### Vector

##### 介绍

Vevtor底层也是一个对象数组。protected Object[] elementData;

Vector是线程同步的，即线程安全，Vector类的操作方法带有synchronized

在开发过程中，需要线程同步安全时，考虑使用Vector



##### Vector 和ArrayList比较

|           | 底层结构 | 版本   | 线程安全（同步）效率 | 扩容倍数                                                     |
| --------- | -------- | ------ | -------------------- | ------------------------------------------------------------ |
| ArrayList | 可变数组 | jdk1.2 | 不安全，效率高       | 如果有参构造1.5倍如果无参1.第一次是10，第二次按1.5扩         |
| Vector    | 可变数组 | jdk1.0 | 安全，效率不高       | 如果是无参默认10，满后，就按两倍扩容。如果指定大小（创建）有参，则每次直接按2倍扩容 |

#### LinkedList

##### 说明

1）LinkedList实现了双向链表和双端队列特点

2）可以添加任意元素（元素可以重复），包括null

3）线程不安全，没有实现同步

##### LinkedList底层机制

1. LinkedList底层维护了一个双向链表

2. LinkedList中维护了两个属性first和last分别指向首节点和尾结点

3. 每个节点（Node对象），里面又维护了prev、next、item三个属性，其中通过prev指向前一个，通过next指向后一个节点。最终实现双向链表

4. 所以LinkedList的元素的 添加和删除，不是通过该数组完成的，相对来说效率较高

5. 模拟一个简单双向链表理解

   ```java
   public static void main(String[] args) {
   //        模拟一个简单的双向链表
           Node jack = new Node("jack");
           Node tom = new Node("tom");
           Node zhangshan = new Node("zhangshan");
   //        链接是三个结点，形成双向链表
   //        jack->tom ->zhangsan
           jack.next = tom;
           tom.next =zhangshan;
   //        zhangsan->tom->jack
           zhangshan.pre = tom;
           tom.pre = jack;
   
           Node first = jack;//让first引用指向jack，就是双向链表的头结点
           Node last =zhangshan;//让last引用指向zhangshan，就是双向链表的尾结点
   
   
   //        演示从头到尾进行遍历
           while (true){
               if (first == null){
                   break;
               }
   //            输出first信息
               System.out.println(first);
               first = first.next;
           }
   
   //        从未到头遍历
           while (true){
               if (last == null){
                   break;
               }
               System.out.println(last);
               last = last.pre;
           }
   
       }
   }
   
   //定义一个Node类，node对象 表示双向链表的一个结点
   class Node{
       public Object item;//真正存放数据
       public Node next;//指向下一个结点
       public Node pre;//指向前一个结点
   
       public Node(Object item) {
           this.item = item;
       }
   
       @Override
       public String toString() {
           return "Node{" +
                   "item=" + item +
                   '}';
       }
   }
   ```

   

![image-20220429152321935](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220429152321935.png)

##### ArrayList 和LinkedList的比较

|            | 底层结构 | 增删的效率         | 改查的效率 | 线程   |
| ---------- | -------- | ------------------ | ---------- | ------ |
| ArrayList  | 可变数组 | 较低；数组扩容     | 较高       | 不安全 |
| LinkedList | 双向链表 | 较高，通过链表追加 | 较低       | 不安全 |

何如选择

1）如果我们改查的操作较多，选择ArrayList

2）如果我们增删的操作多，选择LinkedList

3）一般来说，在程序中80%-90%都是查询，因此大部分情况下会选择ArrayList

4）在一个项目中，根据业务灵活选择，也可能这样，一个模块使用的是ArrayList，另外一个模块是LinkedList，也就是说根据业务来进行合理选择

## set

介绍

1）无序（添加和取出的顺序不一致），没有索引

2）不允许重复元素，所以最多包含和一个null

3）JDK API中Set接口的实现类有![image-20220429173926895](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220429173926895.png)

##### Set接口和常用方法

和List接口一样，Set接口也是Collection的子接口，因此常用方法和Collection接口一样

##### set接口遍历方式

同Collection的遍历方式一样，因为Set接口是Collection接口的子接口

* 使用迭代器
* 增强for
* 不能使用索引的方式获取

##### 案例

```java
public static void main(String[] args) {
//        以set接口实现类HashSet来讲解Set接口的方法
//        set接口的实现类的对象（set接口对象）
//        重复添加的数据只会存进去一个，null值也是只能存放一个
    //输出结果是无序的（存放的数据是无序的，即（添加的顺序和取出的顺序不一致））
    //虽然取出的顺序和添加的顺序不一致，但取出的顺序是固定的，不会一直变化
        Set set = new HashSet();
        set.add("zhansgan");
        set.add("lisi");
        set.add("wa");
        set.add("zhansgan");
        set.add(null);
        set.add(null);
        System.out.println(set);
    }

//        遍历
//        迭代器
        Iterator iterator = set.iterator();
        while (iterator.hasNext()) {
            Object next =  iterator.next();
            System.out.println(next);
        }
//        增强for
        for (Object o :set) {
            System.out.println(o);
        }
----------------输出结果----------------------
    [null, lisi, wa, zhansgan]
```

#### HashSet

1)HashSet实现了Set接口

2）HashSet实际上是HashMap，看源码

![image-20220430145947382](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220430145947382.png)

3）可以存放null值，但是只能有一个null

4）HashSet不保证元素时有序的，取决于hash之后，在确定索引的结果（即：不保证存放元素的顺序和取出的一致  ）

5）不能有重复元素/对象。在前面Set接口使用已经标明

```java
//1.执行add方法后，会返回一个Boolean值
//2.如果添加成功,返回true，否则返回false
//3.可以通过remove指定删除哪个对象
        HashSet set = new HashSet();
        set.add("zhansgan");
        set.add("lisi");
        set.add("wa");
        set.add("zhansgan");
        set.add(null);
        set.add(null);

        set.remove("zhangsan");

        set.add(new HHHH("zzz"));//添加成功
        set.add(new HHHH("zzz"));//添加成功
    }
}
class HHHH{
    private String name;

    public HHHH(String name) {
        this.name = name;
    }
}
```

##### HashSet底层机制说明 

1）HashSet底层是HashMap，HashMap底层是（数组+链表+红黑树）



1. HashSet底层是HashMap
2. 添加一个元素时，先得到hash值 -会转成-索引值
3. 找到储存数据表table，看这个索引位置是否已经存放的有元素
4. 如果没有，直接加入
5. 如果有调用equals比较，如果相同，就放弃添加，如果不相同，则添加到最后
6. 在java8中，如果一条链表的元素个数到了TREEEIFY_THRESHOLD(默认是8)个，并且table的大小>=MIN_TREEIFY_CAPACITY(默认64),就会进行树化（红黑树）
7. ![image-20220430160350549](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220430160350549.png)

源码分析

```java
final V putVal(int hash, K key, V value, boolean onlyIfAbsent,
                   boolean evict) {
    //定义了一个辅助变量
        Node<K,V>[] tab; Node<K,V> p; int n, i;
    //table就是HashMap的一个属性，类型是Node[]
     //if语句表示如果当前table是null，或者大小=0
    //就是第一次扩容，到16个空间
        if ((tab = table) == null || (n = tab.length) == 0)
            n = (tab = resize()).length;
   //（1）根据key，得到hash值去计算key应该存放到table表的哪个索引位置
    //并且把这个位置的对象赋给p
    //（2）判断p是否为null
    //（2.1）如果为null，表示还没有存放元素，就创建了一个Node
    //（2.1）就放在该位置 tab[i] = newNode(hash, key, value, null); 
        if ((p = tab[i = (n - 1) & hash]) == null)
            tab[i] = newNode(hash, key, value, null);
        else {
            Node<K,V> e; K k;
          //如果当前索引位置对应的链表的第一个元素和准备谈价的key的hash值一样
            //并且满足下面条件之一
            //1.准备加入的key和p指向的Node结点和key是同一个对象 
            //2.p指向的Node结点的key的equals（）和准备加入的key比较后相同
            if (p.hash == hash &&
                ((k = p.key) == key || (key != null && key.equals(k))))
                e = p;
            //如果上述条件不满足，再判断p是不是一个红黑树
            //如果是一颗红黑树，就调用putTreeVal，来进行添加判断
            else if (p instanceof TreeNode)
                e = ((TreeNode<K,V>)p).putTreeVal(this, tab, hash, key, value);
            
            else {
                //依次比较链表内的内容
                //如果table对应索引的额位置，已经是一个链表，就是用for循环比较
                //(1)依次和链表的每一个元素比较后都不相同，则加入到该链表的最后
                  //然后立即判断该链表是否已经达到8个结点，就调用   treeifyBin()对当前这个链表进行树化（转成红黑树）
                //注意，在转成红黑树时，要进行判断，判断条件{if(tab == null ||(n = tab.length)<MIN_TREEIEY_CAPACITY)
                //resize();   //table数组是否小于64，结点是否到达8个并不为空      }
                //如果上面条件成立，先table扩容
                //如果上面条件不成立，才进行树化
                //(2)依次和该链表的每一个元素比较过程中，如果有相同的情况，就直接break；
                for (int binCount = 0; ; ++binCount) {
                    if ((e = p.next) == null) {
                        
                        p.next = newNode(hash, key, value, null);
                
                        if (binCount >= TREEIFY_THRESHOLD - 1) // -1 for 1st
                            treeifyBin(tab, hash);
                        break;
                    }
                    if (e.hash == hash &&
                        ((k = e.key) == key || (key != null && key.equals(k))))
                        break;
                    p = e;
                }
            }
            if (e != null) { // existing mapping for key
                V oldValue = e.value;
                if (!onlyIfAbsent || oldValue == null)
                    e.value = value;
                afterNodeAccess(e);
                return oldValue;
            }
        }
        ++modCount;
        if (++size > threshold)
            resize();
        afterNodeInsertion(evict);
        return null;
    }
```

##### HashSet的扩容和转成红黑树机制

1. HashSet底层是HashMap，第一次添加时，table数组扩容到16，临界值（threshold）是16*加载因子（localFactor）是0.75 =12
2. 如果table数组实用到了临界值12，就会扩容到16*2=32，新的临界值就是32 * 0.75 = 24,依次类推
3. 在java8中，如果一条链表的元素个数到达TREEIFY_THRESHOLD(默认是8),并且table的大小>=MIN_TREEIFY_CAPACITY(默认64),就会进行树化（红黑树），否则仍然采用数组扩容机制



### LinkedHashSet

**说明**

1）LinkedHashSet是HashSet的子类

2）LinkedHashSet底层是一个LinkedHashMap，底层维护了一个数组+双向链表

3）LinkedHashSet根据元素的hashCode值来决定元素的储存位置，同时使用链表维护元素的次序（图），这使得元素看起来是以插入顺序保存的![image-20220501174705977](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220501174705977.png)

4）LinkedHashSet不允许添加重复元素 

![image-20220502111826275](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220502111826275.png)

可以理解成不同索引的数，构成双向链表

1. 在LinkedHashSet中维护了一个hash表和双向链表（LinkedHashSet有head和tail）

2. 每一个结点有pre和next属性，这样可以形成双向链表

3. 在添加一个元素时，先求hash值，在求索引。确定该元素在hashtable的位置，然后将添加的元素加入到双向链表（如果已经存在，不添加[原则和hashset一样])

   ```java
   tail.next = newElement //简单指定
   new Element.pre = tail
   tail = newElement;
   ```

4. 这样的话，我们遍历LinkedHashSet也能确保插入顺序和遍历顺序一致


#### TreeSet

1. 当使用无参构造器创建treeset的时候仍然是无序的

2. 需求：希望添加的元素按字符串大小来排序?

   1. 使用TreeSet提供的一个构造器,可以传入一个比较器（匿名内部类）

   2. ```java
      public class TreeSetDemo {
          public static void main(String[] args) {
      //        TreeSet treeSet = new TreeSet();
              TreeSet treeSet = new TreeSet(new Comparator() {
                  @Override
                  public int compare(Object o1, Object o2) {
      //                调用String的compareTo方法比较字符串大小
                      return ((String)o1).compareTo((String) o2);
                  }
              });
              treeSet.add("d");
              treeSet.add("b");
              treeSet.add("a");
              treeSet.add("c");
      
              System.out.println(treeSet);
          }}
      ```

   3. 



## Map

Map**结构**

<img src="https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220503163901620.png" alt="image-20220503163901620" style="zoom:50%;" />

Map接口的特点（JDK8之后的）

1）Map与Collection并列存在。用于保存具有映射关系的数据：Key-Value（双列元素, 遍历出是无序的）

2）Map中的key和value可以是任何引用数据类型，会封装到HashMap&Node对象中

3）Map中的key不允许重复，原因和HashSet一样，前面分析过

4）Map中的value可以重复（key不能重复，当有相同的key时新的key的value会替换旧的value）

5）Map的key可以为null，value可以为null，注意key为null，只能有一个，value 为null，可以多个

6）常使用String类作为Map的key（只要是Object的子类都可以，不范于srting类）

7）key和value之间存在单向一对一关系，即通过指定的key总能找到对应的value

```java
 Map map = new HashMap();
//        1）Map与Collection并列存在。用于保存具有映射关系的数据：Key-Value（双列元素, 遍历出是无序的）
//        2）Map中的key和value可以是任何引用数据类型，会封装到HashMap&Node对象中
//        3）Map中的key不允许重复，原因和HashSet一样，前面分析过
//        4）Map中的value可以重复（key不能重复，当有相同的key时新的key的value会替换旧的value）
        map.put("no1","zhangsan");
        map.put("no2","lisi");
        map.put("no1","lisi");
//        5）Map的key可以为null，value可以为null，注意key为null，只能有一个，value 为null，可以多个
        map.put(null,null);
        map.put(null,null);
        map.put("no3",null);
        map.put("no4",null);
        //        6）常使用String类作为Map的key（只要是Object的子类都可以，不范于srting类）
        map.put(new Object(),"zhangsan");
//        7）key和value之间存在单向一对一关系，即通过指定的key总能找到对应的value
//        通过get方法传入key，会返回对应的value
        System.out.println(map.get("no2"));
        System.out.println(map);
=============输出==================
  lisi
{no2=lisi, null=null, no1=lisi, no4=null, no3=null, java.lang.Object@1540e19d=zhangsan}


```

8）Map存放数据的key-value示意图，一对k-v是放在一个HashMap$Node中的，有因为Node实现了Entry接口，有些书上也说一对k-v就是一个Entry（如图）

![image-20220504165516988](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220504165516988.png)

数据存放在HashMap中，将set和collection作为一组对象放在Entry里面（其中不存放数据只是存放HashMap的引用）

1. 将HashMap中的key和value数据 存放到一个entrySet集合（该集合不存放数据，存放的都是引用）

```java
 Map map = new HashMap();
        map.put("no1","zhangsan");
        map.put("no2","lisi");//k-v
        map.put("no1","lisi");//k-v
//        1.k-v最后是HashMap$Node node = newNode(hash ,key,value,null);
//        2.k-v为了方便程序员遍历，还会创建EntrySet集合，该集合存放的元素类型（Entry），
//        而一个Entry对象就有k-v，EntrySet<Entry<k,v>>，即：transient Set<Map.Entry<k,v>> entrySet;

//        3.在entrySet中，定义的类型是Map.Entry，但是实际上存放的是HashMap$Node类型
//        因为HashMap$Node implement Map.Entry 因为实现了Map.Entry接口，那么这个类的对象实例可以赋给这个接口类型
//        4.当吧HashMap$Node存放到entrySet后就方便我们的遍历，因为Map.Entry提供了两个重要的方法，getKey()和getValue方法
        Set set = map.entrySet();
        System.out.println(set.getClass());
//        输出：class java.util.HashMap$EntrySet
        for (Object o :set) {
            System.out.println(o.getClass());
//            输出：class java.util.HashMap$Node
//            从HashMap$Node取出k-v
//            先做一个向下转型
            Map.Entry entry = (Map.Entry) o;
            System.out.println(entry.getKey() +""+ entry.getValue());
        }
```



#### map接口和常用方法

1）put：添加

2）remove：根据键删除映射关系

3）get：根据键获取值

4）size：获取元素个数

5）isEmpty：判断个数是否为0

6）clear；清楚

7）containsKey：查找键值否存在

```java
Map map = new HashMap();
        map.put("no1","zhangsan");
        map.put("no2","lisi");
        map.put(null,"lisi");
        map.put("no3","lisi");
        map.put("no4","2");

        map.remove(null);
        Object lisi = map.get("no2");
        System.out.println("lisi=="+lisi);

        System.out.println(map.size());

        map.isEmpty();
        System.out.println(map);
        map.clear();
        System.out.println(map);

        System.out.println(map.containsKey("no3"));

```



#### Map遍历方法

1）containsKey：查找键是否存在

2）KeySet：获取所有的键

3）entrySet：获取所有关系

4）values：获取所有的值

```java
  Map map = new HashMap();
        map.put("no1","zhangsan");
        map.put("no2","lisi");
        map.put(null,"sss");
        map.put("no3","lisdsdsi");
        map.put("no4","2");

//        第一粗：先取出所有的key，通过key取出对应的value
        Set set = map.keySet();
//        增强for
        for (Object o :set) {
            System.out.println(map.get(o));
        }
        System.out.println("迭代器");
//        （2） 使用迭代器
        Iterator iterator = set.iterator();
        while (iterator.hasNext()) {
            Object next =  iterator.next();
            System.out.println(map.get(next));
        }
        System.out.println("=========第二中=========");
//      第二组：吧所有的values取出
        Collection values = map.values();
//        这里可以使用所有的collections使用的遍历方法
        for (Object o :values) {
            System.out.println(o);
        }
//        迭代器
        System.out.println("迭代器");
        Iterator iterator1 = values.iterator();
        while (iterator1.hasNext()) {
            Object next =  iterator1.next();
            System.out.println(next);
        }

        System.out.println("=========第三中=========");
//        通过entryset获取
        Set set1 = map.entrySet();
        for (Object entry :set1) {
//            将entry转为map.entry
            Map.Entry  entry1= (Map.Entry) entry;
            System.out.println(entry1.getKey()+" "+entry1.getValue());
        }
        System.out.println("迭代器");
        Iterator iterator2 = set1.iterator();
        while (iterator2.hasNext()) {
            Object next =  iterator2.next();
            Map.Entry m = (Map.Entry) next;
            System.out.println(m.getKey()+" itit "+ m.getValue());
        }
```

#### 小结

1. Map接口的常用实现类：HashMap、Hashtable和Properties
2. HashMap是Map接口使用频率最高的实现类
3. HashMap是以key-value对的方式来存储数据（HashMap$Node类型）
4. key不能重复，但值可以，允许使用null键和null值
5. 如果添加相同的 key，则会覆盖原来的k-v，等同于修改，（key不会替换，val会替换）
6. 与HashSet一样，不保证映射的顺序，因为底层是以hash表的方式来储存的
7. HashMap没有实现同步，因此线程不安全 的

#### HashMap底层机制

1）HashMap底层维护了Node类型的数组table，默认为null

2）当创建对象时，将加载银子（loadfactor）初始化为0.75

3）当添加key-value时，通过key的哈希值得到在table的索引，然后判断该元素的key是否和准备加入的key相等，如果相等，则直接替换val；如果不相等需要判断是树结构还是连链表结构，做出相应处理。如果添加时发现容量不够则需扩容

4）第一次添加，则需扩容table容量为16，临界值(threshold)为12

5）以后再扩容，需要扩容table容量为原来的2倍，临界值为原来的2倍，即24，依次类推

6）在java8中，如果一条链表的元素个数超过TREEIFY_THRESHOLD（默认是8），并且table的大小>=MIN_TREEIFY_CAPACITY(默认64)，就会进行树化。

#### HashTable

**基本介绍**

1）存放的元素时键值对：key-value

2）hashTable的键和值都不能为null，否则会抛出空指针异常

3）hashTable使用方法基本上和HashMap一样

4）hashTable是线程安全的，HashMap是线程不安全的

![image-20220506160740866](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220506160740866.png)

#### Properties

**基本介绍**

1. properties类继承了Hashtable类并实现了Map接口，也是使用一种键值对(key-value)的形式来保存数据
2. 它的使用特点和Hashtable类似
3. properties还可用于从xxx.properties文件中，加载数据到properties类对象，并进行读取和修改
4. 说明：工作后 xxx.properties文件常用作配置文件，io流部分(详细讲解)[www.cnblogs.com/xudong-bupt/p/3758136.html]

## Collections

### Collections工具类

1）Collections是一个操作Set、List和Map等集合的工具类

2）Collections中提供了一系列静态的方法对集合元素进行排序、查询和修改等操作

### 排序操作（均为static方法）

1. reverse（List）：反转List中元素的顺序

2. shuffle（List）：对List集合元素进行随机排序

3. sort（List）：根据元素的自然顺序对指定List集合元素按升序排序

4. sort（List，Comparator）：根据指定的Comparator产生的顺序对List集合元素进行排序

5. swap（List，int，int）：将指定List集合中的i处元素和j处元素进行交换

6. 案例：

   ```java
   public class Collectionsdemo {
       public static void main(String[] args) {
           ArrayList list = new ArrayList();
           list.add("zhansgan");
           list.add("lisi");
           list.add("wngwu");
           list.add("laoliu");
           list.add("dasima");
           System.out.println("list="+list);
   //        1. reverse（List）：反转List中元素的顺序
           Collections.reverse(list);
           System.out.println("reverse="+list);
   //        2. shuffle（List）：对List集合元素进行随机排序
           for (int i = 0; i < 5; i++) {
               Collections.shuffle(list);
               System.out.println("随机"+list);
           }
   //        3. sort（List）：根据元素的自然顺序对指定List集合元素按升序排序
           Collections.sort(list);
           System.out.println("sort"+list);
   //        4. sort（List，Comparator）：根据指定的Comparator产生的顺序对List集合元素进行排序
           Collections.sort(list, new Comparator() {
               @Override
               public int compare(Object o1, Object o2) {
                   return ((String)o1).length()-((String)o2).length();
               }
           });
           System.out.println("字符串长度排序"+list);
   //        5. swap（List，int，int）：将指定List集合中的i处元素和j处元素进行交换
   
           Collections.swap(list,0,1);
           System.out.println("位置交换"+list);
       }
   }
   ```



### 查找、替换

1. Object max(Collection)：根据元素的自然顺序，返回给定集合中的最大元素

2. Object max（Collection，Comparator）：根据Comparator指定的顺序，返回给定集合中最大的元素

3. Object min（Collection)

4. Object min (Collection，Comparator)

5. int frequency （Collection，Object）：染回指定集合中指定元素的出现次数

6. void copy（List dest，List src）：将src中的内容复制到dest中

7. boolean replaceAll（List list，Object oldVal，Object newVal）：使用新值替换List对象的所有旧值

8. ```java
   public static void main(String[] args) {
           ArrayList list = new ArrayList();
           list.add("zhansgan");
           list.add("lisi");
           list.add("wngwu");
           list.add("laoliu");
           list.add("dasima");
           System.out.println("list="+list);
   //        1. Object max(Collection)：根据元素的自然顺序，返回给定集合中的最大元素
           System.out.println("max num="+Collections.max(list));
   //        2. Object max（Collection，Comparator）：根据Comparator指定的顺序，返回给定集合中最大的元素
   //            获取最大长度的值
           //        3. Object min（Collection)
   //        4. Object min (Collection，Comparator)同理
           Object max = Collections.max(list, new Comparator() {
   
               @Override
               public int compare(Object o1, Object o2) {
                   return ((String) o1).length() - ((String) o2).length();
               }
           });
           System.out.println("字符串最大的值为="+max);
   
   
   //        5. int frequency （Collection，Object）：染回指定集合中指定元素的出现次数
   
           System.out.println("lailiu="+ Collections.frequency(list,"lailiu"));
   //        6. void copy（List dest，List src）：将src中的内容复制到dest中
              ArrayList oldList =  new ArrayList();
   //           为了完成一个拷贝，我们需要先给oldList赋值，大小和list一样,不然会报错
           for (int i = 0; i < list.size(); i++) {
               oldList.add("");
           }
   //        拷贝
           Collections.copy(oldList,list);
           System.out.println("oldList="+oldList);
   
   //        7. boolean replaceAll（List list，Object oldVal，Object newVal）：使用新值替换List对象的所有旧值
           Collections.replaceAll(list,"laoliu","老六");
           System.out.println("替换后="+list);
       }
   ```













## 总结

在开发中，选择什么集合实现类，主要取决于业务操作特点，然后根据集合实现类特性进行选择分析如下

1）先判断储存类型（一组对象或一组键值对）

2）一组对象[单列]：Collection接口

* 允许重复：List
  * 增删多：LinkedList（底层维护了一个双向链表）
  * 改查多：ArrayList（底层维护了Object类型的可变数组）
* 不允许重复：Set
  * 无序：HashSet（底层是HashMap，维护了一个哈希表 即（数组+链表+红黑树））
  * 排序：TreeSet
  * 插入和取出顺序一直：LinkedHashSet，维护数组+双向链表

3）一组键值对[双列]：Map

* 键无序：HashMap（底层是：哈希表 jdk7：数组+链表，jdk8：数组+链表+红黑树）
* 键排序：TreeSet
* 键插入和取出顺序一致：LinkedHashMap
* 读取文件：Properties

# 泛型

## 泛型语法

```java
public static void main(String[] args) {
//        1.当我们ArrayList<Dog>表示放到ArrayList集合中的元素只能是Dog类型
//        2.如果编译器发现添加的类型不满足，就会报错
        ArrayList<Dog> dogs = new ArrayList<Dog>();
        dogs.add(new Dog("laogou",12));
        dogs.add(new Dog("xiaogou",1));
    }
//       方便遍历
        for (Dog dog : dogs) {
            System.out.println(dog);
        }
```

好处：

1. 编译时，检查添加元素的类型，提高了安全性
2. 减少了类型转换的次数，提高效率
3. 不再提示编译警告

### 介绍

理解：泛（广泛）型（类型）==> integer，String

可以表示数据类型的数据类型![image-20220509171057972](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220509171057972.png)

1）泛型又称参数化类型，时jdk5.0出现的新特性，解决数据类型的安全性问题

2）在类声明或实例化时只要制定好需要的具体的类型即可

3）java泛型可以保证如果程序在编译时没有发出警告，运行时就不会产生ClassCastException异常。同时，代码更加简洁、健壮

4）泛型的作用是：可以在类声明时通过一个标识表示类中某个属性的类型，或者是某个方法的返回值的类型，或者是参数类型

![image-20220509171249826](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220509171249826.png)

（此时E称为泛型，那么Dog->E（此时E为 ））

```java
Cat<String> tianyuanmao = new Cat<>("tianyuanmao");

class Cat<E> {
    E e;//E表示 e的数据类型，改数据类型在定义Cat对象时指定的，即在编译期间，就确定是什么类型了

    public Cat(E e) {//E也可在参数类型体现
        this.e = e;
    }
    public E method(){//返回类型也可体现
        return e;
    }

}
```

### 语法

泛型的声明

```java
interface 接口<T> {}
class类<K,V,...>{}(可以接收多个泛型等等)
说明：
    1.其中K,V,T不代表值，而是表示类型
    2.任意字母都可以。常用T表示，是type的缩写
```

泛型的实例化

```java
要在类名后面指定类型参数的值（类型）。如
//1
List <String> strList = new ArrayList<String>();
//2
Iterator <Customer> iterator = coustomers.iterator();

```

### 使用细节

1. interface List<T>{},public class HashSet<E>{}....等等

   1. 说明：T，E只能是引用类型
   2. 不能是基本数据类型（八大基本数据类型,int,double 等等）

2. 在指定泛型具体类型后，可以传入该类型或者其子类类型

3. 泛型适用形式

   1. ```java
      List<integer> list1 =new ArrayList<Integer>{}
      
      List<Integer> list2 = new ArrayList<>();
      ```

4. 如果我们这样写List list3 = new ArrayList（）；默认给它的泛型是[<E> E就是Object 类型]

   



## 自定义泛型

### 泛型类

**基本语法**

```java
class 类名<T,R....>{
成员
}
```

细节：

1. 普通成员可以使用泛型（属性，方法）

2. 使用泛型的数组，不能初始化

3. 静态方法中不能使用类的泛型‘

   1. 因为静态是和类相关的，在类加载时，对象还没创建
   2. 所以，如果静态方法和静态属性使用泛型时 ，JVM就无法完成初始化

4. 泛型类的类型，是在创建对象时确定的（因为创建对象时，需要指定确定类型）

5. 如果在创建对象时，没有指定类型，默认为object

6. ```java
   //1.demo后面有泛型，所以我们吧demo就称为自定义泛型类
   //2.T,R,M泛型的标识符，一般是单个大写字母
   //3.泛型标识符可以有多个
   //4.普通成员可以使用泛型 （属性，方法）
   //5.使用泛型的数组，不能初始化
   	//（因为数组在new的
   
   
   class demo<T,R,M>{
   String name;
   T t;
   R r;
   M m;
       T[] t1;//可以声明
       
       public demo11(String name, T t, R r, M m) {//构造器使用泛型
           this.name = name;
           this.t = t;
           this.r = r;
           this.m = m;
       }
       //方法使用泛型
        public String getName() {
           return name;
       }
   
       public void setName(String name) {
           this.name = name;
       }
   
       public T getT() {
           return t;
       }
   
       public void setT(T t) {
           this.t = t;
       }
   
       public R getR() {
           return r;
       }
   
       public void setR(R r) {
           this.r = r;
       }
   
       public M getM() {
           return m;
       }
   
       public void setM(M m) {
           this.m = m;
       }
   }
   ```

   





### 泛型接口

**基本语法**

```java
interface  接口名 <T,R...>{

}
```

细节：

1. 接口中，静态成员也不能使用泛型

2. 泛型接口的类型，在继承接口或者实现接口时确定

3. 没有指定类型，默认为Object

   

### 泛型方法

**基本语法**

```java
修饰符<T,R...>返回类型 方法名（番薯列表）{}
```

**注意细节**：

1. 反省方法，可以定义在普通类中，也可以定义在泛型类中

2. 当泛型方法被调用时，类型会确定

3. public void eat（E e）{}，修饰符后没有<T,R..>eat方法不是泛型方法，而是使用了泛型

4. ```java
   //泛型方法，可以定义在普通类中，也可以定义在泛型类中
   class Car{
       public void run(){//普通方法
   
       }
   //    1.T,R就是泛型标识符
   //    2.提供给fly方法使用的
       public <T,R> void  fly(T t, R r){//泛型方法
   
       }
   
   }
   ```

5. ```java
   class Car2<T,R>{//泛型类
       public <U,M> void  fly(U u, M m){//泛型方法
       }
       public void  fly2(T t){
   //        1.该方法不是泛型方法
   //        2.是fly2方法使用了类声明的泛型
       }
   ```

6. ```java 
   Car car = new Car();
           car.fly("baoma",2000);
           //在调用方法是，编译器会自动识别传入的参数的类型，就会确定型
   ```

7. 泛型方法可以使用类声明的泛型，也可使用自己声明的泛型

## 泛型继承和通配符

**介绍**

1)泛型不具备继承性

```java
List<Object> list = new ArrayList<String>();
//是错误的，因为泛型中没有继承性
```

2）<?>:支持任意泛型类型

3）<? extend A>:支持A类以及 A类的子类，规定了泛型的上限

![image-20220511142709072](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220511142709072.png)

4）<? super A>:支持A类以及A类的父类，不限于直接父类，规定了泛型的下限

![image-20220511142730306](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220511142730306.png)





















 



  









  









# 知识点补充

## JUnit

1. 一个类有很多功能代码需要测试，为了测试，就需要写入main方法中
2. 如果有很多个功能代码测试，就需要来回注销，切换很麻烦
3. 如果可以直接运行一个方法，就会方便很多

### 介绍：

1. 









  







# 练习部分

## 快速入门部分

1. 开发一个hello.java文件，输出：老王 is studying java！

   1. ```java
      public class hello{
      	public static void main(String[] args) {
      	System.out.println("lao wang is studying java");
      	
      	}
      }
      ```

   2. 需注意的事项：记得吧类部分带上public class 带上，不要只写个方法

## 制表符部分

1. ![image-20220204140604059](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220204140604059.png)

   1. ```java
      public class ChangeChar {
          public static void main(String[] args) {
              System.out.println("书名\t作者\t价格\t销量\n三国\t罗贯中\t120\t1000");
          }
      }
      ```

## 进制部分

* 第一部分

  ```
  1. 0b110001100
     =0*2^0 + 0*2^1 + 1*2^2 + 1*2^3 + 0*2^4 + 0*2^5 + 0*2^6 + 1*2^7 + 1*2^8
     =0+0+4+8+0+0+0+128+256
     =396
  02456
  =6*8^0 + 5*8^1 + 4*8^2 + 2*8^3
  =6+40+256+1024
  =1326
  
  0xA45
  =5*16^0 + 4*16^1 + 10*16^2
  =5 + 64 + 2560
  =2629
  ```

## 位运算练习

```
2|3
1. 2的原码：00000000 00000000 00000000 00000010
2. 2的补码：00000000 00000000 00000000 00000010
3. 3的原码：00000000 00000000 00000000 00000011
4. 3的补码：00000000 00000000 00000000 00000011
5.2|3：00000000 00000000 00000000 00000010（都为1结果为1否则为0）
6. 转为原码：00000000 00000000 00000000 00000010
7.结果为：2

2^3
1. 2的原码：00000000 00000000 00000000 00000010
2. 2的补码：00000000 00000000 00000000 00000010
3. 3的原码：00000000 00000000 00000000 00000011
4. 3的补码：00000000 00000000 00000000 00000011
5.2^3:00000000 00000000 00000000 00000001(两位一个为0，一个为1，结果为1，否则为0)
6.转为原码：00000000 00000000 00000000 00000001
7.结果为1
```

## switch练习

1. ![image-20220225162131420](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220225162131420.png)

   * ![image-20220225162214945](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220225162214945.png)

2. 3,4,5为春季。6，7，8，为夏季，9,10,11位秋季。12,1,2为冬季

   * ```java
     Scanner scanner = new Scanner(System.in);
             System.out.println("请输入月份");
             int month = scanner.nextInt();
             if (month>0 && month<=12){
                 switch (month){
                     case 3:
                     case 4:
                     case 5:
                         System.out.println("春季");
                         break;
                     case 6:
                     case 7:
                     case 8:
                         System.out.println("夏季");
                         break;
                     case 9:
                     case 10:
                     case 11:
                         System.out.println("秋季");
                         break;
                     case 12:
                     case 1:
                     case 2:
                         System.out.println("冬季");
                         break;
                 }
             }else {
                 System.out.println("输入不合法");
             }
     ```

## 数组部分

* 已知数组{10,12,45,90}。添加一个数使该数组依然是升序的

```java
//方法1：数组扩容➕冒泡排序

package basics.chapterArray;

import java.time.OffsetDateTime;
import java.util.Scanner;
import java.util.concurrent.ForkJoinPool;

public class exercisesArryHomeWork {
    /*
    * 已知数组{10,12,45,90}
    * 添加一个数使该数组依然是升序的
    * */
    public static void main(String[] args) {
        int[] arr = {10,12,45,90};
        char key;
        Scanner scanner = new Scanner(System.in);
        int inputnum;
        int tmp;

        do {
            int[] arr2 = new int[arr.length+1];
            for (int i = 0; i <arr.length ; i++) {
                arr2[i] = arr[i];
            }
            System.out.println("请输入添加一个数");
            inputnum = scanner.nextInt();
            arr2[arr2.length-1] = inputnum;
            arr = arr2;
            for (int i = 0; i <arr.length ; i++) {
                System.out.print(arr[i]+"\t");
            }


            System.out.println("是否继续输入? y/n");
            key = scanner.next().charAt(0);
            if (key == 'y'){
                System.out.println("continue");
            }else if (key == 'n'){
                System.out.println("end");
                break;
            }else {
                System.out.println("input error");
            }
        }while (true);
        System.out.println("============数组排序==============");
        for (int i = 0; i < arr.length-1; i++) {
            for (int j = 0; j <arr.length ; j++) {
                if (j>=arr.length-1){
                    break;
                }else if (arr[j]<=arr[j+1]){
                    System.out.println("no change");
                }else if (arr[j]>=arr[j+1]){
                    tmp = arr[j+1];
                    arr[j+1] = arr[j];
                    arr[j] = tmp;
                }

            }
        }


        System.out.println("=============输出==============");
        for (int i = 0; i <arr.length ; i++) {
            System.out.print(arr[i]+"\t");
        }





    }
}
```

方法二：定位➕扩容

 ```
 //1. 先定义原数组 
 //2. 遍历数组，如果发现insertnum < arr[i] ,说明i就是要插入的位置
 //3. 如果index 保留 index =i
 //4. 如果遍历完后，没有发现inserNum<=arr[i] ，说明index = arr.length
 即：添加到arr的最后
 ```

```java
package basics.chapterArray;

public class exercisesArrayHomeWorkmethod2 {
    public static void main(String[] args) {
        int[] arr = {10,12,45,90};
        int insertNum = 23;
        int index = -1;
//          数组定位
//        1.遍历数组
        for (int i = 0; i <arr.length ; i++) {
//            2. 如果arr[i]的这个数大于insertNum则表示这个数的位置是要添加的数的位置
            if (insertNum<=arr[i]){
//                3. 用index接受这个位置信息
                index = i;
                break;
            }
        }
//        4. 数组扩容添加
        int[] arr2 = new int[arr.length+1];
//        创建一个j，当插入前半部分时，j指向arr的数组的数不变。
        for (int i = 0,j=0; i <arr2.length; i++) {
//            如果i不等于上面得到的i的位置
            if ( i != index){
//                则将arr的数赋给对应的新数组
                arr2[i] = arr[j];
                j++;
            }else {

                arr2[i] = insertNum;
            }
        }
        arr = arr2;

        for (int i = 0; i <arr.length ; i++) {
            System.out.print(arr[i]+"\t");
        }
    }
}

```



### 二维数组部分

1. ```java
   //            int[][] arr = {{4,6},{1,4,5,7},{-2} };
   //          遍历数组,求和
   ```

   * ```java
     public static void main(String[] args) {
      
            int sum = 0;
            int[][] arr = {{4,6},{1,4,5,7},{-2}};
            for (int i = 0; i < arr.length; i++) {
                for (int j = 0; j <arr[i].length ; j++) {
                    sum = sum+ arr[i][j];
                }
            }
            System.out.println(sum);
        }
     ```

     

## 面向对象部分

```java
package basics.method;

import java.util.Scanner;
import java.util.TreeMap;

public class chapterMethod01 {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("请输入一个整数");
        int num = scanner.nextInt();
        AA aa = new AA();

//        第一种写法
//        boolean t = aa.odd(num);
//        if (t==true){
//            System.out.println("偶数");
//        }else {
//            System.out.println("奇数");
//        }

        /*
        * 第二种写法，较为简洁 。后续较为常见
        *
        * */

        if (aa.odd(1)){ //1 为true 2为false
            System.out.println("偶数");
        }else {
            System.out.println("奇数");
        }
    }
}
class AA{
    public boolean odd(int a){

//        if (a%2 ==0){
//
//            return true;
//        }else {
//
//            return false;
//        }
    return a%2==0 ?  true : false;
    }
}
```

### 递归

1、小球迷宫

![image-20220311132440361](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220311132440361.png)

1. 小球得到的路径和程序员设置的策略有关，即找到的上下左右的顺序相关
2. 再得到小球路径时，可以先使用（下右上左），再改成（上右下左）

```
1. 先用二维数组创建迷宫 8行7列
int[][] map =new int[8][7];
2.先规定map数组，0表示可以走，1表示障碍物
3. 将最上的一行，和最下面的一行。设置为1
for(int i=0;i<7;i++){
	map[0][i]=1;
	map[7][i]=1
}
```

```java
package com.smms.demo.method;

public class homeworkForMaze {
    public static void main(String[] args) {
        //1. 先创建迷宫
        int[][] map = new int[8][7];
        //2. 定义数组
        for (int i1 = 0; i1 <7 ; i1++) {
            map[0][i1] = 1;
            map[7][i1] = 1;
        }
        for (int i = 0; i < 8; i++) {
            map[i][0] = 1;
            map[i][6] = 1;
        }
        map[3][1]=1;
        map[3][2]=1;

        for (int i = 0; i < map.length; i++) {
            for (int j = 0; j < map[i].length; j++) {
                System.out.print(map[i][j]+"\t");
            }
            System.out.println();
        }
        System.out.println("==================分割线======================");

        System.out.println("use findWay");
        T t = new T();
        t.findWay(map,1,1);
        System.out.println("out print");
        for (int i = 0; i < map.length; i++) {
            for (int j = 0; j <map[i].length ; j++) {
                System.out.print(map[i][j]+"\t");

            }
            System.out.println();

        }
    }
}

// 使用递归回溯的思想解决该题
/*
1.创建findway方法
2.如果找到，就返回true ，否则返回false
3.map就是二维数组，即表示迷宫
4.i,j 就是老鼠的位置，初始化的位置为(1,1)
5.因为我们使用的是递归找路，所以先规定map内值的含义
0 表示可以走，1表示障碍物，2表示可以走，3表示走过
6.当map[6][5] =2就说明找到了通路，就可以结束，否则就继续

7.定下找路的策略，下->右->上->左
*
* */
class T{
    public boolean findWay(int[][] map,int i,int j){
        if (map[6][5]==2){
            return true;
        }else {
            if (map[i][j]==0){
//                标记可以走通为2
//                假定可以走通
                map[i][j]=2;
    //  找路策略,下->右->上->左
                if (findWay(map,i+1,j)){
                    return true;
                }else if (findWay(map,i,j+1)){
                    return true;
                }else if (findWay(map,i-1,j)){
                    return true;
                }else if (findWay(map,i,j-1)){
                    return true;
                }else {
                    map[i][j] =3;
                    return false;
                }
            }
            return false;
        }
    }
}

```

2、汉诺塔

```java
class A{
    public void move(int num,char a,char b, char c){
        if (num==1){
            System.out.println(a+"->"+c);
        }else {
//            如果有多个盘num，可以直接看成2个，最下边的和最上边的
//            1.先移动上面的盘子到b，借助c
            move(num-1,a,c,b);
//            2.吧下面的盘子移动到c
            System.out.println(a+"->"+c);
//            3.再把b塔的所有盘，移动到c，借助a
            move(num-1,b,a,c);
        }
    }
}
```

## 集合

1）分析HashSet和TreeSet分别如何实现去重

1. HashSet的去重机制：hahsCode()+equals()，底层先通过存入对象，进行运算得到一个hash值，通过hash得到对应的索引，如果发现table索引所在的位置没有数据直接存放，如果有数据，就进行equals比较（equals可由程序员重写），如果比较厚，不相同，就加入，相同就不加入
2. TreeSet去重机制：如果传入了一个Comparator匿名对象，就使用实现Comparator去重，如果方法返回为0，就认为相同的元素/数据，就不添加。如果没有传入Comparator对象，则以添加的对象实现的Compareable的compareTo去重

# 注意事项

1. 一个java文件中只能有一个public类，其他类的个数不限
   1. public的类名必须和文件名相同
   2. 编译后每一个类都对应一个class文件
2. equals方法两种书写方式
   1. name.equals("xxx");
   2. "xxx".eqauls(name); //推荐这一种，可以避免空指针



## 



# 面试题

**相关可能问道的面试题目**

1、 JDK、JRE、JVM的关系

1. JDK = JRE + java开发工具
2. JRE =  JVM ＋ 核心类库

2、 环境变量path的作用

1. 使dos界面能够使用java和javac 等命令
2. 先配置JAVA_HOME 指向JDK主目录
3. path根据JAVA_HOME 寻找其子目录

3、 为什么计算机都是以补码的方式运行的

* 因为它将正数负数都统一起来了

4、 new一个对象时，此时内存里发生了什么？

1. 先在方法区创建Person类
2. 在堆中开辟一个空间，内部存放形参
   1. 先初始化默认值，0和null，然后再将值赋进去
   2. 当执行到构造器的时候，值才会赋进去
   3. 引用类型的话，会将数据存放在常量池，在堆中放入地址。此时堆中的空间才会有赋值
3. 最后再把堆的地址，赋给栈中的p对象引用 (xxx p = new  xxx;)
4. ![image-20220314215432778](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220314215432778.png)



