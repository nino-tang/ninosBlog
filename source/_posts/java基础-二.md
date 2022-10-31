---
title: java基础(二)
comments: true
toc: true
date: 2022-10-27 14:31:57
categories:
  - 学习笔记
  - 编程
tags: java 编程
pic:
---

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

### 深入理解main方法

解释main方法的形式：public static void main(String[] args){}

main方法是java虚拟机调用的

1. java虚拟机需要调用类的main()方法，所以该方法的访问权限必须是public

2. java虚拟机在执行main()方法是不必创建对象，所有该方法必须是static

3. 该方法接收String类型的数组参数，该数组中保存执行java命令时传递给所运行的类的参数

4. java执行的程序 参数1 参数2  参数3

   ![image-20220403184106869](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220403184106869.png)

### 提示

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

     



## 代码块

### 介绍

代码块又称初始化块，属于类中的成员【即 是类的一部分】。类似于方法，将罗技语句封装在方法体中，通过{}包围起来

和方法不同，没有方法名，没有返回，没有参数，只有方法体。而且不用通过对象或类显式调用，而是在家类是，或创建对象时隐式调用。

### 基本语法



```java
[修饰符]{
	代码
};
```



### 注意：

1. 修饰符 可选，要写的话，也只能写static
2. 代码块分为两类，使用static修饰的叫静态代码块，没有static修饰的，叫普通代码块
3. 逻辑语句可以为任何罗技语句（输入，输出，方法调用，循环，判断等）
4. ; 号可以写上，也可以省略。

### 优点

1. 相当于另一种形式的构造器（对构造器的补充机制），可以做初始化的操作
2. 如果多个构造器中都有重复的语句，可以抽取到初始化块中，提高代码的重用性

### 案例

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

### 使用细节

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

### 介绍

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

### 介绍

final / 最后的，最终的

fianl 可以修饰类、属性、方法和局部变量

某些情况下，程序员可能有以下需求，就会使用到final：

1. 当不希望类被继承时，可以用final修饰
2. 当不希望父类的某个方法可以被子类覆盖/重写（override）时，可以用final关键字修饰
3. 当不希望类的某个属性的值被修改，可以使用final修饰
4. 当不希望某个局部变量被修改，可以使用final修饰



### 使用细节

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



### 介绍

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

### 细节

1. 抽象类不能被实例化
2. 抽象类不一定包含abstract方法。也就是说，抽象类可以没有abstract方法
3. 一旦包含了abstract方法，则这个类必须声明为abstract 
4. abstract 只能修饰类和方法，不能修饰属性和其他的
5. 抽象类可以有任意成员【抽象类的本质还是类】，比如：非抽象方法、构造器、静态属性等等
6. 抽象方法不能有主体，即不能实现。例如：abstract void method()；不能有{}
7. 如果一个类继承了抽象类，则它必须实现抽象类的所有抽象方法，除非它自己也声明为abstract 类（所谓实现就是有那个{}就可，具体内容不管）
8. 抽象方法不能使用private、final和static来修饰，因为这些关键字都是和重写相违背的

### 抽象类实践-模板设计模式

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

### 介绍

接口就是给出一些没有实现的方法，封装到一起，起到某个类要使用的时候，在根据具体情况吧这些方法写出来

### 语法

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

### 注意事项

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

### 介绍：

一个类的内部又完整的嵌套了另一个类结构。被嵌套的类成为内部类（inner class)，嵌套其他类的类成为外部类(out class)。是我们类的第五大成员

类的五大成员：

1. 属性
2. 方法
3. 构造器
4. 代码块
5. 内部类

### 基本语法

```java
class Outer{//外部类
	class inner{//内部类
	}
}

class other{//外部其他类
}
```

 

### 内部类的分类

定义在外部类局部位置上（比如方法内）

#### 1）局部内部类（有类名）

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

#### 2）匿名内部类（没有类名，重点！！！！）

#### 介绍：

1. 本质是类
2. 是一个内部类
3. 该类没有名字
4. 同时还是一个对象

匿名内部类是定义在外部类的局部位置

比如在方法中，并且没有类名

#### 基本语法

```java
new 类 或 接口（参数列表）{
	类体
};

anonymous
```

#### 演示 

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



#### 注意细节

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

#### 1）成员内部类（没用static修饰）

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

#### 2）静态内部类（使用static修饰）

##### 介绍

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

### 介绍

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

#### 处理机制图

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

##### 1）LoaclDate（日期）、localTime（时间）、loacalDateTime（日期和时间内）

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



## Instant 时间戳

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

### Collection接口实现类的特点

```java
Public interface Collection<E> extends Iterable<E>
```

1. Collection实现子类可以存放多个元素，每个元素可以是 Object
2. 有些Collection的实现类，可以存放重复的元素，有些不可以
3. 有些Collection的实现类，有些是有序的（List），有些不是有序（Set）
4. Collection接口没有直接实现子类，是通过它的子接口Set和List来实现的

### Collection接口和常用方法

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

### 使用Iterator（迭代器）

Collection接口遍历元素的方式1-使用Iterator（迭代器）

#### 基本介绍

1）Iterator对象成为迭代器，主要用于遍历Collection集合中的元素

2）所有实现了Collection接口的集合类都有一个iterator()方法，用以返回一个实现了Iterator接口的对象，即可返回一个迭代器

3）Iterator的结构![image-20220420231917444](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220420231917444.png)

4）Iterator仅用于遍历集合，Iterator本身并不存放对象

##### 迭代器的运行原

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

### for循环增强

Collection接口遍历元素的方式2-

增强for循环，可以代替iterator迭代器

特点：增强for就是简化版的iterator，本质一样。只能用于<span style="color:red">遍历集合或数组</span>

#### 基本语法

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

### List接口的常用方法

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

### 注意事项

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

### Set接口和常用方法

和List接口一样，Set接口也是Collection的子接口，因此常用方法和Collection接口一样

### set接口遍历方式

同Collection的遍历方式一样，因为Set接口是Collection接口的子接口

* 使用迭代器
* 增强for
* 不能使用索引的方式获取

#### 案例

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

### HashSet

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

#### HashSet底层机制说明 

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

#### HashSet的扩容和转成红黑树机制

1. HashSet底层是HashMap，第一次添加时，table数组扩容到16，临界值（threshold）是16*加载因子（localFactor）是0.75 =12
2. 如果table数组实用到了临界值12，就会扩容到16*2=32，新的临界值就是32 * 0.75 = 24,依次类推
3. 在java8中，如果一条链表的元素个数到达TREEIFY_THRESHOLD(默认是8),并且table的大小>=MIN_TREEIFY_CAPACITY(默认64),就会进行树化（红黑树），否则仍然采用数组扩容机制



## LinkedHashSet

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


### TreeSet

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

### Map**结构**

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



### map接口和常用方法

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



### Map遍历方法

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

### 小结

1. Map接口的常用实现类：HashMap、Hashtable和Properties
2. HashMap是Map接口使用频率最高的实现类
3. HashMap是以key-value对的方式来存储数据（HashMap$Node类型）
4. key不能重复，但值可以，允许使用null键和null值
5. 如果添加相同的 key，则会覆盖原来的k-v，等同于修改，（key不会替换，val会替换）
6. 与HashSet一样，不保证映射的顺序，因为底层是以hash表的方式来储存的
7. HashMap没有实现同步，因此线程不安全 的

### HashMap底层机制

1）HashMap底层维护了Node类型的数组table，默认为null

2）当创建对象时，将加载银子（loadfactor）初始化为0.75

3）当添加key-value时，通过key的哈希值得到在table的索引，然后判断该元素的key是否和准备加入的key相等，如果相等，则直接替换val；如果不相等需要判断是树结构还是连链表结构，做出相应处理。如果添加时发现容量不够则需扩容

4）第一次添加，则需扩容table容量为16，临界值(threshold)为12

5）以后再扩容，需要扩容table容量为原来的2倍，临界值为原来的2倍，即24，依次类推

6）在java8中，如果一条链表的元素个数超过TREEIFY_THRESHOLD（默认是8），并且table的大小>=MIN_TREEIFY_CAPACITY(默认64)，就会进行树化。

### HashTable

**基本介绍**

1）存放的元素时键值对：key-value

2）hashTable的键和值都不能为null，否则会抛出空指针异常

3）hashTable使用方法基本上和HashMap一样

4）hashTable是线程安全的，HashMap是线程不安全的

![image-20220506160740866](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/image-20220506160740866.png)

### Properties

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

## 介绍：

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



