# obstacle-avoiding-robot-code-

#include <AFMotor.h>
AF_DCMotor motor(3);
AF_DCMotor motor1(4);
int trigpin=12;
int echopin=13;
int distance=0;
int duration=0;
void setup(){
  Serial.begin(9600);
  motor.setSpeed(255);
  motor.run(RELEASE);
    motor1.setSpeed(255);
  motor1.run(RELEASE);
  pinMode(trigpin,OUTPUT);
  pinMode(echopin,INPUT);
  }
  void loop(){
    long duration, distance;
  digitalWrite(trigpin,HIGH);
  delayMicroseconds(1000);
  digitalWrite(trigpin, LOW);
  duration=pulseIn(echopin, HIGH);
  distance =(duration/2)/29.1;
  Serial.print(distance);
  Serial.println("CM");
  delay(10);
  if(distance<20){
    motor.run(FORWARD);
    motor1.run(FORWARD);
  }
  else if(distance>20){
   
    motor.run(BACKWARD);
    motor1.run(FORWARD);
  }
  }
