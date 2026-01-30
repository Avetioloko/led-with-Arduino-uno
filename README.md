int micPin = A0;
int ledPin = 13;

bool ledState = false;
unsigned long lastClap = 0;
int threshold = 600;   // սա կարող ես փոխել

void setup() {
  pinMode(ledPin, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  int soundValue = analogRead(micPin);

  // Debug-ի համար (կարող ես հետո հանել)
  Serial.println(soundValue);

  // Եթե ձայնը անցավ սահմանը
  if (soundValue > threshold && millis() - lastClap > 300) {
    ledState = !ledState;
    digitalWrite(ledPin, ledState);
    lastClap = millis();
  }
}
