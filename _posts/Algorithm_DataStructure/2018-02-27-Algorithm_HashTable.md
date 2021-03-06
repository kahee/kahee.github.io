---
layout: post
title: "알고리즘(해시 테이블)"
date: 2018-02-26  00:00:00
img:
categories:
- Algorithm_DataStructure
tags: [알고리즘/자료구조]
---
> Hello Coding 그림으로 개념을 이해하는 알고리즘 책 정리

---
### 해시 함수의 소개

> 식표품 가게에서 일을 하고 있는 당신, 계산을 하기 위해선 모든 물건 가격이 적혀 있는 가격 장부를 봐야 한다.

1. 알파벳 순서대로 정리되지 않은 가격장부의 실행시간은?
  - 모든 항목을 다 하나씩 찾아봐야 하므로 `O(n)`
2. 그럼 알파벳 순서대로 정리된 가격장부의 실행시간은?
  - 이진 탐색을 사용하면 `O(logn)`

> 가격 장부를 모두 외우고 있는 '알파고'가 있다고 가정하자

3. 그렇다면 알파고가 가격 장부를 찾아보는 실행시간은?
  - 외우고 있기 때문에 즉시 대답한다. `O(1)`

---

### 해시 함수
해시 함수란 **문자열을 받아서 숫자를 반환하는 함수**

#### 해시 함수의 조건
1. 일관성이 있어야 한다.
  -   EX) apple을 넣으면 반환되는 값은 항상 4
2. 다른 단어가 들어가면 다른 숫자가 나와야 한다.
  - Q) 어떤 단어를 넣어도 1만 나온다면?  좋은 해시 함수가 아니다.

#### 해시 함수 만드는 법
1. 해시 함수는 같은 이름에 대해선 항상 같은 인덱스를 할당
2. 다른 문자열에 대해서는 다른 인덱스 할당
3. 배열이 얼마나 큰지 알고 있어야 하며, 유효한 인덱스만 반환

---|-|-|-|-|-
 | | | |
---|-|-|-|-|-
0| 1| 2| 3| 4|


- APPLE -(해시 함수)-> 3

--|-|-|-|-|-
 | | | 0.67 |
--|-|-|-|-|-
0| 1| 2| 3| 4|

- MILK -(해시 함수)-> 0

--|-|-|-|-|-
1.49| | | 0.67 |
--|-|-|-|-|-
0| 1| 2| 3| 4|

---

### 해시 테이블
- 해시 함수 + 배열 -> `해시 테이블` 자료구조
- 해시함수라는 추가적인 논리구조를 가지고 있음
- 해시 맵, 맵, 딕셔너리, 연관배열로 알려져있음
- 해시 테이블은 **키** 와 **값** 을 가짐

```py
prices = dict()

prices['apple'] = 0.67
prices['milk'] = 1.49
```
### 해시 테이블 사용 예
장점)
1. 관계를 모형화할 수 있다.
2. 중복을 막을 수 있다.
3. 서버에 작업을 시키지 않고 자료 캐싱

#### 해시 테이블로 조회
- 사람 이름과 그 사람과 관련된 전봐 번호 추가
- DNS확인 작업 (웹 사이트 주소 -> IP 주소)

#### 중복된 항목을 방지
#### 해시 테이블을 캐시로 사용
- 정보를 다시 계산하지 않고 저장했다가 알려주는 것 `캐싱`

```py
cash = {}

def get_page(url):
  #  해시 테이블의 내용 전송
  if cache.get(url):
    return cache[url]
  else:
    #  서버가 무언가를 작업함
    data = get_data_from_server(url)
    cache[url] = data
    return data
```

---

### 충돌
- 충돌이란, 두개의 키가 같은 공간에 할당되는 것을 말한다.
- 충돌 해결 방법 중 가장 간단한 방법은 **여러개의 키를 연결 리스트로 만들어 넣는 것**

A - Appl:0.67 - AVOCADOS:1.49<br>
B<br>
C<br>
D<br>

- 이상적인 해시 함수는 키를 해시 테이블 전체에 고르게 할당해야 한다
- 연결 리스트가 길어지면, 해시 테이블 속도가 느려짐

### 성능

--|-|-|-|-|-
|해시테이블(평균) |해시테이블(최악) | 배열 |연결리스트|
--|-|-|-|-|-|-|
탐색|O(1) |O(n) |O(1)|O(n)|
--|-|-|-|-|-
삽입| O(1)|O(n)|O(n)| O(1)|
--|-|-|-|-|-
삭제| O(1)|O(n)|O(n)| O(1)|

- 탐색할때는 배열만큼 빠르고, 삽입, 삭제시엔 연결 리스트 만큼 빠름

### 충돌을 피하기 위해선?
[참고 사이트_](http://luyin.tistory.com/191)<br>
[참고 사이트_](http://egloos.zum.com/sweeper/v/925740)<br>
- 충돌을 피하려면 **낮은 사용률** 과 **좋은 해시 함수** 요소가 필요하다
- Chainig 방법 : 연결 리스트 사용
- 적재율 방법 :  적재율 = 현재 key 값의 갯수 / 전체 테이블 갯수

### 사용률
> 100게의 물건 가격을 해시 테이블 100개 공간에 사용하면 사용률은 1
만약 공간이 50개이면 사용률은 2

- 사용률 = 해시테이블에 있는 항목의 수/ 해시 테이블에 있는 공간의 수
- `사용률 > 1` 배열이 공간의 수보다 항목의 수가 많다는 뜻
- 사용률이 1이 되는 경우, 더 이상 항목을 저장 할 수 없게 되는 오버플로(overflow)발생
- 사용률이 커지면 해시 테이블의 공간을 추가 `리사이징(Resizing)`
- `사용률 > 0.7` 리사이징
- 리사이징은 굉장히 비싼 작업

### 좋은 해시 함수란?
- 배열에 값을 고루 분포 시키는 함수
- 이미 다른 사람들이 만들고 있음

### SHA(보안 해시 알고리즘)
- SHA(Secure Hash Algorithm)
- 문자열을 받아 그 문자열에 대한 해시값 반환
ex) "hello" -> abadfj234

#### 사용예
1. 파일 비교 : 파일 크기가 클때 유용
2. 패스워드 확인 : SHA 해시만 저장해서, 데이터베이스에 저장된 패스워드의 해시값과 비교/ 단방향이기 때문에 해시값을 문자열로 바꿀 수 없다.
