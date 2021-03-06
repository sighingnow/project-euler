Problem 46. Goldbach's other conjecture
==================================

## 题目

It was proposed by Christian Goldbach that every odd composite number can be written as the sum of a prime and twice a square.

+ $9 = 7 + 2 \times 1^2$
+ $15 = 7 + 2 \times 2^2$
+ $21 = 3 + 2 \times 3^2$
+ $25 = 7 + 2 \times 3^2$
+ $27 = 19 + 2 \times 2^2$
+ $33 = 31 + 2 \times 1^2$

It turns out that the conjecture was false.

What is the smallest odd composite that cannot be written as the sum of a prime and twice a square?

[Problem 46. Goldbach's other conjecture](https://projecteuler.net/problem=46 "Problem 46")

## 翻译

Christian Goldbach 提出每个奇合数都可以写作一个质数与一个平方数的二倍之和：

+ $9 = 7 + 2 \times 1^2$
+ $15 = 7 + 2 \times 2^2$
+ $21 = 3 + 2 \times 3^2$
+ $25 = 7 + 2 \times 3^2$
+ $27 = 19 + 2 \times 2^2$
+ $33 = 31 + 2 \times 1^2$

但是这个推测是错误的。

最小的不能写作一个质数与一个平方数的二倍之和的奇合数是多少？

[题目46：最小的不能写作一个质数与一个平方数的二倍之和的奇合数是多少？](http://pe.spiritzhang.com/index.php/2011-05-11-09-44-54/47-46 "题目46")

## 题解

答案(answer): 5777

### Python

~~~python
#! /usr/bin/env python
# -*- coding: utf-8 -*-

from math import sqrt

def euler_46():

    def prime(n):
        for x in range(2, int(sqrt(n))+1):
            if n % x == 0:
                return False
        return True

    def judge(n):
        for x in range(3, n, 2):
            if not prime(x):
                continue
            t = int(sqrt((n-x)//2))
            if 2*t*t+x == n:
                return False
        else:
            return True

    for x in range(35, 1000000, 2):
        if not prime(x) and judge(x):
            print(x)
            break

if __name__ == '__main__':
    print(euler_46())

# vim: set sw=4, ts=4
~~~
