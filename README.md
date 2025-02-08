MH-Z19B ESP32 Library
=====================

Overview
--------

This library provides an easy-to-use interface for the **MH-Z19B CO₂ sensor** on the **ESP32**, utilizing **hardware UART** for communication. The library supports flexible pin selection and includes functions to read CO₂ concentration, calibrate the sensor, enable/disable auto-calibration, and configure the detection range.

Features
--------

*   Uses **ESP32 hardware UART** (no SoftwareSerial required)

*   Allows **custom UART pins**

*   Supports the following MH-Z19B commands:

    *   Read CO₂ concentration (`0x86`)

    *   Zero point calibration (`0x87`)

    *   Span calibration (`0x88`)

    *   Auto-calibration on/off (`0x79`)

    *   Set detection range (`0x99`)

*   Automatic **checksum calculation** for data integrity


Installation
------------

1.  Download the library files (`MHZ19B_ESP32.h` and `MHZ19B_ESP32.cpp`).

2.  Place them in your Arduino project's `src/` directory.

3.  Include the header in your code:

    #include "MHZ19B\_ESP32.h"


Usage
-----

### Basic Example

#include "MHZ19B\_ESP32.h"



MHZ19B sensor(Serial2, 16, 17); // Use UART2 with GPIO16 (RX) & GPIO17 (TX)



void setup() {

Serial.begin(115200);

sensor.begin();

}



void loop() {

int co2 = sensor.readCO2();

Serial.print("CO2 Concentration: ");

Serial.println(co2);

delay(2000);

}

Notes
-----

*   **Ensure correct wiring:** The sensor operates at **3.3V UART level**, so direct connection to ESP32 pins is fine.

*   **Preheat Time:** The sensor requires **3 minutes** to warm up before stable readings.

*   **Zero Calibration:** Run `sensor.calibrateZero();` in fresh air (~400 ppm) and wait 20 minutes before execution.


License
-------

This library is open-source and free to use in personal and commercial projects.

* * *

For issues and contributions, feel free to create a pull request or open an issue.
