# ECG-signal-with-ESP32
void setup() {
  // Initialize the serial communication:
  Serial.begin(115200);
  pinMode(12, INPUT); // Setup for leads off detection LO +
  pinMode(13, INPUT); // Setup for leads off detection LO -
  pinMode(34, INPUT); // Setup for analog input
}

void loop() {
  int loPlus = digitalRead(12);
  int loMinus = digitalRead(13);

  // Debugging leads off detection
  Serial.print("LO+: ");
  Serial.print(loPlus);
  Serial.print(" LO-: ");
  Serial.println(loMinus);
0lplp
  if (loPlus == 1 || loMinus == 1) {
    Serial.println('!');  // Indicate leads off
  } else {
    // Read ECG signal
    int sensorValue = analogRead(34);  // GPIO34 for ECG signal input
    Serial.print("ECG Value: ");
    Serial.println(sensorValue);
  }

  delay(5);  
}
