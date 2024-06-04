# Detecting-Human-Presence-Using-Arduino
// Define the pins
const int pirPin = 2;    // PIR sensor pin
const int relayPin = 3;  // Relay pin

void setup() {
  // Initialize the PIR sensor pin as an input
  pinMode(pirPin, INPUT);
  
  // Initialize the relay pin as an output
  pinMode(relayPin, OUTPUT);
  
  // Set the relay to LOW (off)
  digitalWrite(relayPin, LOW);
  
  // Start serial communication for debugging
  Serial.begin(9600);
}

void loop() {
  // Read the state of the PIR sensor
  int pirState = digitalRead(pirPin);
  
  // Print the PIR sensor state to the serial monitor
  Serial.println(pirState);
  
  // If motion is detected
  if (pirState == HIGH) {
    // Turn on the relay (and the LED)
    digitalWrite(relayPin, HIGH);
  } else {
    // Turn off the relay (and the LED)
    digitalWrite(relayPin, LOW);
  }
  
  // Add a small delay to avoid bouncing
  delay(100);
}