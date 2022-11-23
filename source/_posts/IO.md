---
title: io流
comments: true
toc: true
date: 2022-11-23 22:45:59
categories:
  - 学习笔记
  - 编程
tags: 编程
pic:
---

# 文件

## 概念

文件就是保存数据的地方。例如：图片，视频等等。

### 文件流

文件在程序中是以流的方式存在的

![image-20220524105155343](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20220524105155343.png)

流：数据在数据源（文件）和程序（内存）之间经历的路径

输入流：数据从数据源到程序的路径

输出流：数据从程序到数据源的路径



## 常用操作

### 创建文件对象相关构造器和方法

```java
new File(String pathname)//根据路径构建一个File对象
new File(File parent,String child)//根据父目录文件+子路径构建
new File(String prant,String child)//根据父目录+子路径构建
    createNewFile方法  创建新文件
```

```java
package IO;

import java.io.File;
import java.io.IOException;

public class CreateFileDemo {
    public static void main(String[] args) {
//        方法一
//        new File(String pathname)
//          根据路径构建一个File对象
        String path = "D:\\tmp\\";
        String path2 = "D:\\tmp\\a.txt";
//        File file1 = new File("D:\\tmp\\a.txt");
        File file1 = new File(path2);
        try {
            file1.createNewFile();
        } catch (IOException e) {
            e.printStackTrace();
        }

//        方法二
//        new File(String prant,String child)
//        根据父目录+子路径构建
        File file2 = new File("D:\\tmp\\", "b.txt");
        try {
            file2.createNewFile();
        } catch (IOException e) {
            e.printStackTrace();
        }

//      方法三
//        new File(File parent,String child)
//      根据父目录文件+子路径构建
        File file3 = new File(path);
        try {
            new File(file3,"c.txt").createNewFile();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}

```

### 获取文件信息

1. getName   //获取名字
2. getAbsolutePath   //获取绝对路径
3. getParent      //获取父级目录
4. Length    //获取大小（按字节）
5. exists    //是否存在
6. isFile    //是不是一个文件
7. isDirectory   //是不是一个目录

```java
public void Demo1(){
        File file = new File("D:/tmp/a.txt");
        System.out.println(file.getName());
        System.out.println(file.getAbsolutePath());
        System.out.println(file.getParent());
        System.out.println(file.length());
        System.out.println(file.exists());
        System.out.println(file.isFile());
        System.out.println(file.isDirectory());

    }
```

### 常用的文件操作

1）目录的操作和文件删除

1. mkdir创建一级目录
2. mkdirs创建多级目录
3. delete删除空目录或文件

在java中目录和文件都是被当成文件进行处理的

```java
 public static void main(String[] args) {
//        判断d盘tmp文件夹a文件是否存在，如果存在则删除
        File file = new File("d:/tmp/a.txt");
        if (file.exists()){
            file.delete();
        }else {
            System.out.println("没有该文件");
//            没有就创建该目录

        }
    }

```



# IO流的原理和分类

## IO流的原理

I/O是Input和Output的缩写，I/O技术是非常实用的技术，用于处理数据传输。比如读写问价等等

在java程序中，对于数据的输入和输出操作以流的方式进行

java,io包下提供了各种“流”类和接口，用以获取不同种类的数据，并通过方法输入或输出数据

### 输入input

读取外部数据（例如：硬盘，u盘，等）

### 输出output

将程序输出到磁盘光盘等存储设备

## 流的分类

按操作的单位不同分为：字节流（8 bit），字符流（按字符）

按数据流的流向不同分类：输入流，输出流

按流的角色不同分为：节点流，处理流/包装流



| （抽象基类） | 字节流       | 字符流 |
| ------------ | ------------ | ------ |
| 输入流       | InputStream  | Reader |
| 输出流       | OutputStream | Writer |

1. java的io流共涉及40多个子类，实际上非常规则，都是从如上4个抽象基类派生的
2. 由这四个类派生出来的子类名称都是以其父类名作为子类名的后缀

## IO流体系图

![image-20220524155303403](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20220524155303403.png)

## 文件和流的关系

![image-20220524155439991](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20220524155439991.png)

文件数据相当于物品

流相当于外卖员，也就是说是传输媒介

# 输入流☆输出流☆

![image-20220524160446123](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20220524160446123.png)

## InputStream

字节输入流

InputStream抽象类是所有类字节输入流的超类

### FileInputStream

文件输入流

```java
 @Test
//    单个字符读取，效率较低
//    中文会乱码
    public void fileStreamDemo(){
        FileInputStream fileInputStream=null;
        String path = "d:/tmp/b.txt";
        int read=0;
        try {
             fileInputStream = new FileInputStream(path);
//            读取文件是一个字符一个字符的读取所以要使用循环
//           read方法读取
//            如果返回-1表示读取完成
            while ((read = fileInputStream.read())!=-1){
                System.out.print((char) read);//转成char显示
            }

        } catch (IOException e) {
            e.printStackTrace();
        }finally {
//            关闭流
            try {
                fileInputStream.close();
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
```

```java
  @Test
//    单个字符读取，效率较低
//    使用read(byte[] b)读取
    public void fileStreamDemo2(){
        byte[] b = new byte[8];//一次读八个字节
        FileInputStream fileInputStream=null;
        String path = "d:/tmp/b.txt";
        int readlength=0;
        try {
            fileInputStream = new FileInputStream(path);
//            读取文件是一个字符一个字符的读取所以要使用循环
//           read(byte[] b)方法读取
//          如果读取正常返回实际的读取内容
//            如果返回-1表示读取完毕
            while ((readlength = fileInputStream.read(b))!=-1){
//
                System.out.print(new String(b,0,readlength) );//显示
            }

        } catch (IOException e) {
            e.printStackTrace();
        }finally {
//            关闭流
            try {
                fileInputStream.close();
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
```



### BufferedInputStream

缓冲字节输入流

### ObjectInputStream

对象字节输入流

## Reader和Writer

### FileReader和FileWriter

FileReader和FileWriter**介绍**

FileReader和FileWriter都是字符流，即按照字符来操作io

### FileReader

![image-20220525172147626](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20220525172147626.png)



1. new FileReader(File/String)
2. read:每次读取单个字符，返回该字符，如果代文件末尾则返回-1
3. read( char[] ):批量读取多个字符到数组，返回读取到的字符数，如果到文件末尾则返回-1

相关api

1. new String (char []) :将char[]转成String
2. new String (char[],off,len):将char[] 的指定部分转换成String

```java
//    单个字符读取
    @Test
    public void demo1(){
        FileReader fileReader=null;
        String path = "d:\\tmp\\a.txt";
        int status = 0;
        try {
            fileReader = new FileReader(path);
            while ((status = fileReader.read())!=-1){
                System.out.print((char)status);
            }
        } catch (IOException e) {
            e.printStackTrace();
        }finally {
            try {
                fileReader.close();
            } catch (IOException e) {
                e.printStackTrace();
            }
        }

    }
//    数组读取
    @Test
    public void demo2(){
        FileReader fileReader=null;
        String path = "d:\\tmp\\a.txt";
        int status = 0;
        char[] chars = new char[10];
        try {
            fileReader = new FileReader(path);
            while ((status = fileReader.read(chars))!=-1){
                System.out.print(new String(chars,0,status));
            }
        } catch (IOException e) {
            e.printStackTrace();
        }finally {
            try {
                fileReader.close();
            } catch (IOException e) {
                e.printStackTrace();
            }
        }

    }
```

### FileWriter

![image-20220525172528666](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20220525172528666-16534708315411.png)

FileWriter**常用方法**

1. new FileWriter（File/String):覆盖模式。相当于流的指针在首段
2. new FileWriter（File/String, true)：追击模式，相当于流的指针在尾端
3. write（int）：写入单个字符
4. write（char[]）：写入指定数组
5. write（char[]，off，len）：写入指定数组的指定部分
6. write（String）：写入整个字符串
7. write（String，off，len）:写入字符串的指定部分

相关API

String类：toCharArray:将String转换成Char[]

**注意**:FileWriter使用后，必须要关闭（close）或刷新（flush），否则写入不到指定的文件



### BufferedReader

### InoutStreamReader



## OutputStream

### FileOutputStream

```java
package IO;

import java.io.*;
import java.nio.charset.StandardCharsets;

public class OutputStreamDemo {
    public static void main(String[] args) {
        String path = "d:\\tmp\\a.txt";
        String input = "hello word";
        FileOutputStream outputStream = null;

        try {

//            使用outputStream = new FileOutputStream(path);方式创建时，会覆盖原有的数据
//            如果使用outputStream = new FileOutputStream(filepath，true);方法创建时，是以追加的方式写入数据，原有的数据还存在
            outputStream = new FileOutputStream(path);
            //        写入一个字节
//         outputStream.write('a');
//        写入字符串
            String str = "hello word 我d你妈的 我柜子动了";
            outputStream.write(str.getBytes(StandardCharsets.UTF_8));

//            或者使用以下写法
     /** b - 数据。off - 数据中的起始偏移量。len - 要写入的字节数。*/
            outputStream.write(str.getBytes(),0,str.length());
        } catch (IOException e) {
            e.printStackTrace();
        }finally {
            try {
                outputStream.close();
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
}

```

```java
//            解决中文写入乱码
            OutputStreamWriter outputStreamWriter = new OutputStreamWriter(new FileOutputStream(path),"utf-8");
//            追击到文件内
            outputStreamWriter.append(str);
//            关闭流
            outputStreamWriter.close();
```





# 节点流和处理流 

![image-20220601143531379](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20220601143531379.png)





## 节点流

节点流可以从一个特定的数据源读写数据，如FileReader，FileWriter

![image-20220526144023634](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20220526144023634.png)

节点流说白了就是针对不同的数据源使用不同的方法：

![image-20220601144107494](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20220601144107494.png)



## 处理流

### BufferedReader 和 BufferedWriter

处理流（也叫包装流）是“连接”在已存在的流（节点流或处理流）之上，为程序提供更为强大的读写功能，如BufferedReader、BufferedWriter

![](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20220526144705457.png)

![image-20220601144714555](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20220601144714555.png)

如上图，在BufferedReader类中，有属性Reader，既可以封装一个节点流(该节点流可以是任意的，只要是reader的子类就可以了)

只要使用Buffered r/w可以对不同类型的数据源进行操作，不用专门的去调用专门的流操作。

```java
  public static void main(String[] args)  {
//
//        用于copy文本灯类型的文件，不能拷贝音频视频等文件
        String path1 = "d:\\a.txt";
        String path2 = "d:\\b.txt";
        BufferedReader bufferedReader = null;
        BufferedWriter bufferedWriter = null;
        String line;

        try {
            bufferedReader = new BufferedReader(new FileReader(path1));
            bufferedWriter = new BufferedWriter(new FileWriter(path2));


            while ((line = bufferedReader.readLine())!=null){
                bufferedWriter.write(line);
                bufferedWriter.newLine();
            }

        } catch (IOException e) {
            e.printStackTrace();
        }finally {
            try {
                if (bufferedReader!=null){
                    bufferedReader.close();
                }
                if (bufferedWriter!=null){
                    bufferedWriter.close();
                }


            } catch (IOException e) {
                e.printStackTrace();
            }

        }



    }
```

### BufferedInputStream和BufferedOutputStream

```java
    @Test
public void copyFile(){
        String path1 = "d:\\kuan.jpg";
        String path2 = "d:\\kuan2.jpg";
        byte[] bytes = new byte[10];
        int length = 0;

        BufferedInputStream bi  = null;
        BufferedOutputStream bw = null;


        try {
            bi = new BufferedInputStream(new FileInputStream(path1));
            bw = new BufferedOutputStream(new FileOutputStream(path2));

            while ((length = bi.read(bytes)) != -1){
                bw.write(bytes,0,length);
                System.out.println("-----");

            }
        } catch (Exception e) {
            e.printStackTrace();
        }finally {
            try {
                if (bi != null){
                    bi.close();
                }
                if (bw != null){
                    bw.close();
                }

            } catch (IOException e) {
                e.printStackTrace();
            }

        }


    }
```

### 对象处理流

#### ObjectInputStream和ObjectOutputStream

看一个需求

1. 将int num = 100 这个int数据保存到文件中，注意不是100数字，而是int 100 ，并且，能够从文件中恢复int 100。
2. 将Dog dog   = new Dog("小黄"  , 2)这个dog对象保存到文件中，并且能够从文件恢复。
3. 上面的要求，就是能够将基本数据类型挥着对象进行序列化和反序列化操作

#### 序列化和反序列化

1. 序列化就是保存数据时，保存数据的值和数据类型

2. 反序列化就是在恢复数据时，恢复数据的值和数据类型

3. 需要让某个对象支持序列化机制，则必须让其类是可序列化的，为了让某个类是可序列化的，该类必须实现如下两个接口之一：

   * Serializable //这是一个标记接口，没有方法
   * Externalizable //该接口有方法需要实现，因此我们一般使用上面的Serializable接口

   功能：提供了对基本类型或对象类型的序列化和反序列化的方法

   1. ObjectInputStream提供序列化功能

      ![image-20220607141540445](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20220607141540445-16545826558161.png)

   2. ObjectOutputStream提供反序列化功能

      ![image-20220607141900370](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20220607141900370.png)

      ```java 
      //序列化---- 
      public static void main(String[] args) {
      //        序列化之后，保存的文本格式，不是存文本，而是按照它特点有的格式进行保存的，所以后缀可以无视
              String path  = "d:\\demo.bat";
              try {
                  ObjectOutputStream objectOutputStream = new ObjectOutputStream(new FileOutputStream(path));
                  objectOutputStream.write(100);//int -> intger(实现了 Serialzable)
                  objectOutputStream.writeBoolean(true);//boolean--》Boolean（实现了Serialzable）
                  objectOutputStream.writeChar('a');//char --->Char(实现了Serialzable)
                  objectOutputStream.writeDouble(0.3);//double --> Double（实现了Serialzable）
                  objectOutputStream.writeUTF("wdnmd，我柜子动了");//String
                  objectOutputStream.writeObject(new Dog("jiuhuang",4));
      
      
                  objectOutputStream.close();
                  System.out.println("执行完毕");
              } catch (IOException e) {
                  e.printStackTrace();
              }
          }
      注意：创建的Dog对象需要实现Serialzable对象
      ```
      
      ```java
      反序列化   
      public static void main(String[] args) throws IOException, ClassNotFoundException {
      //        指定反序列化文件
              String path = "d:\\demo.bat";
      
              ObjectInputStream objectInputStream = new ObjectInputStream(new FileInputStream(path));
      //        读取
      //        读取（反序列化）的顺序和保存数据（序列化）的顺序一致
              System.out.println(objectInputStream.readInt());
              System.out.println(objectInputStream.readBoolean());
              System.out.println(objectInputStream.readChar());
              System.out.println(objectInputStream.readDouble());
              System.out.println(objectInputStream.readUTF());
              //System.out.println(objectInputStream.readObject());
      //      如果我们需要dog的方法等，需要将其向下转型
              Object dog = objectInputStream.readObject();
              Dog dog1 = (Dog) dog;
              System.out.println(dog1.getName());
              System.out.println(dog1.getAge());
      
      
      
      
              objectInputStream.close();
          }
      ```

#### 区别

注意事项和细节说明

1. 读写顺序要一致
2. 要求实现序列化或反序列化对象，需要实现Serialzable
3. 序列化的类中建议添加SerialVersionUID，为了提高版本的兼容性
   * SerialVersionUID   序列化的版本号，可以提高版本号 
4. 序列化对象时，默认将里面所有属性都进行序列化，但除了static或transient修饰的成员
5. 序列化对象时，要求里面的属性类型也需要实现序列化接口
6. 序列化具备可继承性，也就是如果某类已经实现了序列化，则它的所有子类也已经默认实现了序列化













## 区别

1. 节点流是底层流/低级流，直接跟数据源相接
2. 处理流包括节点流，既可以消除不同节点流的实现差异，也可以提供更方便的方法来完成输 入/输出
3. 处理流（也叫包装流）对节点流进行包装，使用修饰器设计模式，不会直接与数据源相连【模拟修饰器设计模式】

处理流的功能主要体现在以下两个方面：

1. 性能的提高：主要以增加缓冲的方式来提高输入输出的效率。
2. 操作的便捷：处理流可能提供了一系列便捷的方法来依次输入输出大批量的数据，使用更加灵活



## 标准输入输出流

介绍

|                     | 类型        | 默认设备 |
| ------------------- | ----------- | -------- |
| System.in 标准输入  | InputStream | 键盘     |
| System.out 标准输出 | PrintStream | 显示器   |

![image-20220608144751067](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20220608144751067.png)

## 转换流



先看一个文件乱码问题，引出转换流的必要性

![image-20220608145158672](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20220608145158672.png)

读取文件乱码问题，主要原因是没有指定读取该文件的编码方式



**介绍**

InputStreamReader 和 OutputStreamWriter

1. InputStreamReader:Reader的子类，可以将InputStream(字节流)包装秤Reader（字符流）

2. OutputStreamWriter:Writer的子类，实现将OutputStream（字节流）包装秤Writer（字符流）

3. 当处理纯文本数据时，如果使用字符流效率更高，并且可以有效解决中文问题，所以建议将字节流转换成字符流

4. 可以在使用时指定编码格式（比如utf-8，gbk，gb2312，iso8859-1等）

5. ![image-20220608150456021](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20220608150456021.png)

6. ![image-20220608150739490](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20220608150739490.png)

   

```java
package IO;

import sun.nio.cs.ext.GBK;

import java.io.*;

public class convertStream {
    public static void main(String[] args) throws Exception{
        String path = "d:\\a.txt";
//        1. 把FileInputStream转成InputStreamReader、
//        2. 指定编码 gbk
//        InputStreamReader inputStream = new InputStreamReader(new FileInputStream(path),"utf-8");
//         把InputStreamReader传入bufferedReader
//        BufferedReader bufferedReader = new BufferedReader(inputStream);
//        可以直接合成一句话
        BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(new FileInputStream(path),"utf-8"));
//        读取
        String s = bufferedReader.readLine();
        System.out.println("内容==="+s);
//        关闭流
        bufferedReader.close();
    }
}
```

## 打印流

printStream和printWriter

打印流只有输出流，没有输入流



printStream：如下图printStream是字节流不是字符流![image-20220608172432318](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20220608172432318.png)

![image-20220608172507617](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20220608172507617.png)

```java
public class PrintSteam_ {
    public static void main(String[] args) throws IOException {
//        基本使用

        PrintStream out = System.out;
//        在默认情况下，PrintStream输出的位置是标准输出  即显示器
        out.println("hello word");
//      因为print底层使用的write，所以我们可以直接调用write进行打印输出
        out.write("zijie".getBytes());

        out.close();
//        我们可以修改打印流的输出位置或设备
        System.setOut(new PrintStream("d:\\log.txt"));
        System.out.println("xxxxxx");
    }
}
```



   printWriter字符流![image-20220608172616868](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20220608172616868.png)

![image-20220609093321400](https://ninos-img.oss-cn-shanghai.aliyuncs.com/img/image-20220609093321400.png)

```java
   public static void main(String[] args) throws IOException {
//        PrintWriter printWriter = new PrintWriter(System.out);
//      使用new filewriter之后，相当于重定向到该路径下的文件
        PrintWriter printWriter = new PrintWriter(new FileWriter("d:\\log.txt"));

        printWriter.println("zhangsan");

        printWriter.close();
    }
```



 



# properties类

传统方法认识properties

```java
public static void main(String[] args) throws IOException {
        BufferedReader bufferedReader = new BufferedReader(new FileReader("src\\main\\resources\\mysql.properties"));
        String line = "";
        while ((line=bufferedReader.readLine())!=null){
//            使用split分割
            String[] split = line.split("=");
            System.out.println(split[0]+"值是："+split[1]);
        }

        bufferedReader.close();
    }
```

## 介绍

1）专门用于读写配置文件的集合类

配置文件的格式：

键 = 值

键 = 值

2）注意：键值对不需要有空格，值不需要用引号一起来。默认类型是String

3）Properties的常见方法

* load：加载配置文件的键值对到Properties对象
* list：将数据显示到指定设备
* getProperty（key）：根据键获取值
* setProperty（key,value）：设置键值对到Properties对象
* store：将Properties中的键值对存到配置文件，在idea中，保存信息到配置文件，如果含有中文，会储存为unicode码

(unicode码查询工具)[http://tool.chinaz.com/tools/unicode.aspx]

```java
package IO.properties;

import org.junit.jupiter.api.Test;

import java.io.BufferedReader;
import java.io.FileNotFoundException;
import java.io.FileReader;
import java.io.IOException;
import java.util.Properties;

public class properties {
    public static void main(String[] args) throws IOException {
        BufferedReader bufferedReader = new BufferedReader(new FileReader("src\\main\\resources\\mysql.properties"));
        String line = "";
        while ((line=bufferedReader.readLine())!=null){
//            使用split分割
            String[] split = line.split("=");
            System.out.println(split[0]+"值是："+split[1]);
        }

        bufferedReader.close();
    }
}


class properties2{
    @Test
    public void proDeomo() throws IOException {
//        读取文件
//        1.创建properties对象
        Properties properties = new Properties();
//        2. 加载配置文件
        properties.load(new FileReader("src\\main\\resources\\mysql.properties"));
//        3. 吧k-v显示控制台
        properties.list(System.out);

//        根据key获取对应的值
        String user = properties.getProperty("user");
        String password = properties.getProperty("password");
        System.out.println("账号"+user);
        System.out.println("密码"+password);

    }
}
```

```java
public class properties02 {
    public static void main(String[] args) throws IOException {

//        输入中文则是以unicode码保存的

//        1. 使用properties类创建配置文件，修改配置文件内容
        Properties properties = new Properties();
//         2. 创建k-v
//        如果该文件没有key，就是创建
//        如果有则是修改
        /*
        * Properties父类是hashtable，底层就是HashTable核心方法
        * */

        properties.setProperty("username","nino");
        properties.setProperty("password","123123123");
        properties.setProperty("url","www.pornhub.com");
//      3. 将k-v存储文件中
        properties.store(new FileOutputStream("src\\main\\resources\\2.properties"),"注释");
        System.out.println("保存成功");
    }
}
```

