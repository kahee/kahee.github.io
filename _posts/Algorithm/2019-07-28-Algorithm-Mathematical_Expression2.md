---
layout: post
title: "Mathematical Expression"
date: 2019-07-28  00:00:00
img:
categories:
    - Algorithm
tags: [알고리즘]
---

## Mathematical Expression and Reasoning for Computer Science 

### Part1. Mathematical Expression

---

### Predicate logic 
- x is a power of 2(거듭제곱) -> not proposition
    - 이유: x의 값에 따라서 결과값이 달라지기 때문에 
    - if x =8, True / if x = 7 False
- 하나 이상의 변수에 의존하는 statement = predicate 
    - P: predicate 을 의미 
    - ex) P(8) is True
    - Q(x,y) $x^2 = y$ 
    - ex) Q(5, 25) = $5^2 = 25$, True
- P(x) : "x is a power of 2," where x∈N.

### Quantification of variables (변수의 정량화)
- truth value aggregation: 특정 변수에 대한 해석방법을 지정할 수 있다고함 (이해안됨..)
- **existential quantifier**, ∃: 주어진 predicate 에 만족하는 domian 요소가 존재한다는 의미 (적어도 1개이상은 predicate 에 만족하다는 의미라고함, 정확히 몇개의 요소가 들어잇는지는 말해주지 않음)
    - ∃x ∈ N, x ≥ 0: 자연수 x, 0과 같거나 큰 수
    - x = 1, True
    - ∃x ∈ S: a big OR that runs through all possible values for x from the domain S. 
        - ex) $(0 ≥ 0)∨(1 ≥ 0)∨(2 ≥ 0)∨(3 ≥ 0)∨···$
- **universal quantifier**, ∀: domain에 있는 모든 요소들은 predicate 에 만족한다는 의미 
    - $∀x ∈ N, x ≥ 0$: 모든 자연수 x 는 0과 같거나 크다, True
    - $∀x ∈ N, x ≥ 10$: False 
    - $∀x ∈ S$: a big AND that runs through all possible values of x from S.
        - ex) $(0 ≥ 0)∧(1 ≥ 0)∧(2 ≥ 0)∧(3 ≥ 0)∧···$
    - Loves(a,b): 언제나 a 사람은 b 라는 사람을 사랑한다.
        - ![190729_1.png](attachment:190729_1.png)
        - A = {Ella, Patrick, Malena, Breanna}, B = {Laura, Stanley, Thelonious, Sophia}
        - ∃a ∈ A, Loves(a, Thelonious): A에 있는 사람 중 Thelonious 를 사랑하는 사람이 존재한다, True(Malena)
        - ∃a ∈ A, Loves(a, Sophia): A에 있는 사람 중 Thelonious 를 사랑하는 사람이 존재한다, False 
        - ∀a ∈ A, Loves(a,Stanley): A에 있는 모든 사람들은 Stanley 를 사랑한다, True
        - ∀a ∈ A, Loves(a, Thelonious): A에 있는 모든 사람들은 Stanley 를 사랑한다, False
 
### Understanding multiple quantifiers
- $∀a ∈ A, ∀b ∈ B, Loves(a, b)$
    - A에 있는 모든 person a, B에 있는 모든 person B / B에 있는 모든 person B, A에 있는 모든 person a,   -> a loves b
    - two consecutive universal quantifiers 순서 바뀌어도 상관없음 
- $∀x∈S ,∀y∈S ,P(x,y), ∀y ∈ S2,∀x ∈ S1,P(x,y)$
- $∀a ∈ A, ∃b ∈ B, Loves(a, b)$: For every person a in A, there exists a person b in B, such that a loves b.
    - a가 누구를 선택하는가에 따라 영어 후반부 "a loves someone in B" 해석 가능
- $∃b ∈ B, ∀a ∈ A, Loves(a, b)$: there exists a person b in B, where for every person a in A, a loves b.
    - a person b in B that is loved by everyone in A
    - Malena, Stanley 연결이 사라지면 위 예제는 True가 안될 수 있음, 그러나 "everyone in A loves someone" 은 True
- 결론: **기호 순서가 바뀌면 의미가 달라질 수 있음**
    - 첫번째 경우: 기호 a가 quantified 가 된 후에 발생하기에 b의 선택은 a의 선택에 따라 달라짐 (a의 선택에 따라 b가 누군지 달라짐)
    - 두번째 경우: b가 먼저 나와서 b의 선택은 a의 선택과 독립적이어야 함 (a의 선택과 상관없이 b를 선택함)
- 모든 quantified expression 왼쪽에서 오른쪽으로 읽고 기호를 주의해야함 
- True 인지 확인하려면 변수가 사용할 수 있는 모든 값에 대한 명령문을 확인해야함
- 이해가 필요함: one value for that variable such that the statement is True, and this value can depend on the variables to the left of it, but not on the variables to the right of it. -> 왼쪽 변수의 경우 오른쪽 변수에는 의존할 수 없음, (exists quntified)

### Writing sentences in predicate logic
- $∀x ∈ N, x2 > y$: 문장이 아님, x가 quantified 가 되더라도, y는 없기 때문에  formula 의 truth 값이 될 수 없음
    - $∀x,y∈N, x2 >y$ 는 가능함

### Manipulating negation
- ¬: 이 기호를 이용하여 부정할 수 있음 
    - ex) $¬(∀x∈N, ∃y∈N, x≥5∨x2−y≥30)$
    - Not (모든 자연수 x, 자연수 y, x는 5와 크거나 같고 $x^2 - y$ 는 30보다 크거나 같다)
    - ¬(¬p) -> p.
    - ¬(p∨q) -> (¬p)∧(¬q)
    - ¬(p∧q) -> (¬p)∨(¬q)
    - ¬(p ⇒ q) -> p ∧ (¬q)
    - ¬(p⇔q) -> (p∧(¬q))∨((¬p)∧q)) 
    - ¬(∃x ∈ S, P(x)) -> ∀x ∈ S, ¬P(x) ¬(최소 한개를 만족한다) -> 하나도 만족하지 않는다.
    - ¬(∀x ∈ S, P(x)) -> ∃x ∈ S, ¬P(x)
- ⇔ "같은 truch 값을 가짐" -> 부정 "다른 truth 값을 가짐"

### Commas: avoid them!
- If it rains tomorrow, I’ll be sad. -> then 의미 
- David is cool, Toni is cool. -> and 의미 
- P(x), Q(x): 모호성때문에 이렇게 연결하면 안됌!
- comma 의 사용성 
    - immediately after a variable quantification, or separating two variables with the same quantification
    - separating arguments to a predicate
    - $∀x,y ∈ N, ∀z ∈ R, P(x,y) ⇒ Q(x,y,z)$ 유일하게 사용할 수 있는 방법
    
### Defining predicates
- $k ∈ Z, n = dk$: d divides n, or n is divisible by d, 
- $d | n$: “d divides n.”
- every integer x, if x divides 10, then it also divides 100
    - With thepredicate: $∀x∈Z, x|10⇒x|100$
    - Without the predicate: $∀x∈Z, (∃k∈Z, 10=kx) ⇒ (∃k∈Z, 100=kx)$ -> $∀x∈Z, (∃k_1 ∈Z, 10=k_1x)⇒(∃k_2 ∈Z, 100=k_2x).$
- p ∈ N, p: prime 1보다 크고 p를 나눌 수 있는 유일한 자연수가 1일때 p를 소수라함
    - ex) if a number d divides p, then d = 1 or d = p. 
        - $Prime(p): p>1∧(∀d∈N, d|p⇒d=1∨d=p), where p∈N$
        - $Prime(p): p>1∧(∀d∈N, (∃k∈Z, p=kd)⇒d=1∨d=p)$
    - ex) there are infinitely many primes
        - 소수가 자연수이기 때문에 수가 무한히 많으면 그 수가 계속 커져야함 (이해잘안됨)
        - every natural number has a prime number larger than it
        - $∀n∈N, ∃p∈N, p>n∧Prime(p)$
        - $∀n ∈ N, ∃p ∈ N, p > n ∧ p > 1 ∧ (∀d ∈ N, (∃k ∈ Z, p = kd) ⇒ d = 1 ∨ d = p)$
 
### One last example: Fermat's Last Theorem 
- 페르마의 마지막 정리
    - ex) $∀n∈N, n>2 ⇒ ¬(∃a,b,c∈Z+, an+bn =cn)$
        - a, b, c: postitive integer 
        - $an + bn = cn , n > 2$
    - 간략화: $∀n∈N, n>2(∀a,b,c∈Z+, an+bn ̸=cn)$
  
### Our conventions for writing formulas
####  operator precedence (우선순위)
- $∀x,y∈N, ∃z∈N, x+y=z∧x·y=z⇒x=y$
- 우선순위
    1. ¬
    2. ∨,∧ 
    3. ⇒,⇔ 
    4. ∀,∃
- $(p∨¬q)∧r ⇒ ((s∨t)∧u)∨(¬v∧w)$
- $((p∨(¬q))∧r) ⇒ ((s∨t)∧u)∨((¬v)∧w))$
- $∀x,y∈N, ∃z∈N, x+y=z∧x·y=z⇒x=y$
- $∀x,y∈N, (∃z∈N, ((x+y=z∧x·y=z) ⇒x=y))$
#### Variable scope and naming
- 변수가 무엇을 가지고 있는지 혼동을 주지 않기 위해서 변수마다 다름 이름을 사용함 
    - ex) $(∀x∈N, f(x)≥5)∨(∃x∈N, f(x)<5)$
    - 다른 변수로 변경: $(∀x∈N, f(x)≥5)∨(∃y∈N, f(y)<5)$
- expanding the same definition multiple times
    - ex) $x | 10 ⇒ x | 100$, $(∃k1 ∈Z, 10=k1x)⇒(∃k2 ∈Z, 100=k2x)$
- Quantifiers: 왼쪽에서 오른쪽에서 읽음 
    - ex) $ ∀a ∈ A, ∃b ∈ B the variable a is in scope when choosing b, but this is not true in ∃b ∈ B,∀a∈A $
- 낮은 우선 순위로 사용하기 때문에 변수의 범위는 수식의 끝까지 지속되지만, 괄호가 있는 경우에는그 괄호안에서만 지속됨
    - ex) $(∀x∈N, f(x)≥5)∨(∃y∈N, f(y)<5)$, 