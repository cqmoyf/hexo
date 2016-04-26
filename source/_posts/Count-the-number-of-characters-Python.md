title: 统计字符个数-Python-计蒜客
date: 2015-12-24 14:47:04
tags: [计蒜客,Python]
categories: 计蒜客
---
# 题目
输入一行字符，分别统计出其中英文字母、空格、数字和其他字符的个数。
** 输入格式
输入一行字符
** 输出格式
输出为一行，分别输出英文字母、空格、数字、其他字符的个数，用空格分隔
** 样例1

输入：
> aklsjflj123 sadf918u324 asdf91u32oasdf/.';123

输出：
> 23 16 2 4

<!--more-->
# 答案
```
str=list(raw_input())
abc="abcdefghijklmnopqrstuvwxyz"
num="0123456789"
abc=list(abc)
num=list(num)

ew=0
bb=0
nb=0
for e in abc:
    for s in str:
        if e==s.lower():
            ew=ew+1
# print(ew)

for n in num:
    for s in str:
        if n==s:
            nb=nb+1
for s in str:
    if s==" ":
        bb=bb+1
# print(len(str))
other=len(str)-ew-bb-nb
print ew,nb,bb,other
```