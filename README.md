<div align="center">

# nRF24 Jammer
<img src="/image.jpg" alt="Jammer image" width="400" style="border-radius: 10px;">

---

### Overview
Many clones of nRF24 modules work more effectively when targeting specific sequential channels rather than the entire spectrum. This implementation focuses on **13 specific channels** (out of 79) to maximize interference density.

**Targeting:** Effective against **Bluetooth BR/LE** devices and **WiFi Channels 1-14**.

</div>

---

### Technical Insights
*   **Optimal Performance:** To maximize spectrum coverage, hold the jammer by the cable or through a non-conductive surface.
*   **Power Consumption:** Uses approximately **1W**. A 150mAh battery provides **~30 minutes** of continuous operation.
*   **Range:** This is a low-power device. Don't expect effective jamming outside a **~10 meter** radius.
*   **Thermal Note:** Testing shows performance improves once the chip reaches operating temperature. Wait **30 seconds** before repositioning.

<div align="center">
  <img src="/spectrum.jpg" alt="Jammer spectrum analysis" width="600" style="border: 1px solid #ddd;">
</div>

---

### Hardware Requirements
| Item | Quantity |
| :--- | :---: |
| **ESP32 WROOM-32** Dev Board | 1 |
| **nRF24L01+ PA+LNA** Module | 1 |
| **Jumper Cables** | 7 |

---

### Wiring Diagram
| ESP32 WROOM-32 Pin | nRF24L01+ Pin | Function |
| :--- | :--- | :--- |
| **3V3** | VCC | Power (3.3V) |
| **GND** | GND | Ground |
| **GPIO 12** | CE | Chip Enable |
| **GPIO 5** | CSN | Chip Select / Slave Select |
| **GPIO 18** | SCK | SPI Clock |
| **GPIO 23** | MOSI | SPI Master Out Slave In |
| **GPIO 19** | MISO | SPI Master In Slave Out |
| *(Not connected)* | IRQ | Interrupt (optional) |

---

### Flashing Tutorial

#### 1. Environment Setup
*   Install the [Arduino IDE](https://www.arduino.cc/en/software).
*   **Boards Manager:** Search for `esp32` (by Espressif Systems) and install.
*   **Library Manager:** Search for `RF24` and install.

#### 2. Preparation
1.  Open [nrf_jammer.ino](/nrf_jammer.ino) and copy the code.
2.  Paste it into a new Arduino IDE project.
3.  **Linux Users:** Run `sudo chmod 777 /dev/ttyUSB0` to grant port permissions.

#### 3. Uploading
1.  Hold the **BOOT** button on the ESP32 while plugging it into your PC.
2.  In Arduino IDE, go to **Select Board** → **Select other board and port...**
3.  Search for `ESP32 Dev Module` and select your COM/TTY port.
4.  Click the **Upload** (Arrow) button.

---

> [!TIP]
> **Timeout Error:** If you encounter a timeout while downloading the ESP32 board library, refer to [this community thread](https://forum.arduino.cc/t/downloading-esp32-3-3-5-fails/1420739) for a fix.
