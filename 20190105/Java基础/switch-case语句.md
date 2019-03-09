### 1.语法
```java
switch(expression) {
    case v1:
        // to-do
        break;
    case v2:
        // to-do
        break;
    default:
        // to-do
}
```
#### 1.1 expression类型
- 基本数据类型：byte\short\int\char
- 包装类型: Integer\Long\Short\Character
- 枚举类型：Enum
- String类型（JDK 7+后支持）

#### 1.2注意
- case语句里必须跟break
- case条件只能是常量或字面常量
- default最多只能有一个

