---
layout: post
title: CSS Animation
category: CSS
tags: [css]
---

## 简介

单例模式是常用的设计模式，其定义为确保一个类只有一个实例，并提供该实例的全局访问点。

一个类确保只有一个实例说明该类的实例只能在类内部创建，类外部不能通过new的方式创建该实例，这点可以将构造方法访问权限设置为private的来完成。


```
private static Singleton instance;

private Singleton(){}
```

那么外部如何获取该实例呢？

只需要一个公有的获取该实例静态方法即可，像这样

```
public static Singleton getInstance() {
    return instance;
}
```

## 代码实现

一般包含三个要素：  
- 私有的静态变量 
- 私有的构造函数，保证外部不能通过new的方式创建对象
- 公有的获取该实例的静态方法，对外提供访问该对象的访问方法

### 懒汉式单例模式（线程不安全-延迟加载）

懒汉式就是应用刚启动的时候不创建实例，当外部调用获取该类的实例方法时才创建。  
实例被延迟加载，这样做的好处是，如果没有用到该类，那么静态变量instance就不会被实例化，从而节省资源。  
懒汉式单例模式是线程不安全的，在多线程环境下instance可能会被多次实例化。

``` java
/**
 * Singleton 懒汉式单例模式（线程不安全-延迟加载）
 */
public class Singleton {
    private static Singleton instance;
    private Singleton(){}
    public static Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}
```

### 懒汉式单例模式（线程安全-延迟加载）

对getInstance()方法加锁之后，同一时间只有一个线程访问该方法，这样就避免了instance被多次实例化。
getInstance()方法由于加了synchronized关键字，当有一个线程获得锁并访问该方法时，其他线程处于阻塞状态，一定程度上对性能有所损耗。

``` java
/**
 * Singleton 懒汉式单例模式（线程安全-延迟加载）
 */
public class Singleton {
    private static Singleton instance;
    private Singleton(){}
    public static synchronized Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}
```

### 饿汉式单例模式（线程安全）

饿汉式就是应用刚启动的时候，不管外部有没有调用该类的实例方法，该类的实例就已经创建好了。

这是我最喜欢的一种单例模式写法，简单、高效，也没有线程安全问题。

``` java
/** 
 * Singleton 饿汉式单例模式（线程安全）
 */
public class Singleton {
    private static Singleton instance = new Singleton();
    private Singleton(){}
    public static Singleton getInstance() {
        return instance;
    }
}
```

### 双重校验锁单例模式（线程安全-延迟加载）

``` java
/**
 * Singleton 双重校验锁单例模式（线程安全-延迟加载）
 *
 */
public class Singleton {
    private static volatile Singleton instance;
    private Singleton(){}
    public static Singleton getInstance() {
        if (instance == null) {
            synchronized (Singleton.class) {
                if (instance == null) {
                    instance = new Singleton();
                }
            }
        }
        return instance;
    }
}

```
在进入synchronized块之前加入判空逻辑，只有instance在没有被实例化之前才进入同步块，instance实例化之后就不会在进入同步块里了，效率当然也会提高。

是否有必要加volatile关键字？

我们都知道instance = new Singleton()这段代码是分三步运行的  
1、分配内存空间  
2、实例化对象  
3、将instance指向分配的内存地址

由于 JVM 具有指令重排的特性，有可能执行顺序变为了 1>3>2，这在单线程情况下自然是没有问题。但如果是多线程下，有可能获得是一个还没有被初始化的实例，以致于程序运行出错。

使用 volatile 可以禁止指令重排，保证在多线程环境下也能正常运行。所以还是有必要加上volatile关键字的。

### 静态内部类实现(线程安全-延迟加载)

``` java
/**
 * Singleton 静态内部单例模式(线程安全-延迟加载)
 */
public class Singleton {
    private static class SingletonHolder{
        private static Singleton instance = new Singleton();
    }
    private Singleton(){}
    public static Singleton getInstance() {
        return SingletonHolder.instance;
    }
}
```
由于静态内部类的特性，只有在其被第一次引用的时候才会被加载，所以可以保证其线程安全性。

由于在调用 SingletonHolder.instance 的时候，才会对单例进行初始化，而且通过反射是不能从外部类获取内部类的属性的。
所以这种形式，很好的避免了反射入侵。

### 基于枚举实现的单例模式

``` java
/**
 * 枚举实现的单例模式(线程安全)
 */
public enum  Singleton {
    INSTANCE;
}
```

这是 Effective Java 极力推荐的一种，代码为各种实现中最简单的,其实现，完全是基于枚举类的特性，可以说天生受到了 JVM 的支持，而且既不用思考反射，也不用考虑多线程。
