---
title: "codility practice"
date: {{ site.time | date: '%B %d, %Y' }}
categories: codility practice
---

Codility 1번 문제 binary Gap

--- problem
A binary gap within a positive integer N is any maximal sequence of consecutive zeros that is surrounded by ones at both ends in the binary representation of N.

For example, number 9 has binary representation 1001 and contains a binary gap of length 2. The number 529 has binary representation 1000010001 and contains two binary gaps: one of length 4 and one of length 3. The number 20 has binary representation 10100 and contains one binary gap of length 1. The number 15 has binary representation 1111 and has no binary gaps. The number 32 has binary representation 100000 and has no binary gaps.

Write a function:

int solution(int N);

that, given a positive integer N, returns the length of its longest binary gap. The function should return 0 if N doesn't contain a binary gap.

For example, given N = 1041 the function should return 5, because N has binary representation 10000010001 and so its longest binary gap is of length 5. Given N = 32 the function should return 0, because N has binary representation '100000' and thus no binary gaps.

Write an efficient algorithm for the following assumptions:

N is an integer within the range [1..2,147,483,647].
---

​``` java

public class OddOccurrencesInArray {

	public static void main(String[] args) {
		int A[] = {1,2,3,4,3,2,1,6,4,6,999999,12};
		
		int temp = 0;
		
		HashSet<Integer> map = new HashSet<Integer>();
		
		for(int i=0; i<A.length; i++) {
			if(map.add(A[i])) { //없으면 ture = 추가
				temp = A[i];
			}
			
			
		}
		System.out.println(temp);
		
	}
}

​```
