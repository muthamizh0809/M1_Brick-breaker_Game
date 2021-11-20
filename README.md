# M1_Brick-breaker_Game
###  Introduction
The goal of this ENSC 452 course is to implement a program on ZedBoard with
both Xilinx's system software and hardware. We decide our project to be a video game
similar to the brick breaker. In our game, the user can move the bar at the bottom of the
screen left and right in order to bounce the movable ball up and try to hit the bricks.
Once the ball hit any brick, the brick will be downgraded and eventually wiped out. We
will split our job into 6 milestones and use Agile methodology to accept greater
flexibility and to get higher efficiency. Each part will be tested by a specific test plan to
ensure the completeness.
###  Background
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
3
This game connects to a standard keyboard to get user input and use VGA port
to display the whole video screen. If we have enough time, we will play audio and make
sound synchronous to break a brick. And try to use the mouse to control the paddle.
