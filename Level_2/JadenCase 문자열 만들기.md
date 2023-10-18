### JadenCase 문자열 만들기.md

 - url: https://school.programmers.co.kr/learn/courses/30/lessons/12951
 
 --------
 
#### 문제 설명
JadenCase란 모든 단어의 첫 문자가 대문자이고, 그 외의 알파벳은 소문자인 문자열입니다. 단, 첫 문자가 알파벳이 아닐 때에는 이어지는 알파벳은 소문자로 쓰면 됩니다. (첫 번째 입출력 예 참고)
문자열 s가 주어졌을 때, s를 JadenCase로 바꾼 문자열을 리턴하는 함수, solution을 완성해주세요.

##### 제한 사항
 - s는 길이 1 이상 200 이하인 문자열입니다.
 - s는 알파벳과 숫자, 공백문자(" ")로 이루어져 있습니다.
   - 숫자는 단어의 첫 문자로만 나옵니다.
   - 숫자로만 이루어진 단어는 없습니다.
   - 공백문자가 연속해서 나올 수 있습니다.
   - 
--------
 
#### 입출력 예
|s|return|
|:---:|:---:|
|"3people unFollowed me"|"3people Unfollowed Me"|
|"for the last week"|"For The Last Week"|
 
--------


```python

def solution(s):
    answer = ''
    s = s.lower()
    
    if s[0].isalpha():
        s = s[0].upper() + s[1:]
    
    for i in range(1, len(s)):
        if s[i] != " " :
            if s[i-1] == " ":
                if s[i].isdigit():
                    continue
                else:
                    s = s[:i] +s[i].upper() + s[i+1:]
                    
                
    answer = s
    
    return answer

```

------
### COMMENT
처음엔 공백을 기준으로 잘라 첫글자만 대문자로 바꾸는 형식으로 해결하려했으나, 공백문자가 연속해서 나올수 있다는 조건때문에 실패하였다
따라서 for문을 통해 전체 문자열을 하나씩 보며 직전값의 공백을 기준으로 첫글자를 대문자로 만들었다.

```python
def Jaden_Case(s):
    # 함수를 완성하세요
    return s.title()

# 아래는 테스트로 출력해 보기 위한 코드입니다.
print(Jaden_Case("3people unFollowed me for the last week"))
```
다른사람의 해결방법을 보니 title() 이라는 내장함수를 쓰면 바로 해결되었다..



