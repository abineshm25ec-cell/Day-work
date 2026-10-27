// Soil Moisture Based Smart Irrigation System

const int soilSensor = A0;    // Soil moisture sensor pin
const int relayPin = 7;       // Relay module pin

int moistureValue;
int threshold = 500;          // Adjust based on soil condition

void setup() {
  Serial.begin(9600);
  pinMode(relayPin, OUTPUT);
  digitalWrite(relayPin, HIGH); // Pump OFF initially
}

void loop() {

  moistureValue = analogRead(soilSensor);

  Serial.print("Soil Moisture Value: ");
  Serial.println(moistureValue);

  // Dry soil condition
  if (moistureValue > threshold) {
    digitalWrite(relayPin, LOW);   // Pump ON
    Serial.println("Soil Dry - Pump ON");
  }

  // Wet soil condition
  else {
    digitalWrite(relayPin, HIGH);  // Pump OFF
    Serial.println("Soil Wet - Pump OFF");
  }

  delay(1000);
}
