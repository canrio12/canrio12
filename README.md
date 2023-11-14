#include <LiquidCrystal_I2C.h>

LiquidCrystal_I2C lcd(0x27, 16, 2);
long duration;
int distance;
void setup() {
  pinMode(8, OUTPUT); // Sets the trigPin as an Output
  pinMode(7, INPUT); // Sets the echoPin as an Input
  Serial.begin(9600); // Starts the serial 
  lcd.init();
  lcd.backlight();
}
void loop() {
  // Clears the trigPin
  digitalWrite(8, LOW);
  delayMicroseconds(2);
  // Sets the trigPin on HIGH state for 10 micro seconds
  digitalWrite(8, HIGH);
  delayMicroseconds(10);
  digitalWrite(8, LOW);
  // Reads the echoPin, returns the sound wave travel time in microseconds
  duration = pulseIn(7, HIGH);
  // Calculating the distance
  distance = duration * 0.034 / 2;
  // Prints the distance on the Serial Monitor
  Serial.print("Distance: ");
  Serial.println(distance);
  lcd.setCursor(0,0);
  lcd.print(" Distance : ");
  lcd.println(distance);
  delay(1000);
}
