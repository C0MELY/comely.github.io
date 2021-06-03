---
title:  "코딩연습14 - 소수 구하기"
excerpt: "코딩 연습 14"

categories:
  - CodingTest
tags:
  - Method
  - Mathmatics
last_modified_at: 2021-06-03T23:00:00-05:00
---

코딩 테스트 연습 열 네 번째,  
백준 알고리즘 9단계 "기본 수학 2" - 소수 구하기  
(문제 원문은 백준 알고리즘 1929번 참고)  
  
두 자연수 M와 N을 입력받은 다음, M이상 N이하 소수를 출력하면 된다.  
M이상 N이하의 소수는 반드시 하나 이상 있는 입력만 주어진다.  
한 줄에 하나씩, 증가하는 순서대로 소수를 출력한다.  

"에라토스테네스의 체"를 이용하였다.  
고대 그리스 수학자 에라토스테네스가 발견한 소수를 찾는 방법이다.  
알고리즘은,  
2부터 시작하여 소수는 true, 그 소수의 배수는 false 처리하여 true로 남아있는 수만 출력하게 된다.  

이번 문제에서 주의할 점이 하나 더 있었는데,  
N의 최대 수인 1,000,000을 size로 갖는 array를 main 안에 선언하니 문제가 발생했다. (Stack overflow)  
이렇게 size가 클 땐 전역변수로 선언하자! 잊지 말기!  

```cpp  
#include <iostream>
using namespace std;
int eratos[1000001]; //전역변수로 선언하기! (Stack Overflow 방지 목적)
int main(){
    int M,N,i,j;
    cin>>M>>N;
    for(i=0;i<1000001;i++) eratos[i]=0; //ALL TRUE
    eratos[0]=1; eratos[1]=1; //Not Prime Number
    for(i=2;i<=N;i++){
        if(eratos[i]==0){ //Prime Number
            for(j=2;j<(N/i)+1;j++){
                if(eratos[i*j]!=1) eratos[i*j]=1; //배수 False 처리
            }
        }
    }
    for(i=M;i<=N;i++){
        if(eratos[i]==0) cout<<i<<'\n';
    }
    
}
```