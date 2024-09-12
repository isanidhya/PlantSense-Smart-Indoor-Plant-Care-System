# PlantSense-Smart-Indoor-Plant-Care-System
## Overview

The **Smart Indoor Plant Care System** is an innovative IoT and AI-based solution designed to automate and optimize the care of indoor plants. Utilizing a variety of sensors, this system monitors vital factors like soil moisture, light intensity, temperature, and humidity to ensure that plants receive the appropriate care. By automatically watering plants and adjusting light levels, this system ensures the optimal growing environment for indoor plants, even when the user is away.

This project was built to simplify plant care for individuals who may lack time or knowledge about maintaining indoor plants. The system promotes sustainable, automated plant care and reduces water wastage by providing only the necessary amount of water based on real-time data.

## Features

- **Automated Watering**: Detects soil moisture levels and triggers the water pump to irrigate when moisture falls below a set threshold.
- **Light Control**: Monitors ambient light and automatically turns on LED grow lights if natural light is insufficient for plant growth.
- **Real-Time Environmental Monitoring**: Tracks temperature and humidity using sensors, providing insights into the plant’s growing environment.
- **Cloud-Based Monitoring** (optional): Real-time sensor data can be uploaded to a cloud platform for remote monitoring and notifications.
- **AI-Powered Health Monitoring** (optional): Use AI to analyze images of plants and detect potential health issues like disease or pests.

## Hardware Components

- **SIPEED MAXDUINO IoT Kit**: Microcontroller for controlling the system and interfacing with sensors and actuators.
- **Soil Moisture Sensor**: Measures the moisture level in the soil to determine when watering is needed.
- **DHT11/DHT22 Temperature & Humidity Sensor**: Monitors environmental conditions around the plant.
- **LDR (Light Dependent Resistor)**: Measures ambient light intensity to control grow lights.
- **Water Pump & Relay Module**: Automatically waters the plant when moisture levels are low.
- **LED Grow Lights**: Provides supplementary light when natural light is insufficient.

## Circuit Diagram

![Circuit Diagram](diagrams/circuit_diagram.png)

The circuit diagram illustrates how the various sensors and actuators are connected to the SIPEED MAXDUINO. The soil moisture sensor, DHT11/DHT22, LDR, relay module, and water pump are all interfaced with the microcontroller to enable automatic plant care.

## Code Explanation

The system's functionality is driven by the code uploaded to the SIPEED MAXDUINO. Here's a breakdown of the key components:

- **Sensor Data Acquisition**: The soil moisture sensor, DHT11/DHT22, and LDR are read periodically to gather real-time data.
  
  ```cpp
  int soil_moisture = analogRead(A0);
  int light_level = analogRead(A1);
  float temperature = dht.readTemperature();
  float humidity = dht.readHumidity();
  ```

- **Watering Logic**: Based on the soil moisture level, the system decides whether to activate the water pump.
  
  ```cpp
  if (soil_moisture < moisture_threshold) {
      digitalWrite(pump_pin, HIGH);  // Turn on water pump
  } else {
      digitalWrite(pump_pin, LOW);   // Turn off water pump
  }
  ```

- **Light Control**: The system turns on the grow lights if the ambient light level is below a threshold.
  
  ```cpp
  if (light_level < light_threshold) {
      digitalWrite(light_pin, HIGH);  // Turn on grow light
  } else {
      digitalWrite(light_pin, LOW);   // Turn off grow light
  }
  ```

- **Real-Time Monitoring**: The sensor data can be sent to the cloud for remote monitoring and analysis (optional feature).
  
  ```cpp
  // Code to send data to cloud (Firebase, etc.) can be added here
  ```

## Working Demonstration

**Step 1: Initial Setup**  
Once the hardware is assembled and the code is uploaded to the SIPEED MAXDUINO, the system starts by monitoring the soil moisture, light, temperature, and humidity levels.

**Step 2: Automated Watering**  
When the soil moisture sensor detects that the moisture level is below the specified threshold, the water pump automatically waters the plant. This process is stopped once the soil reaches an optimal moisture level.

**Step 3: Light Adjustment**  
If the ambient light is insufficient for the plant's growth, the grow lights are activated, ensuring the plant receives adequate light for photosynthesis.

**Step 4: Real-Time Data Visualization**  
(optional) The data from all the sensors is uploaded to the cloud for real-time visualization and monitoring. Users can receive notifications when the plant needs attention.

## Images of the Project

- **Initial Hardware Setup**: ![Hardware Setup](images/setup.jpg)
- **Wiring Connections**: ![Wiring Connections](images/wiring.jpg)
- **System in Action**: ![System in Action](images/demo.jpg)

## Installation & Setup

### 1. Clone the repository:
```bash
git clone https://github.com/yourusername/Smart-Indoor-Plant-Care-System.git
```

### 2. Open the `main_code.ino` file:
- Open the source code in the Arduino IDE.
- Install necessary libraries such as `DHT` for temperature and humidity sensors.
- Modify the threshold values for soil moisture and light intensity as per your plant's requirements.

### 3. Upload the code to the SIPEED MAXDUINO:
- Connect the SIPEED MAXDUINO to your computer via USB.
- Upload the code using the Arduino IDE.

### 4. Assemble the hardware:
- Follow the circuit diagram and connect the sensors, relay module, and water pump to the SIPEED MAXDUINO.
- Power the components and place the sensors in the soil of your plant.

### 5. Monitor your plant:
- The system will automatically water the plant and adjust lighting based on real-time data.
- (Optional) Set up cloud integration for remote monitoring.

## Future Enhancements

- **AI-Powered Plant Health Monitoring**: Integrating a camera and AI models to analyze plant images for detecting diseases or pests.
- **Mobile App**: Develop a mobile app for easier real-time monitoring and control of the plant care system.
- **Energy Efficiency**: Incorporating solar power to make the system more energy-efficient.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

### Additional Tips:
- Include all images of the hardware in action and provide detailed circuit diagrams.
- Ensure all sensor data and cloud integration are working properly before demonstrating.
- Keep the README updated with any future developments or improvements you make to the system.

Let me know if you need more details on any part!
