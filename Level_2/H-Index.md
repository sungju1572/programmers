### H-Index.md

 - url: https://school.programmers.co.kr/learn/courses/30/lessons/42747#qna
 
 --------
 
#### 문제 설명
H-Index는 과학자의 생산성과 영향력을 나타내는 지표입니다. 어느 과학자의 H-Index를 나타내는 값인 h를 구하려고 합니다. 위키백과1에 따르면, H-Index는 다음과 같이 구합니다.

어떤 과학자가 발표한 논문 n편 중, h번 이상 인용된 논문이 h편 이상이고 나머지 논문이 h번 이하 인용되었다면 h의 최댓값이 이 과학자의 H-Index입니다.

어떤 과학자가 발표한 논문의 인용 횟수를 담은 배열 citations가 매개변수로 주어질 때, 이 과학자의 H-Index를 return 하도록 solution 함수를 작성해주세요.

##### 제한 사항
 - 과학자가 발표한 논문의 수는 1편 이상 1,000편 이하입니다.
 - 논문별 인용 횟수는 0회 이상 10,000회 이하입니다.
--------
 
#### 입출력 예
|citations|return|
|:---:|:---:|
|[3, 0, 6, 1, 5]|3|
 
--------

#### 입출력 예 설명
이 과학자가 발표한 논문의 수는 5편이고, 그중 3편의 논문은 3회 이상 인용되었습니다. 그리고 나머지 2편의 논문은 3회 이하 인용되었기 때문에 이 과학자의 H-Index는 3입니다.

```python

def solution(citations):
    answer = 0
    
    max_list = []
    length = len(citations)
    sort_list = sorted(citations)
    
    
    #정렬하여 차례대로 계산했을떄, 인용횟수가 현재 순번보다 낮아지기 전까지 확인
    for i in range(len(sort_list)):
        if  sort_list[i] >=  length - i :
            answer += 1
            print(length - i)

    return answer

```

------
### COMMENT
h-index는 특정 저자의 전체 논문수와 피인용수를 바탕으로 과학자(물리학자)의 연구성과, 공헌도를 하나의 수로 나타내는 지표이다

설명이 너무 부족해서 따로 h-index를 계산하는법을 찾았고, 바로 해결하였다

출처: https://postechlibrary.tistory.com/489 [포스텍 학술정보매거진 온ː 에어(ON AIR):티스토리]


