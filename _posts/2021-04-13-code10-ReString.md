---
title:  "코딩연습10 - 문자열 반복"
excerpt: "코딩 연습 10"

categories:
  - CodingTest
tags:
  - Basic
  - Array
  - CString
last_modified_at: 2021-04-13T23:50:00-05:00
---

코딩 테스트 연습 열 번째,  
백준 알고리즘 7단계 "문자열" - 문자열 반복  
(문제 원문은 백준 알고리즘 2675번 참고)  
  
입력받은 문자열의 각 문자를 주어진 수만큼 반복하여 출력하는 문제이다.  
예를 들어,  
"3 ABC"를 입력 받은 경우,  
출력값은 "AAABBBCCC"가 된다.  
  
입력받은 문자열의 길이를 알고 싶어서 'strlen()' 함수를 사용했다.  
함수 사용을 위해 필요한 header는 <cstring>이다.  

```cpp  
#include <cstring>
int main(){
    int t,r,i,j,k;
    char s[20];
    cin>>t;
    for(i=0;i<t;i++){
        cin>>r;
        cin>>s; //문자열 한번에 입력 받음  
        for(j=0;j<strlen(s);j++) { //문자열s 길이만큼 반복  
            for(k=0;k<r;k++) cout<<s[j];
        }
        cout<<'\n';
    }
}
```