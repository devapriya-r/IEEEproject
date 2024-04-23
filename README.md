# IEEEproject
Distance Measuring and Obstacle Detection Device
This project implements an Obstacle detection system on Tinkercad using an Arduino Uno R3. The system employs an ultrasonic distance sensor with four pins to measure distance. Three LEDs (red, yellow, and green) with 330Ω resistors provide visual feedback on obstacle proximity. The green LED signifies a clear zone (distance<100cm and >75cm), yellow indicates caution (distance between 50cm and 75cm), and red signifies an obstacle detected (distance < 50cm).
![Daring Jarv (2)](https://github.com/devapriya-r/IEEEproject/assets/167847291/1827caa6-b1ea-47a7-a560-203838523eea)
Project link: https://www.tinkercad.com/things/agi9Nf6lTpp-daring-jarv/editel?sharecode=xySc1jdmc5pOUzv-I2SkKpFIQj45_6oURZOE7NFF_ZA
Code: 
// C++ code
//
int val = 0;

long readUltrasonicDistance(int triggerPin, int echoPin)
{
  pinMode(triggerPin, OUTPUT);  // Clear the trigger
  digitalWrite(triggerPin, LOW);
  delayMicroseconds(2);
  // Sets the trigger pin to HIGH state for 10 microseconds
  digitalWrite(triggerPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(triggerPin, LOW);
  pinMode(echoPin, INPUT);
  // Reads the echo pin, and returns the sound wave travel time in microseconds
  return pulseIn(echoPin, HIGH);
}

void setup()
{
  Serial.begin(9600);
  pinMode(8, OUTPUT);
  pinMode(9, OUTPUT);
  pinMode(10, OUTPUT);
}

void loop()
{
  val = 0.01723 * readUltrasonicDistance(6, 5);
  Serial.println(val);
  if (val < 100) {
    digitalWrite(8, HIGH);
  } else {
    digitalWrite(8, LOW);
  }
  if (val < 75) {
    digitalWrite(9, HIGH);
  } else {
    digitalWrite(9, LOW);
  }
  if (val < 50) {
    digitalWrite(10, HIGH);
  } else {
    digitalWrite(10, LOW);
  }
  delay(10); // Delay a little bit to improve simulation performance
}
