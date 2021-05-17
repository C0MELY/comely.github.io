---
title:  "코딩연습13 - 큰 수 A+B"
excerpt: "코딩 연습 13"

categories:
  - CodingTest
tags:
  - Mathmatics
  - String
  - Stack
last_modified_at: 2021-05-17T23:00:00-05:00
---

코딩 테스트 연습 열 세 번째,  
백준 알고리즘 8단계 "기본 수학 1" - 큰 수 A+B  
(문제 원문은 백준 알고리즘 10757번 참고)  
  
두 정수 A와 B를 입력받은 다음, A+B를 출력하면 되는 간단해 보이는 문제이다.  
단, 입력받는 A와 B의 size가 매우 클 뿐.  
최대 10^10000까지 받을 수 있다.  
  
이렇게 큰 수는 C++에서는 간단하게 정수형으로 받을 수 없다. (지원하는 자료형이 없다.)  
따라서 String 형태로 입력을 받았다.  
연산은 Stack을 활용하여 진행했다.  
  
String.length() : String의 길이 반환  
String.at(i) : i번째 원소 반환  
Stack.push(i) : Stack에 i를 push  
Stack.top() : Stack의 마지막 원소 반환  
Stack.pop() : Stack의 마지막 원소 제거  

```cpp  
  #include <iostream>
  #include <stack>
  #include <string>
  using namespace std;
  int main() {
    int i,carry=0;
    string a, b, c;
    cin >> a >> b;
    stack<int> first, second, answer;
    if (b.length() > a.length()) {
      c = b;
      b = a;
      a = c; //a is longer
    }
    for (i = 0; i < a.length(); i++) {
      first.push(a.at(i)-'0');
    }
    for (i = 0; i < b.length(); i++) {
      second.push(b.at(i) - '0');
    }

    while (!second.empty()) {
      i = first.top() + second.top();
      if (carry == 1) i += 1;
      if (i >= 10) {
        carry = 1; i -= 10;
      }
      else carry = 0;
      answer.push(i);
      first.pop();
      second.pop();
    }
    while (!first.empty()) {
      i = first.top();
      if (carry == 1) i += 1;
      if (i >= 10) {
        carry = 1; i -= 10;
      }
      else carry = 0;
      answer.push(i);
      first.pop();
    }
    if (carry == 1) answer.push(1);
    while (!answer.empty()) {
      cout << answer.top();
      answer.pop();
    }
  }
  }
```