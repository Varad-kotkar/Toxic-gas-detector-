//# Toxic-gas-detector-
// Define pin numbers for sensors and buzzer
#define MQ4_PIN A0
#define MQ7_PIN A1
#define BUZZER_PIN 11

// Define threshold values for gas levels
#define MQ4_THRESHOLD 500 // Adjust as needed
#define MQ7_THRESHOLD 500  // Adjust as needed

void setup() {
  // Initialize serial communication
  Serial.begin(9600);

  // Set buzzer pin as output
  pinMode(BUZZER_PIN, OUTPUT);
}

void loop() {
  // Read analog values from sensors
  int mq4Value = analogRead(MQ4_PIN);
  int mq7Value = analogRead(MQ7_PIN);

  // Print sensor values to serial monitor
  Serial.print("MOS-gas Value: ");
  Serial.println(mq4Value);
  Serial.print("CO-gas Value: ");
  Serial.println(mq7Value);

  // Check if gas levels exceed threshold
  if (mq4Value > MQ4_THRESHOLD || mq7Value > MQ7_THRESHOLD) {
    // Activate buzzer
    digitalWrite(BUZZER_PIN, HIGH);
    Serial.println("Gas levels above threshold! Buzzer activated.");
  } else {
    // Deactivate buzzer
    digitalWrite(BUZZER_PIN, LOW);
  }

  // Delay for stability
  delay(1000); // Adjust delay as needed
}
