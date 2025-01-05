Sensor Pins(Soil moisture sensor):

    VCC: Power supply for the sensor (3.3V or 5V from the Arduino).
    GND: Ground connection.
    DO: Digital output, sends HIGH or LOW based on a threshold set by the onboard potentiometer.
    AO: Analog output, provides a continuous voltage based on moisture level.

Connections:
Sensor Pin	Arduino Pin	Purpose
VCC	5V or 3.3V	Power the sensor
GND	GND	Ground
DO	Any Digital Pin (e.g., D2)	Digital output (on/off moisture level)
AO	Any Analog Pin (e.g., A0)	Analog output (moisture percentage)
How to Use:

    Digital Output (DO):
        The DO pin will give a HIGH or LOW signal depending on the threshold set by the sensor’s potentiometer.
        Connect it to D2
    Analog Output (AO):
        The AO pin gives a voltage proportional to the soil moisture level.
        Connect it to A0

Example Code:

// Pin definitions
#define DIGITAL_PIN 2 // DO connected to D2
#define ANALOG_PIN A0 // AO connected to A0

void setup() {
  Serial.begin(9600);
  pinMode(DIGITAL_PIN, INPUT); // Set DO as input
}

void loop() {
  int digitalValue = digitalRead(DIGITAL_PIN); // Read digital pin
  int analogValue = analogRead(ANALOG_PIN);   // Read analog pin
  
  Serial.print("Digital Output (DO): ");
  Serial.println(digitalValue);
  
  Serial.print("Analog Output (AO): ");
  Serial.println(analogValue);
  
  delay(1000);
}


Sensor pins(Relay)
Relay Pins:

    VCC: Connects to the Arduino's 5V to power the relay.
    GND: Connects to the Arduino's GND.
    IN: Signal pin to control the relay (HIGH to turn on, LOW to turn off).

VCC-5V	
GND-GND
IN-D3

Water Pump Connection (AC/DC Load):

    Relay Terminals: The relay has three terminals:
        COM: Common (middle pin).
        NO: Normally Open (default disconnected).
        NC: Normally Closed (default connected).

    Wire the Water Pump:
        Connect the COM terminal of the relay to one terminal of the water pump.
        Connect the other terminal of the water pump to your power source (e.g., mains for AC or a DC source).
        Connect the power source’s other wire to the NO terminal of the relay (for switching the pump ON/OFF).

testing Code:

#define RELAY_PIN 3 // IN connected to D3

void setup() {
  pinMode(RELAY_PIN, OUTPUT); // Set relay pin as output
  digitalWrite(RELAY_PIN, LOW); // Ensure relay is off initially
}

void loop() {
  // Turn the pump ON
  digitalWrite(RELAY_PIN, HIGH);
  delay(5000); // Keep it ON for 5 seconds

  // Turn the pump OFF
  digitalWrite(RELAY_PIN, LOW);
  delay(5000); // Keep it OFF for 5 seconds
}

    Water Pump:
        connect the pump's positive terminal to the relay's NO terminal and the negative terminal to the power source's ground.
