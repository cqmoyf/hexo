title: 简单斐波那契-Python-计蒜客
date: 2015-12-24 15:35:08
tags: [计蒜客,Python]
categories: 计蒜客
---
# 题目
斐波那契数列是一种非常有意思的数列，由 0 和 1 开始，之后的斐波那契系数就由之前的两数相加。用数学公式定义斐波那契数列则可以看成如下形式：
$F_{0}=0$
$F_{1}=1$
$F_{n}=F_{n}-1+F_{n}-2$
我们约定Fn表示斐波那契数列的第n项，你能知道斐波那契数列中的任何一项吗？
输入包括一行，包括一个数字N（0≤N≤50）。
输出包括一行，包括一个数字，为斐波那契数列的第N项的值。
**样例1**
输入：
7
输出：
13
<!--more-->
# 答案
```
num=int(raw_input())
list=[0,1]
i=0
for i in range(1,50):
    fn=list[-1] + list[-2]
    list.append(fn)
print list[num]
```