const int PWMA = 5;
const int PWMB = 6;
const int STBY = 3;
const int AIN1 = 2;
const int AIN2 = 4;
const int BIN1 = 7;
const int BIN2 = 8;
void setup() {
  // put your setup code here, to run once:
  Serial.begin(9600);
}
void loop() {
  // put your main code here, to run repeatedly:
  float lineFollowerPassenger = analogRead (A1) * 5.0 / 1024.0;
  float lineFollowerDriver = analogRead (A0) * 5.0 / 1024.0;
  Serial.print(lineFollowerDriver);
  Serial.print(lineFollowerPassenger);
  Serial.println("V\t");
  digitalWrite(STBY, HIGH);
  analogWrite(PWMA, 90);
  analogWrite(PWMB, 85);
  digitalWrite(AIN1, HIGH);
  digitalWrite(AIN2, LOW);
  digitalWrite(BIN1, LOW);
  digitalWrite(BIN2, HIGH);
  // for bot to follow tape
   if (lineFollowerPassenger > 4.0) {
      // turn right
    analogWrite(PWMA, 50);
    analogWrite(PWMB, 250);
    digitalWrite(AIN1, HIGH);
    digitalWrite(AIN2, LOW);
    digitalWrite(BIN1, LOW);
    digitalWrite(BIN2, HIGH);}
    else {
      digitalWrite(STBY, HIGH);
    }
   if (lineFollowerDriver > 4.0){
      // turn left
    analogWrite(PWMA, 245);
    analogWrite(PWMB, 45);
    digitalWrite(AIN1, HIGH);
    digitalWrite(AIN2, LOW);
    digitalWrite(BIN1, LOW);
    digitalWrite(BIN2, HIGH);}
    else {
      digitalWrite(STBY, HIGH);
  }
  if (lineFollowerPassenger > 4.0 && lineFollowerDriver > 4.0 ){ 
  digitalWrite(STBY, HIGH);
  analogWrite(PWMA, 255);
  analogWrite(PWMB, 255);
  digitalWrite(AIN1, HIGH);
  digitalWrite(AIN2, LOW);
  digitalWrite(BIN1, HIGH);
  digitalWrite(BIN2, LOW);
  
  delay(650);
  }
    else {
      digitalWrite(STBY, HIGH);
  }}
