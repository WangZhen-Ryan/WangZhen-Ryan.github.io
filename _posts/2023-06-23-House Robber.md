---
title: House Robber
author: Zhen
date: 2023-06-23
categories: [Leetcode]
tags: [House Robber, Dynamic Programming, Leetcode]
pin: true

math: true
---

## The Problem Setting

Input: nums = [1,2,3,1]
Output: 4
Explanation: Rob house 1 (money = 1) and then rob house 3 (money = 3).
Total amount you can rob = 1 + 3 = 4.

## dp

For the k-th array, we can only store the former two elements with maximal.


```python
class Solution:
    def rob(self, nums: List[int]) -> int:
        rob1, rob2 = 0,0
        for n in nums:
            temp = max(n+rob1, rob2) # [rob1, rob2, n, n+1, ...]
            rob1 = rob2
            rob2 = temp
        return rob2
        
```
