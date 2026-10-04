# ESP32 Smart Light Classifier Using TinyML

## Aim

To develop a smart light classification system using ESP32, an LDR sensor, an OLED display, Wi-Fi, and a TinyML model to classify light intensity as Dark, Normal, or Bright, control an LED automatically, and display sensor readings and classification results on a web dashboard.

## Components Required

* ESP32 Development Board
* LDR (Light Dependent Resistor)
* 10 kΩ Resistor
* SSD1306 OLED Display (128 × 64, I2C)
* LED
* 220 Ω Resistor
* Breadboard
* Jumper Wires

## Technologies Used

* Arduino C++
* Python
* TensorFlow
* TensorFlow Lite
* TensorFlow Lite Micro
* HTML
* CSS
* JavaScript
* Wi-Fi
* Google Colab
* Wokwi Simulator

## System Architecture

LDR Sensor → ESP32 Analog Input → TinyML Model Inference → Light Classification → OLED Display and Automatic LED Control → Wi-Fi Web Dashboard → Result Logging

## Pin Connections

### LDR Sensor

* 3.3V → LDR
* LDR and 10 kΩ resistor junction → GPIO 34
* 10 kΩ resistor → GND

### OLED Display

| OLED Pin | ESP32 Pin |
| -------- | --------- |
| VCC      | 3.3V      |
| GND      | GND       |
| SDA      | GPIO 21   |
| SCL      | GPIO 22   |

### LED

* GPIO 23 → 220 Ω resistor → LED anode
* LED cathode → GND

## Machine Learning Model

A small neural network is trained using TensorFlow in Google Colab. The trained model is converted into TensorFlow Lite format and embedded into the ESP32 program as a C/C++ header file for on-device inference.

## Classification Categories

* Dark – Low light intensity
* Normal – Medium light intensity
* Bright – High light intensity

The initial demonstration model uses synthetic training data. Real-world deployment requires collecting actual LDR measurements and calibrating the model to the sensor and environment.

## Working Principle

1. The LDR senses the surrounding light intensity.
2. The ESP32 reads the analog value from the sensor.
3. The sensor reading is normalized according to the model's input format.
4. The TinyML model performs inference directly on the ESP32.
5. The predicted class is displayed on the OLED screen.
6. The ESP32 automatically turns the LED ON when the predicted class is Dark and OFF otherwise.
7. The ESP32 connects to Wi-Fi and hosts a web dashboard.
8. The dashboard displays live sensor readings, predicted classes, LED status, and recent results.
9. The dashboard refreshes its data automatically every second.

## Features

* Real-time light intensity monitoring
* On-device TinyML inference
* Dark, Normal, and Bright classification
* OLED display of sensor readings and predictions
* Automatic LED control
* Wi-Fi-enabled web dashboard
* Automatic dashboard updates
* Recent result logging in ESP32 memory
* Edge AI processing without cloud inference

## Expected Output

### OLED Display

```text
SMART LIGHT CLASSIFIER
----------------------
ADC: 850
Class: Dark
LED: ON
```

### Web Dashboard

```text
Smart Light Classifier

ADC Value: 850
Prediction: Dark
Automatic LED: ON

Recent Result Log
Time | ADC | Class | LED
```

Note: The readings above are illustrative. Actual output depends on the sensor reading and trained model.

## Result Logging

The ESP32 stores the latest 20 readings in RAM, including the timestamp since startup, ADC value, predicted class, and LED status. The web dashboard displays this recent history. The log is cleared when the ESP32 restarts.

## Future Enhancements

* Train the model using real-world LDR measurements.
* Store historical results in a database or cloud platform.
* Add manual LED control through the web dashboard.
* Display prediction confidence scores.
* Add charts for light intensity over time.
* Improve model accuracy and reduce memory usage.

## Result

The Smart Light Classifier integrates Wi-Fi, an LDR sensor, an OLED display, TinyML inference, automatic LED control, and a web dashboard to monitor light intensity and record recent classification results.

## Project Type

Embedded Systems, Internet of Things (IoT), TinyML, Edge AI, and Smart Automation
