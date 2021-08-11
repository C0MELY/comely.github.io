---
title:  "코딩연습17 - 하노이 탑 이동 순서"
excerpt: "코딩 연습 17"

categories:
  - CodingTest
tags:
  - Recursion
  - Queue
last_modified_at: 2021-08-11T22:00:00-05:00
---

코딩 테스트 연습 열 일곱 번째,  
백준 알고리즘 10단계 "재귀" - 하노이 탑 이동 순서  
(문제 원문은 백준 알고리즘 11729번 참고)   
  
전형적인 하노이 탑 옮기기 문제.  
몇 개 옮길 지 입력 받은 후,  
최소 이동 횟수와 수행 과정 출력하기.  
  
수행과정 저장 및 출력을 위해 Queue 사용.  
```cpp
#include <queue>
queue<int> q; //자료형 지정 필요!!
q.push(element); //element input
q.pop(); //delete first element of queue q
q.empty(); //check empty
```
  
그리고 알고리즘 test는 시험용이니까!
잊지말자, >>전역변수<< 적극 활용!

```cpp  
#include <iostream>
#include <queue>
using namespace std;
queue<int> q;
int K = 0; //전역변수 
void move(int dep, int des, int N) {
	if (N == 1) { q.push(dep); q.push(des); K++; }
	else {
		move(dep, (6 - dep - des), N - 1);
		q.push(dep); q.push(des); K++;
		move((6 - dep - des), des, N - 1);
	}
}
int main() {
	int N;
	cin >> N;
	move(1, 3, N); //Recursion
	cout << K << '\n';
	while (!q.empty()) {
		cout << q.front() << ' ';
		q.pop();
		cout << q.front() << '\n';
		q.pop();
	}
}
```