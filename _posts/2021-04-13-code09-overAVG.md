---
title:  "코딩연습9 - 평균은 넘겠지"
excerpt: "코딩 연습 9"

categories:
  - CodingTest
tags:
  - Basic
  - Array
  - TypeConversion
last_modified_at: 2021-04-13T23:30:00-05:00
---

코딩 테스트 연습 아홉 번째,  
백준 알고리즘 5단계 "1차원 배열" - 평균은 넘겠지  
(문제 원문은 백준 알고리즘 4344번 참고)  
  
여태까지 학습한 내용이 많이 적용되는 문제라서 기록한다.  
  
1. 형변환  
  출력 시 double형으로 강제 형변환을 지정해주었다.  
2. 소수점 이하 자릿수 지정 + 반올림  
  반올림한 숫자를 출력해야해서 다른 방법이 있는 줄 알았더니,  
  기존에 외워둔 precision()을 사용하면 반올림이 적용된다고..!  
  ```cpp
  cout<<fixed;
  cout.precision(3); //소수점이하 네번째 자리에서 세번째 자리로 반올림되어, 소수점이하에 숫자는 3개만 출력됨.
  ```

이하 전체 코드,
```cpp  
int C,N,score[1000],i,j,count=0;
double sum=0, avg=0, result=0;
cin>>C; //테스트 케이스 개수
for(i=0;i<C;i++){
	cin>>N; //학생 수 (1<=N<=1000, N은 정수)
	sum=0; count=0;
    for(j=0;j<N;j++) {
		cin>>score[j];
        sum+=score[j];
    }
    avg=(double)sum/N; //평균. 형변환.
    for(j=0;j<N;j++){
		if(score[j]>avg) count++; //평균 넘는 학생 수
    }
    result=(double)count/N*100; //출력값 계산.
    cout<<fixed;
    cout.precision(3); //소수점 이하 세자리만 출력. 네번째 숫자에서 반올림.
    cout<<result<<"%\n";
```