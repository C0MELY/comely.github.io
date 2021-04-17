---
title:  "코딩연습12 - 그룹 단어 체커"
excerpt: "코딩 연습 12"

categories:
  - CodingTest
tags:
  - Basic
  - String
last_modified_at: 2021-04-17T15:07:00-05:00
---

코딩 테스트 연습 열 두 번째,  
백준 알고리즘 7단계 "문자열" - 그룹 단어 체커  
(문제 원문은 백준 알고리즘 1316번 참고)  
  
그룹 단어란 단어에 존재하는 모든 문자에 대해서 각 문자가 연속해서 나타나는 경우만을 말한다.  
예를 들면, ccazzzzbb는 c, a, z, b가 모두 연속해서 나타나고, kin도 k, i, n이 연속해서 나타나기 때문에 그룹 단어이지만, aabbbccb는 b가 떨어져서 나타나기 때문에 그룹 단어가 아니다.  
  
지난 번에 공부했던 getline을 활용해 문제를 풀었다.  
단, 주의할 점은 'cin'과 'getline'을 같이 사용하고 싶으면 cin이후 buffer flush가 필요하다는 점.  
-. cin: input을 space/tab/enter로 구분. 단, 버퍼에는 공백문자를 그대로 갖고 있음.  
-. getline : input을 enter로만 구분. enter까지 한 문장을 읽고 버퍼에 enter를 남기진 않음.  
  
즉, 이번 문제처럼 테스트 할 단어 개수를 먼저 cin으로 입력 받은 후 단어들을 getline으로 받고자 할 경우,  
cin 이후 반드시 buffer flush를 해주어야 한다.  
아니면 cin입력으로 인해 buffer에는 enter가 남아있고, 다음 getline에서 그 enter를 읽게 되므로  
첫번째 getline에서 아무것도 읽지 않게 된다.  

```cpp  
#include <string>  //string header 추가
int main() {
	string s;  //string형 변수 
	cin >> t;  //cin 입력 시 buffer에 enter남음
    cin.ignore();  //buffer flush for getline
    for (t;t>0;t--){
        fill_n(aph,26,0);
        getline(cin,s);  //getline input    
        for(i=0;i<s.length();i++){
            if(aph[s[i]-97]==0) aph[s[i]-97]=i+1;
            else if(aph[s[i]-97]==i) aph[s[i]-97]=i+1;
            else break;
        }
        if(i==s.length()) count++;
    }
	cout << count;
}
```