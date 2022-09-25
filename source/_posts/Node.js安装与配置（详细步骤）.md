---
title: Node.js安装与配置（详细步骤）
date: 2022-09-24 21:52:45
tags: 安装
comments: true
toc: true
categories:
 - 安装文档
pic:
---

[TOC]



# 一、安装Node.js

## 1.下载

[Node.js官网下载](http://nodejs.cn/download/)
根据自身系统下载对应的安装包（我这里为Windows11 64位，故选择下载第一个安装包）

![在这里插入图片描述](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/914dfb1bae004d71bab1d7cc2c01a671.png)

## 2.安装

双击安装包，点击Next，勾选使用许可协议，点击Next，选择安装位置（可根据个人情况更换路径，我这里选择安装在E:\devTools\nodejs）

![在这里插入图片描述](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/493dfc78735841f395c4a116898f5c6f.png)

继续点击Next，点击Next，点击Install，点击Finish完成安装。

## 3.添加环境变量

### 3.1 进入环境变量，编辑【系统变量】下的变量【Path】

![选择Path变量](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/d128a4fe1ce34016b08a2842cde77166.png)

### 3.2 添加Node.js的安装路径（此处为E:\devTools\nodejs\）

![写入Node.js安装路径](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/4609bccc18d8419ea764fb0153454ca9.png)

# 二、验证是否安装成功

进入cmd命令行窗口，输入node -v查看nodejs版本

``` 
node -v
```

输入npm -v查看npm版本

```
npm -v
```


如下图所示，即为安装成功：

![验证是否安装成功](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/ff513962ea164d019d3a9d542d26f0ba.png)

# 三、修改模块下载位置

<span style="color:yellow;background:red">**此步骤修改以后npm全局下载模块的保存位置，可根据自身情况选择是否更改。**</span>

## 1.查看npm默认存放位置

使用npm get prefix查看npm全局模块的存放路径

```
npm get prefix
```


使用npm get cache查看npm缓存默认存放路径

```
npm get cache
```

![在这里插入图片描述](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/e21684575b404a7f87f83572f8df3d4c.png)

如上图所示，npm 全局模块存放位置以及cache的存放位置，默认是在 C 盘 “C:\Users\用户\AppData” 下。

## 2.在 nodejs 安装目录下，创建 “node_global” 和 “node_cache” 两个文件夹

![在这里插入图片描述](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/e9847471a84c45ddb1fc416a223cdb55.png)

## 3.修改默认文件夹

设置全局模块的安装路径到 “node_global” 文件夹，

```
npm config set prefix "E:\devTools\nodejs\node_global"
```

设置缓存到 “node_cache” 文件夹

```
npm config set cache "E:\devTools\nodejs\node_cache"
```


如下图所示：

![在这里插入图片描述](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/6e67a30770ff40c49f640007f96703d1.png)

<span style ="color:red">**注意：**</span>由于 node 全局模块大多数都是可以通过命令行访问的，还要把【node_global】的路径“E:\devTools\nodejs\node_global”加入到【系统变量 】下的【PATH】 变量中，方便直接使用命令行运行，如下图所示：

![在这里插入图片描述](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/bb96741ac93447aba9e65f0a184e3d11.png)

## 4.测试默认位置是否更改成功

经过上面的步骤，nodejs下载的模块就会自动下载到我们自定义的目录，接下来我们测试一下是否更改成功。输入下面的命令：

```
npm install express -g
```

或者

```
npm install express --global
```

<span style="color:red">**注意：**</span>“-g”等同于“–global”，“-g” 是全局安装，不加“-g”就是默认下载到当前目录。“-g” 表示安装到之前设置的【node_global】目录下，同时nodejs会自动地在node_global文件夹下创建【node_modules】子文件夹， 即自动下载到“E:\devTools\nodejs\node_global\node_modules” 路径下。

![在这里插入图片描述](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/e05642e304a443ec85794f2ac3bad6a8.png)如上图所示，下载express模块成功，然后在文件管理器中查看是否保存到上面自定义的路径下。

![在这里插入图片描述](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/d460d0cd30884a83bb175a6e6127aeca.png)可以看到，express模块已经成功地下载到【E:\devTools\nodejs\node_global\node_modules】下。

<span style="color:red">**注意：**</span>若执行命令npm install express -g出现如下报错：

![在这里插入图片描述](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/6caaa64529e0401aa2d467a8a5ceec22.png)

是由于对文件夹操作的权限不够，右击Nodejs文件夹->属性->安全，点击编辑，将所有权限都✔即可。

![在这里插入图片描述](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/d1a6f84379d3443bad6af4c734e169d7.png)

※执行npm install express -g仍然出错的话继续将nodejs下【node_cache】、【node_global】、【node_modules】这三个文件夹的所有权限勾选，再次执行：

```
npm install express -g
即可下载成功。
```

# 四、设置淘宝镜像

## 1.将npm默认的registry修改为淘宝registry

说明：npm 默认的 registry ,也就是下载 npm 包时会从国外的服务器下载，国内下载会很慢，一般更换为淘宝镜像：https://registry.npm.taobao.org。

### 1.1 查看当前使用的镜像路径

```
npm config get registry
```

![在这里插入图片描述](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/ef81e85548b74e06bc325a27a9914258.png)

### 1.2 更换npm为淘宝镜像

```
npm config set registry https://registry.npm.taobao.org/
```

### 1.3 检查镜像是否配置成功

再次执行npm config get registry，检查当前的镜像路径：

```
npm config get registry
```

![在这里插入图片描述](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/5e6a5bd3b935462fb2521db2d9ea2577.png)

如上图所示，npm默认的registry已修改为淘宝registry。

## 2.全局安装基于淘宝源的cnpm

说明：由于npm的服务器在海外，所以访问速度比较慢，访问不稳定 ，cnpm的服务器是由淘宝团队提供，服务器在国内，cnpm是npm镜像，一般会同步更新，相差在10分钟，所以cnpm在安装一些软件时候会比较有优势。但是cnpm一般只用于模块安装，在项目创建与卸载等相关操作时仍使用npm。

### 2.1 全局安装基于淘宝源的cnpm

```
npm install -g cnpm --registry=https://registry.npm.taobao.org
```

![在这里插入图片描述](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/b1247b4bd75d4e128914eba35e2ed91f.png)

### 2.2 本地查看cnpm模块

![在这里插入图片描述](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/d9dddf1705e84f5990b2062db823cde4.png)

### 2.3 执行命令查看cnpm是否安装成功

```
cnpm -v
```

如下图所示，即代表cnpm配置成功。

![在这里插入图片描述](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/a73fe1fb625b45ef9a04765a1e46fbae.png)

