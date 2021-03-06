Problem 16. Power digit sum
============================

## 题目

$2^{15} = 32768$ and the sum of its digits is $3 + 2 + 7 + 6 + 8 = 26.$

What is the sum of the digits of the number $2^{1000}$?

[Problem 16. Power digit sum](https://projecteuler.net/problem=16 "Problem 16")

## 翻译

$2^{15} = 32768$ 并且其各位之和为 $3 + 2 + 7 + 6 + 8 = 26$.

$2^{1000}$ 的各位数之和是多少？

[题目16: 2的1000次方的各位之和是多少](http://pe.spiritzhang.com/index.php/2011-05-11-09-44-54/17-1621000 "题目16")

## 题解

答案(answer): 1366

### Python

~~~python
#! /usr/bin/env python
# -*- coding: utf-8

def euler_16():
    return sum([int(i) for i in str(2**1000)])

if __name__ == '__main__':
    print(euler_16())

~~~
