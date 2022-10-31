---
title: java基础(一)
comments: true
toc: true
date: 2022-10-27 12:40:00
categories:
  - 学习笔记
  - 编程
tags: java 编程
pic:
---



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



```
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

```java
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
```



# 注释

1. 文档注释

   ```
      javadoc -d 路径文件 -xx -yy xxx.java
      生成文档命令
      xx yy 分别代码javadoc标签命令 例如-auther -version等
   ```

   ```java
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

### equals

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

### 提示：

在断点调试的过程中，是运行状态，是以对象运行类型来执行的

### 介绍：

​	断点调试是指程序在的某一行设置一个断点，调试时，程序运行到这一行就会停住，然后可以一步一步往下调，调试过程中可以看到各个变量当前的值，出错的话，调试到出错的代码行即显示错误，停下。进行分析从而找到这个bug。

### 快捷键

* F7（跳入）
  * 跳入方法内
* F8（跳过）
  * 逐行执行代码
* shift+F8（跳出）
  * 跳出方法
* F9（resume，执行到下一个断点）

![image-20220324141333874](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220324141333874.png)



