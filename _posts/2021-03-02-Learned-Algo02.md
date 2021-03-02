---
layout: categories
excerpt: 스택/큐 문제 
title:  "test"
author_profile: true
categories : Algorithm

---

* [문제보러가기](https://programmers.co.kr/learn/courses/30/lessons/42587 "프로그래머스 사이트로 이동합니다.")
---
#### 01 나의 풀이

```python
def solution(priorities,location):
a=[0] * len(priorities)
a[location] =1
k = priorities[location]
answer =0 

while True:
    if priorities[0] ==max(priorities):
        answer +=1
        if priorities[0] == k and a[0] ==1 :
            break
        else:
            priorities.pop(0)
            a.pop(0)
    else:
        priorities.append(priorities[0])
        priorities.pop(0)
        a.append(a[0])
        a.pop(0)
return answer
```

1. 리스트 a를 priorities의 길이와 같게 만들고 인쇄를 요청한 문서 위치를 1로 바꿉니다.
2. 무한루프틀 통해 대기목록의 가장 앞에 있는 문서의 중요도가 가장 높은지 확인합니다.
3. 가장 높으면 인쇄를 요청한 문서인지 확인하고 맞으면 무한루프를 나오고 아니면 문서를 인쇄
4. 높지 않으면 문서를 대기목록의 마지막에 넣고 가장 앞의 값을 뺀다.
5. 몇번째로 인쇄디는지 answer를 리턴.

---
### 02 다른 풀이
```python
def solution(a,location):
    queue = [(i,p) for i,p in enumerate(a)]
    answer= 0
    while True:
        cur = queue.pop(0)
        if any(cur[1] < q[1] for q in queue):
            queue.append(cur)
            print(queue)
        else:
            answer +=1
            if cur[0] == location:
                return answer
```
* any를 통해 q[1]에 하나라도 값이 큰게 있다면 우선순위를 뒤로 빼고 값을 추가하는 식으로 로직을 구성해 간결하게 푼 코드라고 생각해서 추가해봤습니다.
---
