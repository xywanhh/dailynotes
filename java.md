√  （对）
---
- 操作系统
- 数据库
- 中间件
- 编程语言
- 软件产品

James Gosling

- 编译型语言
- 解释型语言

java是两种的结合体：
- javac.exe  编译命令
- java.exe    解释命令

Java程序组成：源文件、字节码文件、机器码指令

字节码和平台无关，各个平台有自己的Java Virtual Machine（在一台计算机上由软件或者硬件模拟的计算机）

```
>java Hello.java
>javac Hello
>hello leaf
```

一个java文件只能有一个public class定义，可以有多个class定义，编译后生成多个.class文件

默认情况下，javac都是从当前目录找class，可以通过CLASSPATH改变路径
- set CLASSPATH = E:\demo
- javac Hello
---
设置当前路径是class路径
- set CLASSPATH = .
- javac Hello

---
- path：操作系统属性定义，定义所有exe程序的路径
- classpath：class文件加载路径定义
---
数字、字母、_、$

```
A-Z 65-90  a-z 97-122
字符char可以和int互相转换
>char a = 'a';
>int b = a;
>char c = a - 32;
```
String是一个特殊的类，不是数据类型

数据类型转换都是从小到大，从大到小要用强制转换

```
++ a  先+1，然后在使用a
a ++  先使用a，然后在+1

左移和幂方运算等价
>2 <<2
>2 ^ 3
```
"&" "|" 可以在位运算中使用，"&&" "||" 不能用于位运算中

```
{} 代码块，用的不多
类中的代码块优先于构造方法执行
方法中的代码块用于分割，可以变量重名
静态代码块只会加载一次，优先于所有的代码块加载，一般不用，用于测试代码
```

```
if表达式用布尔表达式控制流程
switch表达式不能用布尔，1.5可以用枚举，1.7可以用String
switch (数字 | 字符 | 枚举 | String) {
    case 内容 : {
        // to-do
        [break;]
    }
    case 内容 ：{
        // to-do
        [break;]
    }
    default : {
        // to-do
    }
}
```

```
循环控制语句：continue、break
while (布尔) {
    //to-do
    //循环结束控制语句
}
do {
    //to-do
    //循环结束控制语句
} while (布尔)
for (int x=1;x<=9;x++) {
    for (int y=1;y<=x;y++) {
        System.out.println(x + "*" + y + "=" (x*y) + "\t");
    }
}
```

面向对象是一种组件化的编程思想，有3大特征：继承、封装、多态

堆内存：保存属性内容，需要用new关键字来开辟
栈内存：保存一块堆内存的地址

编译期异常：NullPointerException,

```java
            同类、同包、子类、不同包
public      √     √     √     √
protected   √     √     √ 
default     √     √
private     √
```

方法的重载：只看参数的个数和类型
方法的重写：override

```
数组：堆内存中一块连续的内存空间
>int[] array = new int[10];
>int[] array = {1,2,3};
>int[] array = new int[]{1,2,3};
```

```java
排序：
0-1 1-2 2-3...
for (int x=0;y<array.lenght;x++) {
    for (int y=0;y<array.lenght;y++) {
    if (array[y]>array[y+1]) {
        int t = array[y];
        array[y] = array[y+1];
        array[y+1] = t;
    }
    }
}
```

```java
数组的转置：
int[] array = new int[] {1,2,3,5};
int foot = array.length - 1;
int[] result = new int[foot];
for (int x=0;y<array.lenght;x++) {
    result[x] = array[foot];
    foot --; 
}
return result;
改变原数组的转置：
reverse(int[] array){
    int len = array.length / 2;
    int head = 0;
    int tail = array.length - 1;
    for (int x=0;x<len;x++) {
        int temp = array[head];
        array[head] = array[tail];
        array[tail] = temp;
        head ++;
        tail --;
    }
    return array;
}
```

二维数组，行列式

数组的clone:
```java
System.arraycopy(原数组名称, 原数组拷贝开始索引, 目标数组名称, 目标数组拷贝开始索引, 拷贝长度);

数组的排序：
Arrays.sort(数组);
Arrays.copyOf()

public static <T,U> T[] copyOf(U[] original, int newLength, Class<? extends T[]> newType) {
        @SuppressWarnings("unchecked")
        T[] copy = ((Object)newType == (Object)Object[].class)
            ? (T[]) new Object[newLength]
            : (T[]) Array.newInstance(newType.getComponentType(), newLength);
        System.arraycopy(original, 0, copy, 0,
                         Math.min(original.length, newLength));
        return copy;
}
```

```
>String s = "hello";
>String s = new String("hello");
public String(String original)
初始化一个新创建的 String 对象，使其表示一个与参数相同的字符序列；换句话说，新创建的字符串是该参数字符串的副本。由于 String 是不可变的，所以无需使用此构造方法，除非需要 original 的显式副本。

字符串常量会存在与对象池中，new String操作会在堆中开辟2个内存空间，其中一个不在对象池中，需要执行new String("a").intern()来入池。

String内容不可变
```

public boolean equals(Object anObject)
将此字符串与指定的对象比较。当且仅当该参数不为 null，并且是与此对象表示相同字符序列的 String 对象时，结果才为 true。

== 数值相等运算符，用在引用数据类型时，判断内存地址

Always override hashcode when you override equals
Always override toString

```java
private final char value[];
public boolean equals(Object anObject) {
        if (this == anObject) {
            return true;
        }
        if (anObject instanceof String) {
            String anotherString = (String)anObject;
            int n = value.length;
            if (n == anotherString.value.length) {
                char v1[] = value;
                char v2[] = anotherString.value;
                int i = 0;
                while (n-- != 0) {
                    if (v1[i] != v2[i])
                        return false;
                    i++;
                }
                return true;
            }
        }
        return false;
}
```
```java
字符串常量相当于String匿名对象
字符串常量写在左边，可以避免NullPointerException
>"hello".equals(obj)
>obj.equals("hello")

将字符串转为字符数组
>String s = "hello";
>char[] charArray = s.toCharArray();
>char a = s.charAt(int index);

将字符串转为字节数组，用于转码，IO操作
>String s = "hello";
>byte[] byteArray = s.getBytes();

比较数值
equals
equalsIgnoreCase

比较字符串大小，只有String类的对象有大小的比较
compareTo

contains
indexOf
startsWith
endsWith
replace
substring
split
trim
toUpperCase
toLowerCase

public boolean isEmpty() {
    return value.length == 0;
}

调用无参构造方法，只能写在构造方法体首行
this()  
this(name)
```


```
static保存的数据在内存的全局数据区
内存：栈内存，堆内存，全局数据区，全局代码区

```

```
内部类好处在于内部类可以直接访问外部类的私有属性
外部类.内部类 a = new 外部类().new 内部类();

static内部类相当于一个外部类，只能访问外部类的static方法和变量
外部类.内部类 a = new 外部类().内部类();

方法中的内部类如果要使用方法的参数，在jdk1.8之后的版本可以直接使用，在这之前变量要用 final 修饰才能使用
```














