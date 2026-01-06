⚠️dont use code below use code from zip file uploaded here⚠️

Anti-Sleeping Alarm System
This project is an Arduino-based safety wearable (mounted on goggles) designed to detect when a user falls asleep. It utilizes an IR sensor to monitor eye blinks; if the eyes remain closed for a specific duration, an alarm (buzzer) sounds and the motor (vibration/propulsion) stops to alert the user or stop a vehicle.
🛠 Components List
 * Microcontroller: Arduino Uno
 * Sensor: IR Sensor (FC-51)
 * Actuators: * Piezo Buzzer
   * DC Motor with wheels
 * Transistor: BD140 PNP Transistor (for motor control)
 * Resistor: 1k\Omega Resistor
 * Misc: Goggles (for mounting), Breadboard, and Jumper Wires.
🔌 Circuit Connections
1. IR Sensor (FC-51)
 * VCC: Arduino 5V
 * GND: Arduino GND
 * OUT: Arduino Digital Pin 2
2. BD140 Transistor (Motor Control)
The BD140 is a PNP transistor. Note the pinout: 1=Emitter, 2=Collector, 3=Base.
 * Emitter (Pin 1): Connected to Motor +V Supply / Arduino 5V
 * Collector (Pin 2): Connected to Motor Positive terminal
 * Base (Pin 3): Connected to Arduino Pin 13 through a 1k\Omega resistor
3. Buzzer
 * Positive (+): Arduino Digital Pin 12
 * Negative (-): Arduino GND
4. DC Motor
 * Positive (+): BD140 Collector
 * Negative (-): Arduino GND / Battery Negative
💻 Logic & Code
The system uses inverted logic for the motor because of the BD140 PNP transistor:
 * Arduino Pin HIGH: Motor is OFF.
 * Arduino Pin LOW: Motor is ON.
Arduino Sketch (Anti_Sleeping_Alarm.ino)
// Source: https://youtu.be/87A5ncuahyQ

const int blinkPin = 2;     // IR Sensor Input
const int motorPin = 13;    // Motor Control Pin (BD140 Base)
const int buzzerPin = 12;   // Buzzer Pin

long time;

void setup() {
  pinMode(motorPin, OUTPUT);
  pinMode(buzzerPin, OUTPUT);
  pinMode(blinkPin, INPUT);
  
  // Initial state: Eyes open, motor running
  digitalWrite(motorPin, HIGH); // Inverted logic: HIGH is OFF for some PNP setups, 
                                // but based on your requirement: Eyes Open = Motor ON.
}

void loop() {
  // If IR sensor detects "Eyes Open" (Signal is HIGH)
  if(digitalRead(blinkPin)){
    digitalWrite(buzzerPin, LOW);   // Buzzer Off
    digitalWrite(motorPin, HIGH);   // Motor On (Verify logic with your BD140 wiring)
  } 
  // If IR sensor detects "Eyes Closed" (Signal is LOW)
  else {
    time = millis();
    while(!digitalRead(blinkPin)){ 
      // If eyes closed for > 3 seconds, turn on buzzer
      if(TimeDelay() >= 3) digitalWrite(buzzerPin, HIGH);
      
      // If eyes closed for > 5 seconds, turn off motor
      if(TimeDelay() >= 5) digitalWrite(motorPin, LOW);
      
      delay(1000);
    }
  }
}

int TimeDelay(){
  long t = millis() - time;
  t = t / 1000;
  return t;
}
🚀 Setup Instructions
 * Hardware Assembly: Mount the IR sensor on the side of the goggles so it points toward the eyelid.
 * Wiring: Follow the pinout for the BD140 carefully. PNP transistors act as a switch on the high side.
 * Calibration: Use the small potentiometer (blue dial) on the IR sensor to adjust sensitivity until it reliably detects the difference between an open eye and a closed eyelid.
 * Upload: Connect your Arduino Uno to your PC and upload the provided code using the Arduino IDE.
⚠️ Important Note on Motor Logic
In your specific request:
 * Eyes Open: Motor ON / Buzzer OFF.
 * Eyes Closed: Motor OFF / Buzzer ON.
If the motor behaves the opposite way, simply swap the HIGH and LOW commands for motorPin in the code, as PNP transistor behavior depends on whether you are switching the ground or the power rail.

