Problem 15. Lattice-paths
==================================

## 题目

Starting in the top left corner of a $2 \times 2$ grid, and only being able to move to the right and down, there are exactly 6 routes to the bottom right corner.

![Problem 15](../images/p015-1.png)

How many such routes are there through a $20 \times 20$ grid?

[Problem 15.Lattice-paths](https://projecteuler.net/problem=15 "Problem 15")

## 翻译

从一个 $2 \times 2$ 网格的左上角开始，有6条（不允许往回走）通往右下角的路。

![题目15](../images/p015-1.png)

对于 $20 \times 20$ 的网格，这样的路有多少条？

[题目15:从网格的左上角通往右下角有多少条路](http://pe.spiritzhang.com/index.php/2011-05-11-09-44-54/16-152020 "题目15")

## 题解

答案(answer): 137846528820

### 分析

从一个定点到对角的顶点，必然需要`m+n`步，从中选出`m`步向下走，另外`n`步向右走即可，因此答案为 $$ans = \binom{m+n}{m} = \binom{m+m}{n}.$$
在本题中，最终的结果为：$$\frac {40!}{20! \times 20!}$$

### Python

~~~python
#! /usr/bin/env python
# -*- coding: utf-8

def euler_15():

    def fact(n):
        ans = 1
        for i in range(1, n+1):
            ans *= i
        return ans

    return fact(40)//fact(20)//fact(20)

if __name__ == '__main__':
    print(euler_15())

# vim: set sw=4, ts=4, fileencoding=utf-8
~~~
