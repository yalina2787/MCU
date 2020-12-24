# serial port communication
#### DEc 24 2020

```
#include "Servo.h" // servo system （伺服系统，随动系统）

#define IN1 4 
#define IN2 2
#define STBY 7 //STBY(standby) connects to 7th pin;
#define PWM2 6 //pwm(Pulse width modulation) connects to the 6th pin;  

//STBY==1 work; STBY==0 not work;
//if the 7th pin set to high， STBY works
//analogWrite(): writes an analog value(PWM) to a pin. Can be used to drive a motor at various speeds.
//analogwrite pwm range is 0~255, means the voltage range is 0~5;


int angle=90;
int speed = 45;
Servo servo; 
int direction=1;

void setup() {
  pinMode(IN1, OUTPUT);
  pinMode(IN2, OUTPUT);
  pinMode(STBY, OUTPUT);
  pinMode(PWM2, OUTPUT);
  
  servo.attach(5);
  
  Serial.begin(19200); // Baud rate 19200；（波特率）
}

void loop() {

  digitalWrite(STBY, HIGH);  // set to high, keep work status.
  
  byte cmd;
  
  if(Serial.available()) {
  
    cmd = Serial.read();    // read message from the raspberrypi;
    
    if(cmd == 'q') {
    
      speed -= 5;
      if(speed < 30) speed = 30;
      analogWrite(PWM2, speed);
      
    } else if(cmd == 'e') {
      
      speed += 5;
      if(speed > 100) speed = 100;
      analogWrite(PWM2, speed);
      
    } else if(cmd == 'w') {
    
      digitalWrite(IN1, LOW);
      digitalWrite(IN2, HIGH);  // move forward;
      analogWrite(PWM2, speed);
      
    } else if(cmd == 's') {
    
      digitalWrite(IN1, HIGH);
      digitalWrite(IN2, LOW);  // go backward;
      analogWrite(PWM2, speed);
      
    } else if(cmd == 'a') {
    
      servo.write(65);        // turn left;
      
    } else if(cmd == 'd') {
    
      servo.write(115);     // turn right;
      
    } else if(cmd == 'z') {
    
      servo.write(90);      // set the angle value back to 90;
      
    } else if(cmd == 'x') {
    
      digitalWrite(IN1, LOW);
      digitalWrite(IN2, LOW); // set both to low;
      analogWrite(PWM2, 0); // stop the motor;
      
    }
  }
  
}
```
