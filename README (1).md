# Smart Temperature Monitor

## Problem Statement
In many environments such as homes, laboratories, server rooms, and industrial setups, temperature plays a critical role in ensuring safety and proper functioning of equipment. Manual monitoring of temperature is inefficient, error-prone, and often delayed, which can lead to equipment damage, safety hazards, or uncomfortable conditions.

There is a need for an automated system that can continuously monitor temperature values and alert users when the temperature crosses a predefined threshold, enabling timely action to prevent damage or hazards.

## Project Description
The **Smart Temperature Monitor** is an embedded system built using Arduino that reads real-time temperature values from a sensor and displays them on an LCD screen. The system continuously monitors the temperature and can trigger alerts when the value crosses a set threshold, helping users take corrective action quickly.

## Features
- Real-time temperature reading using an analog temperature sensor
- Live display of temperature values on a 16x2 LCD
- Serial monitor output for debugging and logging
- Threshold-based alert mechanism for abnormal temperature conditions
- Simulated and tested on Tinkercad Circuits

## Components Used
- Arduino (Uno/compatible board)
- Temperature Sensor (Analog, connected to A0)
- 16x2 LCD Display (I2C - Adafruit_LiquidCrystal)
- Connecting wires
- Tinkercad simulation environment

## Working
1. The analog temperature sensor reads the ambient temperature and sends an analog voltage value to pin A0.
2. The Arduino reads this analog value and converts it into a meaningful temperature range using mathematical mapping.
3. The converted temperature value is displayed on the LCD screen along with a system label.
4. The temperature value is also printed to the Serial Monitor for monitoring and debugging.
5. The system can be extended to trigger alerts (buzzer/LED) when the temperature crosses a defined threshold.

## Circuit Diagram / Simulation
View the live simulation on Tinkercad:
[Smart Temperature Monitor - Tinkercad](https://www.tinkercad.com/things/khra6uX6y88-smart-temperature-system-?sharecode=hLdfhvUiku8a57DBGODCEsYM2SOSlCYQil3mGF7jhfI)

## Code
```cpp
// C++ code
//
#include <Adafruit_LiquidCrystal.h>

int temp = 0;

Adafruit_LiquidCrystal lcd_1(0);

void setup()
{
  pinMode(A0, INPUT);
  Serial.begin(9600);
  lcd_1.begin(16, 2);
}

void loop()
{
  temp = map(((analogRead(A0) - 20) * 3.04), 0, 1023, -20, 120);
  Serial.println(temp);
  lcd_1.setCursor(0, 0);
  lcd_1.print("Temp.Monitr.system");
  lcd_1.setCursor(0, 1);
  lcd_1.print("Temp Value= ");
  lcd_1.setCursor(12, 1);
  lcd_1.print(temp);
  delay(10); // Delay a little bit to improve simulation performance
}
```

## Future Scope
- Add buzzer/LED alert when temperature exceeds threshold
- Integrate with IoT platforms (Wi-Fi/Bluetooth) for remote monitoring
- Add data logging for historical temperature analysis
- Support multiple sensors for multi-zone monitoring

## Conclusion
The Smart Temperature Monitor provides a simple, cost-effective, and reliable solution for real-time temperature monitoring, forming the foundation for more advanced smart environmental monitoring systems.
