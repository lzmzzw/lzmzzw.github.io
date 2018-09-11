---

layout: post
title:  Java零基础（2）--this关键字
date:   2018-09-03 17:15:00 +0800
categories: Java基础
tag: this keyword

---

* content
{:toc}


---------------------------------------


## this关键字
### this关键字说明
1. `this`关键字只能在方法内部使用，表示调用该方法的那个对象。
2. 在方法内部调用同一个类的其他方法，无需使用`this`，直接调用即可。
3. 通过`this`调用其他构造器必须放在构造器的第一行中执行。
4. 由于`super`调用父类的构造器也必须放在构造器的第一行中执行，因此，通过`this`和`super`调用构造方法不能同时出现一个构造方法中。
5. 不能在一个构造器中多次调用不同的构造器。

## this关键字用法
### 1 区分形参和成员变量

```java
public class Apple{
    public String color;
    public void setColor(String color) {
        this.color = color;                 //调用成员变量Apple.color
    }
}
```

### 2 调用其它构造器

```java
public class Apple{
    public String color;
    public Apple(){        
        this("red");                        //调用Apple构造器
    }
}
```

### 3 返回对象的值

```java
public class Apple{
    public Apple func() {
        return this;                        //返回Apple类的引用
    }
}
```

### 4 作为参数传递

```java
class Peeler {
    static Apple peel(Apple apple) {
        return apple;
    }
}

class Apple {
    Apple getPeeled() {
        return Peeler.peel(this);           //将apple类作为参数传递
    }
}
```


