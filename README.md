# FreeRTOS Threads, Mutexes & Notifications on STM32F411-NUCLEO

![FreeRTOS](https://img.shields.io/badge/FreeRTOS-10.4.3-green)
![STM32](https://img.shields.io/badge/STM32F411-84MHz-03234B?logo=stmicroelectronics)
![UART](https://img.shields.io/badge/UART-115200_8N1-blueviolet)
![Notifications](https://img.shields.io/badge/Thread-Notifications-important)


<img src="https://github.com/user-attachments/assets/c4fb808a-4458-41e5-9293-d43f23e27825" width="650" alt="335642A6-F1DA-4228-9401-A11C48F09CAB">


STM32F411 FreeRTOS Project featuring inter-thread notifications, mutex-protected UART, and button-triggered events. Includes 4 threads with Tera Term monitoring.



## Key Features
- 🧵 **4 FreeRTOS Threads** with execution profiling
- 🔔 **Thread Notifications** - Lightweight inter-thread signaling
- 🔒 **Mutex-Protected UART** for clean serial output
- 📡 **Tera Term Integration** via ST-LINK VCP
- 💡 **Hardware Triggers** - Button (PC13) activates Thread3

## Hardware Setup
| Component | NUCLEO-F411RE Connection |
|-----------|--------------------------|
| USART2_TX | PA2 (ST-LINK VCP) |
| USART2_RX | PA3 (ST-LINK VCP) |
| LED (LD2) | PA5 |
| User Button | PC13 |

## Thread Architecture
```c
// Notification Flow:
Thread2 (on button press) → xTaskNotify() → Thread3
// Mutex Protection:
All threads → [Take Mutex] → UART_Transmit() → [Give Mutex]
