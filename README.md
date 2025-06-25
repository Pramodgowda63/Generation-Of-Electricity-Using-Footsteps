# Generation-Of-Electricity-Using-Footsteps
#include<LiquidCrystal.h>
LiquidCrystal lcd(2,3,4,5,6,7);

void setup()
{
  Serial.begin(9600);

lcd.begin(16,2);
  lcd.clear();
  lcd.setCursor(0,0);
  lcd.print("Electrical Power");
  lcd.setCursor(0,1);
  lcd.print("Genaretor");
  delay(1500);
}


void loop()
{
  int volt = analogRead(A0);// read the input
  double voltage = map(volt,0,1023, 0, 2500);// map 0-1023 to 0-2500 and add correction offset
  voltage /=100;
  Serial.println("Voltage:"+String(voltage));
  lcd.clear();
  lcd.setCursor(0,0);
  lcd.print("Voltage:"+String(voltage)+String("V"));
  delay(300);
}
