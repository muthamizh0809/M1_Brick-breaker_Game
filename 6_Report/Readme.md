# Software Implementation
### A. Paddle control
The paddle will be controlled by a mouse. The mouse’s moving to left or right will
correspond to the paddle’s movement. The moving speed will also relate to how fast we
move the mouse. By clicking on the left key, the paddle can launch extra balls as bonus
in higher level rounds.
Software will be used to keep track of the current status of the paddle, to see if it’s
under special status, like elongated, shortened, multi-ball launching, or fireball
launching (fireball can destroy all bricks in its trajectory).
### B. Bouncing ball
Software will be used to assigning new locations of the ball as the ball bounce around
walls (edges of the screen), bricks and paddle. When the angle of incidence changes, the
angle of reflection changes too.
We will also need a status tracker to see whether the ball is in regular status or fireball
status. Also, we implement the game with player have multiple lives.
### C. Bricks
For each brick, the software will have a status tracker. The tracker will record how many
breaks needed to break a specific brick (different types of brick may need 1 or 2 or 3
times of breaking before they are destroyed), what special effect they have and when to
release, and to display or not (remaining or destroyed).
### D. Score counting
Software will count for the scores and calculate the bonus points gotten by how many
bricks broken in a row and other effects. The score will be displayed on the up right
corner of the screen.
##  Milestones Plan
### Milestone 1:
Display bricks, paddle, and ball in sprites. The ball should be bouncing when there are no
obstacles. The paddle should move left and right controlled by the keyboard. If time permits,
attach a sound effect when the ball hits the wall.
### Milestone 2:
Hardware part should be finished by then so we don’t have to make those files every time.
Bouncing should work for most bricks and paddle, while it could be tricky when the ball hits the
corner. More sound effects will be added, making it a generally playable game.
### Milestone 3:
While some of us trying to figures out the math in irregular bouncing scenarios on the paddle
