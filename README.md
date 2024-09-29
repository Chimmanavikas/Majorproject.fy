# Majorproject.fy
#include<SoftwareSerial.h>
SoftwareSerial rfid(2,3);  //rx,tx
String rcv; 
/*
   This sample sketch demonstrates the normal use of a TinyGPSPlus (TinyGPSPlus) object.
   It requires the use of SoftwareSerial, and assumes that you have a
   4800-baud serial GPS device hooked up on pins 4(rx) and 3(tx).
*/

int motor1 =4;
int motor2 =5;
int motor3 =6;
int motor4 =7;
// The TinyGPSPlus object

void setup()
{
  pinMode(motor1, OUTPUT); pinMode(motor3, OUTPUT);
  pinMode(motor2, OUTPUT); pinMode(motor4, OUTPUT);

  Serial.begin(9600);
   
  rfid.begin(9600);
}
void loop()
{
  
  while (rfid.available())
  {
    rcv = rfid.readString();
    Serial.println(rcv);
//  }

  if(rcv=="550019849B53")
  {
    Serial.println("path 1");
    Serial.println("forward");
    analogWrite(motor1,150); analogWrite(motor2,0);
    analogWrite(motor3,150); analogWrite(motor4,0);
    delay(3000);
    Serial.println("right");
    analogWrite(motor1,250); analogWrite(motor2,0);
    analogWrite(motor3,0); analogWrite(motor4,0);
    delay(1000);
    Serial.println("forward");
    analogWrite(motor1,150); analogWrite(motor2,0);
    analogWrite(motor3,150); analogWrite(motor4,0);
    delay(3000);
    Serial.println("stop");
   analogWrite(motor1,0); analogWrite(motor2,0);
   analogWrite(motor3,0); analogWrite(motor4,0);
  }
  if(rcv=="550019242D45")
  {
     Serial.println("path 2");
   Serial.println("backward");
   analogWrite(motor1,0); analogWrite(motor2,150);
   analogWrite(motor3,0); analogWrite(motor4,150);
   delay(3000);
   Serial.println("left");
    analogWrite(motor1,0); analogWrite(motor2,0);
    analogWrite(motor3,250); analogWrite(motor4,0);
    Serial.println("forward");
    delay(3000);
    analogWrite(motor1,150); analogWrite(motor2,0);
    analogWrite(motor3,150); analogWrite(motor4,0);
    delay(3000);
    Serial.println("stop");
   analogWrite(motor1,0); analogWrite(motor2,0);
   analogWrite(motor3,0); analogWrite(motor4,0);
  }
  if(rcv=="5500129005D2")
  {
    Serial.println("path 3");
   Serial.println("left");
    analogWrite(motor1,0); analogWrite(motor2,0);
    analogWrite(motor3,250); analogWrite(motor4,0);
    delay(2000);
    Serial.println("forward");
    //delay(4000);
    analogWrite(motor1,150); analogWrite(motor2,0);
    analogWrite(motor3,150); analogWrite(motor4,0);
    delay(4000);
    Serial.println("right");
    analogWrite(motor1,250); analogWrite(motor2,0);
    analogWrite(motor3,0); analogWrite(motor4,0);
    delay(3000);
    Serial.println("forward");
    analogWrite(motor1,150); analogWrite(motor2,0);
    analogWrite(motor3,150); analogWrite(motor4,0);
    delay(4000);
    Serial.println("stop");
   analogWrite(motor1,0); analogWrite(motor2,0);
   analogWrite(motor3,0); analogWrite(motor4,0);
  }
  if(rcv=="15008DDD7732")
  {
   Serial.println("stop");
   analogWrite(motor1,0); analogWrite(motor2,0);
   analogWrite(motor3,0); analogWrite(motor4,0);
  }
}
}
