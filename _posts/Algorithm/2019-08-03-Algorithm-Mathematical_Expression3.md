---
layout: post
title: "Mathematical Expression"
date: 2019-08-03  00:00:00
img:
categories:
    - Algorithm
tags: [알고리즘]
---

## Mathematical Expression and Reasoning for Computer Science 

### Part2. Introduction to Proofs

---
- internal components: 내가 먼저 이게 ture, false 인지 판단
- external components: 외부에 내가 결정한 사고의 과정을 설명해야함
- 위의 과정들을 통해 에러나 추론의 틈을 찾아 낼 수 있음 
- **mathematical proof**: 다른사람에게 statement 의 거짓, 참을 전달하는 것 

### Some basic exapmles
1. 증명과 반증
2. predicate logic (술어 논리)로 번역
3. 이 statemnet 가 왜 참인지에 대해 논의
4. 공식적인 증거를 얻으려함 

- ex 2.1) $15·32 −7 = 7+(19+3)2/4.$
    - translation: 논리 연산자, 변수가 없기 때문에 이 predicate logic 자체가 번역임
    - discussion: 직접 계산을 하여 이게 진짜인지 아닌지 판단
    - proof: 128 
    
- ex 2.2) there *exsists* a power of two (2의 제곱) bigger than 10000
    - translation: $∃n∈N, 2n >1000.$
    - discussion: power of 2 grwo to infinity -> 이에 해당하는 n값을 찾아야함 
    - proof: Let n = 10, Then $n^2 = 1024$
- a typical proof of an existential(실질적인)
    - stagement to prove: $∃x ∈ S, P(x)$, S에 있는 적어도 한개의 원소는 P를 만족한다. 
    - proof: Let x = ___ , [Proof that P(_) is true]
    - blanks = the same element of S, existence proofs 보통 도메인의 정확한 요소를 찾는 것임
- ex 2.3) 20보다 큰 실수 n이 부등식(in-equlity) $1.5n − 4 ≥ 3$ 을 만족하는지 증명하라
    - translation: $∀n∈R, n>20⇒1.5n−4≥3$
    - discussion
        - n = 25 $1.5(25) - 4  = 33.5 > 3$, 한 숫자에 대해서만 증명하기 때문에 적당하지 않음 
        - (이해안감)Now is a good time to review the section on Inequalities. : 여기서 부등식을 보존한다는 의미는 무엇인가?
    - proof: Let n = $R$ 
        - $n > 20$
        - $1.5n > 30$
        - $1.5n - 4 > 26$
        - $1.5n - 4 ≥ 3$
        - 위 증명과는 다르게 여러 숫자에 대한 증명을 한 것임
        - n을 an arbitrary real number(임의의 수)라고 가정하고 증명함
- a typical proof of a universal
    - statement: $∀x ∈ S, P(x)$
    - proof: Let $x ∈ S (x be an arbitrary element of S)$, [Proof that P(x) is true].
    
- a typical proof of an implication(direct) 
    - n> 20 가정하는 것을 나타낼때 $P ⇒ Q$, P가 참이면 Q는 반드시 참이다.
    - statement: $P ⇒ Q$
    - proof: Assume P, [Proof that Q is true.]

### Variables as representing arbitrary numbers
```
25 > 20
1.5(25) > 30 
1.5(25) − 4 > 26
1.5(25)−4 ≥ 3


4 > 20 
1.5(4) > 30 
1.5(4) − 4 > 26
1.5(4)−4 ≥ 3
```
- 수학적 증명의 변수는 절대값을 변경하지 않음 
- (이해안됨) Even when we say n represents an arbitrary real number, this doesn’t mean we can substitute different real numbers for n at different points in the proof!

```
25 > 20 
1.5(16) > 30
1.5(3000) − 4 > 26
1.5(3.14159) − 4 ≥ 3
```
- 증명중에는 변경되지 않음 

### A note about inequalities, bounds, and approximation (부등식, 경계, 근사) (이해안감)
- $1.5n − 4 ≥ 3 -> n ≥ 14 , 3
not n ≥ 20.$ 
- 차이점은 변수의 정확한 범위를 결정하여 해결하는 것이 아니라inequalities을 조작하여 더 많은 inequalities을 만드는 것
- inequalities은 bounding 값에 관한 것이며 정확하지 않음

### What goes into a proof?
### Proof header: setting up the proof 
- proof header: 모든 변수, 그리고 증명에 사용될 가정을 소개하는 것, 번역문에 나타나는 것과 동일한 순서로 
- universally-quantified variable (∀x ∈ S)
    - $Let x ∈ S$
    - $Let x be an arbitrary element of S$
- nexistentially-quantifiedvariable(∃x∈S) 구체적인 수로 나타낼때
    - $Let x = 5$
- 원래 문장에 나타나지 않는 변수는 정량화된 변수처럼 표현? (이해안감)
    - $Let ε = x−⌊x⌋$
- $∀x ∈ N, P(x) ⇒ Q(x)$
    - $Let x ∈ N. Assume P(x)$
- 여러 술어가 잇는 경우에는 AND 사용 $∀x ∈ N, P1(x) ∧ P2(x) ∧ P3(x) ⇒ Q(x)$
    - $Let x ∈ N. Assume that P1(x), P2(x), and P3(x) are all true$
- 술어를 가정하는 경우 $ P(x) : “x3 < 10x + 300” (where x ∈ N). $
    - $Let x ∈ N. Assume that P(x) is true, i.e., that x3 < 10x + 300$
- ex)2.4 $∀x∈R, ∀y∈N,x>10∧y<x⇒(∃z∈R, P(x,y,z))$
    - proof: $.Letx∈Randlety∈N. Assumethatx>10andthaty<x. Let
z = _____. We will prove that P(x, y, z) is true.$

### Proof body: the chain of reasoning
- statement가 실제로 참인지를 증명하는 이유가 포함되어잇어야 함
- deductions: sequence of true statements 
- 각 진술은 아래의 조합으로 이루어진다.
    - Definitions
    - Assumptions (mad in the prrof header)
    - Previous deductions (made eariler in the proof body)
    - external true statements 
```
Since [reason], [deduction].
Because we know [reason], we can conclude [deduction].
Then [deduction] (by the fact that [reason]).
It follows from [reason] that [deduction] is also true/holds.
```

### Logical deductions 
- modus ponens: 우리가 일반적으로 증명할때 사용하는 논리적인 형태, intuition과 같음 
    - p and p ⇒ q are both true -> q도 참이라는 결론을 내릴 수 있음 
    - $Because we know x > 10 and that x > 10 implies x2 − x > 90, we can conclude that x2 − x > 90$
-  universal instantiation: which matches our intuition for what a universally-quantified statement means.
- $∀x ∈ S, P(x), y 값은 도메인 Z의 요소이다$ -> P(y) 참이다라는 결론을 내릴 수 있음 
    - Because we know that y ∈ N and that ∀x ∈ N, x2 +5x+4 is not prime, we can conclude that y2 + 5y + 4 is not prime
 
### Writing reasons and deductions
- 두가지 질문을 만족하면 okay
    - What deduction am I saying is true here?
    - What reason(s) am I giving for why this is true?
- 예외 두가지
    1. Any deduction(추론) whose truth can be verified using a calculator, and any com- parison, divisibility and floor/ceiling operation on concrete numbers. 
        - ex) 100 > 3 · 4” and “165 is not divisible by 6”
    2.  Any basic manipulation(조작) of an equality or inequality to get another valid equality or inequality described in the earlier section on inequalities.
        - ex) x > 4 to 2x > 8 
        - 이게 의미하는게 증명하는 변수가 바뀌게 해서는 안된다는 건가?

### The direction of a proof
- 위에서 아래로 진행됨
- $ ∀n ∈ N, n > 20 ⇒ 1.5n − 4 ≥ 3$
```
n > 20 
1.5n > 30 
1.5n − 4 > 26
1.5n−4 ≥ 3
```
- 해결하는 방식으로 한다면.. 
```
1.5n − 4 ≥ 3 
1.5n ≥ 7
n ≥ 14/3
```
- $ 1.5n − 4 ≥ 3 ⇒ n ≥ 14$ 이걸 보여주게됨

### A new domain: number theory 
- $ Let n, d ∈ Z$, d divides n or n is divisible by d 
- ex 2.5) Prove 23 | 115 
    - $∃k ∈ Z, 115 = 23k$
    - proof: Let k = 5, Then 115 = 23*5
- ex 2.6) 
    - Tranlatiton: $∃a ∈ Z, a | 104$, $∃a, k ∈ Z, 104 = ak$
    - disussion: 104의 pair of divisors 를 골라야함 
    - Let a = -2 and let k = -52. then 104 = ak


