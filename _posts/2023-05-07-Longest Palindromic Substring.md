---
title: Longest Palindromic Substring
author: Zhen
date: 2023-05-07
categories: [Leetcode]
tags: [Longest Palindromic Substring, Leetcode]
pin: true
comment: true
---

# The Problem Setting

A palindrome is a string which reads the same in both directions. For example, 
S = "aba" is a palindrome,  S = "abc" is not.

Example:
```  
Input: s = "babad"
Output: "bab" or "aba"
```

## Approach 1: Brutal Force 

The brutal way is to check every possible substring if it is a palindrome. The trick to check palindrome by expanding to the outside is better than expanding to the inside.

There is a difference between expanding from inside to the outside and expanding from outside to inside.

```python
class Solution:
    def longestPalindrome(self, s: str) -> str:
        res = ""
        resLen = 0
        for i in range(len(s)):
            # odd length
            l, r = i, i
            while l >= 0 and r < len(s) and s[l] == s[r]:
                if (r-l+1) > resLen: # update the longest
                    res = s[l:r+1]
                    resLen = r-l+1
                l -= 1
                r += 1
            
            # even length
            l, r = i, i+1
            while l >= 0 and r < len(s) and s[l] == s[r]:
                if (r-l+1) > resLen: # update the longest
                    res = s[l:r+1]
                    resLen = r-l+1
                l -= 1
                r += 1
        return res
```
## Approach 3 The DP with longest common substring: 

Common Strategy is to find the longest common substring between S and S’, where S’ is the reverse of S. The problem is that this attempt fails when there exists a reversed copy of a non-palindromic substring in some other part of S.

Example: S = abacdfgdcaba	S’ = abacdgfdcaba 
The longest common substring is abacd or dcaba and either of them is palindrome

Algorithm: To rectify this, each time we find a longest common substring candidate, we check if the substring’s indices are the same as the reversed substring’s original indices. If it is, then we attempt to update the longest palindrome found so far; if not, we skip this and find the next candidate.

DP: 
come up a recursive solution to the problem
store(memoize) the intermediate result so that don’t need to repeat the computation 
buttom-up(this can be consequence of building the recursion)




## Approach 4: Expand Around Center

In fact, we could solve it in $O(n^2)$ time using only constant space.

We observe that a palindrome mirrors around its center. Therefore, a palindrome can be expanded from its center, and there are only $2n−1$ such centers.

You might be asking why there are $2n−1$ but not $n$ centers? The reason is the center of a palindrome can be in between two letters. Such palindromes have even number of letters (such as "abba") and its center are between the two 'b's.

```python
class Solution:
    def longestPalindrome(self, s):
        self.maxlen = 0
        self.start = 0
        
        for i in range(len(s)):
            self.expandFromCenter(s,i,i)
            self.expandFromCenter(s,i,i+1)
        return s[self.start:self.start+self.maxlen]
        

    def expandFromCenter(self,s,l,r):
        while l > -1 and r < len(s) and s[l] ==s[r]:
            l -= 1
            r += 1
        
        if self.maxlen < r-l-1:
            self.maxlen = r-l-1
            self.start = l + 1
```

Refer to [five approaches](https://zkf85.github.io/2019/03/26/leetcode-005-longest-palindrome#approach-1-longest-common-substring) for this question

