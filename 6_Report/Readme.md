# Introduction
In our game, the user can move the bar at the bottom of the
screen left and right in order to bounce the movable ball up and try to hit the bricks.
Once the ball hit any brick, the brick will be downgraded and eventually wiped out. We
will split our job into 6 milestones and use Agile methodology to accept greater
flexibility and to get higher efficiency. Each part will be tested by a specific test plan to
ensure the completeness.
# Background
Breakout is a traditional arcade game developed and published by Atari, Inc. And
Brick Breaker is a clone of Breakout. The game consists of 50 bricks on the top of the
screen, a flying ball and a movable paddle on the bottom of the screen. The paddle is
controlled by the user to move either left or right. Player need to use this paddle to
prevent the ball from falling out of the screen. Three unbreakable walls on the side of
the screen are used to deflect the ball. The collision between the ball and bricks can
make brick downgraded or disappear. The speed of ball gradually goes up with time.
The level of bricks is also upgraded as time goes on, which means it requires more than
one collision to smash the upgraded bricks. The game will continuously proceed as long
as the ball is not falling out of the screen. During playing, the user is able to pause the
game and continuous again.
This game connects to a standard keyboard to get user input and use VGA port
to display the whole video screen. If we have enough time, we will play audio and make
sound synchronous to break a brick. And try to use the mouse to control the paddle.
# Benefits
brick breaker Game offers a few benefits. Here are just a few of them:


### Prepares for more complex games
It prepares a person for more complex games because they have to think of multiple things at one time.

### Mannerism
It helps one to learn how to follow rules and take turns.

### Concentration
It can help to improve a person's concentration as well as strategic thinking
# Features
Brick Breaker (platformer) is a Breakout clonewhich the player must smash a wall of bricks by deflecting a bouncing ball with a paddle. The paddle may move horizontally and is controlled with the BlackBerry's trackwheel, the computer's mouse or the touch of a finger (in the case of touchscreen).
# SWOT analysis
stregth:It helps with creative thinking.Improve concentration.

Weakeness:Can be addictive.Works only with keyboard.

Opportunity:Enhanced problem solving skills.Prepare for more complex games.

Threat:Can be somewhat demotivating because it is not easy to complete the level.
# 4W's and 1H
Who:someone who is interested to play the game.

What:this game improves a player concentration.

When:this game can be played whenever your feeling board.

Where:A variety of websites make a simple brick breaker game available.

How:When the ball start to move the game is also started.
# shematic diagram


![download123](https://user-images.githubusercontent.com/94265667/143014701-4ba6e1a4-71d2-42f4-bff3-809ee9ddbcee.png)



# behavioural diagram


![images (2)](https://user-images.githubusercontent.com/94265667/143015472-72ca3193-e9b1-4500-9bcb-a732a7492ffa.jpeg)


# Source code
#include<iostream>
#include<conio.h>
#include<dos.h>
#include<stdlib.h>
#include<string.h>
#include <windows.h>
#include <time.h>

#define SCREEN_WIDTH 52
#define SCREEN_HEIGHT 20

#define MINX 2
#define MINY 2
#define MAXX 49
#define MAXY 19

using namespace std;
 
HANDLE console = GetStdHandle(STD_OUTPUT_HANDLE);
COORD CursorPosition;

int bricks[24][2] = {
						{2,7},{2,12},{2,17},{2,22},{2,27},{2,32},{2,37},{2,42},
					  	{4,7},{4,12},{4,17},{4,22},{4,27},{4,32},{4,37},{4,42},
					  	{6,7},{6,12},{6,17},{6,22},{6,27},{6,32},{6,37},{6,42}
					};

int visibleBricks[24] = {1,1,1,1, 1,1,1,1, 1,1,1,1, 1,1,1,1, 1,1,1,1, 1,1,1,1};
int sliderPos[2] = {18,22}; 
int ballPos[2] = {17,26}; 
int startBall = 0;
int dir = 1; 
int bricksLeft = 24;
int win = 0;
int lose = 0;

void gotoxy(int x, int y)
{
	CursorPosition.X = x;
	CursorPosition.Y = y;
	SetConsoleCursorPosition(console, CursorPosition);
}

void setcursor(bool visible, DWORD size) 
{
	if(size == 0)
	{
		size = 20;	
	}
	CONSOLE_CURSOR_INFO lpCursor;	
	lpCursor.bVisible = visible;
	lpCursor.dwSize = size;
	SetConsoleCursorInfo(console,&lpCursor);
}

void drawBorder(){
	gotoxy(0,0);cout<<"----------------------------------------------------";
	gotoxy(0,SCREEN_HEIGHT);cout<<"----------------------------------------------------";
	
	for(int i=0; i<SCREEN_HEIGHT; i++){
		gotoxy(0,i); cout<<"|";
		gotoxy(SCREEN_WIDTH,i); cout<<"|";
	}
}

void drawBricks(){
	for( int i=0; i<24; i++){
		if( visibleBricks[i] == 1 ){ 
			gotoxy(bricks[i][1], bricks[i][0]);
			cout<<"±±±±"; 
		}
	}
}

void ballHitSlider(){
	if( ballPos[1]>=sliderPos[1] && ballPos[1]<=sliderPos[1]+8){
		if( ballPos[0] == sliderPos[0]-1 ){
			if( dir == 3 ) 
				dir = 2;
			else if( dir == 4 )
				dir = 1;
		}
	}
}

void ballHitBrick(){
	for( int i=0; i<24; i++){
		if(visibleBricks[i]==1){
			if( ballPos[1]>=bricks[i][1] && ballPos[1]<=bricks[i][1]+8){
				if( ballPos[0] == bricks[i][0] ){
					visibleBricks[i] = 0;
					bricksLeft--;
				}
			}
		}
	}
}

void play(){
	while(1){
		system("cls");
		drawBricks();
		drawBorder();

		gotoxy(sliderPos[1],sliderPos[0]);
		cout<<"±±±±±±±±±";

		gotoxy(ballPos[1],ballPos[0]);
		cout<<"0";
 
		if(kbhit()){
			char ch = getch();
			if( ch=='d'||ch=='D'|| ch==77 ){
				if(sliderPos[1] < 44)
					sliderPos[1] = sliderPos[1]+2;
			} 
			if( ch=='a'||ch=='A'|| ch==75 ){
				if(sliderPos[1] > 2)
					sliderPos[1] = sliderPos[1]-2;
			} 
			if(ch==32){
				startBall = 1;
			} 
			if(ch==27){
				break;
			}
		}
		
		if( startBall == 1 ){
			if( dir == 1) { 
				ballPos[0] = ballPos[0] - 1;
				ballPos[1] = ballPos[1] + 2;
				if( ballPos[1] > MAXX ){
					dir = 2;
				}  
				else if( ballPos[0] < MINY ){
					dir = 4;
				}   
			}
			else if( dir == 2) {
				ballPos[0] = ballPos[0] - 1;
				ballPos[1] = ballPos[1] - 2;
				if( ballPos[0] < MINY ){
					dir = 3;
				}  
				else if( ballPos[1] < MINX  ){
					dir = 1;
				}   
			}
			else if( dir == 3) { 
				ballPos[0] = ballPos[0] + 1;
				ballPos[1] = ballPos[1] - 2;
			  
				if( ballPos[0] > MAXY ){
					lose = 1;
					break;
				}  
				else if( ballPos[1] < MINX  ){
					dir = 4;
				}    
			}
			else if( dir == 4) {
				ballPos[0] = ballPos[0] + 1;
				ballPos[1] = ballPos[1] + 2;  
				if( ballPos[1] > MAXX ){
					dir = 3;
				} 
				else if( ballPos[0] > MAXY ){
					lose = 1;
					break;
				}
			}

			ballHitSlider();
		}
		
		ballHitBrick();
	
		if( bricksLeft == 0){
			win = 1;	
			break;
		}		

		Sleep(30);
	}
	
	if( lose == 1){
		system("cls");
		
		gotoxy(10,5); cout<<" --------------------- "; 
		gotoxy(10,6); cout<<" |     YOU LOSE      | "; 
		gotoxy(10,7); cout<<" --------------------- "; 			

		gotoxy(10,9); cout<<"Press any key to go back to Menu."; 	
		getch(); 
	}

	if( win == 1){
		system("cls");
		gotoxy(10,5); cout<<" --------------------- "; 
		gotoxy(10,6); cout<<" |     YOU WIN       | "; 
		gotoxy(10,7); cout<<" --------------------- "; 			

		gotoxy(10,9); cout<<"Press any key to go back to Menu.";
		getch(); 	  			 
	}
}

void instructions(){
	
	system("cls");
	cout<<"Instructions";
	cout<<"\n----------------";
	cout<<"\n1. Use 'a' key to move slider to left";
	cout<<"\n2. Use 'd' key to move slider to right";
	cout<<"\n3. Press spacebar to start game";
	cout<<"\n\nPress any key to go back to menu";
	getch();
}

int main()
{
	setcursor(0,0);  
	
	do{
		system("cls");
		gotoxy(10,5); cout<<" -------------------------- "; 
		gotoxy(10,6); cout<<" |     BRICK BREAKER      | "; 
		gotoxy(10,7); cout<<" --------------------------";
		gotoxy(10,9); cout<<"1. Start Game";
		gotoxy(10,10); cout<<"2. Instructions";	 
		gotoxy(10,11); cout<<"3. Quit";
		gotoxy(10,13); cout<<"Select option: ";
		char op = getche();
		
		if( op=='1') play();
		else if( op=='2') instructions();
		else if( op=='3') exit(0);
		
	}while(1);

	play();

	cout<<endl<<endl;	
	return 0;
}
	
	# TEST PLAN:

## Table no: High level test plan

| **Test ID** | **Description**                                              | **Exp I/P** | **Exp O/P** | **Actual Out** |**Type Of Test**  |    
|-------------|--------------------------------------------------------------|------------|-------------|----------------|------------------|
|  H_01       |               Start game                                               | Success             |    Success   |    Pass        | Requirement based |
|  H_02       |            Instruction                                                  | Success             | Success            |       Pass         |Scenario based    |
|  H_03       |           Quit                                                   |  Success            |  Success           |  Pass              |Boundary based    |

## Table no: Low level test plan

| **Test ID** | **Description**                                              | **Exp IN** | **Exp OUT** | **Actual Out** |**Type Of Test**  |    
|-------------|--------------------------------------------------------------|------------|-------------|----------------|------------------|
|  L_01       |  Basic UI display                                                            |Success            | Success            | Pass               |Requirement based |
|  L_02       |     Display data                                                         |  Success          |  Success           |  Pass              |Scenario based    |
|  L_03       |         No                                                     |    No        |   No          |    No            |Boundary based    |

	

	   # Before stating


![images 23](https://user-images.githubusercontent.com/94265667/143164905-53b22805-bb9f-4d63-97a2-767e30784ff1.jpeg)


            # After stating
            
            
![unnamed 1](https://user-images.githubusercontent.com/94265667/143164292-b1c3e50b-6240-47fb-b2e9-c861ff0858bb.png)
