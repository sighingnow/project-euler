Problem 39. Integer right triangles
==================================

## 题目

If $p$ is the perimeter of a right angle triangle with integral length sides, $\{a, b, c\}$, there are exactly three solutions for $p = 120$.

$$\{20, 48, 52\}, \{24, 45, 51\}, \{30, 40, 50\}$$

For which value of $p \le 1000$, is the number of solutions maximised?

[Problem 39. Integer right triangles](https://projecteuler.net/problem=39 "Problem 39")

## 翻译

如果 $p$ 是一个直角三角形的周长，三角形的三边长 $\{a, b, c\}$ 都是整数。对于 $p = 120$ 一共有三组解：

$$\{20, 48, 52\}, \{24, 45, 51\}, \{30, 40, 50\}$$

对于 $1000$ 以下的 $p$ 中，哪一个能够产生最多的解？

[题目39：如果 $p$ 是直角三角形 $\{a, b, c\}$ 的周长，$1000$ 以下的 $p$ 中哪一个具有最多的解？](http://pe.spiritzhang.com/index.php/2011-05-11-09-44-54/40-39pabc1000p "题目39")

## 题解

答案(answer): 840

### Python

~~~python
#! /usr/bin/env python
# -*- coding: utf-8 -*-

def euler_39():
    ans, maxcnt = 0, 0
    for s in range(3, 1000):
        cnt = 0
        for a in range(0, s//2):
            for b in range(1, (s-a)//2):
                if a*a == b*b + (s-a-b)*(s-a-b):
                    cnt += 1
        if cnt > maxcnt:
            maxcnt = cnt
            ans = s
    return ans, maxcnt

if __name__ == '__main__':
    print(euler_39())

# vim: set sw=4, ts=4
~~~
