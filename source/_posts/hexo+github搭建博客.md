---
title: hexo+github搭建博客
date: 2022-09-24 21:52:45
cover: https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/343d28b9c9178b0b857abee140a668b1.png
tags: 安装
comments: true
toc: true
categories:
 - 安装文档
 - 博客相关
pic:
---

[TOC]



# 环境准备

## 1、安装nodejs

直接到官网上下载安装即可https://nodejs.org/en/download/

- [Node.js](http://nodejs.org/) (Node.js 版本需不低于 10.13，建议使用 Node.js 12.0 及以上版本)
- Node自带npm

详细安装配置

nodejs配置



## 2、安装git

Windows：下载并安装 git.
Mac：使用 Homebrew, MacPorts 或者下载 安装程序。
Linux (Ubuntu, Debian)：sudo apt-get install git-core
Linux (Fedora, Red Hat, CentOS)：sudo yum install git-core

![img](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/343d28b9c9178b0b857abee140a668b1.png)

npm下载慢的话也可以下载淘宝下载源cnpm

```
npm install -g cnpm --registry=https://registry.npm.taobao.org
```

![img](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/e21b605afbc75a0e08824e062dae3ea4.png)

# 开始安装Hexo

## 1.安装hexo

```
npm install -g hexo-cli
或者
cnpm install -g hexo-cli
123
```

安装完成可输入hexo -v查看版本

![image-20211203164700035](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/bba538484708b3e30f14af8557501c3c.png)

## 2、初始化hexo，新建存储博客的文件夹

```
hexo init myblog（本地文件夹名称：可自定义）
```

![image-20211203165005655](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/d01a6881209137448e5385dd3534097d.png)

## 3、进入文件夹，安装一下npm

```
cd myblog
npm install
```

可以看到我们的hexo站点就已经安装好了，接下来就可以直接启动他了

![iShot2021-12-03 16.55.54](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/bcf516435e0c18ccdd4bb12f2fe04e2a.png)

## 4、启动服务站点

```
hexo g 
hexo server
```

![image-20211203165829687](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/af32bf9e9c204c69d873df7c3437c3a4.png)

访问http://localhost:4000/ 至此hero就搭建好了。可以在本地访问了

![20211203170208](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/3a611caeb2993779a773aaad9864d493.png)

# 将hexo博客站点上传到github上

## 1、新建guthub仓库

仓库名称限制了为你的：用户名+.github.io

![image-20211203213307819](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/d2560d7f2d59f5f9b587a34cd2819307.png)

## 2、安装hexo上传插件

这里需要安装一个hexo的上传插件deploy-git

```
npm install hexo-deployer-git --save
```

![image-20211203171157254](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/49d71ebd13729dd4acb6f52cb5b07b70.png)

## 3、修改hexo配置文件指定仓库路径

可在文件夹中直接打开文件，也可通过vim直接编辑

![image-20211203213606004](https://imagebed-1306275532.cos.ap-shanghai.myqcloud.com/img/57b7452a5399f57b0e3ef2ef1a5d8271.png)

## 4、推送站点到github

```
推送命令
hexo d
```



# 注意事项

推送过程中需要输入你的github用户名和密码。但是在2021年8月14日开始github官方就加强安全访问。不能通过原有账号密码git访问，密码需要用官方的token或者采用ssh公私钥访问。否则会出现下图：鉴权失败（用户名密码错误）



# hexo文件夹详解：

* node_modules：是依赖包
*  public：存放的是生成的页面
*  scaffolds：命令生成文章等的模板
*  source：用命令创建的各种文章
*  themes：主题
*  _config.yml：整个博客的配置
*  db.json：source解析所得到的
*  package.json：项目所需模块项目的配置信息

