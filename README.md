CSE406 Lab Assignment 02: Water Level Monitoring System
Show Image
Show Image
Show Image
📋 Project Overview
Real-time water level monitoring system using Arduino Uno and an analog water level sensor. This project demonstrates comprehensive sensor interfacing, data processing, threshold-based alerting, and real-time visualization techniques for IoT applications.
📝 Detailed Description
This laboratory assignment focuses on developing a complete IoT solution for water level monitoring. The system reads analog signals from a water level sensor, processes the raw data through calibration and mapping algorithms, implements intelligent threshold-based alerting, and calculates real-time rate of change to predict water level trends.
Key Capabilities:

Real-time Monitoring: Continuous measurement of water levels with 10 Hz sampling rate (10 readings per second)
Intelligent Processing: Converts raw ADC values (0-1023) to intuitive percentage scale (0-100%) using linear interpolation
Smart Alerting: Four-tier alarm system provides early warnings before critical water levels are reached
Trend Analysis: Rate of change calculation enables predictive insights into water level behavior
Dual Visualization: Supports both text-based Serial Monitor and graphical Serial Plotter interfaces

Practical Applications:

Water tank level monitoring in residential buildings
Industrial liquid level control systems
Flood detection and early warning systems
Aquarium water level management
Agricultural irrigation monitoring
Laboratory liquid handling automation

Technical Implementation:
The water level sensor operates as a variable resistor, changing its resistance based on the amount of water contact. More water coverage increases conductivity, raising the output voltage. The Arduino's 10-bit ADC reads this voltage and converts it to digital values. Through calibration and mathematical mapping, these raw values are transformed into meaningful percentage readings that trigger appropriate alerts based on predefined thresholds.
This project serves as a foundational building block for more complex IoT applications, demonstrating essential concepts such as analog signal processing, state management, data normalization, conditional logic implementation, and serial communication protocols.

👤 Author Information

Name: Rafi Uddin
Student ID: 2022-1-60-037
Course: CSE406 - Internet of Things
Lab Assignment: 02 - Analog Sensor Interfacing
Date: October 6, 2025


🎯 Course Outcome
CO4: Designing and implementing end-to-end IoT solutions
This lab assignment contributes directly to achieving CO4 by providing hands-on experience with:

Analog sensor integration
Real-time data acquisition and processing
Alert system implementation
Data visualization techniques


🛠️ Hardware Requirements
ComponentSpecificationQuantityArduino Uno BoardATmega328P1Water Level SensorAnalog output1BreadboardStandard size1Jumper WiresMale-to-Male3+USB CableType A to Type B1Water ContainerAny suitable container1

💻 Software Requirements

Arduino IDE (Version 1.8.x or 2.x)
Serial Monitor (Built into Arduino IDE)
Serial Plotter (Built into Arduino IDE)
Operating System: Windows/Mac/Linux


🔌 Circuit Diagram
Wiring Connections
Water Level Sensor         Arduino Uno
─────────────────         ────────────
    S (Signal)    ────►      A0
    + (VCC)       ────►      5V
    - (GND)       ────►      GND
Pin Mapping Table
Sensor PinDescriptionArduino PinFunctionSSignal OutputA0Analog input for water level reading+Power Supply5VProvides 5V power to sensor-GroundGNDCommon ground reference

✨ Features Implemented
📊 Task 1: Data Mapping & Visualization

✅ Converts raw analog values (0-1023) to percentage scale (0-100%)
✅ Implements proper sensor calibration
✅ Uses map() and constrain() functions for accurate conversion
✅ Real-time visualization via Serial Plotter
✅ Displays both raw values and percentage simultaneously

🚨 Task 2: Threshold-Based Alarm System

✅ Low Level (25%): Informational alert
✅ Medium Level (75%): Warning message
✅ High Level (95%): Critical alert
✅ Four distinct status states with clear messaging
✅ Cascading if-else logic for proper priority handling

📈 Task 3: Rate of Change Calculation

✅ Calculates water level change rate
✅ Positive values indicate rising water
✅ Negative values indicate falling water
✅ Zero values indicate stable level
✅ Visual trend indicators (↑ ↓ →)
✅ Helps predict water level behavior


📥 Installation & Setup
Step 1: Clone Repository
bashgit clone https://github.com/rafiuddin/CSE406-Lab02.git
cd CSE406-Lab02
Step 2: Open Arduino IDE

Launch Arduino IDE
Go to File → Open
Navigate to the cloned folder
Open CSE406_Lab02_WaterLevelMonitoring.ino

Step 3: Calibrate Sensor
Before uploading, calibrate your specific sensor:

Dry Calibration:

Keep sensor completely dry
Upload basic code and note the raw value
Update dryValue constant (typically 0-50)


Wet Calibration:

Fully submerge sensor to MAX line
Wait 2-3 seconds for stable reading
Note the raw value (typically 500-800)
Update wetValue constant



Step 4: Connect Hardware

Connect water level sensor to Arduino as per circuit diagram
Plug Arduino into computer via USB cable
Ensure proper contact for all connections

Step 5: Upload Code

Select Tools → Board → Arduino Uno
Select Tools → Port → COM# (Arduino Uno)
Click Upload button (→)
Wait for "Done uploading" message

Step 6: Monitor Output
For Serial Monitor:

Open Tools → Serial Monitor (Ctrl+Shift+M)
Set baud rate to 9600
View formatted readings and alerts

For Serial Plotter:

Open Tools → Serial Plotter (Ctrl+Shift+L)
Set baud rate to 9600
Use plotter-optimized code version (see comments)


🎮 Usage Instructions

Power On:

Connect Arduino to computer or external 5V power supply
System initializes and displays welcome message


Testing:

Start with sensor completely dry
Gradually dip sensor into water container
Observe real-time readings and alerts
Test all threshold levels (25%, 75%, 95%)


Monitoring:

Serial Monitor shows detailed text output
Serial Plotter provides graphical visualization
Note rate of change indicators for trends


Safety:

Never submerge sensor beyond MAX line
Keep Arduino board away from water
Disconnect power before adjusting wiring




📊 Expected Output
Serial Monitor Output Example
==========================================================
   CSE406 - Lab 02: Water Level Monitoring System
==========================================================
Initializing sensor...
Calibration Values:
  - Dry Value:  0
  - Wet Value:  700
----------------------------------------------------------
System ready. Starting measurements...
==========================================================

Raw: 0 | Level: 0% | Rate: 0%/s | ✓ STATUS: Normal - Water level very low [STABLE →]
Raw: 175 | Level: 25% | Rate: +25%/s | ℹ️ INFO: Low water level [RISING ↑]
Raw: 350 | Level: 50% | Rate: +25%/s | ℹ️ INFO: Low water level [RISING ↑]
Raw: 525 | Level: 75% | Rate: +25%/s | ⚠️ WARNING: Medium water level detected [RISING ↑]
Raw: 665 | Level: 95% | Rate: +20%/s | ⚠️ ALERT: HIGH WATER LEVEL! CRITICAL! [RISING ↑]
Raw: 700 | Level: 100% | Rate: +5%/s | ⚠️ ALERT: HIGH WATER LEVEL! CRITICAL! [RISING ↑]
Raw: 665 | Level: 95% | Rate: -5%/s | ⚠️ ALERT: HIGH WATER LEVEL! CRITICAL! [FALLING ↓]
Raw: 525 | Level: 75% | Rate: -20%/s | ⚠️ WARNING: Medium water level detected [FALLING ↓]
Serial Plotter Visualization
The Serial Plotter displays three lines:

Line 1 (Blue): Raw sensor value (0-1023 range)
Line 2 (Red): Water level percentage (0-100 range)
Line 3 (Green): Rate of change (-100 to +100 range)


🏗️ Code Structure
CSE406_Lab02_WaterLevelMonitoring.ino
│
├── Global Constants
│   ├── Pin definitions (sensorPin)
│   ├── Calibration values (dryValue, wetValue)
│   └── Threshold constants (LOW_LEVEL, MEDIUM_LEVEL, HIGH_LEVEL)
│
├── Global Variables
│   ├── previousLevel (rate calculation)
│   └── firstReading (initialization flag)
│
├── setup()
│   ├── Initialize serial communication (9600 baud)
│   └── Display system information and calibration values
│
└── loop()
    ├── Read analog sensor value (analogRead)
    ├── Task 1: Map raw value to percentage
    ├── Task 3: Calculate rate of change
    ├── Task 2: Check alarm thresholds
    ├── Display formatted output
    ├── Update previous level
    └── Delay 100ms

🔧 Calibration Guide
Why Calibration is Important
Each water level sensor has slightly different characteristics. Proper calibration ensures:

Accurate percentage readings
Correct threshold triggering
Reliable rate of change calculations

Calibration Process
Step 1: Find Dry Value
cppconst int dryValue = 0;  // Update with your measured value

Ensure sensor is completely dry
Upload basic reading code
Open Serial Monitor
Note the stable raw value (usually 0-50)
Update dryValue in code

Step 2: Find Wet Value
cppconst int wetValue = 700;  // Update with your measured value

Fill container with water
Fully submerge sensor to MAX line
Wait 2-3 seconds for reading to stabilize
Note the raw value (typically 500-800)
Update wetValue in code

Step 3: Verify Calibration

Dry sensor should read ~0%
Fully submerged sensor should read ~100%
Partial submersion should show proportional values


🐛 Troubleshooting
ProblemPossible CauseSolutionErratic/jumping readingsPoor connections, electrical noiseClean sensor contacts, check wiring, ensure stable powerAlways reads 0Sensor not connectedVerify wiring, check if S pin connected to A0Always reads 1023Short circuit or wrong connectionCheck all connections, ensure +/- not reversedPercentage exceeds 100%Incorrect wetValue calibrationRecalibrate with fully submerged sensorNo response when submergedSensor damaged or wrong typeTest with multimeter, verify sensor is analog typeUpload failsWrong COM port or board selectionCheck Tools → Port and Tools → Board settingsRate of change unstableWater movement or delay too shortKeep water still, increase delay to 200msSerial Monitor blankWrong baud rateEnsure Serial Monitor set to 9600 baud

📚 Learning Outcomes Achieved
Through this lab assignment, I have gained practical experience in:
✅ Analog Sensor Interfacing

Understanding ADC (Analog-to-Digital Conversion)
Working with 10-bit resolution (0-1023 values)
Proper sensor wiring and power management

✅ Data Processing

Using analogRead() for sensor data acquisition
Implementing map() function for value conversion
Applying constrain() for data validation

✅ Conditional Logic

Designing threshold-based systems
Implementing cascading if-else structures
Creating priority-based alert systems

✅ Algorithm Development

Rate of change calculation
State tracking between iterations
Trend analysis and prediction

✅ Serial Communication

UART protocol at 9600 baud
Formatted data output
Real-time monitoring techniques

✅ Data Visualization

Serial Monitor for detailed output
Serial Plotter for graphical representation
Multi-stream data plotting


🚀 Future Enhancements
Potential improvements for extended functionality:

 LCD Display Integration: Add 16x2 LCD for standalone operation
 SD Card Logging: Store historical data for analysis
 WiFi Connectivity: ESP8266/ESP32 for IoT cloud integration
 Web Dashboard: Real-time monitoring via web interface
 Audio Alerts: Buzzer for critical level warnings
 Moving Average Filter: Implement smoothing algorithm for stable readings
 Multiple Sensors: Monitor multiple tanks simultaneously
 SMS Notifications: Send alerts via GSM module
 Battery Backup: Add power management for remote deployment
 Machine Learning: Predict water consumption patterns


📖 References & Resources

Arduino Official Documentation: https://www.arduino.cc/reference/en/
analogRead() Reference: https://www.arduino.cc/reference/en/language/functions/analog-io/analogread/
map() Function: https://www.arduino.cc/reference/en/language/functions/math/map/
Serial Communication: https://www.arduino.cc/reference/en/language/functions/communication/serial/
Course Materials: CSE406 Lecture Notes and Lab Manuals


📄 License
This project is created for educational purposes as part of CSE406 coursework at East West University.
Academic Integrity Statement: This code is submitted as original work for Lab Assignment 02. All implementations are based on course materials and personal understanding.
📞 Contact Information
Rafi Uddin

Student ID: 2022-1-60-037
Email: 2022-1-60-037@std.ewubd.edu
GitHub: https://github.com/iamiot15/CSE406


📊 Project Statistics

Lines of Code: ~250 (including comments)
Comment Ratio: ~60% (thoroughly documented)
Functions Used: 7 core Arduino functions
Tasks Completed: 3/3 (100%)
Testing Status: ✅ Fully tested and verified
Code Quality: Production-ready with error handling


🔗 Repository Information
GitHub Repository: https://github.com/rafiuddin/CSE406-Lab02
Repository Contents:
CSE406-Lab02/
│
├── README.md                                      (This file)
├── CSE406_Lab02_WaterLevelMonitoring.ino         (Main Arduino sketch)
├── .gitignore                                     (Arduino gitignore)
└── documentation/                                 (Optional: screenshots, diagrams)
    ├── circuit_diagram.png
    ├── serial_monitor_output.png
    └── serial_plotter_screenshot.png

📅 Version History
VersionDateDescription1.0October 6, 2025Initial release with all three tasks completed

✅ Submission Checklist

 Code thoroughly commented
 All three tasks implemented and tested
 README.md created with complete documentation
 Repository is public
 Repository name: CSE406-Lab02
 Code uploaded to GitHub
 Repository URL ready for submission
 All requirements met


Last Updated: October 6, 2025
