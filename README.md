# 7DTEWY_translationer
I made it!!!!! / 와 이걸 내가 만들어냈다!!!

// 반대로 번역하는 기계 7DTEWY -> ENGLISH
#include <iostream>

using namespace std;

int main()
    
    // type words. only big-alpabet(s).
    // Worry the Max-longth of 7DTEWY. DISAPPEARED = disap.
    
{   
    
    // input place!!
    
    string word;
    cin>>word;
    int wordlength = word.length();
    string alpha[wordlength+10]; // 0, 1, 2, 3, 4 ,+ ~10
    for (int i=0;i<wordlength;i++) {
        alpha[i]=word.substr(i, 1); // 0, 1, 2, 3, 4.
    }
    
    // test place.
    
    //for (int i=0;i<5;i++) {
    //    cout << alpha[i] << '\n';
    //}

    // output place!!
    
    int key=0; // 이 수만큼 단어를 밀어야 한다.
    
    int omega[wordlength+10]; // 오메가, 이 배열에는 글자 번호를 넣는다. 왜인지는 몰라도 string인 alpha 변수에는 안 들어가기 때문.
    
    // 브루트 포스를 활용해야 한다.
    string input_everyalphawithzero[1+25+10] = {"__ERROR__","A","B","C","D","E","F","G","H","I","J","K","L","M","N","O","P","Q","R","S","T","U","V","W","X","Y","Z" };
    
    // 우선, 각각의 단어를 모두 이 단어와 비교하여 키를 뽑고 글자 순서를 받는다.
    for (int i=0;i<wordlength;i++) {
        for (int j=0;j<28;j++) {
            
            // cout <<i+1<<"번째_글자인_"<<alpha[i]<<"와"<<input_everyalphawithzero[j]<<"를_비교합니다"<<'\n'; // 테스트용
            
            if (alpha[i]==input_everyalphawithzero[j]) {
                
                // cout <<alpha[i]<<"와"<<j<<"번째 글자인"<<input_everyalphawithzero[j]<<"가 일치합니다"; // 테스트용
                
                key+=j; // 나중에 28로 나눈 나머지로 업데이트될 키
                omega[i]=j; // 해당 글자의 최초 글자 번호 수집
                cout<<omega[i]<<" "<<j;
                cout<<'\n';
                
            }
        } 
    }
    
    cout<<"Key:"<<key<<","<<key%26<<'\n'; // 테스트용
    int final_key=key%26;
    
    // 자, 키를 뽑고 기존 글자까지 가져왔다.
    // 이제 키만큼 모든 배열에 더하고 출력해보자.
    // 아자아자 화이자!!!
    
    //cout<<"~~수정전 테스트~~"<<'\n';
    //for (int i=0;i<4;i++) {
    //    cout<<omega[i]<<'\n';
    //}
    //cout<<"~~수정중~~"<<'\n';
    for (int i=0;i<wordlength;i++) {
        //cout<<(omega[i]+key%26)%26<<'\n';
        omega[i]=(omega[i]+final_key)%26;
    }
    
    //자, 이제 26으로 나눠진 최종키(변수는 그대로 key)를 각각 글자의 순서를 말하는 번호에 더해줬다.
    //이제 이 숫자를 다시 알파벳 (소문자)로 변환해서 다시 출력해야 한다.
    
    string output_everyalphawithzero[1+25+10] = {"__ERROR__","a","b","c","d","e","f","g","h","i","j","k","l","m","n","o","p","q","r","s","t","u","v","w","x","y","z" };
    // 이 시점에서, 인풋과 아웃풋용 알파벳 배열을 분리하였다. 만약 에러가 발생한다면 추가 조치 부탁한다.
    // 또다시 브루트 포스...
    for (int i=0;i<28;i++) {
        for (int j=0;j<wordlength;j++) {
            if (omega[j]==i) { // 숫자
            // cout<<i<<"equals" << omega[j] <<'\n';
            alpha[j]=output_everyalphawithzero[i];
            }
        }
        
    }
    
    for (int i=0;i<wordlength;i++) {
        cout<<alpha[i];
    }


}// 끝!
