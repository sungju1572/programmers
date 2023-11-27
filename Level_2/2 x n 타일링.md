### 2 x n 타일링.md

 - url: https://school.programmers.co.kr/learn/courses/30/lessons/12900#qna
 
 --------
 
#### 문제 설명
가로 길이가 2이고 세로의 길이가 1인 직사각형모양의 타일이 있습니다. 이 직사각형 타일을 이용하여 세로의 길이가 2이고 가로의 길이가 n인 바닥을 가득 채우려고 합니다. 타일을 채울 때는 다음과 같이 2가지 방법이 있습니다.

 - 타일을 가로로 배치 하는 경우
 - 타일을 세로로 배치 하는 경우
예를들어서 n이 7인 직사각형은 다음과 같이 채울 수 있습니다.

![image](https://github.com/sungju1572/programmers/assets/70958560/7da0676c-de04-416c-ae4e-295c8d73ebc5)


직사각형의 가로의 길이 n이 매개변수로 주어질 때, 이 직사각형을 채우는 방법의 수를 return 하는 solution 함수를 완성해주세요.


##### 제한 사항
 - 가로의 길이 n은 60,000이하의 자연수 입니다.
 - 경우의 수가 많아 질 수 있으므로, 경우의 수를 1,000,000,007으로 나눈 나머지를 return해주세요.
   
--------
 
#### 입출력 예
|n|result|
|:---:|:---:|
|4|5|

 
--------

#### 입출력 예 설명
![image](https://github.com/sungju1572/programmers/assets/70958560/2ddc658d-cd02-4cae-9abc-0e41a6908dbb)
![image](https://github.com/sungju1572/programmers/assets/70958560/d5acc278-e67b-4d4c-bce0-22c93f702f3c)
![image](https://github.com/sungju1572/programmers/assets/70958560/d950f28c-0318-4fd2-b889-aeedb5fa99c4)
![image](https://github.com/sungju1572/programmers/assets/70958560/836ea3a3-2bfe-499d-a9a8-6c2b813c0227)
![image](https://github.com/sungju1572/programmers/assets/70958560/6f62514e-d934-4e83-b550-6f3ac32d4e14)


```python

#피보나치 수열
def solution(n):


    if n == 1 :
        return 1
    elif n == 2 :
        return 2

    a, b = 1, 2
    for _ in range(3, n+1):
        a, b = b, a + b
    
    
    return b % 1000000007

```

------
### COMMENT
규칙성을 찾아야하는 문제인 것을 깨닫고 처음엔 조합(combinations)을 사용하려 해결하려했다

주어진 길이중 `(2x + y = n)` 방정식의 해를 찾아 배치할수 있는 모양의 개수를 찾았다.


```python

import math
def solution(n):
    answer = 0

    com_list = []
    
    for i in range(0,n//2 + 1):
        for j in range(0,n+1):
            if 2*i + j == n:
                com_list.append([i,j])
                break

                
    for i in com_list:
        answer += math.comb(sum(i), i[0])


    return answer
 % 1000000007

```

하지만 이방식으론 시간초과 & 효율성 문제를 해결 할 수가 없었다.

더 명확한 규칙성을 찾기위해 해를 쭉 나열해보니, 피보나치 수열인것을 깨달았다.

- F(N-1) 이 F(N)으로 가기 위해선 세로 막대 1개를 추가해야함
- F(N-2) 이 F(N)으로 가기 위해선 가로막대 2개 가로로 추가하는방법 or 세로막대 2개 세로로 추가하는방법 ( F(N-1)과 동일)

즉 F(N)에는 F(N-1)과정과  F(N-2)과정이 전부 포함되어 있으므로 

피보나치수열 `F(N) = F(N-1) + F(N-2)`를 얻을 수 있다.




