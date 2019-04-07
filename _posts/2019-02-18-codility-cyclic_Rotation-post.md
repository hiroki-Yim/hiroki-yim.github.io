---
title: "Codility 2번 문제 CyclicRotation"
date: "19-02-18 4:10pm"
categories: codility practice
---

**Codility 2번 문제 CyclicRotation**

---

**問題**

An array A consisting of N integers is given. Rotation of the array means that each element is shifted right by one index,
and the last element of the array is moved to the first place. For example,
the rotation of array A = [3, 8, 9, 7, 6] is [6, 3, 8, 9, 7] (elements are shifted right by one index and 6 is moved to the first place).
The goal is to rotate array A K times; that is, each element of A will be shifted to the right K times.
Assume that the following declarations are given:

```java
struct Results {
int \* A;
int N; // Length of the array
};
```

Write a function : struct Results solution(int A[], int N, int K);

that, given an array A consisting of N integers and an integer K, returns the array A rotated K times.

For example, given

```java
A = [3, 8, 9, 7, 6]
K = 3
```

the function should return [9, 7, 6, 3, 8]. Three rotations were made:
[3, 8, 9, 7, 6] -> [6, 3, 8, 9, 7][6, 3, 8, 9, 7] -> [7, 6, 3, 8, 9][7, 6, 3, 8, 9] -> [9, 7, 6, 3, 8]

For another example, given

```java
A = [0, 0, 0]
K = 1
```

the function should return [0, 0, 0]

Given

```java
    A = [1, 2, 3, 4]
    K = 4
```

the function should return [1, 2, 3, 4]

Assume that:
N and K are integers within the range [0..100];
each element of array A is an integer within the range [−1,000..1,000].
In your solution, focus on correctness. The performance of your solution will not be the focus of the assessment.

---

```java
    	public static void main(String[] args) {
    	int A[] = new int [] {1,2,3,4,5,6,7};
    	int K = 3;

    	int result[] = solution(A,K);

    	for(int i =0; i < result.length; i++)
    		System.out.print(result[i]);
    }

        public static int[] solution(int[] A, int K) {
        	try{	// 정상값이 들어올 경우 그냥 실행
            	for(int i=0; i<K; i++) {
    			int temp = A[A.length-1];
    				for (int k = A.length-1; k>0; k--) {
    					A[k] = A[k-1];
    				}
    			A[0] = temp;
    			}
            }catch(ArrayIndexOutOfBoundsException e){
            	return A;
            }	//만약 배열의 크기가 이상한 것이 들어오면 그냥 그배열 리턴해줌
        	return A;
        }
```
