---
title: '[leetcode总结] 题目 476 与 Int 边际值'
layout: 
date: 2021-12-30 16:49:23
tags: Leetcode
math: true
---

# 前言

今天的题目是Leetcode编号为476的题目，虽然是一道简单题但是里面涉及的关于Int型极值的问题让我想把他记录下来。



# [题目](https://leetcode.com/problems/number-complement/)

The **complement** of an integer is the integer you get when you flip all the 0's to 1's and all the 1's to 0's in its binary representation.

For example, The integer 5 is "101" in binary and its complement is "010" which is the integer 2.

Given an integer num, return it's _complement_.

**Example 1:**
``` 
Input: num = 5
Output: 2
Explaination: The binary representation of 5 is 101 (no leading zero bits), and its complement is 010. So you need to output 2.
```

**Example 2:**
```
Input: num = 1
Output: 0
Explaination: The binary representation of 1 is 1 (no leading zero bits), and its complement is 0. So you need to output 0.
```

### Constaints:

1 <= num < $2^{31}$


# 思路
每个数的complement的本质就是与这个数的二进制有着相同长度，而且每一位都是1的数与这个数的二进制的差。

**举例**

num = 5 

二进制表达方式 num_in_binary = 101

与原数字有着相同长度，而且每一位都是1的二进制数 mask = 111

两个数之差：111-101 = 010 => 2 (从二进制转换到十进制)

所以 5 的complement就是 2。


# 代码实现

按照这个思路，首先我们要知道num二进制表达中有多少位。 然后根据位数来获得mask，最后做差。

获得十进制表达的数字的二进制表达的位数，我们可以通过以2为底的log操作来获得。

``` java
int num_digit_binary = (int) (Math.log(num) / Math.log(2));
```

获得对应的mask，我们可以通过2的位数加一次再减一来获得。

``` java
int mask = (int) (Math.pow(2,num_digit_binary + 1) - 1);
```

最后我们求两数之差就是complement了。
``` java
int complement = mask - num;
```

上述解法大部分情况可以都可以得到正确答案。不过在num_digit_binary为31位的时候, $ 2^{31}$ 存入Int会早成overflow，因为的int型的MAX_VALUE是$2^{31} - 1$，存入$2^{31}$的结果会是$2^{31} - 1$，这时候我们再减一就会让最后mask变为$2^{31} - 2$。 我们可以通过先减一再cast成int来避免这个情况。




