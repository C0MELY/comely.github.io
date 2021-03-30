---
title:  "코딩연습4 - 빠른 A+B"
excerpt: "코딩 연습 4"

categories:
  - CodingTest
tags:
  - Basic
last_modified_at: 2021-03-29T23:50:00-05:00
---

코딩 테스트 연습 네 번째, 빠른 A+B  
그동안 코테 준비를 하면서 수많은 시간초과들을 이해하지 못 한 채 넘겼었다.  
오늘 그 이유를 알게 됐다.  
  
1. cin.tie(NULL)  
  >cin.tie(NULL)은 cin과 cout의 묶음을 풀어 줍니다.  
  >기본적으로 cin으로 읽을 때 먼저 출력 버퍼를 비우는데, 마찬가지로 온라인 저지에서는 화면에 바로 보여지는 것이 중요하지 않습니다.  
  >입력과 출력을 여러 번 번갈아서 반복해야 하는 경우 필수적입니다.  
  >(출처 : https://www.acmicpc.net/board/view/22716)  
  
    사용 방법은 간단하다.  
    아래와 같이 main 함수 시작할 때 작성해 주면 된다.  
  
    ```c++  
    int main(){  
      cin.tie(NULL);  //main 함수 안에 작성  
      return 0;  
    }  
    ```   
  
2. endl 대신 '\n'  
  >endl은 개행문자를 출력할 뿐만 아니라 출력 버퍼를 비우는 역할까지 합니다.  
  >그래서 출력한 뒤 화면에 바로 보이게 할 수 있는데, 그 버퍼를 비우는 작업이 매우 느립니다.  
  >게다가 온라인 저지에서는 화면에 바로 보여지는 것은 중요하지 않고 무엇이 출력되는가가 중요하기 때문에 버퍼를 그렇게 자주 비울 필요가 없습니다.  
  >그래서 endl을 '\n'으로 바꾸는 것만으로도 굉장한 시간 향상이 나타납니다.  
  >(출처 : https://www.acmicpc.net/board/view/22716)  
  
3. sync_with_stdio(false)
  >ios_base::sync_with_stdio(false)는 C와 C++의 버퍼를 분리합니다.  
  >이것을 사용하면 cin/cout이 더 이상 stdin/stdout과 맞춰 줄 필요가 없으므로 속도가 빨라집니다.  
  >단, 버퍼가 분리되었으므로 cin과 scanf, gets, getchar 등을 같이 사용하면 안 되고,  
  >cout과 printf, puts, putchar 등을 같이 사용하면 안 됩니다.  
  >(출처 : https://www.acmicpc.net/board/view/22716)  
  
    3번 내용은 적용하지 않고 제출해도 정답처리 됐다.  
    사용법은 1번과 동일한 듯 하다.  