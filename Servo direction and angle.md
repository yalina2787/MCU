```
#include "Servo.h"

int angle=90;
Servo servo;
int direction=1;

void setup() {

  servo.attach(5); //connect the fifth pin; yellow line transmits signal, red line transmits current voltage, the brown one connects to ground wire；
}

void loop() {
  
  //the servo angle range:[60, 120];
  //servo.write(angle);
  
  if(direction == 1){
    if(angle<120){
      angle += 1;
    }else{
      direction =-1;
      delay(2000); //stop for 2 seconds.
    }
  }else{
    if(angle>60){
      angle -= 1;
    }else{
      direction = 1;
      delay(2000);
    }
  }
  servo.write(angle); //transmit the data to the servo.
  
  delay(10); //stop for 10 milliseconds, then execute next loop.
  
  
}

```
