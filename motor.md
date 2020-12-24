# Connecting motor

## Dec 23 2020


```
#include "Servo.h"

#define IN1 4 
#define IN2 2
#define STBY 7 //STBY(standby) connects to 7th pin;
#define PWM2 6 //pwm(Pulse width modulation) connects to the 6th pin;  

//STBY==1 work; STBY==0 not work;
//if the 7th pin set to high， STBY works
//analogWrite(): writes an analog value(PWM) to a pin. Can be used to drive a motor at various speeds.
//analogwrite pwm range is 0~255, means the voltage range is 0~5;


int angle=90;
Servo servo;
int direction=1;

void setup() {
  pinMode(IN1, OUTPUT);
  pinMode(IN2, OUTPUT);
  pinMode(STBY, OUTPUT);
  pinMode(PWM2, OUTPUT);
  
  //servo.attach(5);
}

void loop() {
  digitalWrite(STBY, HIGH);
  digitalWrite(IN1, LOW);
  digitalWrite(IN2, HIGH);
  analogWrite(PWM2, 50); // transmits the PWM signal to the motor to drive at the given speed. 
  
  /*
  digitalWrite(STBY, HIGH);
  digitalWrite(IN1, HIGH);
  digitalWrite(IN2, LOW);  // these two lines control the current direction (电流方向)
  analogWrite(PWM2, 0); // transmits the PWM signal to the motor to drive at the given speed. 
  */ 
  
  
  //servo.write(angle);
  
  if(direction == 1){
    if(angle<60){
      angle += 1;
    }else{
      direction =-1;
      delay(2000);
    }
  }else{
    if(angle>30){
      angle -= 1;
    }else{
      direction = 1;
      delay(2000);
    }
  }
  //servo.write(angle);
  //analogWrite(PWM2, angle); // drive the motor at virous speeds.
  delay(20);
  
  
}
```
