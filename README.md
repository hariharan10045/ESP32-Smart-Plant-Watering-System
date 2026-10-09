#define SOIL_PIN 34
#define PUMP_PIN 26

int threshold = 1600;

void setup() {
  Serial.begin(115200);

  pinMode(SOIL_PIN, INPUT);
  pinMode(PUMP_PIN, OUTPUT);

  digitalWrite(PUMP_PIN, LOW);

  Serial.println("Smart Plant Watering System");
}

void loop() {
  int moisture = analogRead(SOIL_PIN);

  Serial.print("Moisture value: ");
  Serial.println(moisture);

  // Low reading represents dry soil
  if (moisture < threshold) {
    digitalWrite(PUMP_PIN, HIGH);
    Serial.println("Soil DRY - Pump ON");
  } else {
    digitalWrite(PUMP_PIN, LOW);
    Serial.println("Soil WET - Pump OFF");
  }

  delay(1000);
}
