# ⚡ Universal Smart-Home Modular Hub  
A compact, scalable, multi-protocol communication platform designed for modern smart homes.  
Built around a powerful **ESP32-S3**, with plug-in radio modules for Zigbee/Thread and Proprietary RF.  
Reliable power architecture, clean RF design, and automatic module detection.

---

## 🌍 Overview  
This system uses a **three-board modular hub architecture**:

### **1) Main Board – ESP32-S3 Controller**
Contains the ESP32-S3 with native **Wi-Fi + Bluetooth LE**, full power management, Ethernet support, and the universal expansion bus.

### **2) Zigbee/Thread Module – EFR32MG24**
A dedicated 2.4 GHz radio module supporting **Zigbee**, **Thread**, and **Matter over Thread** with a high-efficiency antenna.

### **3) Proprietary RF Module – nRF24L01+**
A flexible low-power 2.4 GHz module for **custom protocols**, legacy devices, and private links.

⚠️ **Only one expansion module is active at a time.**  
The **Main Board can run standalone** using Wi-Fi and BLE even with no module attached.

---

## 🎯 Problem This Project Solves  
Most smart-home hubs are:

- Locked to one brand or protocol  
- Difficult to expand  
- Closed hardware  
- Not modifiable or repairable  
- Dependent on cloud services  
- Not designed for RF noise isolation  

This project solves these issues with a fully documented, open, modular, serviceable platform.

---

# 🚀 Main Features

---

## 🧠 Main Board – ESP32-S3 Core Controller  

### **Capabilities**
- Native Wi-Fi + BLE  
- USB programming  
- JTAG debugging  
- I²C bus for module identification  
- SPI bus shared with expansion modules  
- Presence-detect signal  
- Ethernet PHY  
- Local battery backup  
- Clean, isolated power rails  

### **Standalone Operation**
If no radio module is plugged in, the board still supports:

- Wi-Fi control  
- BLE provisioning  
- Local automation  
- OTA updates  

---

## 📡 Zigbee / Thread / Matter Module – EFR32MG24  

### **Capabilities**
- Zigbee 3.0  
- Thread 1.3  
- Matter over Thread  
- High-efficiency chip antenna or external u.FL  
- SPI + IRQ communication  
- Local low-noise LDO  
- EEPROM with module ID  
- Hardware reset & enable control  
- SWD header for development  

### **Why a Separate Board?**
- RF noise isolation  
- Easy upgrades  
- Thermal and EMI improvements  
- Lower main-board complexity  

---

## 📡 Proprietary RF Module – nRF24L01+  

### **Capabilities**
- 2.4 GHz bidirectional transceiver  
- SPI interface  
- IRQ line  
- CE line for TX/RX control  
- Local LDO for clean RF power  
- On-board EEPROM for identification  

### **Why It Exists**
- Legacy systems  
- Private, encrypted links  
- Ultra-low-power sensors  
- Custom protocols  

---

# 🔋 Power Architecture

### **Main Board**
- 12 V input  
- Step-down to 5 V  
- 3.3 V LDO for logic  
- Local LDOs for each RF module  
- Battery charger & backup  
- Inrush, surge, ESD protection  
- Proper decoupling everywhere  

### **Radio Modules**
- Dedicated LDO  
- Ferrite-bead power filtering  
- Enable pin for power control  
- RF-clean power domain  

---

# 🧩 Automatic Module Identification (EEPROM)

Every expansion module includes a **24AA02E48 EEPROM** that stores:

- Unique EUI-48  
- Module type ID  

The ESP32 reads the EEPROM via I²C on boot and:

1. Identifies the module type  
2. Powers only the selected module  
3. Loads the appropriate firmware configuration  

---

# 🛡️ Reliability & Safety

- TVS on power rails  
- ESD protection on connectors  
- Solid ground planes  
- RF-clean routing  
- Ferrite-bead domain separation  
- Reverse-polarity protection  
- Controlled RF impedance paths  

---

# 🧭 Why This Architecture Is Better

- **Fully modular** — plug-in radio modules  
- **Upgradable** — replace modules anytime  
- **Main board works standalone**  
- **Automatic detection** via EEPROM  
- **Clean RF design** with isolated power  
- **Open hardware**  
- **Supports Wi-Fi, BLE, Zigbee, Thread, Matter, Proprietary RF**  
- **Future-proof** platform  
- **Easy to manufacture & repair**  

---

# 🛠️ Usage

1. Power the Main Board with 12 V  
2. Plug in a Zigbee or Proprietary RF module  
3. Firmware reads the module EEPROM  
4. Selected module is powered via EN_LDO  
5. ESP32 configures SPI/I²C pins  
6. Start using the hub via Wi-Fi, BLE, or RF  

---

# 🚀 Getting Started

1. Download design files  
2. Open schematic and PCB in KiCad  
3. Review:
   - Power sections  
   - Module connector  
   - RF networks  
   - Decoupling and filtering  
4. Manufacture PCBs  
5. Assembly order:
   1. Power stage  
   2. ESP32-S3 main board  
   3. Expansion connectors  
   4. RF module components  
   5. Antennas  
6. Flash the ESP32-S3 via USB  
7. Flash EFR32 module via SWD (if needed)  
8. Test and integrate with your smart-home backend  

---

# 🪪 License  
This project is licensed under the MIT License. See the [MIT License ↗](https://opensource.org/license/mit/) file for more information.
