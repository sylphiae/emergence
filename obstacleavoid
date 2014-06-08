//Obstacle switches are connected to these pins on the Arduino
const int leftObstacle = 1;
const int rightObstacle = 2;
const int leftEdge = 6;
const int rightEdge = 7;
int leftObstacleDetect = 0;
int rightObstacleDetect = 0;
int leftEdgeDetect = 0;
int rightEdgeDetect = 0;
//motor A connected between A01 and A02 on driver board
//motor B connected between B01 and B02 on driver board
int STBY = 10; //standby
//Motor A connections to driver board
int PWMA = 3; //Speed control
int AIN1 = 9; //Direction
int AIN2 = 8; //Direction
//Motor B connections to driver board
int PWMB = 5; //Speed control
int BIN1 = 11; //Direction
int BIN2 = 12; //Direction
void setup(){
  //Obstacle setup
  pinMode(leftObstacle, INPUT);
  pinMode(rightObstacle, INPUT);
  pinMode(leftEdge, INPUT);
  pinMode(rightEdge, INPUT);
 
  //Motor setup
  pinMode(STBY, OUTPUT);
  pinMode(PWMA, OUTPUT);
  pinMode(AIN1, OUTPUT);
  pinMode(AIN2, OUTPUT);
  pinMode(PWMB, OUTPUT);
  pinMode(BIN1, OUTPUT);
  pinMode(BIN2, OUTPUT);
}
void loop(){
 
    leftObstacleDetect = digitalRead(leftObstacle);
    rightObstacleDetect = digitalRead(rightObstacle);
    leftEdgeDetect = digitalRead(leftEdge);
    rightEdgeDetect = digitalRead(rightEdge);
   
   // Check if obstacles are detected
   // If they are, the detection state is HIGH:
   if (leftObstacleDetect == HIGH) {        
      //Move back...
      move(1, 128, 0); //motor 1, half speed, right
      move(2, 128, 0); //motor 2, half speed, right
      delay(1000);
      stop();
      delay(250);
     
      //...then turn
      move(1, 128, 1); //motor 1, half speed, left
      move(2, 128, 0); //motor 2, half speed, right
      delay(2000);
      stop();
      delay(250);
   }
 
     else if (rightObstacleDetect == HIGH) {        
      //Move back...
      move(1, 128, 0); //motor 1, half speed, right
      move(2, 128, 0); //motor 2, half speed, right
      delay(1000);
      stop();
      delay(250);
     
      //...then turn
      move(1, 128, 0); //motor 1, half speed, right
      move(2, 128, 1); //motor 2, half speed, left
      delay(2000);
      stop();
      delay(250);
   }
   
     else if (leftEdgeDetect == HIGH) {        
      //Move back...
      move(1, 128, 0); //motor 1, half speed, right
      move(2, 128, 0); //motor 2, half speed, right
      delay(1000);
      stop();
      delay(250);
     
      //...then turn
      move(1, 128, 1); //motor 1, half speed, left
      move(2, 128, 0); //motor 2, half speed, right
      delay(2000);
      stop();
      delay(250);
   }
     else if (rightEdgeDetect == HIGH) {        
      //Move back...
      move(1, 128, 0); //motor 1, half speed, right
      move(2, 128, 0); //motor 2, half speed, right
      delay(1000);
      stop();
      delay(250);
     
      //...then turn
      move(1, 128, 1); //motor 1, half speed, left
      move(2, 128, 0); //motor 2, half speed, right
      delay(2000);
      stop();
      delay(250);
   }
  
   else {
   }
  move(1, 255, 1); //motor 1, full speed, left
  move(2, 255, 1); //motor 2, full speed, left
}

// Motor Driver board setup
void move(int motor, int speed, int direction){
//Move specific motor at speed and direction
//motor: 0 for B 1 for A
//speed: 0 is off, and 255 is full speed
//direction: 0 clockwise, 1 counter-clockwise
  digitalWrite(STBY, HIGH); //disable standby
  boolean inPin1 = LOW;
  boolean inPin2 = HIGH;
  if(direction == 1){
    inPin1 = HIGH;
    inPin2 = LOW;
  }
  if(motor == 1){
    digitalWrite(AIN1, inPin1);
    digitalWrite(AIN2, inPin2);
    analogWrite(PWMA, speed);
  }else{
    digitalWrite(BIN1, inPin1);
    digitalWrite(BIN2, inPin2);
    analogWrite(PWMB, speed);
  }
}
void stop(){
//enable standby 
  digitalWrite(STBY, LOW);
}
