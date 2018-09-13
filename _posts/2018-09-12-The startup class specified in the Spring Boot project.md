---

layout: post
title:  指定Spring Boot工程启动类
date:   2018-09-12 13:45:00 +0800
categories: Java
tag: [Spring Boot]

---

* content
{:toc}


---------------------------------------



在Spring Boot工程中如果有多个main()函数，需要指定启动类，作为启动的入口

示例如下，工程启动入口为com.demo包里面的Application类中的main方法，在pom.xml文件中配置：

```xml
<properties>  
    <!-- The main class to start by executing java -jar -->  
    <start-class>com.demo.Application</start-class>                 #包含main方法的类    
</properties>
```

或者

```xml
<build>  
    <plugins>  
        <plugin>  
            <groupId>org.springframework.boot</groupId>  
            <artifactId>spring-boot-maven-plugin</artifactId>  
            <configuration>	
                <mainClass>com.demo.Application</mainClass>         #包含main方法的类  
            </configuration>  
        </plugin>  
    </plugins>  
</build>
```




