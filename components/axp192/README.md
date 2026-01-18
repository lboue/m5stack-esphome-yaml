# AXP192 Power Manager 

## Connections on M5Stack M5Core2

### Power Outputs (DC / LDO)

| AXP192 Output | Type         | Typical Voltage | Connected To        | Notes                             |
| ------------- | ------------ | --------------- | ------------------- | --------------------------------- |
| **DC1**       | Buck (DC-DC) | ~3.3 V          | ESP32 VDD33         | Main MCU supply                   |
| **DC2**       | Buck (DC-DC) | ~1.4 V          | ESP32 Core          | ESP32 core voltage                |
| **DC3**       | Buck (DC-DC) | ~3.0 V          | LCD / peripherals   | Display power                     |
| **LDO1**      | LDO          | 3.3 V           | Not used            | Reserved                          |
| **LDO2**      | LDO          | ~3.0 V          | Internal sensors    | Shares voltage register with LDO3 |
| **LDO3**      | LDO          | 1.8–3.3 V       | **Vibration motor** | Vibration ON/OFF & intensity      |
| **LDOIO0**    | LDO          | 3.3 V           | External GPIO power | Logic-level supply                |

### Diagram

- https://m5stack.lang-ship.com/howto/m5unified/axp192/

<img width="2311" height="1892" alt="image" src="https://github.com/user-attachments/assets/7a5de030-c6c8-4185-8e24-1589730249ad" />


**Text diagram**

             USB-C (5V)
                  │
                VBUS
                  │
          ┌─────────────────┐
          │     AXP192      │
          │  Power Manager  │
          └─────────────────┘
                  │
        ┌─────────┼─────────┬───────────┬─────────┐
        │         │         │           │         │
      DC1       DC2       DC3         LDO2      LDO3
     3.3V      ~1.4V      ~3.0V        ~3.0V   1.8–3.3V
        │         │         │           │         │
     ESP32   ESP32 Core     LCD     Internal     Vibration
     VDD33                 Panel    sensors       Motor
