---
title:  "코딩연습1 - 인형뽑기(카카오 2019 겨울 인턴십)"
excerpt: "코딩 연습 1"

categories:
  - CodingTest
tags:
  - stack
last_modified_at: 2021-03-09T23:23:00-05:00
---

코딩 테스트 연습 첫 번째,  
카카오 2019 겨울 인턴십 채용 1번 문제.  
(문제 원문은 카카오 Tech Blog 참고)  
  
카카오 코딩테스트는 프로그래머스를 이용하므로 Vector 사용법을 익히는 것이 필수이다.  
코드 제출 후 C++의 stack 라이브러리를 include 하여 사용해도 된다는 것을 알았다.  
다음에는 stack 라이브러리를 사용해 봐야겠다.   
  
stack 라이브러리 없이 vector로만 구현하였고,  
여기서 사용한 function은 아래와 같다.  
  
v.push_back() : vector의 마지막에 원소 삽입  
v.pop_back() : vector의 마지막 원소 삭제  
v.back() : vector의 마지막 원소 참조  
v.empty() : vector의 size가 0인지 확인  
v.size() : vector의 size (vector가 가진 원소 수) 반환  
  
추가로, 새로운 vector를 선언할 때  
2차원 vector를 선언하기 위해 size를 지정해 주었다.  
아래 코드에서 "vector<vector<int>> dolls(board.size());" 부분이 이에 해당한다.  
board.size()를 지정하지 않았을 경우, error 발생하며 프로그램이 실행되지 않는다.  
  
  
***  
int solution(vector<vector<int>> board, vector<int> moves) {
    vector<vector<int>> dolls(board.size()); //board data trans
    vector<int> basket; //뽑은 인형 저장용 stack

    for (i=board.size()-1;i>=0;i--){
        for(j=0;j<board[0].size();j++){
            if(board[i][j]!=0) dolls[j].push_back(board[i][j]);
        }
    }

    for(i=0;i<moves.size();i++){
        d_point=moves[i]-1;
        if(dolls[d_point].empty())  continue; //해당 칸에 뽑을 인형 없으면 아무 동작도 수행하지 않음
        if(basket.empty()) basket.push_back(dolls[d_point].back()); //아직 뽑은 인형 없으면 무조건 push
        else{
            if(basket.back()==dolls[d_point].back()) {
                answer=answer+2;
                basket.pop_back();
            }
            else basket.push_back(dolls[d_point].back());
        }
        dolls[d_point].pop_back();
    }
}