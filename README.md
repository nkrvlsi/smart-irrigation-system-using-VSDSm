# Project: Agriculture automation using VSD_suqadron_Mini board
## OBJECTIVE: 
This Project On Agriculture Smart irrigation system like water pump controller features like, smart drip irrigation to automate the watering process based on soil moisture levels using the CH32V003F4U6 microcontroller. solenoid valve. 

## 1. Components needed:  

### 1.1. Hardware:  
**CH32V003F4U6 Microcontroller:**     The core of the system.  
**Soil Moisture Sensors:**            To measure the soil moisture levels.  
**Water Pump/Valves:**                To control the water flow.  
**Relay Module:**                     To interface the microcontroller with the water pump/valves.  
**Temperature and Humidity Sensor:**  Optional, for more advanced control based on weather conditions.  
**Power Supply:**                     To power the system.  
**Water Flow Sensor:**                Optional, to measure the amount of water used.  
**Wi-Fi Module:**                     Optional, for remote control and monitoring.  

### 1.2. Software:  
**Integrated Development Environment (IDE)**:     To program the microcontroller.  
**Programming Language**:                         C or Assembly, depending on your preference and the IDE support.  
**Mobile or Web Application**:                    Optional, for remote control and monitoring.  

## 2. Circuit Design  

### 2.1. Basic Connections:  
    - Connect the soil moisture sensors to the analog input pins of the CH32V003F4U6.  
    - Connect the relay module to the digital output pins of the microcontroller, which will control the water pump/valves.  
    - Connect the power supply to all components ensuring proper voltage levels.  

### 2.2. Optional Connections:  
    - Connect the temperature and humidity sensor to the appropriate pins for advanced environmental monitoring.  
    - Connect the water flow sensor to monitor water usage.  
    - Connect the Wi-Fi module for remote access.  

## 3. Software Development  

### 3.1. Microcontroller Programming:   
**Initialize Sensors:**  Write code to initialize and read data from the soil moisture sensors.  
**Control Logic:**       Implement the logic to turn the water pump on or off based on soil moisture levels.  
**Relay Control:**       Write code to control the relay module for operating the pump/valves.  
**Advanced Features:**   If using additional sensors (like temperature, humidity, or water flow), integrate their readings into the control logic.  

**Example Code Outline (C):**

```
#include <ch32v003.h>

// Define pins for sensors and relay
#define SOIL_MOISTURE_SENSOR_PIN  PA0
#define RELAY_PIN                 PB0

void setup() {
    // Initialize serial communication for debugging (if needed)
    Serial.begin(9600);

    // Initialize pins
    pinMode(SOIL_MOISTURE_SENSOR_PIN, INPUT);
    pinMode(RELAY_PIN, OUTPUT);

    // Initially turn off the relay
    digitalWrite(RELAY_PIN, LOW);
}

void loop() {
    // Read soil moisture sensor value
    int soilMoistureValue = analogRead(SOIL_MOISTURE_SENSOR_PIN);

    // Debugging print
    Serial.print("Soil Moisture: ");
    Serial.println(soilMoistureValue);

    // Control relay based on soil moisture value
    if (soilMoistureValue < THRESHOLD) {
        // If soil is dry, turn on the pump
        digitalWrite(RELAY_PIN, HIGH);
    } else {
        // If soil is wet enough, turn off the pump
        digitalWrite(RELAY_PIN, LOW);
    }

    // Delay for a short period before next reading
    delay(1000);
}
```

