# ardino-projects
Based on the code provided, this program is designed to create an automated proximity-based barrier or lid system (commonly used for things like automatic trash cans or smart gates).  Essentially, it uses an ultrasonic sensor to "see" if an object is nearby and then triggers a physical movement and a visual signal.  How it Works

#include <Servo.h>
const int trigPin =7;
const int echoPin = 6;
const int ledPin = 13;
const int servoPin = 9;
Servo myServo;
void setup() {
Serial.begin(9600);
pinMode(7, OUTPUT);
pinMode(6, INPUT);
pinMode(13, OUTPUT);
myServo.attach(servoPin);}
void loop() {
long duration,distance;
digitalWrite(7, LOW);
delayMicroseconds(2);
digitalWrite(trigPin, HIGH);
delay(10);
digitalWrite(7, LOW);
duration = pulseIn(7, HIGH);
distance = duration * 0.034/2;
Serial.print("Distance:");
Serial.print(distance);
Serial.println(" cm");
if (distance <20) {
digitalWrite(ledPin, HIGH);
myServo.write(90);
} else { }
digitalWrite(ledPin, LOW);
myServo.write(0);
delay(5000);
 }
