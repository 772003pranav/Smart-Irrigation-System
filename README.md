
#include <LiquidCrystal.h>

const int temp = A1;
const int motor_terminal1 = 10;
const int motor_terminal2 = 11;
const int LedRed = 12;
const int LedGreen = 9;
const int Buzzer = 8;


LiquidCrystal lcd(2, 3, 4, 5, 6, 7);

void setup() {
  Serial.begin(9600);
  Serial.print("Smart irrigation system");
  Serial.print("\n");
  Serial.print("\n");
  lcd.begin(16, 2);
  lcd.print("Smart Irrigation");
  lcd.setCursor(4,1);
  lcd.print("System!!");
  pinMode(Buzzer, OUTPUT);
  pinMode(LedRed, OUTPUT);
  pinMode(LedGreen, OUTPUT);
  pinMode(motor_terminal1, OUTPUT);
  pinMode(motor_terminal2, OUTPUT);
  delay(2000);
  lcd.clear();
  lcd.print("Temp = ");
  lcd.setCursor(0,1);
  lcd.print("WaterPump= ");
}

void loop() {

  int value = analogRead(temp);
  float Temperature = value;
  Serial.print("Soil Temperature = ");
  Serial.print(Temperature);
  Serial.print("\n");Serial.print("\n");
  lcd.setCursor(6,0);
  lcd.print(Temperature); 
  lcd.setCursor(11,1);
  

  if (Temperature > 50){
    digitalWrite(motor_terminal2, HIGH);
    digitalWrite(motor_terminal1, LOW);
    digitalWrite(LedRed, HIGH);
    digitalWrite(LedGreen, LOW);
    tone(Buzzer,220,100);
    lcd.print("ON ");
    Serial.print("Warning...!!!! Soil temperature is high");
    Serial.print("\n");Serial.print("\n");
    Serial.print("Need water!! Switch on water pump");
    Serial.print("\n");Serial.print("\n");
  }
  else {
    digitalWrite(motor_terminal2, LOW);
    noTone(Buzzer);
    digitalWrite(LedRed, LOW);
    digitalWrite(LedGreen, HIGH);
    lcd.print("OFF");
    Serial.print("Soil Temperature is fine...!!!");
    Serial.print("\n");Serial.print("\n");
  }
  
   delay(1000);
}
