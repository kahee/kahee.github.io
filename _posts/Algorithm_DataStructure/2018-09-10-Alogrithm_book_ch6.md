---
layout: post
title: "알고리즘 ch6.무식하게 풀기"
date: 2018-09-06 00:00:00
img:
categories:
- Algorithm_DataStruct
tags: [알고리즘/자료구조]
---
> 프로그래밍대회에서 배우는 알고리즘 문제해결전략 정리

----

## 6.1 도입
**무식하게 푼다(brute-force)** 는 말은 컴퓨터의 빠른 계산 능력을 이용하여 가능한 경우의 수를 일일이 나열하면서 답을 찾는 방법을 의미한다.
<br> 가능한 방법을 전부 만들어 보는 알고리즘들을 가리켜 흔히 **완점 탐색(exhaustive search)** 라고 한다. 이는 컴퓨터의 장점을 가자 잘 이용하는 방법이다. 컴퓨터의 최대 장점은 결국 속도가 빠르다는 것이다.

## 6.2 재귀호출과 완전탐색
### 재귀함수(recursive function) 재귀호출(recursion)
- 자신이 수행할 작업을 유사한 형태의 여러 조각으로 쪼갠 뒤 그 중 한조각을 수행하고 나머지를 자기 자신을 호출해 실행하는 함수를 가르킴
### 재귀호출의 기저사례(base case)
- 모든 재귀 함수는 **더 이상 쪼개지지 않는** 최소한의 작업에 도달했을 때 답을 곧장 반환하는 조건문을 포함해야 한다.
### 예제 : 중첩 반복문 대체하기
- n=7 이라면 (0,1,2,3),(0,1,2,4),(0,1,2,5),...,(3,4,5,6)
```python
for i in  range(0,n):
  for j in range(i+1,n):
    for k in range(j+1,n):
      for l in range(k+1,n):
        print(i,j,k,l)
```

### 재귀함수 이용한 코드
```python
def pick(n, picked, to_pick):
    """
    n개의 원소 중 m개를 고르는 모든 조합을 찾는 알고리즘
    :param n: 젠처 원소의 수
    :param picked: 지금까지 고른 원소들의 번호 - list()
    :param to_pick: 더 고를 원소의 수
    :return:
    """

    # 기저 사례 : 더 고를 원소가 없을 때 고른 원소들 출력
    if to_pick is 0:
        return print(picked)

    # 고를 수 잇는 가장 작은 번호를 계산
    if len(picked) is 0:
        smallest = 0
    else:
        smallest = picked[-1] + 1

    # 이 단계에서 원소 하나를 고름
    for next in range(smallest, n):
        picked.append(next)
        pick(n, picked, to_pick - 1)
        picked.pop()


if __name__ == '__main__':
    result = list()
    pick(7, result, 4)

```

### 코드 실행
```console
[0, 1, 2, 3]
[0, 1, 2, 4]
[0, 1, 2, 5]
[0, 1, 2, 6]
[0, 1, 3, 4]
[0, 1, 3, 5]
[0, 1, 3, 6]
[0, 1, 4, 5]
[0, 1, 4, 6]
[0, 1, 5, 6]
[0, 2, 3, 4]
[0, 2, 3, 5]
[0, 2, 3, 6]
[0, 2, 4, 5]
[0, 2, 4, 6]
[0, 2, 5, 6]
[0, 3, 4, 5]
[0, 3, 4, 6]
[0, 3, 5, 6]
[0, 4, 5, 6]
[1, 2, 3, 4]
[1, 2, 3, 5]
[1, 2, 3, 6]
[1, 2, 4, 5]
[1, 2, 4, 6]
[1, 2, 5, 6]
[1, 3, 4, 5]
[1, 3, 4, 6]
[1, 3, 5, 6]
[1, 4, 5, 6]
[2, 3, 4, 5]
[2, 3, 4, 6]
[2, 3, 5, 6]
[2, 4, 5, 6]
[3, 4, 5, 6]
```