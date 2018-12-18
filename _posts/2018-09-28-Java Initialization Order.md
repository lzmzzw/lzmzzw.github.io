---

layout: post
title:  Java零基础（3）--Java初始化顺序
date:   2018-09-28 16:45:00 +0800
categories: Java
tag: Java基础

---

* content
{:toc}


---------------------------------------



## 初始化顺序
1. 继承体系的所有静态成员初始化（先父类，后子类）
2. 父类初始化完成（普通成员的初始化&rarr;构造函数的调用）
3. 子类初始化（普通成员&rarr;构造函数）

## 初始化机制
1. 首先初始化静态域是因为静态域是放在方法区和class对象在一起的。
2. 由于类加载的时候，会向上查找基类，因为子类的初始化依赖于基类首先初始化。所以会首先发生“基类&rarr;子类"顺序的类加载，类加载过程中，顺便完成了静态域的初始化。
3. 另外一条规则是初始化块和域的初始化按照声明的顺序进行。

## 代码实例

```java
class Parent {
        /* 静态变量 */
    public static String p_StaticField = "父类--静态变量";
        /* 变量 */
    public String p_Field = "父类--变量";
    protected int i = 1;
    protected int j = 2;
        /* 静态初始化块 */
    static {
        System.out.println( p_StaticField );
        System.out.println( "父类--静态初始化块" );
    }
        /* 初始化块 */
    {
        System.out.println( p_Field );
        System.out.println( "父类--初始化块" );
    }
        /* 构造器 */
    public Parent()
    {
        System.out.println( "父类--构造器" );
        System.out.println( "i=" + i + ", j=" + j );
        j = 3;
    }
}

public class SubClass extends Parent {
        /* 静态变量 */
    public static String s_StaticField = "子类--静态变量";
        /* 变量 */
    public String s_Field = "子类--变量";
        /* 静态初始化块 */
    static {
        System.out.println( s_StaticField );
        System.out.println( "子类--静态初始化块" );
    }
        /* 初始化块 */
    {
        System.out.println( s_Field );
        System.out.println( "子类--初始化块" );
    }
        /* 构造器 */
    public SubClass()
    {
        System.out.println( "子类--构造器" );
        System.out.println( "i=" + i + ", j=" + j );
    }


        /* 程序入口 */
    public static void main( String[] args )
    {
        System.out.println( "子类--main方法" );
        new SubClass();
    }
}
```

输出

```
父类--静态变量
父类--静态初始化块
子类--静态变量
子类--静态初始化块
子类--main方法
父类--变量
父类--初始化块
父类--构造器
i=1, j=2
子类--变量
子类--初始化块
子类--构造器
i=1,j=3
```





