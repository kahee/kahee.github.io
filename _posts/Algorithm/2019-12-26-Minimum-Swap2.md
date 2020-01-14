---
layout: post
title: "Minimum Swaps 2"
date: 2019-12-26 00:00:00
img:
categories:
- Algorithm
tags: [알고리즘]
---

## Minimum Swaps 2

[Minimum Swaps 2](https://www.hackerrank.com/challenges/minimum-swaps-2/problem)

## 문제 풀이 

```python
#!/bin/python3

import math
import os
import random
import re
import sys

# Complete the minimumSwaps function below.
def minimumSwaps(arr):
    swap_count = 0 
    for i in range(0, n - 1):
        # 해당 index 에 자신의 숫자가 아닌 경우만
        while arr[i] != i + 1:
            j = arr[i] - 1
            arr[i], arr[j] = arr[j], arr[i]
            swap_count += 1
    return swap_count

if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')

    n = int(input())

    arr = list(map(int, input().rstrip().split()))

    res = minimumSwaps(arr)

    fptr.write(str(res) + '\n')

    fptr.close()

```

## 오답

- 선택정렬로 문제를 풀었으나, arr 이 1000개 이상이 되면 timeout 발생

```python
#!/bin/python3

import math
import os
import random
import re
import sys

# Complete the minimumSwaps function below.
def minimumSwaps(arr):

    swap_count = 0
    for i in range(0, len(arr) - 1):
        min_idx = i
        for j in range(i + 1, n):
            if arr[j] < arr[min_idx]:
                min_idx = j

        if i != min_idx:
            swap_count += 1
            arr[i], arr[min_idx] = arr[min_idx], arr[i]
    return swap_count

if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')

    n = int(input())

    arr = list(map(int, input().rstrip().split()))

    res = minimumSwaps(arr)

    fptr.write(str(res) + '\n')

    fptr.close()
```