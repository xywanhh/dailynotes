```
深入理解jvm

- 历史
- 内存结构
- 垃圾回收机制
- 性能监控工具
- 性能调优
- 类的文件结构
- 类加载机制
- 字节码执行引擎
- 虚拟机编译及运行时优化
- java线程高级

JDK  Java Development Kit
JRE  Java Runtime Environment
JVM  Jave Virtual Machine

模拟内存溢出：
List<Demo> list = new ArrayList<Demo>();
for(;;){
    list.add(new Demo());
}
->java.lang.OutOfMemoryError: Java heap space
在运行时生成堆栈快照：
VM arguments:
-XX:+HeapDumpOnOutOfMemoryError -Xmx20m -Xmx20m
--> 
Dumping heap to java_pid1880.hprof ...
Heap dump file created [245425 bytes in 0.131 secs]
利用工具来分析堆栈快照文件
Eclipse Memory Analyzer
file->Open Heap Dump

jvm监控工具：
/bin/jconsole.exe -->lib/tools.jar  源码

>jps    -列出所有进程

HotSpot VM  Oracle
J9  IBM
Azul VM   Liquid VM   高性能的Java虚拟机
Taobao VM  

Java 虚拟机规范

```

```java
class Main extends JFrame {
    private JButton jb;
    public Main(){
        this.setBounds(200,200,200,200);
        this.setTitle("lambda测试");
        
        jb = new JButton("click here");
        jb.addActionListener(new ActionListener(){
            @Override
            public void actionPerformed(ActionEvent e){
                System.out.println("click");
            }
        });
        // use lambda
        jb.addActionListener(evnet -> System.out.print("click"));
        this.add(jb);
        this.setVisible(true);
        this.setDefaultCloseOperation(EXIT_ON_CLOSE);
    }

}
```

```
Java内存区域：

线程独占区域 / 程序计数器:
- 程序计数器是一块较小的内存空间，它可以看做是当前线程所执行的字节码的行号指示器
- 程序计数器处于线程独占区
- 如果线程执行的是java方法，这个计数器记录的就是正在执行的虚拟机字节码指令的地址。如果正在执行的是native方法，这个计算器的值是undefined
- 此区域是唯一一个在java虚拟机规范中没有规定任何OutOfMemoryError情况的区域

线程独占区域 / Java虚拟机栈：
- 虚拟机栈描述的是Java方法执行的动态内存模型
- 栈帧：每个方法执行，都会创建一个栈帧，伴随着方法从创建到执行完成，用于存储局部变量表，操作数栈，动态链接，方法出口等
- 局部变量表：存放编译期可知的各种基本数据类型，引用类型，returnAddress类型。局部变量表的内存空间在编译期完成分配，当进入一个方法时，这个方法需要在帧分配多少内存是固定的，在方法运行期间是不会改变局部变量表的大小。
- 大小：jvm设置 超过报java.lang.StackOverflowError  java.lang.OutOfMemoryError

线程独占区域 / 本地方法栈：
- 在HotSpot中，本地方法栈和虚拟机栈是放在一起的，不区分，一般的话，有区分，虚拟机栈是为虚拟机执行java方法服务，本地方法栈是为虚拟机执行native方法服务，两者基本相似

线程共享区 / Java堆：
- 存放对象实例
- 垃圾收集器管理的主要区域
- 新生代，老年代，Eden空间
- OutOfMemory

线程共享区 / 方法区：
- 存储虚拟机加载的类信息（类的版本，字段，方法，接口等），常量（池），静态变量，即时编译器编译后的代码等数据
- 方法区和永久代
- 垃圾回收在方法区的行为
- 异常 OutOfMemoryError


方法区 / 运行时常量池

String s1 = "abc";
String s2 = "abc";
String s3 = "a" + "bc";
String s4 = new String("abc");
System.out.println(s1 == s2); // true
System.out.println(s1 == s3); // true
System.out.println(s1 == s4); // false
System.out.println(s1 == s4.intern()); // true

直接创建的字符串对象，是放在方法区的常量池中，常量池的实现类似StringTable:HashSet（唯一不重复）
new出来的的字符串放在栈中，intern()方法把栈中的引用移动到常量池中

对象的结构：
- Header(对象头)
自身运行时的数据（Mark Word） 哈希值 GC分代年龄 锁状态标志  线程持有的锁 偏向线程ID 偏向时间戳
类型指针
- InstanceData
- Padding

对象的访问定位：
- 使用句柄
- 直接指针

垃圾回收
- 如何判定对象为垃圾
    - 引用计数法
    - 可达性分析法
- 如何回收
    - 回收的策略
        - 标记-清除算法
        - 复制算法
        - 标记-整理算法
        - 分代收集算法
    - 垃圾回收器
        - Serial
        - Parnew
        - Cms
        - G1        
- 何时回收

引用计数法：
在对象中添加一个引用计数器，当有地方引用这个对象的时候，+1，引用失效，-1

VM arguments:
-verbose:gc -xx:+PrintGCDetail
后台打印GC信息

System.gc();

可达性分析算法：
- 作为GCRoots的对象
    - 虚拟机栈
    - 方法区的类属性所引用的对象
    - 方法区中常量所引用的对象
    - 本地方法栈中所引用的对象

标记-清除算法：
- 效率问题
- 空间问题


堆：
- 新生代
    - Eden 
    - Survivor
    - Tenured Gen
- 老年代

复制算法：性能好，但空间容易浪费，主要针对Eden区域

标记-整理-清除-算法：针对老年代区域

分代收集算法：根据内存的分代，选择不同的算法

Serial收集器：
- 单线程的垃圾收集器

Parnew收集器：

Parallel Scavenge 收集器
- 复制算法（新生代收集器）
- 多线程收集器
- 达到可控制的吞吐量
-XX:MaxGCPauseMillis 垃圾收集器停顿时间
-XX:GCTimeRatio 吞吐量大小

吞吐量：CPU用于运行用户代码的时间 / CPU消耗的总时间
 吞吐量：CPU用于运行用户代码的时间 / （CPU用于运行用户代码的时间 + 垃圾回收占用的时间）

CMS收集器： concurrent mark sweep 并发 标记 清除
工作过程：
- 初始标记
-并发标记
- 重新标记
-并发清理

优点：
-并发收集
-低停顿

缺点：
-占用大量的CPU资源
-无法处理浮动垃圾
-出现 concurrent mode failure
-空间碎片






```