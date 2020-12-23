# MCU control LED light

## Dec 23 

```
void setup() {
  pinMode(13, OUTPUT);
  pinMode(2, INPUT);
}                      // choose input & output pin, don't chose V1n pin (this pin has 12 Voltage, too high)

void loop() {

  int btn = digitalRead(2);
  
  if (btn == HIGH){
    digitalWrite(13, HIGH);
    delay(500);
    digitalWrite(13, LOW);
    delay(200);
    digitalWrite(13, HIGH);
    delay(500);
    digitalWrite(13, LOW);
    delay(200);
    digitalWrite(13, HIGH);
    delay(500);
    digitalWrite(13, LOW);
    delay(2000);
  }else{
    digitalWrite(13, LOW);
  }                             // control LED light
}
```
