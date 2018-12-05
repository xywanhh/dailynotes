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
```
各大公司在线笔试题库
http://www.acmcoder.com/index
https://www.nowcoder.com
Google Code Jam 系统
https://code.google.com/codejam/kickstart
```

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


```sql
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

```java
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

```
编码技巧
- 递归控制
- 循环控制
- 边界控制
- 数据结构
- 树的遍历

数学归纳法
用于证明断言对所有自然数成立
数学归纳法是编码的依据

递归写法：
- 严格定义递归函数作用，包括参数，返回值
- 先一般，后特殊
- 每次调用必须缩小问题规模
- 每次缩小程度必须为1

```

```java
利用递归，实现一个链表linkedlist，返回链表的head节点(数学归纳法的思想)
public class Node {
    private final int value; // final,value can not change
    private Node next;
    
    public Node(int value){
        this.value = value;
        this.next = null; // construc a pure node
    }
    
    public int getValue(){
        return value;
    }
    public void setNext(Node next){
        this.next = next;
    }
    public Node getNext(){
        return next;
    }

    public static void printNodeList(Node head){ // send head,print list
        while (head != null) {
            System.out.print(head.value);
            System.out.print("-->");
            head = head.getNext();
        }
        System.out.println("=====");
    }
}

public class Main {

    public Node createLinkedList(List<Integer> data) {
        if (data.isEmpty()) {
            return null; // recursive end cause
        }
        Node firstNode = new Node(data.get(0));
        //Node firstNodeSubList = createLinkedList(data.subList(1, data.size())); // if subList's fromIndex == endIndex ,return null
        firstNode.setNext(
            createLinkedList(data.subList(1, data.size())) // avoid create a local object
        );
        return firstNode;
    }

    public static void main(String[] args){
        Main main = new Main();
        Node.printNodeList(main.createLinkedList(new ArrayList<>()));
        Node.printNodeList(main.createLinkedList(Arrays.asList()));
        Node.printNodeList(main.createLinkedList(Arrays.asList(1, 2, 3)));
    }
}
```

```java
利用数学归纳法的思想，来反转一个list
public Node reverseLinkedList(Node node){
    if (node == null || node.getNext() == null) {
        return node;
    }
    Node newNode = reverseLinkedList(node.getNext());
    node.getNext().setNext(node);
    node.setNext(null);
    return newNode;
}
测试代码：
Main main = new Main();
Node.printNodeList(main.reverseLinkedList(main.createLinkedList(new ArrayList<>())));
Node.printNodeList(main.reverseLinkedList(main.createLinkedList(Arrays.asList())));
Node.printNodeList(main.reverseLinkedList(main.createLinkedList(Arrays.asList(1, 2, 3))));
```

```java
数学归纳法完成递归
side-effect 控制边界值 ---List<Integer> selected
data  -->待处理数组
n --> 组合位数
public void combinations(List<Integer> selected, List<Integer> data, int n){

    if (n == 0) {
        // output all selected elements
        for (Integer element : selected) {
            System.out.print(element);
            System.out.print(" ");
        }
        system.out.println();
    }

    if (data.isEmpty()) {
        return;
    }

    //是否选取首位
    // select element 0 
    selected.add(data.get(0));
    combination(selected, data.subList(1, data.size()-1), n-1);
    // un-select element 0
    selected.remove(selected.size() -1);
    combination(selected, data.subList(1, data.size()-1), n);
}
测试：
Main main = new Main();
main.combinations(new ArrayList<>(), Arrays.asList(1, 2, 3, 4), 2);
main.combinations(new ArrayList<>(), Arrays.asList(), 2);
main.combinations(new ArrayList<>(), Arrays.asList(), 0);
main.combinations(new ArrayList<>(), Arrays.asList(1, 2, 3), 1);
main.combinations(new ArrayList<>(), Arrays.asList(1, 2, 3, 4), 0);
main.combinations(new ArrayList<>(), Arrays.asList(1, 2, 3, 4, 5, 6), 4);

```

```
递归会带来一个问题：
在递归层级高的时候，每一个层级的数据会维护在同一个栈中，层级高了，容易stack overflow
考虑用循环来解决，但是还是要设置这么大的栈，只是栈里的数据会少点，去掉不需要入栈的数据
```

```
REST描述的是在网络中client和server的一种交互形式；REST本身不实用，实用的是如何设计 RESTful API（REST风格的网络接口）
看Url就知道要什么
看http method就知道干什么
看http status code就知道结果如何

RPC
https://www.jianshu.com/p/5b90a4e70783
```

```java
利用循环来反转一个链表
loop invariant 循环不变式

public Node reverseLinkedList(Node head){
    Node newHead = null; // 初始循环定义
    Node curHead = head;

    //loop invariant
    //newHead points to the linked list already reversed.
    //curHead points to the linked list not yet reversed.
    while (curHead != null) {
        // loop invariant
        Node next = curHead.getNext();
        curHead.setNext(newHead);
        newHead = curHead;
        curHead = next;
        // loop invariant
    }
    return newHead;
}
测试代码：
Main main = new Main();
Node.printNodeList(main.reverseLinkedList(main.createLinkedList(new ArrayList<>())));
Node.printNodeList(main.reverseLinkedList(main.createLinkedList(Arrays.asList())));
Node.printNodeList(main.reverseLinkedList(main.createLinkedList(Arrays.asList(1, 2, 3))));
```

```java
利用循环创建一个很大的链表，如果用之前递归的方法来创建，太大会报错，java.lang.StackOverflowError
public Node createLargeLinkedList(int n){
    Node prev = null;
    Node head = null;
    for (int i=1;i<=n;i++) {
        Node node = new Node(i);
        if (prev != null) {
            prev.setNext(node);
        } else {
            head = node;
        }
        prev = node;
    }
    return head;
}
```

```java
delete-if一个链表
public Node deleteIfEquals(Node head, int value){
    while (head != null && head.getValue() == value) {
        head = head.getNext();
    }

    if (head == null) {
        return null;
    }

    Node prev = head;
    // loop invariant : list nodes from head up to prev has been 
    // proecessed.(Nodes with values equal to value were deleted)
    while (prev.getNext != null) {
        if (prev.getNext.getValue() == value) {
            // delete it.
            prev.setNext(prev.getNext().getNext());
        } else {
            prev = prev.getNext();
        }
    }
    return prev;
}

```

```java
二分查找 binarySearch
要点在于边界值的控制
public int binarySearch(int[] arr, int k){
    int a = 0;
    int b = arr.length;

    // loop invariant : [a, b) is a valid range.(a<=b)
    // while k may only be within range [a, b)
    //使用[a, b)有好处：[a, b)+[b, c)=[a, c); [a, a) == empty; b-a = length([a, b))
    while (a < b) {
        // a = b : m = a = b 被 a<b过滤
        // b=a+1 : m = a
        // b=a+2 : m = a + 1
        int m = (a+b)/2;
        if (k < arr[m]) {
            b = m;
        } else if (k > arr[m]) {
            a = m+1;
        } else {
            return m;
        }
    }
    return -1;
}
```

```
数据结构与算法
树的遍历
算法复杂度分析
- 时间复杂度
- 空间复杂度

列表：
- 数组
- 链表
- 队列，栈

树：
- 二叉树
- 搜索树
- 堆/优先队列

Map<K, V>/Set<K>
- HashMap/HashSet --> K.hashCode()
- TreeMap/TreeSet --> k implements Comparable

图
- 无向图
- 有向图
- 有向无环图

图的算法
- 深度优先遍历
- 广度优先遍历
- 拓扑排序
- 最短路径、最小生成树

二叉树的遍历
- 前序遍历  ： 先遍历树根，然后前序遍历左子树，然后前序遍历右子树
- 中序遍历
- 后序遍历
- 层次遍历

```

```java
public class TreeNode {
    private final char value;
    private TreeNode leftNode;
    private TreeNode rightNode;

    public TreeNode(char value){
        this.value = value;
        this.leftNode = null;
        this.rightNode = null;
    }
    public char getValue(){
        return value;
    }
    public TreeNode getLeftNode(){
        return leftNode;
    }
    public TreeNode getRightNode(){
        return rightNode;
    }
    public void setLeftNode(TreeNode leftNode){
        this.leftNode = leftNode;
    }
    public void setRightNode(TreeNode rightNode){
        this.rightNode = rightNode;
    }
}

public class TreeMaker{
    public TreeNode createTree(){
        TreeNode rootA = new TreeNode('A');
        TreeNode rootB = new TreeNode('B');
        TreeNode rootC = new TreeNode('C');
        TreeNode rootD = new TreeNode('D');
        TreeNode rootE = new TreeNode('E');
        TreeNode rootF = new TreeNode('F');
        TreeNode rootG = new TreeNode('G');
        
        rootA.setLeftNode(rootB);
        rootA.setRightNode(rootC);

        rootB.setLeftNode(rootD);
        rootB.setRightNode(rootE);

        rootE.setLeftNode(rootG);
        rootC.setRightNode(rootF);

        return rootA;
    }
}

public void preOrder(TreeNode root){
    if (root == null) {
        return;
    }
    System.out.print(root.getValue);
    preOrder(root.getLeftNode());
    preOrder(root.getRightNode());
}
public void inOrder(TreeNode root){
    if (root == null) {
        return;
    }
    inOrder(root.getLeftNode());
    System.out.print(root.getValue());
    inOrder(root.getRightNode());
}
public void postOrder(TreeNode root){
    if (root == null) {
        return;
    }
    postOrder(root.getLeftNode());
    postOrder(root.getRightNode());
    System.out.print(root.getValue());
}
```

```java
由前序和中序来输出后序，这种情况是可以唯一确定一棵树的。
如果缺少中序，比如之后前序和后序，那么结果就不唯一了。
public TreeNode createTree(String preOrder, String inOrder){
    if (preOrder.isEmpty()) {
        return null;
    }
    char rootValue = preOrder.charAt(0);
    int rootIndex = inOrder.indexOf(rootValue);
    TreeNode root = new TreeNode(rootValue);
    root.setLeftNode(
        createTree(preOrder.substring(1,1+rootIndex), inOrder.substring(0,rootIndex));
    );
    root.setRightNode(
        createTree(preOrder.substring(1+rootIndex),inOrder.substring(1+rootIndex));
    );
    return root;
}
可以省去root创建节点的动作
public String createTree(String preOrder, String inOrder){
    if (preOrder.isEmpty()) {
        return "";
    }
    char rootValue = preOrder.charAt(0);
    int rootIndex = inOrder.indexOf(rootValue);
    return 
        createTree(preOrder.substring(1,1+rootIndex), inOrder.substring(0,rootIndex)) 
        + createTree(preOrder.substring(1+rootIndex),inOrder.substring(1+rootIndex))
        + rootValue;
}
```

```java
如果给定了中序遍历序列，随意找一个节点的下一个节点，这个问题复杂，面试难度大
面试可能会问：二叉查找树的遍历顺序
搜索树：节点的右子树值小，左子树值大
TreeMap/TreeSet 内部实现都是以搜索树为基础
在此基础上，有平衡搜索树，实现了层次数的平衡
```

```
算法复杂度，在数量级上谈，最坏情况
O(N!)  O(2^N)  O(N^2) O(NlogN)  O(N) O(logN) ...

O(N^2)  --插入排序  选择排序
O(NlogN) --归并排序 快速排序（平均）

O(logN)  二分查找


```

这是分卷压缩，需要完整下载所有压缩包文件，然后解压.001文件即可。不懂的自行百度“分卷 解压”。
度盘：传送门    提取：c78x    解压：YBBer
[提取：c78x 解压：YBBer][云宝宝er]49套合集(5.8G)

百度网盘：传送门    提取码：3h68  解压码：Little_tori
onedrive:  传送门

