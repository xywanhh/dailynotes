### 1. 字符串拼接+和concat的区别
> +和concat都可以用来拼接字符串

```java
String s1 = "s1";
System.out.println(s1 + 2); // s12
System.out.println(2 + s1); // 2s1

String s2 = "s2";
s2 = s2.concat("a").concat("c");
System.out.println(s2); // s2ac

String s3 = "s3";
System.out.println(s3 + null); // s3null
System.out.println(null + s3); // nulls3

String s4 = null;
System.out.println(s4.concat("a")); // NullPointerException
System.out.println("a".concat(s4)); // NullPointerException
```

```java
public String concat(String str) {
    int otherLen = str.length();
    if (otherLen == 0) {
        return this;
    }
    int len = value.length;
    char buf[] = Arrays.copyOf(value, len + otherLen);
    str.getChars(buf, len);
    return new String(buf, true);
}
```

- +可以是字符串或者数字及其他基本类型数据，而concat只能接收字符串。
- +左右可以为null，concat为会空指针。
- 如果拼接空字符串，concat会稍快，在速度上两者可以忽略不计，如果拼接更多字符串建议用StringBuilder。
- 从字节码来看+号编译后就是使用了StringBuiler来拼接，所以一行+++的语句就会创建一个StringBuilder，多条+++语句就会创建多个，所以为什么建议用StringBuilder的原因。
