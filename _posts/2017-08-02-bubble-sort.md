---
layout: post
title: 数据结构与算法 - 排序算法之冒泡排序
category: 数据结构与算法
tags: [数据结构与算法]
---

冒泡排序（Bubble Sort）是一种简单的基于比较替换的排序算法

冒泡排序重复走访要排序的元素集合，依次比较相邻的两个元素，如果他们的顺序错误就把他们交换过来，直到没有相邻元素需要交换，排序完成。

冒泡排序算法的名字由来是因为越大的元素会经由交换慢慢“浮”到数列的顶端（升序或降序排列），就如同碳酸饮料中二氧化碳的气泡最终会上浮到顶端一样，故名“冒泡排序”。

## Java 代码实现

冒泡排序经典实现

```java
public void bubbleSort(int[] a) {
    int tmp,length = a.length;
    for (int i = 0; i < length - 1; i++) { // 第一层循环,比较次数
        for (int j = 0; j < length - i - 1; j++) { // 比较交换元素位置
            if (a[j] > a[j + 1]) {
                tmp = a[j + 1];
                a[j + 1] = a[j];
                a[j] = tmp;
            }
        }
    }
}
```

## 冒泡排序优化

如果要排序的的数组有一部分数据是有序的，冒泡排序还会继续循环比较。比如下面一个数组
```java
int[] a = {5,4,9,3,2,1};
```
当元素4排好序后，3、2、1其实已经有序了不需要继续循环比较了，但是冒泡排序还会继续循环比较，完全是浪费时间，有没有办法让他不再继续循环比较了呢？当然有只需要一个变量 flag，当有数据交换的时候设置为true，有数据交换的时候直接 break 结束循环。

```java
/*
 * 优化冒泡排序
 */
public void bubbleSort(int[] a) {
    int tmp,length = a.length;
    for (int i = 0; i < length - 1; i++) { //第一层循环,比较次数
        boolean flag = false; // 提前退出冒泡循环的标志位
        for (int j = 0; j < length - i - 1; j++) { //比较交换元素位置
            if (a[j] > a[j + 1]) {
                tmp = a[j];
                a[j] = a[j + 1];
                a[j + 1] = tmp;
                flag = true; // true 表示有数据交换
            }
        }
        if (!flag) break;// 没有数据交换，提前退出
    }
}
```

## 算法分析

### 时间复杂度

最好情况时间复杂度是 O(n)。

最坏情况时间复杂度为 O(n2)。

平均情况时间复杂度就是 O(n2)。

空间复杂度 O(1)


### 算法稳定性

冒泡排序就是把小的元素往前调或者把大的元素往后调。比较是相邻的两个元素比较，交换也发生在这两个元素之间。所以，如果两个元素相等，是不会再交换的；如果两个相等的元素没有相邻，那么即使通过前面的两两交换把两个相邻起来，这时候也不会交换，相同元素的前后顺序并没有改变，所以冒泡排序是一种**稳定排序算法**。

