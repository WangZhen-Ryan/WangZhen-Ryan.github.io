---
title: Median of Two Sorted Arrays
author: Zhen
date: 2023-05-07
categories: [Leetcode]
tags: [Median of Two Sorted Arrays, Leetcode]
pin: true

math: true
---

# The Problem Setting

Brute Force:

List1: 1 2 3 5 7 12 14  length m 
List2: 4 9 10 length n

比如说 插入 4 到List1以后, 下一个element 9只会比较 1 2 3 4 5 7 12 14 后面一个 从 5 开始比 所以 所有的list2 都插入 list1以后 所有的list1的element都被check过了

Merging two lists directly will take O(m+n) complexity. The best case has complexity of O(m) if the second list is all larger or smaller than the first list.

Binary search:

We want to find the median, which can be done by partitioning the array into two halves such that the two halves have the same length and that the element in the left half is less than the right half. 

List1: x1, x2 | x3, x4, x5, x6
List2: y1, y2, y3, y4, y5 | y6, y7, y8

This separation would work if x2 <= y6 and y5 <= x3

```python
import random
import time

class Solution(object):
    def findMedianSortedArrays(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: float
        """
        length = len(nums1) + len(nums2)
        if length % 2 == 0:
            return (self.find_k(nums1, nums2, length / 2) +
                    self.find_k(nums1, nums2, length / 2 + 1)) / 2.0
        else:
            return self.find_k(nums1, nums2, length / 2 + 1) * 1.0

    def find_k(self, nums1, nums2, K):
        if len(nums1) == 0:  return nums2[int(K-1)]
        if len(nums2) == 0:  return nums1[int(K-1)]

        mid1, mid2 = int(len(nums1) / 2), int(len(nums2) / 2)
        if nums1[mid1] >= nums2[mid2]:
            if K >= mid1 + mid2 + 2:
                return self.find_k(nums1, nums2[mid2+1:], K - mid2 - 1)
            else:
                return self.find_k(nums1[:mid1], nums2, K)
        else:
            if K >= mid1 + mid2 + 2:
                return self.find_k(nums1[mid1+1:], nums2, K - mid1 - 1)
            else:
                return self.find_k(nums1, nums2[:mid2], K)
```
