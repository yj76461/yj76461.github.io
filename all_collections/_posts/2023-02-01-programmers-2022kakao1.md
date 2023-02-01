---
title: "[Algorithm] 프로그래머스 2022 KAKAO BLIND RECRUITMENT 양궁대회 문제"
excerpt: ""

categories:
    - Algorithm, DFS
tags:
    - [Algorithm]

toc: true
toc_sticky: true

date: 2023-02-01
---
# 양궁대회 문제 풀이
## DFS 공부중...

``` python

answer = []
maxNum = 0

def solution(n, info):

    def cpr(a,b):
        result = 0
        for i in range(11):
            if(a[i] == 0 and b[i] == 0):
                continue
            elif(a[i] < b[i]):
                result += 10 - i
            else:
                result -= 10 - i
        return result
    
    def dfs(li1,idx):
        global answer, maxNum
        
        if(idx == 11):
            if(sum(li1) == n):
                result = cpr(info, li1)
            elif(sum(li1) < n):
                li1[10] += n - sum(li1)
                result = cpr(info, li1)
            else:
                return
            if(maxNum < result):
                maxNum = result
                answer = [li1[:]]
            elif(maxNum == result and result != 0):
                answer.append(li1[:])
            return
        li1.append(info[idx] + 1)
        dfs(li1, idx + 1)
        li1.pop()
        li1.append(0)
        dfs(li1, idx + 1)
        li1.pop()
        
    dfs([],0)
    if(not answer):
        return [-1]
    
    answer.sort(key = lambda x : x[::-1], reverse = True)
    return answer[0]

```

## 아이디어
- 화살을 어피치보다 한발 많이 쏘는 경우, 아예 0발을 쏘는 경우로 DFS
- 제일 적은 배점의 칸을 많이 맞춘 경우 -> 같다면 그 다음으로 적은 칸 찾기

## 풀이
- 둘 사이의 점수 격차 result를 반환하는 cpr함수 선언
- dfs함수를 선언하여 두가지 경우로 재귀함수 호출
- 리스트의 끝 칸까지 모두 진행한경우 라이언이 쏜 화살 수를 주어진 화살 수와 비교
- 라이언이 많이 쐈으면 조건 위배로 그대로 종료
- 적게 쐈으면 마지막 칸에 남은 화살 몰아주고, 딱 맞게 쐈으면 바로 cpr 함수에 투입
- 최댓값을 저장하는 maxNum과의 비교 1) 크면 2차원 형식으로 갱신하고 2) 같으면 기존 답안 리스트에 2차원 형식으로 추가
- 이후 2차원 답안 리스트의 sort에서 맨 마지막 칸이 높은 순서대로 내림차순 정렬
- 첫번째 답안 반환

## 주의 사항
- 2차원 리스트에 1차원 리스트를 대입하거나 추가할 때 1차원 리스트 뒤에 "[:]" 슬라이싱 기호가 붙어야 함