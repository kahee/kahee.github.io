---
layout: post
title: "946. Validate Stack Sequences"
date: 2020-01-15 00:00:00
img:
categories:
- Algorithm
tags: [알고리즘]
---

## 946. Validate Stack Sequences

[https://leetcode.com/problems/validate-stack-sequences/](https://leetcode.com/problems/validate-stack-sequences/)

## 문제 풀이

- popped 리스트의 값이 현재 push 되는 값과 같은지 비교하는 구문을 어디에 넣어야하는지 헷갈렸음

```python
class Solution:
    def validateStackSequences(self, pushed: List[int], popped: List[int]) -> bool:
        stack = list()
        
        pop_idx = 0 
        for i in pushed:
            stack.append(i)
            while stack and stack[-1] == popped[pop_idx]:
                stack.pop()
                pop_idx += 1
        return pop_idx == len(popped)
```