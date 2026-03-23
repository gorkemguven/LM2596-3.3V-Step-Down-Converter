# LM2596-3.3V High-Efficiency Step-Down (Buck) Converter

This project features a robust and optimized **3.3V DC-DC Step-Down Converter** based on the **LM2596-3.3** fixed-voltage regulator. The design focuses on high-grade component selection to ensure long-term stability, low EMI, and minimal output ripple for sensitive electronic loads.

## 🚀 Technical Specifications

- **Topology:** Non-isolated Buck (Step-Down)
- **Input Voltage ($V_{IN}$):** 4.75V – 40V (Optimized for high-voltage transients)
- **Output Voltage ($V_{OUT}$):** Fixed 3.3V
- **Max Output Current:** 3A (with appropriate thermal dissipation)
- **Switching Frequency:** 150 kHz
- **Target Applications:** ESP32/STM32 power supply, IoT Gateways, Industrial sensors.

## 🛠 Engineering Design Decisions

### 1. Fixed Voltage Precision
By using the **LM2596S-3.3** (Fixed version), we eliminated the need for external feedback resistors. This design decision significantly improves noise immunity at the feedback node and ensures higher output accuracy by utilizing the internal laser-trimmed resistor network of the IC.

### 2. High-Performance Filtering (BOM Excellence)
The component selection prioritizes Low-ESR (Equivalent Series Resistance) and thermal stability:
* **Rubycon ZLH Series (C1):** A high-reliability, low-impedance capacitor used for input bulk filtering to handle ripple currents effectively.
* **Tantalum Output Filtering (C4):** The addition of a 10µF Tantalum capacitor (TCTP1C106M8R) provides superior high-frequency response and much lower ESR compared to standard electrolytic capacitors, minimizing output voltage spikes.
* **Shielded Inductor (L1):** The Bourns SRR1280 series ensures low EMI radiation and high saturation current.



[Image of buck converter schematic diagram]


## 📋 Bill of Materials (BOM)

| Designator | Manufacturer Part Number | Value / Description | Package | Purpose |
| :--- | :--- | :--- | :--- | :--- |
| **U1** | **LM2596S-3.3** | Regulator (Fixed 3.3V) | TO-263-5 | Main Switching Regulator |
| **L1** | **SRR1280-330M** | 33µH Shielded Inductor (3.6A) | SMD (12x12) | Energy Storage |
| **D1** | **ACDBA560-HF** | Schottky Diode (60V/5A) | DO-214AC | Catch Diode |
| **C1** | **100ZLH100MEFC10X20** | 100µF 100V (Rubycon ZLH) | Radial | Input Bulk Filter |
| **C2** | **MCASH21GSB7104KTNA01** | 100nF 50V (X7R MLCC) | 0805 | High-Freq Input Bypass |
| **C3** | **80-ESH227M063AH4AA** | 220µF 63V (KEMET ESH) | Radial | Output Filter |
| **C4** | **TCTP1C106M8R** | 10µF 16V (Tantalum) | 0805 (P) | Low-ESR Ripple Filter |



## 📐 PCB Layout Considerations

To achieve the best performance, the following layout rules were followed:
1. **The Power Loop:** The path between the input capacitor, the LM2596, and the Schottky diode is kept extremely short to reduce parasitic inductance.
2. **Ground Plane:** A solid ground plane is used on the bottom layer to provide a low-impedance return path and aid in heat dissipation.
3. **Thermal Vias:** Multiple vias are placed under the LM2596 tab to transfer heat to the bottom copper layer.



## 📄 License
This project is licensed under the **MIT License** - see the LICENSE file for details.

---
*Designed with precision by [Görkem Güven](https://github.com/gorkemguven)*
