- 笔试
- google 在线编程  gugou~

```
基础知识
编程能力
```

```
alibaba
需要掌握流行的编程语言和工具，对数据结构、算法、数据库、操作系统原理、计算机体系结构、计算机网络、离散数学
等基础学科要点掌握扎实，或者在某一领域特别突出
了解目前广泛应用的技术，有好奇心，愿意学习新知识、新技术，并且有很好的方法快速掌握，能够找到合适的场景实际动手
操作，并取得一定的成果

算法面试优秀不意味着技术面试优秀
- 项目经历和项目中遇到的实际问题
- 你遇到的印象最深的bug是什么
- 面向对象、设计模式
- 网络相关、安全相关、内存相关、并发相关
- 系统设计、scalability
```

```
计算机基础
- 操作系统  -网络  -数据库

编程语言基础
- 数据类型  -装箱与拆箱

编码技巧
- 递归控制
- 循环控制
- 边界控制
- 数据结构
- 树的遍历

面向对象思想
- 类与对象
- 接口与实现
- 继承与封装
- 不可变类型
- 泛型

设计模式
- 再谈Singleton
- 变继承关系为组合关系
- 对象如何创建

高级知识点
- 并行计算
- 多线程
- 资源管理
```

各大公司在线笔试题库
http://www.acmcoder.com/index
https://www.nowcoder.com
Google Code Jam 系统
https://code.google.com/codejam/kickstart

```
beautiful number
1 <= N <= 1000
1000 <= N <= 10^18
3 --> 2
13 --> 3
```

```
操作系统
进程  VS 线程
Process         Thread

32位，64位
操作系统为进程分配的最大内存使用大小不同

进程，程序运行的最小单位，包含线程，是线程的容器，进程之间不共享内存，进程之间的通信不容易实现
文件/网络句柄

线程
栈：包含变量，方法变量等
PC:program calculate  下一条执行指令的地址，放在内存中
TLS: thread local storage 

存储和寻址
硬盘-->内存-->缓存（CPU中）-->寄存器（CPU中）
寻址空间
进程中的指针在内存中能够取到的地址范围
每个进程有自己独立的寻址空间
32位操作系统，每个进程最大的寻址空间是 4G
64位系统，最大寻址空间是 ~10^19 byte
64位的JVM，可以使用更大的内存，32位的程序用64位的JVM，只需要重新编译

逻辑内存
虚拟内存（分页）
物理内存
```

```
网络协议，来解决信息传输过程中的可靠性和安全性问题
七层架构
应用层（HTTP/FTP协议）
传输层（UDP/TCP协议）
网络层（路由节点之间）
数据链路层（数据包，校验）

不可靠：
丢包，重复包，出错，乱序
不安全：
中间人攻击，窃取，篡改
```

```
传输如果是发送一个包，确认一个包，效率慢，影响吞吐
改进方式：发送多个包，确认多个包，顺序发送
滑动窗口问题
TCP协议中使用（三次握手 SYN--SYN,ACK--ACK）
维持发送方/接受方缓冲区
```
wireshark 网络抓包工具


```
关系型数据库
- 基于关系代数理论
- 缺点：表结构不直观（二维结构不完美），实现复杂，速度慢
- 优点：健壮性高，社区庞大
当时现在分布式技术的应用，导致对健壮性要求不那么高

事务 Transaction
ACID
- Atomicity  原子性
- Consistency 一致性
- Isolation 隔离性（互相不影响）
- Durability 持久性

事务的隔离级别（Isolation）：
- Read uncommitted
- Read committed
- Repeatable Reads 重复读
- Serializable 

set session transation isolation level repeatable read;
set session transation isolation level serializable;
begin;
set autocommit = 0;
select @@tx_isolation;
select a from tb for update;
update tb set a=1 ;
rollback;

事务太笨重，耗费资源，使用乐观锁
select a from tb where b=1;
update tb set a=2 where b=1;
乐观锁：
- 读取数据，记录Timestamp
- 修改数据
- 检查和提交数据

```

```
类型检查：
- 编译时：C  C++ Java  Go...
- 运行时：Python  Perl JS Ruby...

运行/编译：
- 编译为机器代码执行：C  C++...
- 编译为中间代码，在VM运行：Java  C#...
- 解释执行：Python  Perl JS...

编程范式（Programming Paradigm）
- 面向过程： C  Visual Basic...
- 面向对象： Java C# C++ Scala...
- 函数式: Haskell Erlang...
```

>补码，正数+负数=0 计算方式是取反+1

```
浮点数的比较
×  a == b
√  Math.abs(a-b) < eps
使用BigDecimal来计算浮点数
```

```
Java数据类型
primitive type VS  Object

primitive type：
- int,long,float...
- 值类型
- 使用 == 判断相等

Object：Integer,Long,Float,String...
- 引用类型
- == 判断是否为同一个Object
- equals或者Objects.equals(a,b)（1.7加的）判断值相等

装箱与拆箱
Boxing and Unboxing
Integer a = 2;// Boxing
Integer a = new Integer(2);// Boxing
int value = a.intValue();// Unboxing

new Integer(2) == 2? true  自动拆箱
new Integer(2) == new Integer(2)? false 

-- this method will always cache values in the range -128-127
Integer.valueOf(2) == Integer.valueOf(2)? true 返回同一个Integer
Integer.valueOf(1000) == Integer.valueOf(1000)? false 返回同一个Integer

Integer.valueOf(2).intValue == 2? true intvalue-->拆箱

new Integer(2).equals(new Integer(2))? true equals判断值相等
public boolean equals(Object obj){
    if (obj instanceof Integer) {
        return value == ((Integer)obj).intValue();
    } 
    return false;
}
```

