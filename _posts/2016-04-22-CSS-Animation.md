---
layout: post
title: Spring Boot 快速入门示例
category: [Spring Boot]
tags: [Spring Boot]
---

越来越多的公司选择使用 Spring Boot 来开发系统，它到底有什么优点？为什么越来越受欢迎？

Spring Boot 是由 Pivotal 团队提供的全新框架，其设计目的是用来简化新 Spring 应用的初始搭建以及开发过程。该框架使用了特定的方式来进行配置，从而使开发人员不再需要定义样板化的配置。使用 Spring Boot，可以轻松的创建独立运行的程序，构建独立的服务组件，是实现分布式架构、微服务架构利器。Spring Boot 简化了第三方包的引用，通过提供的`starter`，简化了依赖包的配置。

## 快速入门

Spring Boot 项目依赖 Maven 3.2+ ，如果你还没有安装 Maven，可以按照[Maven 官方文档](https://maven.apache.org)进行安装配置。

Spring Boot 依赖项使用`org.springframework.boot` groupId。通常，POM文件将继承`spring-boot-starter-parent`项目并声明对一个或多个`starters`的依赖关系。 Spring Boot还提供了一个可选的Maven插件来创建可执行jar。    

下面是一个典型的 Spring Boot 项目 POM 文件

``` xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>demo</artifactId>
    <version>0.0.1-SNAPSHOT</version>

    <!-- Inherit defaults from Spring Boot -->
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>1.5.16.RELEASE</version>
    </parent>

    <!-- Add typical dependencies for a web application -->
    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
    </dependencies>

    <!-- Package as an executable jar -->
    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
        </plugins>
    </build>

</project>
```

使用 idea 或者 eclipse 创建一个 Maven 项目，将上边内容复制到 POM 文件中，保存，等待 jar 包下载完毕，一个 Spring Boot 项目就搭建成功了。

那么它如何运行呢？很简单，只需要创建一个启动类就 OK 了，像这样

``` Java
package com.example.demo;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class DemoApplication {

    public static void main(String[] args) {
        SpringApplication.run(ApiGatewayApplication.class, args);
    }
}
```

运行该主方法，控制台就会打印日志，当看到以下内容说明启动成功了。

``` java
Tomcat started on port(s): 8080 (http) with context path ''
```

## Hello World

让我们写一个 Hello Spring Boot 的 Controller 吧

``` Java
package com.example.demo;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@@RestController
public class DemoController {

   @GetMapping("/")
   public String helloSpringBoot() {
       return "Hello Spring Boot";
   }
   
}
```

重新启动 Spring Boot ，浏览器访问<http://localhost:8080/>

![Spring Boot](/images/spring-boot/spring-boot-hello-world.jpg)
