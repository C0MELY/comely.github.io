---
title:  "코딩연습11 - 단어의 개수"
excerpt: "코딩 연습 11"

categories:
  - CodingTest
tags:
  - Basic
  - String
last_modified_at: 2021-04-16T00:40:00-05:00
---

코딩 테스트 연습 열 한 번째,  
백준 알고리즘 7단계 "문자열" - 단어의 개수  
(문제 원문은 백준 알고리즘 1152번 참고)  
  
입력받은 문자열에 몇 개의 단어가 있는지 세는 문제.  
예를 들어,  
"The Curious Case of Benjamin Button"를 입력 받은 경우,  
출력값은 6이다.  
단, 문자열 앞/뒤로 공백이 있을 수 있고,  
단어는 공백으로 구분되어 있다.  
  
'공백'을 포함하여 입력을 받는 방법은,  
'getline'을 사용하는 것.  
입력받은 문자열의 크기는 'string' header를 추가해서 'length()' 함수를 사용하여 구했다.  

```cpp  
#include <string>  //string header 추가
int main() {
	string s;  //string형 변수 
	getline(cin, s); //getline으로 공백 포함한 입력 받기  
	for (i = 0; i < s.length(); i++) { //length() 함수로 문자열 size 구함.
		if (s[i] == ' ') count++;
	}
	count++;
	if (s[0] == ' ') count--; //맨 앞 공백 제외  
	if (s[s.length() - 1] == ' ') count--; //맨 뒤 공백 제외  
	cout << count;
}
```