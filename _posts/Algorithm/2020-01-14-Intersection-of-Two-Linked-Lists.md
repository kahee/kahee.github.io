---
layout: post
title: "16. Intersection of Two Linked Lists"
date: 2020-01-14 00:00:00
img:
categories:
- Algorithm
tags: [알고리즘]
---

## Intersection of Two Linked Lists

[https://leetcode.com/problems/intersection-of-two-linked-lists/](https://leetcode.com/problems/intersection-of-two-linked-lists/)

### Notes

- If the two linked lists have no intersection at all, return `null`.
- The linked lists must retain their original structure after the function returns.
- You may assume there are no cycles anywhere in the entire linked structure.
- Your code should preferably run in O(n) time and use only O(1) memory.

## 문제풀이

- python set() 을 이용하면 쉽게 풀 수 있는 문제라고 생각했으나, O(n) 이기 때문에 요구조건에 맞지 않았다.
- O(1) 을 충족시키기 위해선 더 긴 리스트를 작은 리스트 길이의 차이보다 header 를 먼저 움직인 후 같이 이동하면서 비교를 해야한다.
- 실수 했던 부분은 Value를 비교해서 찾으면 된다고 생각했으나, `val`  만 같은게 아니라 이후 리스트들의 모든 `val` 들도 같아야 한다.

```python
# Definition for singly-linked list.
class ListNode:
    def __init__(self, x):
        self.val = x
        self.next = None
        
class Solution:
    def get_length(self, head: ListNode) -> int:
        length = 0
        cur_node = head
        while cur_node:
            length += 1
            cur_node = cur_node.next
        return length 
    
    def jump_by_index(self, head: ListNode, index: int) -> ListNode:
        cur_node = head
        for i in range(index):
            cur_node = cur_node.next
        return cur_node
    
    def getIntersectionNode(self, headA: ListNode, headB: ListNode) -> ListNode:
        a_len = self.get_length(headA)
        b_len = self.get_length(headB)
        
        if a_len > b_len:
            cur_node = self.jump_by_index(headA, a_len - b_len)
            other_node = headB
        else:
            cur_node = self.jump_by_index(headB, b_len - a_len)
            other_node = headA
                        
        while cur_node or other_node:
            if cur_node == other_node:
                return cur_node
            else:
                cur_node = cur_node.next
                other_node = other_node.next
```