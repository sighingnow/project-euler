Problem 500. Problem 500!!!
============================

## 题目

The number of divisors of 120 is 16.

In fact 120 is the smallest number having 16 divisors.

Find the smallest number with $2^{500500}$ divisors.

Give your answer modulo 500500507.


[Problem 500. Problem 500!!!](https://projecteuler.net/problem=500 "Problem 500")

## 题解

答案(answer): 35407281

### 分析

引自[https://news.ycombinator.com/item?id=8977550](https://news.ycombinator.com/item?id=8977550)的关于此题的解答：

> So at this point, we think about doubling factor count and the ways we can do it. Out options are:
>   <1>. Multiply by a prime that we have never used so far.
>   <2>. Multiply by an existing prime k + 1 times, where k is the number of times it has been used.
> We repeat this 500500 times, using rule <1> and <2> (which can be generalized to one rule) and the result is the final answer.

| factor count   | n                           |
|:--------------:|:---------------------------:|
|  $2$           | $2$                         |
|  $4$           | $2*3$ <1>                   |
|  $8$           | $2*3*2*2$ <2>               |
|  $16$          | $2*3*2*2*5$ <1>             |
|  $32$          | $2*3*2*2*5*7$ <1>           |
|  $64$          | $2*3*2*2*5*7*3*3$ <2>       |
|  $128$         | $2*3*2*2*5*7*3*3*11$ <1>    |

> For 16 factors the number works out to be 120 (just like the example!). For numbers shown in the questions, sieving the prime takes some time, I also found it helpful to use a binary heap for speeding up finding the next smallest factors.

### Python

~~~python
#! /usr/bin/env python
# -*- coding: utf-8 -*-

from math import sqrt
from heapq import heappush, heappop

class comb:
    def __init__(self, n, c, nc):
        self.n = n
        self.c = c
        self.nc = nc
    def __cmp__(self, other):
        return self.nc - other.nc
    def __lt__(self, other):
        return self.nc < other.nc
    def __gt__(self, other):
        return self.nc > other.nc
    def __eq__(self, other):
        return self.nc == other.nc
    def __str__(self):
        return '(%d,%d,%d)'%(self.n, self.c, self.nc)

def euler_500():

    def nextprime():
        n, bound = 5, 7376507  # bound is the 500500th prime.
        yield 2
        yield 3
        while n < bound:
            i, r = 2, int(sqrt(n))
            while i <= r:
                if n % i == 0:
                    break
                i += 1
            if i > r:
                yield n
            n += 1

    n, mod, bound, mult, p = 1, 500500507, 500500, 1, 0
    heap, prime = [], nextprime()

    for i in range(1, 500500):
        p = next(prime)
        heappush(heap, comb(p, 1, p))

    while n <= bound:
        h, n = heappop(heap), n+1
        mult = (mult*h.nc) % mod
        heappush(heap, comb(h.n, 2*h.c, h.nc*h.nc))

    return mult

if __name__ == '__main__':
    print(euler_500())

# vim: set sw=4, ts=4
~~~
