# ph-sensor-integration-with-soil-moisture
this code is basically the integration code of ph sensor with the arduino board

// Define the pin connections for the sensors
#define soilMoisturePin A0
#define pHPin A1

void setup() {
  // Start the serial communication
  Serial.begin(9600);
}

void loop() {
  // Read the soil moisture sensor value
  int soilMoistureValue = analogRead(soilMoisturePin);

  // Convert the analog value to a percentage value
  int soilMoisturePercentage = map(soilMoistureValue, 0, 1083, 0, 100);

  // Read the pH sensor value
  int pHValue = analogRead(pHPin);

  // Convert the analog value to a pH value
  float pH = (float)pHValue * 5 / 1024;

  // Print the sensor values to the serial monitor
  Serial.print("Soil Moisture Percentage: ");
  Serial.print(soilMoisturePercentage);
  Serial.print("%, pH Value: ");
  Serial.println(pH);

  // Wait for 1 second before taking the next reading
  delay(1000);
}

