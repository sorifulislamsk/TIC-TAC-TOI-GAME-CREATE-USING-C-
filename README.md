# TIC-TAC-TOI-GAME-CREATE-USING-C++

 	#include<iostream>
	 using namespace std;
 
 	char arr[3][3]={'1','2','3','4','5','6','7','8','9'};
	 char turn ='X';
	 int row,column;
	 bool draw =false;
 
 	void display()
	{
	
 	system("cls");
	cout<<"\t Player1 [X] \n\t Player2 [O]\n\n";
	cout<<"\t\t     |     |     \n";
	cout<<"\t\t"<<  arr[0][0] <<"    | "<< arr[0][1]<<"   |  "<<arr[0][2]<<" \n";
	cout<<"\t\t-----|-----|-----\n";
	cout<<"\t\t     |     |     \n";
	cout<<"\t\t"<<  arr[1][0] <<"    | "<< arr[1][1]<<"   |  "<<arr[1][2]<<" \n";
	cout<<"\t\t     |     |     \n";
	cout<<"\t\t-----|-----|-----\n";
	cout<<"\t\t"<<  arr[2][0] <<"    | "<< arr[2][1]<<"   |  "<<arr[2][2]<< "\n";
    cout<<"\t\t     |     |     \n";
	}

	void player_turn()
	{
	
 	int choice;
	if(turn =='X')
	cout<<"\n\tPlayer1 [X] Turn : ";
	else if(turn =='O')
	cout<<"\n\tPlayer2 [O] Turn : ";
	cin>>choice;
	  switch(choice)
      {
        case 1: row=0; column=0; break;
        case 2: row=0; column=1; break;
        case 3: row=0; column=2; break;
        case 4: row=1; column=0; break;
        case 5: row=1; column=1; break;
        case 6: row=1; column=2; break;
        case 7: row=2; column=0; break;
        case 8: row=2; column=1; break;
        case 9: row=2; column=2; break;
        default:
            cout<<"Invalid Move";
        }
        
        if(turn=='X' && arr[row][column]!='X' && arr[row][column]!='O')
        {
        	arr[row][column]='X';
        	turn='O';
		}
		 else if(turn=='O' && arr[row][column]!='X' && arr[row][column]!='O')
        {
        	arr[row][column]='O';
        	turn='X';
		}
		else 
		{
		cout<<"Invalid Input!!\n Please Try Again";
		player_turn();
		}
		display();
	}

	bool gameover()
	{
    
    for(int i=0; i<3; i++)
    if(arr[i][0] == arr[i][1] && arr[i][0] == arr[i][2] || arr[0][i] == arr[1][i] && arr[0][i] == arr[2][i])
    return false;

    //checking the win for both diagonal

    if(arr[0][0] == arr[1][1] && arr[0][0] == arr[2][2] || arr[0][2] == arr[1][1] && arr[0][2] == arr[2][0])
    return false;

    //Checking the game is in continue mode or not
    for(int i=0; i<3; i++)
    for(int j=0; j<3; j++)
    if(arr[i][j] != 'X' && arr[i][j] != 'O')
    return true;

    //Checking the if game already draw
    draw = true;
    return false;
	}
	main()
	{
	
 	cout<<"\n\n    Tic  Tac  Toi Game"<<endl;
        while(gameover())
            {
	            display();
	            player_turn();
                gameover();
            }

    if(turn=='X' && draw ==false)
	cout<<"Player-2 [O] Wins!! Congratulations \n";
    if(turn=='O'  && draw ==false)
	cout<<"Player-1 [X] Wins!! Congratulations \n";	

    else cout<<"Game Draw!!"<<endl;	
	
	}
