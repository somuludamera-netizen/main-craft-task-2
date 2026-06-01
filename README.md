// Temperature Sensor with LED
// TMP36/TMP sensor connected to A0
// LED connected to pin 9

int sensorPin = A0;
int ledPin = 9;

void setup() {
  Serial.begin(9600);
  pinMode(ledPin, OUTPUT);
}

void loop() {

  // Read analog value from sensor
  int sensorValue = analogRead(sensorPin);

  // Convert reading to voltage
  float voltage = sensorValue * (5.0 / 1023.0);

  // Convert voltage to temperature (TMP36)
  float temperatureC = (voltage - 0.5) * 100;

  // Print temperature
  Serial.print("Temperature: ");
  Serial.print(temperatureC);
  Serial.println(" °C");

  // LED ON if temperature > 30°C
  if (temperatureC > 30) {
    digitalWrite(ledPin, HIGH);
  }
  else {
    digitalWrite(ledPin, LOW);
  }

  delay(1000);
}
