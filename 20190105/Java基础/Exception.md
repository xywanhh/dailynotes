### 1.异常继承体系
![exception-tree](.\image\exception-tree.png)

#### 1.1 说明
- 红色异常类是程序需要显示捕捉或者抛出的

#### 1.2 Throwable
- Throwable接口是异常的顶级类，所有的异常都继承于这个类。
- Error，Exception是异常类的两个大分类。

##### 1.2.1 Error
- 非程序异常，即程序不能捕获的异常，一般是编译或者系统性的错误，如OutOfMemorry内存溢出异常等。

##### 1.2.2 Exception
- 程序异常类，由程序内部产生。
- Exception又分为运行时异常、非运行时异常。

###### 1.2.2.1 运行时异常
> ***特点是Java编译器不会检查它***，也就是说，当程序中可能出现这类异常，即使没有用try-catch语句捕获它，也没有用throws子句声明抛出它，也会编译通过，运行时异常可处理或者不处理。运行时异常一般常出来定义系统的自定义异常，业务根据自定义异常做出不同的处理。

> 常见的运行时异常如NullPointException、ArrayIndexOutOfBoundsException等。

###### 1.2.2.2 非运行时异常
> ***是程序必须进行处理的异常***，捕获或者抛出，如果不处理程序就不能编译通过。

> 如常见的IOException、ClassNotFoundException等。