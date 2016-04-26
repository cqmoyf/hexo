title: A+B+C问题-Python-计蒜客
date: 2015-12-24 15:09:12
tags: [计蒜客,Python]
categories: 计蒜客
---
# 题目
这是一个非常简单的题目，意在考察你编程的基础能力。千万别想难了哦。输入为一行，包括了用空格分隔的三个整数A、B、C（数据范围均在-40~40之间）。输出为一行，为“A+B+C”的计算结果。
**样例1**
输入：
22 1 3
输出：
26
<!--more-->
# 答案
```
# coding=utf-8
list1=raw_input("").split(" ")
list2=[]
for i in list1:
    if -40<=int(i)<=40:
        a=int(i)
        list2.append(a)
print sum(list2)
```