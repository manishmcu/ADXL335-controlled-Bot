# ADXL335-controlled-Bot
A bot is moving forward, backward, left, right, and stop with Arduino-Microcontroller  and ADXL335 sensor.

**Output:** Check the project demo on my [Linkedin Page](https://www.linkedin.com/posts/manish-pakhira-bb7333171_adxlabr335-paralyzedabrpatient-robotics-activity-6622495226718146561-liZw)

### Coding:

```

#include <ADXL335.h>

int xA;
int yA;
int zA;

int LM1 = 11;       // left motor
int LM2 = 10;       // left motor
int RM1 = 9;       // right motor
int RM2 = 5;      // right motor
 
void setup() {
  Serial.begin(9600);
  pinMode(LM1, OUTPUT);
  pinMode(LM2, OUTPUT);
  pinMode(RM1, OUTPUT);
  pinMode(RM2, OUTPUT);

}
 
void loop() {
 
  xA = analogRead(A0);
  yA = analogRead(A1);
  zA = analogRead(A2);
 
 if(zA > 395)     // Move Forward

  {
    analogWrite(LM1, 100);
    analogWrite(LM2, LOW);
    analogWrite(RM1, 100);
    analogWrite(RM2, LOW);
  }
  
  if(xA > 395)     // Turn right
  {
    analogWrite(LM1, LOW);
    analogWrite(LM2, LOW);
    analogWrite(RM1, 100);
    analogWrite(RM2, LOW);
    delay(25);
  }
  
  if(xA < 270)     // turn left
  {
    analogWrite(LM1, 100);
    analogWrite(LM2, LOW);
    analogWrite(RM1, LOW);
    analogWrite(RM2, LOW);
    delay(25);
  } 
  if(zA < 270)     // stop
  {
    analogWrite(LM1, LOW);
    analogWrite(LM2, LOW);
    analogWrite(RM1, LOW);
    analogWrite(RM2, LOW);
  }
  if(zA < 270)     // back
  {
    analogWrite(LM1, LOW);
    analogWrite(LM2, 80);
    analogWrite(RM1, LOW);
    analogWrite(RM2, 80);
  }
  

  if (xA > 395) {
    Serial.println(" X - - ist oben");
  } 
  else if (yA > 395) {
    Serial.println(" - Y - ist oben");
  }
  else if (zA > 395) {
    Serial.println(" - - Z ist oben");
  }
 
}

```
