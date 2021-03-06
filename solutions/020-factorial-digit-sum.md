Problem 20. Factorial digit sum
==================================

## 题目

$n!$ means $$n \times (n - 1) \times ... \times 3 \times 2 \times 1$$

For example, $$10! = 10 \times 9 \times ... \times 3 \times 2 \times 1 = 3628800$$
and the sum of the digits in the number 10! is $$3 + 6 + 2 + 8 + 8 + 0 + 0 = 27.$$

Find the sum of the digits in the number $100!$

[Problem 20. Factorial digit sum](https://projecteuler.net/problem=20 "Problem 20")

## 翻译

$$n! = n \times (n - 1) \times ... \times 3 \times 2 \times 1$$

例如， $$10! = 10 \times 9 \times ... \times 3 \times 2 \times 1 = 3628800$$
那么 $10!$ 的各位之和就是 $$3 + 6 + 2 + 8 + 8 + 0 + 0 = 27.$$

算出 $100!$ 的各位之和。

[题目20:算出 $100!$ 的各位之和](http://pe.spiritzhang.com/index.php/2011-05-11-09-44-54/21-20100 "题目20")

## 题解

答案(answer): 648

### Python

~~~python
#! /usr/bin/env python
# -*- coding: utf-8

def euler_20():
    ans = 1
    for i in range(1, 101):
        ans *= i
    return sum([int(i) for i in str(ans)])

if __name__ == '__main__':
    print(euler_20())

# vim: set sw=4, ts=4
~~~

