
# MCU (Microcontroller Unit)control LED light  [设备：UNO]



## Dec 23 

```
void setup() {
  pinMode(13, OUTPUT); // the 13th pin connects to the LED light;
  pinMode(2, INPUT);   // choose 2th pin for the current voltage input;
}                      // choose input & output pin, don't chose V1n pin (this pin has 12 Voltage, too high)

void loop() {

  int btn = digitalRead(2);
  
  if (btn == HIGH){
    digitalWrite(13, HIGH); // the 13th pin get high current voltage after excuting this line; sets the LED on.
    delay(500);
    digitalWrite(13, LOW); //the 13th pin get low current voltage after excuting this line; sets the LED off.
    delay(200);
    digitalWrite(13, HIGH);
    delay(500);
    digitalWrite(13, LOW);
    delay(200);
    digitalWrite(13, HIGH);
    delay(500);
    digitalWrite(13, LOW);
    delay(2000); //stop for 2 seconds;
  }else{
    digitalWrite(13, LOW);
  }                             // control LED light
}
```
