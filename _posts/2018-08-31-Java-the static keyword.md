﻿---

layout: post
title:  Java零基础（1）--static关键字
date:   2018-08-31 10:00:00 +0800
categories: Java
tag: Java基础

---

* content
{:toc}


---------------------------------------


## static关键字

 - 当我们定义一个类时，只确定了那个类的对象的外观与行为，直到用`new`创建那个类的一个实例时，才生成了一个对象。对于非static数据和方法,只有执行了`new`创建一个对象后，才会正式生成数据存储空间，并用那个对象访问数据或方法。
    
 - 当使用了`static`（静态）关键字，数据或方法就不会同那个类的任何对象实例联系到一起。所以尽管从未创建那个类的一个对象，仍能调用一个`static`方法，或访问一些`static`数据。

 - `static`（静态）关键字满足两种特殊的情形的要求。一种情形是只想用一个存储区域来保存一个特定的数据——无论要创建多少个对象，甚至根本不创建对象（**静态变量**）。另一种情形是我们需要一个特殊的方法，它没有与这个类的任何对象关联。也就是说，即使没有创建对象，也需要一个能调用的方法**（静态方法**）。
    
### static变量

`static`变量也称作静态变量，静态变量和非静态变量的区别是：静态变量被**所有的对象所共享**，在**内存中只占一个区域**，它当且仅当在类初次加载时会被初始化。而非静态变量是对象所拥有的，在创建对象的时候被初始化，占有多个内存区域，各个对象占有的内存区域各不相同。静态变量是属于整个类的变量而不是属于某个对象的，**不能把任何方法体内的变量声明为静态**。

定义并初始化一个静态变量：

```java
class StaticTest {
    Static int i = 47;
}
```

创建两个`StaticTest`对象，它们只占据`StaticTest.i`的一个存储空间（共享同样的`i`）：

```java
StaticTest st1 = new StaticTest();
StaticTest st2 = new StaticTest();
```

此时，无论`st1.i`还是`st2.i`都有同样的值`47`，因为它们引用的是同样的内存区域。

引用`static`变量，有两种方法：
1. 将`static`变量的类实例化，使用实例化的对象引用，如`st2.i`；
2. 直接用`static`变量的类名引用，非静态成员里是不行的（最好用这个办法引用`static`变量，因为它强调了那个变量的“静态”本质），例如：

```java
StaticTest.i++;
```

此时，无论`st1.i`还是`st2.i`的值都是`48`。
    
### static方法

`static`方法一般称作静态方法，这是**一个不需要创建对象的方法**，由于静态方法**不依赖于任何对象**就可以进行访问，因此对于静态方法来说，是没有`this`的，因为它不依附于任何对象。由于这个特性，在静态方法中不能访问类的非静态成员变量和非静态成员方法，因为非静态成员方法/变量都是必须依赖具体的对象才能够被调用。
    

定义一个静态方法：

```java
class Incrementable {
    static void increment() { 
        StaticTest.i++; 
    }
}
```

与`static`变量相同，引用`static`方法，有两种方法：
1. 通过`Incrementable`类实例化一个对象`sf`，可用典型的方法调用：

```java
Incrementable sf = new Incrementable();
sf.increment();
```

2. 由于`increment()`是一种静态方法，可以采用`类名.方法()`的方法，通过它的类直接调用：

```java
Incrementable.increment();
```

对方法来说，`static`一项重要的用途就是帮助我们在不必创建对象的前提下调用那个方法,如`main`方法。在使用静态方法的时候需要注意：
1. 在静态方法里只能直接调用同类中其他的静态成员（包括变量和方法），而不能直接访问类中的非静态成员。这是因为，对于非静态的方法和变量，需要先创建类的实例对象后才可使用，而静态方法在使用前不用创建任何对象。
2. 静态方法不能以任何方式引用`this`和`super`关键字，因为静态方法在使用前不用创建任何实例对象，当静态方法调用时，`this`所引用的对象根本没有产生。




