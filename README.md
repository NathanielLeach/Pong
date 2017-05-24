# Pong
My version of pong
//Nathaniel Leach
int radius= 20;
int ballx = 800;
int bally = 450;
float speed = 8;
int direction = 1;
int direction2 = 1;
int score = 0;
int s = millis();
PFont font;

void setup() { 
fullScreen();

}

void draw() {
  
smooth();
background(0);
  
font = loadFont("ArialMT-30.vlw");
textFont(font);
text("Time:", 5, 40);//timer
text(s++/50, 100, 40);
text("Score:", 5, 80);//score
text(score, 100, 80);
  
 if ((ballx > width - radius) || (ballx < radius)){//ball bounce
   direction = -direction;
 }
 
 if(bally < radius){
   direction2 = -direction2;//ball bounce
 }
 
 if ((ballx > mouseX - 75) && (ballx < mouseX + 75)) {//paddle bounce
   if ((bally > height - (10 + radius)) && (bally < height)){
     direction2 = -direction2;
     speed += 2;
     score ++;
 }
}

ballx += speed * direction;//ball
bally += speed * direction2;
ellipse(ballx + speed, bally + speed, radius, radius);
  
rectMode(CENTER);
fill(0, 100, 255);
rect(mouseX, height - 10, 150, 20);//paddle
  
 if (bally > height) {
   background(0, 100, 255);
   fill(255, 50, 0);
   text("Game Over", .5 * width - 50, .5 * height);
  }

}
