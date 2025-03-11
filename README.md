# Overview
<img src="https://github.com/user-attachments/assets/25bb6b1d-0c7f-405f-9b2d-d43ba2f852da" width="40%" height="40%">


With the growing number of sensors in my garden, I needed a reliable way to integrate them with Home Assistant. While searching for an existing solution, I quickly realized that most available options were either lacking essential features or required unnecessary complexity. None of them met my needs, so I decided to build my own.

# Key Features
- ESP32-Based
- Compatible with ESPHome.
- Ethernet Interface
- Integrated DC-DC Converter
- I2C Accelerator footprint
- Screw Terminals

# Hardware
<img src="https://github.com/user-attachments/assets/0628e098-4e27-4df9-9126-5b242d2ca340" width="40%" height="40%">

### ESP32
ESP32 is an affordable, widely available microcontroller combatibile with ESPHome, making it an ideal choice for smart home automation and IoT projects.

### Ethernet connector
I used an integrated Magjack from TE (TE 2301994-2). I’m aware that it’s not the cheapest option, and there are plenty of more affordable alternatives available on AliExpress. However, in a previous project, I used one of those cheaper substitutes and ended up wasting a lot of time troubleshooting a non-working connection, only to discover that the Magjack itself was faulty. This time, I decided to go with a reliable, component to avoid unnecessary debugging and ensure stable Ethernet performance.

### Ethernet controller
I decided to use the LAN7820, which is one of the most popular Ethernet PHYs for DIY enthusiasts and development boards. It is also fully compatible with ESPHome.

### Power
The DC/DC converter is based on the MIC4684, which converts input voltages of up to 32V to 5V, which is then regulated to 3.3V by the MIC39100-3.3. 

In the previous version, I used PoE with the LTC4267, but I wasn’t completely satisfied with its performance. The PoE solution required a lot of additional components, which increased the overall cost. Additionally, I didn't properly protect the LAN7820 chip, and after several cycles of plugging and unplugging the Ethernet cable, I ended up damaging the chip. In this version, I decided to use affordable external active or passive PoE splitters from AliExpress.

### i2c accelerator
I added an extra footprint for the LTC4311 chip on the board to extend the range of the I2C bus. This allows for more reliable communication over longer distances.

# Software
The software includes a YAML file that contains the configuration for Ethernet and the I2C pins.
