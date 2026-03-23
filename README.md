# LM2596-3.3V High-Efficiency Step-Down (Buck) Converter

This project features a robust and optimized **3.3V DC-DC Step-Down Converter** based on the widely used **LM2596-3.3** fixed-voltage regulator. The design is focused on power stability, low output ripple, and minimal component count for industrial-grade applications.

## 🚀 Technical Specifications

- **Topology:** Non-isolated Buck (Step-Down)
- **Regulator IC:** LM2596S-3.3 (Fixed Voltage Version)
- **Input Voltage ($V_{IN}$):** 4.75V – 40V (Recommended $V_{IN} > 5.5V$ for stability)
- **Output Voltage ($V_{OUT}$):** Fixed 3.3V
- **Max Output Current:** 3A (with proper thermal management)
- **Switching Frequency:** 150 kHz
- **Output Ripple:** Optimized with additional MLCC decoupling

## 🛠 Engineering Design Decisions

### 1. Fixed vs. Adjustable Selection
Unlike common adjustable designs, this project utilizes the **Fixed 3.3V** version of the LM2596. 
* **Benefit:** By removing external feedback resistors, we eliminated potential noise injection at the feedback node and reduced the Bill of Materials (BOM) cost.
* **Accuracy:** Internal laser-trimmed resistors provide higher precision than standard 1% external resistors.

### 2. Advanced Noise Filtering
To ensure stability for sensitive electronics (like ESP32 or STM32), the following capacitors were added:
* **Input Bypass (100nF X7R MLCC):** Placed close to the VIN pin to suppress high-frequency switching noise.
* **Output Ripple Reduction (10uF X5R MLCC):** Placed in parallel with the main 220uF electrolytic capacitor to reduce ESR and high-frequency voltage spikes.


## 📋 Bill of Materials (BOM)

| Component | Value / Part No | Package | Purpose |
| :--- | :--- | :--- | :--- |
| **U1** | LM2596S-3.3 | TO-263-5 | Step-Down Regulator |
| **L1** | 33µH (SRR1280) | SMD | Power Inductor |
| **D1** | ACDBA560-HF | DO-214AC | Schottky Diode (60V/5A) |
| **C1** | 100µF | Electrolytic | Input Bulk Cap |
| **C2** | 100nF | 0805 (X7R) | High-Freq Input Bypass |
| **C3** | 220µF | Electrolytic | Output Filter Cap |
| **C4** | 10µF | 0805 (X5R) | Low-ESR Output Ripple Filter |

## 📐 PCB Layout Considerations

For optimal performance:
1. **Power Loop:** The loop between $V_{IN}$, the IC, the Diode, and the Ground is kept as short as possible to minimize EMI.
2. **Thermal Management:** Large copper pours are used around the GND pins of the LM2596 to act as a heatsink.
3. **Feedback Trace:** The FB trace (Pin 4) is routed away from the inductor (L1) to avoid magnetic interference.

## 📄 License
This project is licensed under the **MIT License** - feel free to use it for your own hardware projects!

---
*Designed with ❤️ by [Görkem Güven](https://github.com/gorkemguven)*
