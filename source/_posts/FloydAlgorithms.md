---
title: 'Leetcode 287与Floyd判圈算法'
date: 2022-01-09 17:46:21
tags: [Leetcode, Algorithms]
math: true
---

# 前言

今天的题目是Leetcode编号为276的题目，是一道乍看很简单，不过在考虑所有的constrain之后会发现很难的题目。要在所有的条件下解出这道题会用到Floyd判圈算法，也称龟兔赛跑算法，Floyd判圈算法可以用于检测链表，迭代算法中是否存在环(circle)。

# [题目](https://leetcode.com/problems/find-the-duplicate-number/)

Given an array of integers nums containing n + 1 integers where each integer is in the range [1, n] inclusive.

There is only **one repeated number** in nums, return this repeated number.

You must solve the problem without modifying the array nums and uses only constant extra space.

**Example 1:**
```
Input: [1,2,3,4,4]
Output: 4
```


