---
title: 8张图-Java基础
date: 2019-01-05 10:34:06
tags: String,equal,hash,exception,collection,thread,JVM
---

### 1、字符串不变性
![1](.\image\string-java-1.png)

### 2、equals()和hashCode()区别
> hashCode被设计用来提升性能。
<br/>
1.如果两个Object相等（equal），那么hash值一定相等。
<br/>
2.如果两个Object的hash值相同，但未必相等（equal）。

![22](.\image\equal-hashcode.png)

### 3、异常层次结构
> 红色是受检查异常，必须被捕获，或者在函数中声明为抛出该异常

![33](.\image\exception-tree.png)

### 4、集合类层次结构
> Collections和Collection的区别（Collections包含有各种有关集合操作的静态多态方法）

![4](.\image\collection-collections.png)

### 5、Java同步机制
> 形象的示意图 <br/>
锁持有线程或进程<br/>
等待锁线程或进程<br/>


![5](.\image\thread-synchronize.png)

### 6、别名
> 多个变量指向同一内存块，别名可能是不同的对象类型（继承）

![6](.\image\othername.png)

### 7、heap和stack
> 方法和对象在运行时内存中的位置

![7](.\image\function-object.png)

### 8、虚拟机运行时数据区
> JVM内存管理

![8](.\image\jvm.png)
