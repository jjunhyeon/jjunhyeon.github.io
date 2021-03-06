---
layout: categories
excerpt: 스택/큐 문제 
title:  "프로그래머스 문제 풀기2"
author_profile: true
categories : Algorithm

---

### 스택/큐를 활용한 문제(주식 가격)

* [문제보러가기](https://programmers.co.kr/learn/courses/30/lessons/42584 "프로그래머스 사이트로 이동합니다.")
---
#### 01. 나의 풀이
<br/>

```python
def solution(prices):
    answer = [0] * len(prices)
    for i in range(len(prices)):
        for j in range(i+1, len(prices)):
            if prices[i] <= prices[j]:
                answer[i] += 1
            else:
                answer[i] += 1
                break
    return answer
```

<br/>
*이중 포문을 사용해서 다음 prices[j]의 값이 이전 prices[i]이상이면 값 증가 그렇지 않아도 그 순간까지는 기간을 인정하고 포문을 빠져나올 수 있도록 생각해 코드를 구현했습니다.

<br/>

---

#### 02.다른 사람의 풀이

```python
from collections import deque
def solution(prices):
    answer = []
    prices = deque(prices)
    while prices:
        c = prices.popleft()

        count = 0
        for i in prices:
            if c > i:
                count += 1
                break
            count += 1

        answer.append(count)

    return answer
```

* 취지에 가장 적합하게 큐를 활용한 코드 구현
---

### 03. 스택과 큐에 대해

**스택(stack) 영역<br/>
```
메모리의 스택(stack) 영역은 함수의 호출과 관계되는 지역 변수와 매개변수가 저장되는 영역입니다.

스택 영역은 함수의 호출과 함께 할당되며, 함수의 호출이 완료되면 소멸합니다.

이렇게 스택 영역에 저장되는 함수의 호출 정보를 스택 프레임(stack frame)이라고 합니다.

스택 영역은 푸시(push) 동작으로 데이터를 저장하고, 팝(pop) 동작으로 데이터를 인출합니다.

이러한 스택은 후입선출(LIFO, Last-In First-Out) 방식에 따라 동작하므로, 가장 늦게 저장된 데이터가 가장 먼저 인출됩니다.

스택 영역은 메모리의 높은 주소에서 낮은 주소의 방향으로 할당됩니다.
```


<br/>

**힙(heap) 영역**
```
메모리의 힙(heap) 영역은 사용자가 직접 관리할 수 있는 ‘그리고 해야만 하는’ 메모리 영역입니다.

힙 영역은 사용자에 의해 메모리 공간이 동적으로 할당되고 해제됩니다.

힙 영역은 메모리의 낮은 주소에서 높은 주소의 방향으로 할당됩니다.
```

**스택과 힙의 장단점**
<br/>
```

* 스택

매우 빠른 액세스

변수를 명시 적으로 할당 해제 할 필요가 없습니다.

공간은 CPU에 의해 효율적으로 관리되고 메모리는 단편화되지 않습니다.

지역 변수 만

스택 크기 제한 (OS에 따라 다름)

변수의 크기를 조정할 수 없습니다.

* 힙
변수는 전역 적으로 액세스 할 수 있습니다.

메모리 크기 제한 없음

(상대적으로) 느린 액세스

효율적인 공간 사용을 보장하지 못하면 메모리 블록이 할당 된 후 시간이 지남에 따라 메모리가 조각화되어 해제 될 수 있습니다.

메모리를 관리해야합니다 (변수를 할당하고 해제하는 책임이 있습니다)

변수는 C언어 realloc() or 자바 new
```
---