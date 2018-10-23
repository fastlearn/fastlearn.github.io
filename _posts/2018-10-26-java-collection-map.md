---
layout: post
title: Java 基础知识回顾 - 集合框架概述
category: [Java]
tags: [Java]
---

Java 集合是 Java 提供的工具包，包含了常用的数据结构：集合、链表、队列、栈、数组、映射等。Java 集合在 `java.util.*` 包下，主要可以划分为 5 个部分：List 列表、Set 集合、Map 映射、迭代器（Iterator 和 Enumeration)、工具类(Arrays 和 Collections)。

Java 集合主要包含两大类 Collection 和 Map。

## Collection

Collection 是高度抽象出来的接口，包含了集合的基本属性和方法，主要有两个分支：List 和 Set。

### List

List 接口表示一个列表(数组，队列，链表，栈)，List 元素有序、可重复。常用实现类有
- [ArrayList]()
- [LinkedList]()
- [Vector]()
- [CopyOnWriteArrayList]()

### Set 

Set 接口表示一个集合，Set 元素无序、不可重复。常用实现类有
- [HashSet]()
- [LinkedHashSet]()
- [TreeSet]()
- [TreeSet]()
- [CopyOnWriteArraySet]()
- [ConcurrentSkipListSet]()

## Map

Map 是键值对映射接口，一个元素就是一个键值对，一个键对应一个值。

### AbstractMap

抽象类 AbstractMap 通过适配器模式实现了 Map 接口中的大部分函数，HashMap、LinkedHashMap、TreeMap、WeakHashMap 等实现类都通过继承 AbstractMap 来实现，另外，不常用、同步安全的 HashTable 直接实现了 Map 接口，它和 Vector 都是 JDK1.0 就引入的集合类。



