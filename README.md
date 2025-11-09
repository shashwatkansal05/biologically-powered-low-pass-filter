const int OUT_PIN = 9;
unsigned long hold_ms = 3000;  // stay at each frequency for 3 seconds

void setup() {
  pinMode(OUT_PIN, OUTPUT);
}

void loop() {
  float freqs[] = {1, 2, 5, 10, 20, 50};  // frequencies in Hz
  int n = sizeof(freqs) / sizeof(freqs[0]);

  for (int i = 0; i < n; i++) {
    float period_ms = 1000.0 / freqs[i]; // one full cycle time in ms
    unsigned long start = millis();

    while (millis() - start < hold_ms) {
      digitalWrite(OUT_PIN, HIGH);
      delay(period_ms / 2);
      digitalWrite(OUT_PIN, LOW);
      delay(period_ms / 2);
    }
  }

  digitalWrite(OUT_PIN, LOW);
  delay(2000);  // pause before repeating
}

