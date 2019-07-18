---
title: "programmers 문제 피보나치의 수"
date: "2019-07-18 20:50:00"
categories: programmers practice
author_profile: true
read_time: true
toc: true #Table Of Contents 목차 보여줌
toc_label: "Fibonacci" # toc 이름 정의
# toc_icon: "cog" #font Awesome아이콘으로 toc 아이콘 설정
toc_sticky: true # 스크롤 내릴때 같이 내려가는 목차
---

# 피보나치 수란?

수학에서, 피보나치 수(영어: Fibonacci numbers)는 첫째 및 둘째 항이 1이며 그 뒤의 모든 항은 바로 앞 두 항의 합인 수열이다. 처음 여섯 항은 각각 1, 1, 2, 3, 5, 8이다. 편의상 0번째 항을 0으로 두기도 한다.

[참조](https://ko.wikipedia.org/wiki/%ED%94%BC%EB%B3%B4%EB%82%98%EC%B9%98_%EC%88%98)피보나치 수란?

## 문제설명

피보나치 수는 F(0) = 0, F(1) = 1일 때, 1 이상의 n에 대하여 F(n) = F(n-1) + F(n-2) 가 적용되는 수 입니다.

예를들어

- F(2) = F(0) + F(1) = 0 + 1 = 1
- F(3) = F(1) + F(2) = 1 + 1 = 2
- F(4) = F(2) + F(3) = 1 + 2 = 3
- F(5) = F(3) + F(4) = 2 + 3 = 5

와 같이 이어집니다.

2 이상의 n이 입력되었을 때, n번째 피보나치 수를 1234567으로 나눈 나머지를 리턴하는 함수, solution을 완성해 주세요.

**입출력 예**

| **n** | **return** |
| :---: | :--------: |
|   3   |     2      |
|   5   |     5      |

입출력 예 설명
피보나치수는 0번째부터 0, 1, 1, 2, 3, 5, ... 와 같이 이어집니다.

```java
	public int solution(int n) {
     int answer = fibo(n);
		return answer;
	}

	static int fibo(int n){ // 피보나치 수열 알고리즘 구현
	    int before=0;
	    int cur=1;
	    int temp;
	    if (n == 0) return 0;
	    else if (n == 1) return 1;
	    else{
	        for (int i = 1; i < n; i++){
	            temp = cur;
	            cur = (before + cur)%1234567;   // 수열을 구하는 과정에 1234567 바로 나눈 몫을 넣는다.
	            before = temp;
	        }
	        return cur; // n번 째 피보나치 수를 1234567으로 나눈 몫을 바로 리턴 하는 것이 아닌, 계산 후에 리턴 해주어야 100점을 받을 수 있다.
	    }
	}
```
