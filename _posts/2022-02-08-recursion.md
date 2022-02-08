---
layout: single
title:  "순환 (Recursion)"
categories: al
tag: algorithm
toc: true
---



# 순환이란?

자기 자신을 호출하는 함수


```java
int func(int n) {
 if (n==0)  --------- base case: 순환되지 않고 종료되는 case
 return 0;
    
 else
 return n + func(n-1);  ---------- recursive case
 }
```

<br>

base case: 적어도 하나의 recursion에 빠지지 않는 경우가 존재해야 한다.

recursive case: recursion을 반복하다보면 결국 base case로 수렴한다.

<br>

## 순환을 사용하는 예

- Factorial: n!

- x^n
- Fibonacci Number
- 최대공약수: Euclid Method
- 문자열의 길이 계산
- 순차 탐색

<br>

## Recursion vs Iteration

- 모든 순환함수는 반복문(iteration)으로 변경 가능
- 그 역도 성립함. 즉 모든 반복문은 recursion으로 표현 가능
- 순환함수는 복잡한 알고리즘을 단순하고 알기 쉽게 표현하는 것을 가능하게 함
- 하지만 함수 호출에 따른 오버해드가 있음 (매개변수 전달, 액티베이션 프레임 생성 등)

<br>



# 순환적 알고리즘 설계

<strong>암시적(implicit)</strong> 매개변수를  <strong>명시적(explicit)</strong> 매개변수로 바꾸어라.

```java
int *binarySearch(int data[], int target, int begin, int end) {
	 if (begin>end)
	 	 return -1;
	 else	 {
	 	 int middle = (begin+end)/2;
	 	 if (data[middle] == target)
	 	 	 return middle;
	 	 else if (data[middle] > target)
	 	 	 return **binarySearch(data, target, begin, middle-1);
	 	 else
	 	 	 return **binarySearch(data, target, middle+1, end);
	 }
}
```

<br>

함수의 첫 입력(*binarysearch) <strong>=/=</strong> recursive되는 매개변수(**binarysearch). 

그래서 매개변수가 <strong>일반화</strong>되기 위해서는 명시적이어야함.

