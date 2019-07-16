---
title: "programmers 문제 H-Index 구하기"
date: "2019-07-16 10:30:00"
categories: programmers practice
author_profile: true
read_time: true
toc: true #Table Of Contents 목차 보여줌
toc_label: "H-Index" # toc 이름 정의
# toc_icon: "cog" #font Awesome아이콘으로 toc 아이콘 설정
toc_sticky: true # 스크롤 내릴때 같이 내려가는 목차
---

# H-Index란?

어느 과학자의 h개 논문이 h번 이상 인용되고 나머지 논문들은 h번 미만 인용되었다면, 그 과학자의 h-index는 h일까?

참고) 어떤 연구자의 논문들 중 h개 논문이 최소 h회 이상씩 인용되면 H-index는 h이다.

그래프로 나타내면
![572425518181e858f3b72a2c14ae0d17](https://user-images.githubusercontent.com/33077726/61262927-13d91a80-a7c2-11e9-8d23-2cc3747040d2.png)
이러한 그래프가 그려진다 x축이 논문수가 되고, y축이 인용수가 된다.

피인용수가 논문수보다 같거나 작아지기 직전하는 숫자 즉 피 인용수 >= 논문 수가 H-index가 된다.

이 H-Index를 구하는 공식은 자바로 하면

## 풀이

```java

public static int solution(int[] arr) {
		ArrayList<Integer> list = new ArrayList<Integer>();
		for (int i = 0; i < arr.length; i++) {
			list.add(arr[i]);
        }                                   // Collections 메서드를 이용하기 위해 ArrayList에 담는다.

		Collections.sort(list);             // 논문수와 인용수를 비교하기 쉽게 정렬한 다음
		Collections.reverse(list);          // 그래프의 형태를 이용하여 값을 구하기 위해 배열을 뒤집는다.
		for (int i = 0; i < list.size(); i++) {
			if (list.get(i) < i+1) {		// 논문수는 1부터 시작하니 i(0) + 1부터 비교한다.
				return i;                   // 인용수가 논문수보다 작아지는 시점에 논문의 인덱스 번호(H-Index)를 리턴함
			}
		}
		return list.size();                 // H-index의 그래프가 그려지지 않는 값은 논문수 = H-index 이다.
	}

```
