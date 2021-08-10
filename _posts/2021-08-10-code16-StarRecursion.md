---
title:  "코딩연습16 - 별 찍기 - 10"
excerpt: "코딩 연습 16"

categories:
  - CodingTest
tags:
  - Recursion
last_modified_at: 2021-08-10T23:00:00-05:00
---

코딩 테스트 연습 열 여섯 번째,  
백준 알고리즘 10단계 "재귀" - 별 찍기 - 10  
(문제 원문은 백준 알고리즘 2447번 참고)  
  
한 동안 소홀했던 알고리즘 풀기를 다시 시작하며,  
재귀 함수 짜는 법을 고민하게 했던 문제.  
재귀적인 패턴으로 별을 찍는 문제를 기록한다!  
  
문제:  
N이 3의 거듭제곱(3, 9, 27, ...)이라고 할 때, 크기 N의 패턴은 N×N 정사각형 모양이다.  
크기 3의 패턴은 가운데에 공백이 있고, 가운데를 제외한 모든 칸에 별이 하나씩 있는 패턴이다.  
```
***  
* *  
***  
```
N이 3보다 클 경우, 크기 N의 패턴은 공백으로 채워진 가운데의 (N/3)×(N/3) 정사각형을 크기 N/3의 패턴으로 둘러싼 형태이다.  

입력:  
첫째 줄에 N이 주어진다.  
N은 3의 거듭제곱이다.  
즉 어떤 정수 k에 대해 N=3k이며, 이때 1 ≤ k < 8이다.  

출력:  
첫째 줄부터 N번째 줄까지 별을 출력한다.  

----

고민 Point :  
재귀를 어디서부터 어떻게 쓰면 좋을까 고민했다.  
특별한 알고리즘이나 수학 기법은 사용하지 않았다.  
아래 코드 전문 첨부한다!  

```cpp  
#include <iostream>
using namespace std;
char arr[6561][6561];  //가능한 최대 size 전역변수 선언.
void sleft(int x, int y, int size){ //left stars copy
    int i,j;
    for(i=x;i<x+size;i++){
        for(j=y;j<y+size;j++){
            arr[i][j]=arr[i][j-size];
        }
    }
}
void sup(int x, int y, int size){ //up stars copy
    int i,j;
    for(i=x;i<x+size;i++){
        for(j=y;j<y+size;j++){
            arr[i][j]=arr[i-size][j];
        }
    }
}
void star(int N){
    if(N/3!=3) star(N/3); //좌상단 패턴 채우기  
    sleft(0,N/3,N/3); sleft(0,N/3*2,N/3);
    sup(N/3,0,N/3); sup(N/3,N/3*2,N/3);
    sup(N/3*2,0,N/3); sleft(N/3*2,N/3,N/3); sup(N/3*2,N/3*2,N/3);
}
int main(){
    int N,i,j;
    cin>>N;
    for(i=0;i<N;i++) for(j=0;j<N;j++) arr[i][j]=' '; //빈칸으로 Initialize
    arr[0][0]='*'; arr[0][1]='*'; arr[0][2]='*';
    arr[1][0]='*'; arr[1][1]=' '; arr[1][2]='*';
    arr[2][0]='*'; arr[2][1]='*'; arr[2][2]='*';
    if(N/3!=1) star(N); //첫 3x3 만들어놓고, 왼쪽 혹은 위쪽 복사하는 방식.
    
    for(i=0;i<N;i++) { for(j=0;j<N;j++) cout<<arr[i][j]; cout<<'\n'; } //출력
}
```