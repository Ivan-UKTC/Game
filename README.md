int sizeX=600, sizeY=600;
float x = sizeX;
float y = random(0, sizeY);
float y2 = random(0, sizeY);
float y3 = random(0, sizeY);
float y4 = random(0, sizeY);
float y5 = random(0, sizeY);
float x2, x3, x4, x5;
boolean game_over = false;
PFont f;
void setup() {
  size(600, 600);
  background(255);
  f = createFont("Times New Roman", 25, true);
}
void randomrect(float rx, float ry, float rx2, float ry2, float rx3, float ry3, float rx4, float ry4,float rx5, float ry5) {
  fill(0);
  if (frameCount>10) {
    rect(rx2, ry2, 40, 40);
  }
  if (frameCount>40) {
    rect(rx3, ry3, 40, 40);
  }
    if (frameCount>60) {
    rect(rx4, ry4, 40, 40);
  }
  rect(rx, ry, 40, 40);
  if (frameCount>80) {
    rect(rx5, ry5, 40, 40);
  }
}

void gameover(float squarex, float squarey) {
  if (((mouseY>squarey) && (mouseY<squarey+40) && (squarex <= 80) && (squarex >= 0)) || ((mouseY+40>squarey) && (mouseY+40<squarey+40) && (squarex <= 80) && (squarex >= 0))) {
    textFont (f, 25);
    fill(255, 0, 0);
    text("GAME OVER", 140, 160);
    game_over= true;
  }
}
void draw() {
  if (game_over == false) { // if not game over do
    println(y, y2, y3, y4);
    background(255);
    noStroke();
    fill(200, 0, 0);
    rect(40, mouseY, 40, 40);
    x = x - 5;
    x2 = x2 -4;
    x3 = x3 -6;
    x4 = x4 -3;
    x5 = x5 -8;
    if ( x<  -40) {
      x = sizeX;
      y = random(0, sizeY);
    }
    if ( x2<  -40) {   
      x2 = sizeX;
      y2 = random(0, sizeY);
    }
    if ( x3<  -40) {
      x3 = sizeX;
      y3 = random(0, sizeY);
    }
    if ( x4<  -40) {
      x4 = sizeX;
      y4 = random(0, sizeY);      
    }
    if ( x5<  -40) {
      x5 = sizeX;
      y5 = random(0, sizeY);
    }
    randomrect(x, y, x2, y2, x3, y3, x4, y4, x5, y5); // draw square
    gameover(x, y);
    gameover(x2, y2);
    gameover(x3, y3);
    gameover(x4, y4);
    gameover(x5, y5);
  }
}
void mousePressed() { // if ckliked reset program
  if (mouseButton == LEFT) {
    if (game_over == true) { // if game over reset all
      x = x2 = x3 = x4 = x5 = sizeX;
      y = random(0, sizeY);
      y2 = random(0, sizeY);
      y3 = random(0, sizeY);
      y4 = random(0, sizeY);
      y5 = random(0, sizeY);
      game_over = false;
    }
  }
  if (mouseButton == RIGHT) { // if clicked exit program
    exit();
  }
}
