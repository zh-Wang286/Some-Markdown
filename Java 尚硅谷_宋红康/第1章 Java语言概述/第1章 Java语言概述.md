**第1章 Java语言概述**

> Java系列整理自尚硅谷_宋红康老师

[TOC]



# 1.1 软件开发介绍

常用的DOS指令

| 命令 | 功能                              |
| ---- | --------------------------------- |
| dir  | 列出当前目录下的文件及文件夹      |
| md   | 创建目录                          |
| rd   | 删除目录                          |
| cd   | 进入指定目录（绝对位置/相对位置） |
| del  | 删除文件                          |
| exit | 退出DOS命令行                     |



# 1.2 Java语言概述

## 1.2.1 Java技术体系平台

| 版本                                   | 描述                                                         |
| -------------------------------------- | ------------------------------------------------------------ |
| Java SE(Java Standard Edition)标准版   | 支持面向桌面级应用（如Windows下的应用程序）的Java平台，提供了完整的Java核心API |
| Java EE(Java Enterprise Edition)企业版 | 是为开发企业环境下的应用程序提供的一套解决方案。该技术体系中包含的技术如:Servlet 、Jsp等，主要针对于Web应用程序开发。 |
| Java ME(Java Micro Edition)小型版      | 支持Java程序运行在移动终端（手机、PDA）上的平台，对Java API有所精简，并加入了针对移动终端的支持 |

## 1.2.2 主要特性

1. 易学的。语法与C语言和C++接近。
2. 强制面向对象。提供类、接口和继承等源语，只支持类之间的单继承，但支持接口之间的多继承，并支持类与接口之间的实现机制。
3. 分布式的。在基本的Java应用编程接口中有一个网络应用编程接口（java net），它提供了用于网络应用编程的类库，包括URL、URLConnection、Socket、ServerSocket等。Java的RMI（远程方法激活）机制也是开发分布式应用的重要手段。
4. 健壮的。Java的强类型机制、异常处理、垃圾的自动收集等是Java程序健壮性的重要保证。对指针的丢弃是Java的明智选择。
5. 安全的。
6. 体系是中立的。Java程序（后缀为java的文件）在Java平台上被
   编译为体系结构中立的字节码格式（后缀为class的文件），然后可以在实现这个
   Java平台的任何系统中运行。
7. 解释型的。
8. 性能略高的。
9. 原生态支持多线程的。在Java语言中，线程是一种特殊的对象，它必须
   由Thread类或其子（孙）类来创建。

# 1.3 Java运行机制及运行过程

Java虚拟机（JVM, Java Virtal Machine）

垃圾收集机制（GC, Garbage Collection）

环境搭建

1. 下载并安装JDK
2. 配置环境变量PATH。将Java工具所在路径定义到PATH环境变量中。
   1. 我的电脑-属性-高级系统设置-环境变量
   2. 编辑环境变量，在变量值开始处加上Java所在\bin目录
   3. 打开DOS命令行，任意目录下敲javac。如果出现javac的参数信息，配置成功。

# 1.4 开发体验 Hello World

1. 编写

   - ```java
     public class Test{
     	public static void main(String[] args) {
     		System.out.println(“Hello World!”);
     	}
     }
     ```

2. 编译

   - javac Test.java

3. 运行

   - java Test

4. 注释

   ```java
   // 单行注释
   
    /* 
   	多行注释 
   */ 
   
   /** 
   	文档注释
   */
   ```

   