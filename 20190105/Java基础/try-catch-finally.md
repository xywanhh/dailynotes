### 1.测试
```java
int test1() {
    int a = 1;
    try {
        return a;
    } catch (Exception e) {
        e.printStackTrace();
    } finally {
        a = 2;
    }
    return a;
}
// 返回 a = 1;
```

```java
int test2() {
    int a = 1;
    try {
        return a;
    } catch (Exception e) {
        e.printStackTrace();
    } finally {
        a = 2;
        return a;
    }
}
// 返回 a = 2;
```

```java
int test3() {
    User u = new User("a")
    try {
        return u;
    } catch (Exception e) {
        e.printStackTrace();
    } finally {
        u = new User("b");
    }
    return null;
}
// 返回 u"a";
```

```java
int test4() {
    User u = new User("a")
    try {
        return u;
    } catch (Exception e) {
        e.printStackTrace();
    } finally {
        u.set("b");
    }
    return null;
}
// 返回 u"b";
```
- 1、不管try,finally都会执行；
- 2、在try中return，在finally执行前会把结果保存起来，即使在finally中有修改也以try中保存的值为准，但如果是引用类型，修改的属性会以finally修改后的为准；
- 3、如果try/finally都有return，直接返回finally中的return。
