# 🔋 4-Cell Battery Management & Safety Monitoring System
## 🔗 Project Links

- 🧪 **Wokwi Simulation:** [Open Wokwi Project]([YOUR_WOKWI_LINK](https://wokwi.com/projects/476036431640472577))
- ☁️ **Blynk Dashboard:** [View Blynk Dashboard](https://blynk.cloud/dashboard/760290/global/devices/290445/organization/760290/devices/2283210/dashboard)

An **ESP32-based intelligent Battery Management System (BMS)** designed to monitor, analyze, protect, diagnose, and remotely visualize a simulated **4-cell lithium battery pack** in real time.

The project combines **battery voltage monitoring, battery analytics, fault detection, event-driven safety protection, LCD-based HMI, and Blynk IoT cloud monitoring** in a non-blocking embedded architecture.

## 🚀 Key Features

* 🔋 Individual monitoring of 4 battery cells
* 📊 Pack voltage and average voltage calculation
* ⚖️ Cell voltage difference and imbalance detection
* 🔎 Strongest and weakest cell identification
* ❤️ Battery health classification
* 🛡️ Event-driven safety protection
* ⚠️ Undervoltage and overvoltage detection
* 📈 Rapid voltage fluctuation detection
* 🔌 Sensor fault detection
* 🔄 Automatic fault recovery
* 🖥️ 20×4 I2C LCD HMI
* 🔴🟡🟢 Status LEDs
* 🔔 Buzzer and relay protection
* ☁️ Blynk IoT cloud monitoring
* ⏱️ Non-blocking `millis()`-based architecture
* 🧪 Complete Wokwi simulation

## 🧠 Battery Intelligence

The system continuously processes the four cell voltages and calculates:

```text
Pack Voltage = V1 + V2 + V3 + V4

Average Voltage = Pack Voltage / 4

Voltage Difference = Vmax - Vmin

Imbalance (%) = (Vmax - Vmin) / Vavg × 100
```

ADC averaging and EMA filtering are used to stabilize the simulated voltage measurements.

### Battery Health States

* **Healthy**
* **Minor Imbalance**
* **Critical Imbalance**
* **Pack Failure**

## 🛡️ Safety Protection

The protection system monitors six major abnormal conditions:

1. Undervoltage
2. Overvoltage
3. Pack abnormality
4. Excessive cell imbalance
5. Rapid voltage fluctuation
6. Invalid sensor data

The protection logic uses timing confirmation to reduce false trips and relay chattering.

### Protection State Machine

```text
             Warning Condition
SAFE ───────────────────────────► WARNING
 ▲                                  │
 │                                  │ Fault Confirmed
 │                                  ▼
 │                              TRIPPED
 │                                  │
 │                         Safe + Stable
 │                                  ▼
 └────────────── RECOVERY ◄─────────┘
```

The four states are:
*🟢 SAFE – Normal operation
*🟡 WARNING – Abnormal condition detected
*🔴 TRIPPED – Fault confirmed and protection activated
*🔵 RECOVERY – Conditions become safe and stable
*🟢 SAFE – System resumes normal operation

## 🔧 Hardware / Simulation Components
______________________________________________________
| Component          | Purpose                       |
| ------------------ | ----------------------------- |
| ESP32              | Main controller               |
| 4 × Potentiometers | Simulated cell-voltage inputs |
| 20×4 I2C LCD       | Local HMI                     |
| Relay              | Battery protection/cutoff     |
| Buzzer             | Fault warning                 |
| Green LED          | Normal status                 |
| Yellow LED         | Warning status                |
| Red LED            | Critical fault                |
| Wi-Fi              | Cloud communication           |
| Blynk              | Remote monitoring             |
------------------------------------------------------
The simulated cell-voltage range is **2.50 V–4.20 V**.

## 📌 ESP32 Pin Configuration
___________________________
| Function   | ESP32 GPIO |
| ---------- | ---------: |
| Cell 1     |    GPIO 32 |
| Cell 2     |    GPIO 33 |
| Cell 3     |    GPIO 34 |
| Cell 4     |    GPIO 35 |
| Relay      |    GPIO 25 |
| Buzzer     |    GPIO 26 |
| Green LED  |    GPIO 27 |
| Yellow LED |    GPIO 14 |
| Red LED    |    GPIO 12 |
| LCD SDA    |    GPIO 21 |
| LCD SCL    |    GPIO 22 |
---------------------------

## 🖥️ LCD Monitoring

The 20×4 LCD automatically rotates through four information screens:

1. **Cell Monitoring** – Individual cell voltages and health
2. **Pack Analytics** – Pack voltage, average voltage, imbalance
3. **Cell Analysis** – Strongest/weakest cell and voltage difference
4. **Protection** – Protection state, relay, buzzer, and fault reason

## ☁️ Blynk IoT Monitoring

Blynk provides remote visualization of:

* Cell voltages
* Pack voltage
* Average voltage
* Imbalance percentage
* Strongest/weakest cell
* Battery health
* System/protection status
* Relay and buzzer status
* Diagnostics and trends

Local protection continues to operate independently of cloud connectivity.

## 🧪 Wokwi Simulation

The complete system is simulated using **Wokwi**.

The simulation supports testing of:

* Normal operation
* Cell imbalance
* Undervoltage
* Overvoltage
* Sensor faults
* Rapid voltage changes
* Protection trips
* Fault recovery
* Wi-Fi disconnection/reconnection

## 🛠️ Technologies Used

* **ESP32**
* **Embedded C / Arduino**
* **Wokwi**
* **Blynk IoT**
* **I2C LCD**
* **ADC**
* **millis()-based scheduling**
* **Finite State Machine (FSM)**
* **Signal filtering**
* **Embedded fault handling**

## 📊 Verification

The system is verified through tests covering:

* Cell measurements
* Battery calculations
* Health classification
* Fault detection
* Protection states
* Relay operation
* Buzzer and LED responses
* LCD information
* Blynk telemetry
* Recovery behavior

The project documentation defines **15 test cases** covering major normal and fault conditions.

## ⚠️ Limitations

This project is a **simulation-based prototype**, not a production-certified BMS.

Current limitations include:

* Potentiometers do not reproduce real battery chemistry
* No current measurement
* No physical cell balancing
* No real temperature monitoring
* No certified battery safety thresholds
* Wokwi cannot fully reproduce real electrical and thermal battery behavior

## 🔮 Future Enhancements

Possible future improvements include:

* Current sensing
* State-of-Charge (SoC) estimation
* Temperature monitoring
* Active/passive cell balancing
* Persistent fault logging
* OTA firmware updates
* MQTT communication
* AI-based battery fault prediction
* Battery degradation analysis

## 🎯 Project Outcome

This project demonstrates how an **ESP32-based embedded system** can integrate battery monitoring, analytics, safety protection, diagnostics, HMI, fault handling, and IoT monitoring into a single architecture.

It provides a foundation for further development toward real-world battery monitoring and management applications.

---

### 👨‍💻 Project Type

**Embedded Systems | Battery Management System | IoT | ESP32 | Wokwi Simulation**

> **“A battery may store energy, but intelligent engineering gives that energy direction, protection, and purpose.”**
