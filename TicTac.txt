#include <iostream>
using namespace std;

class TicTac{
  char arr[9]={ '1', '2', '3', '4', '5', '6', '7', '8', '9' };
  char Data[9]={ '1', '2', '3', '4', '5', '6', '7', '8', '9' };
  int arrs[9];
  char start;
  bool begin=true;
  bool turn=true;
  int num=0;
  int turnCounter;
  
  
  public:
  
  TicTac(){
      for(int i=0;i<9;i++){
          arrs[i]=i+1;
      }
      
      
  }
  
  void Start(){
     
     do{
         
          system("clear");
          
          turnCounter=0;
      int index=0;
      cout<<endl<<endl;
      for(int i=0;i<3;i++){
          for(int j=0;j<3;j++){
                arr[index]=Data[index];
                cout<<"\t\t\t"<<arr[index];
                index++;
          }
          cout<<endl<<endl<<endl;
      }
      cout<<endl<<"This is the rule of the game"<<endl;
      cout<<endl<<"Click y to continue"<<endl;
      cin>>start;
      if(start=='y'||start=='Y'){
          begin=StartGame();
      }else{
          break;
      }
        
      }while(begin);
      
      
  }
  
  bool StartGame(){
      bool decide=true;
      do{
      system("clear");
         int index=0;
      cout<<endl<<endl;
      for(int i=0;i<3;i++){
          for(int j=0;j<3;j++){
                cout<<"\t\t\t"<<arr[index];
                index++;
          }
          cout<<endl<<endl<<endl;
      } 
          decide=GameBoardMarker();
      }while(decide);
    return decide;
      
  }
  
  bool GameBoardMarker(){
      char mark;
      bool ch=true;
      if(turnCounter<9){
      cout<<"\t\t\tEnter the corresponding number"<<endl;
      if(turn){
          cout<<"Player 1 turn is here"<<endl;
          cin>>num;
          for(int i=0;i<9;i++){
              if(arrs[i]==num){
                  mark='X';
                  arr[i]=mark;
                  if(turnCounter>2){
                  ch=GameDecider(mark);
                  if(ch==false){
                      return false;
                  }
                  }
              }
          }
          turn=false;
      }else{
           cout<<"Player 2 turn is here"<<endl;
          cin>>num;
          for(int i=0;i<9;i++){
              if(arrs[i]==num){
                  mark='O';
                  arr[i]=mark;
                  if(turnCounter>3){
                  ch=GameDecider(mark);
                  if(ch==false){
                      return false;
                  }
                  }
              }
          }
          turn=true;
      }
      
      turnCounter++;
      return true;
  }else{
      turn=true;
      return false;
  }
  }
  
  bool WinnerDeclare(){
      system("clear");
          cout<<"\t\t\tPlayer "<<turn<<" Win"<<endl;
          cout<<endl<<"\t\t\tDo want to continue the game(y/n)";
          cin>>start;
          if(start=='y'||start=='Y'){
              Start();
              return true;
          }else{
             system("clear");
             return false;
          }
          
  }
  
  
  bool GameDecider(char mark){
      int turns=0;
      bool ch=true;
      if(mark=='X'){
         turn=1; 
      }else if(mark=='O'){
          turn=2;
      }
      if(arr[0]==mark&&arr[1]==mark&&arr[2]==mark){
          ch=WinnerDeclare();
      }else if(arr[4]==mark&&arr[5]==mark&&arr[3]==mark){
          ch=WinnerDeclare();
      }else if(arr[7]==mark&&arr[8]==mark&&arr[6]==mark){
          ch=WinnerDeclare();
      }else if(arr[0]==mark&&arr[3]==mark&&arr[6]==mark){
          ch=WinnerDeclare();
      }else if(arr[1]==mark&&arr[4]==mark&&arr[7]==mark){
          ch=WinnerDeclare();
      }else if(arr[2]==mark&&arr[5]==mark&&arr[8]==mark){
          ch=WinnerDeclare();
      }else if(arr[0]==mark&&arr[4]==mark&&arr[8]==mark){
          ch=WinnerDeclare();
      }else if(arr[2]==mark&&arr[4]==mark&&arr[6]==mark){
          ch=WinnerDeclare();
      }
      
      return ch;
  }
  
~TicTac(){
    system("clear");
    cout<<"Game Over";
}
  
    
};


int main(){
    TicTac t;
    t.Start();
    return 0;
}