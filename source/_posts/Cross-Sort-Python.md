title: 交叉排序-Python-计蒜客
date: 2015-12-24 16:06:57
tags: [计蒜客,Python]
categories: 计蒜客
---
# 题目
输入一行 k 个用空格分隔开的整数，依次为 n1, n2 … nk。请将所有下标不能被 3 但可以被 2 整除的数在这些数字原有的位置上进行升序排列，此外，将余下下标能被 3 整除的数在这些数字原有的位置上进行降序排列。
输出包括一行，与输入相对应的若干个整数，为排序后的结果，整数之间用空格分隔。
**样例1**
输入：
1 5 4 3 10 7 19
输出：
1 3 7 5 10 4 19
提示信息
请注意，题面中的下标是从 1 开始的哦！
<!--more-->
# 答案
这道题没做出来,答案是百度.
```
input_str=raw_input()
input_list=input_str.split()


up_list=[]
down_list=[]
unum,dnum=0,0
for i in range(len(input_list)):
    if (i+1)%3!=0 and (i+1)%2==0:
        up_list.append(int(input_list[i]))
        input_list[i]='u'+str(unum)
        unum+=1
    elif (i+1)%3==0:
        down_list.append(int(input_list[i]))
        input_list[i]="d"+str(dnum)
        dnum+=1
up_list.sort()
down_list.sort(reverse=True)

for i,item in zip(range(len(input_list)),input_list):
    if type(item)==str:
        if item[0]=='u':
            input_list[i]=str(up_list[int(item[1:])])
        elif item[0]=='d':
            input_list[i]=str(down_list[int(item[1:])])

print ' '.join(input_list)
```