Problem 22. Names scores
==================================

## 题目

Using [names.txt](../resource/p022-names.txt) (right click and 'Save Link/Target As...'), a 46K text file containing over five-thousand first names, begin by sorting it into alphabetical order. Then working out the alphabetical value for each name, multiply this value by its alphabetical position in the list to obtain a name score.

For example, when the list is sorted into alphabetical order, COLIN, which is worth 3 + 15 + 12 + 9 + 14 = 53, is the 938th name in the list. So, COLIN would obtain a score of 938 × 53 = 49714.

What is the total of all the name scores in the file?

[Problem 22. Names scores](https://projecteuler.net/problem=22 "Problem 22")

## 翻译

文件 [names.txt](../resource/p022-names.txt) （右键另存为）是一个46K大小的文本文件，包含5000多个英文名字。利用这个文件，首先将文件中的名字按照字母排序，然后计算每个名字的字母值，最后将字母值与这个名字在名字列表中的位置相乘，得到这个名字的得分。

例如将名字列表按照字母排序后， COLIN这个名字是列表中的第938个，它的字母值是3 + 15 + 12 + 9 + 14 = 53。所以COLIN这个名字的得分就是938 × 53 = 49714.

文件中所有名字的得分总和是多少？

[题目22：文件中所有名字的得分之和是多少？](http://pe.spiritzhang.com/index.php/2011-05-11-09-44-54/23-22 "题目22")

## 题解

答案(answer): 871198282

### Python

~~~python
#! /usr/bin/env python
# -*- coding: utf-8

def euler_22():
    # Initial.
    s = None
    with open('p022-names.txt', 'r') as fp:
        s = fp.read()
    s = s.split(',');
    s.sort()
    ans, index = 0, 1
    for name in s:
        score = 0
        for char in name[1:-1]:
            score += (ord(char)-ord('A')+1)
        ans += (index*score)
        index += 1
    return ans, index

if __name__ == '__main__':
    print(euler_22())

# vim: set sw=4, ts=4
~~~
