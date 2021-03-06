Problem 25. 1000-digit Fibonacci number
==================================

## 题目

The Fibonacci sequence is defined by the recurrence relation:

$$F_n = F_{n-1} + F_{n-2}, \textit{ where } F_1 = 1 \textit{ and } F_2 = 1.$$

Hence the first 12 terms will be:

<pre>
    F1 = 1
    F2 = 1
    F3 = 2
    F4 = 3
    F5 = 5
    F6 = 8
    F7 = 13
    F8 = 21
    F9 = 34
    F10 = 55
    F11 = 89
    F12 = 144
</pre>

The $12_{th}$ term, $F_{12}$, is the first term to contain three digits.

What is the first term in the Fibonacci sequence to contain 1000 digits?

[Problem 25. 1000-digit Fibonacci number](https://projecteuler.net/problem=25 "Problem 25")

## 翻译

以下是斐波那契数列的递归定义：

$$F_n = F_{n-1} + F_{n-2}, F_1 = 1, F_2 = 1.$$

那么其12项为:

<pre>
    F1 = 1
    F2 = 1
    F3 = 2
    F4 = 3
    F5 = 5
    F6 = 8
    F7 = 13
    F8 = 21
    F9 = 34
    F10 = 55
    F11 = 89
    F12 = 144
</pre>

因此第 $12$ 项，$F_{12}$，是第一个包含三位数字的项。

斐波那契数列中第一个包含 $1000$ 位数字的项是第几项？

[题目25：第一个包含 $1000$ 位数字的斐波那契数列项是第几项](http://pe.spiritzhang.com/index.php/2011-05-11-09-44-54/26-251000 "题目25")

## 题解

答案(answer): 4782

### Python

~~~python
#! /usr/bin/env python
# -*- coding: utf-8 -*-

def euler_25():
    a, b, cnt = 1, 1, 1
    while str(a).__len__() < 1000:
        a, b = b, a+b
        cnt += 1
    return cnt

if __name__ == '__main__':
    print(euler_25())

# vim: set sw=4, ts=4
~~~

### Haskell

~~~haskell
main :: IO ()
main = print euler_25

euler_25 :: Int
euler_25 = length $ takeWhile ((< 1000) . length . show) fib
    where
        fib = fix (scanl (+) 0 . (1:))
~~~
