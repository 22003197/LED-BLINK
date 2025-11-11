# LED-BLINK
# 💡 Experiment 01 – Interfacing a Digital Output (LED) with ARM Development Board

### 🎯 **Aim**
To interface a digital output (LED) to an ARM development board and write a blink code.

---

### ⚙️ **Components Required**
- STM32CubeIDE  
- NUCLEO ARM Development Board  

---

### 🧠 **Theory**

**ARM (Advanced RISC Machine)** is a 32-bit processor architecture developed by ARM Holdings. It is widely used in embedded systems and SoC (System-on-Chip) products. Many semiconductor companies like Samsung, Atmel, and Texas Instruments license ARM architecture to design their own SoCs.
### 🧩 **What is an ARM7 Processor?**
The **ARM7 processor** is commonly used in embedded system applications. It provides a balance between the classic ARM architecture and the newer Cortex series, offering an excellent platform for both hardware and software development.
### 🔍 **LPC2148 Microcontroller**
The **LPC2148**, developed by NXP Semiconductors (Philips), is a 16/32-bit ARM7-based microcontroller featuring a wide range of peripherals.
#### **Key Features**
- 16/32-bit ARM7TDMI-S core in LQFP64 package  
- On-chip **Flash memory**: 32 KB – 512 KB  
- On-chip **SRAM**: 8 KB – 40 KB  
- **ISP/IAP** via on-chip bootloader  
- **Embedded ICE-RT** and **Real Monitor** for real-time debugging  
- **USB 2.0** full-speed device controller with 2 KB endpoint RAM  
- **10-bit ADC** (6 or 14 channels, 2.44 μs conversion time)  
- **10-bit DAC** for analog output  
- **Timers:** Two 32-bit timers, watchdog, and PWM unit  
- **RTC** with 32 kHz clock input  
- **UARTs (2x), I²C (2x)** up to 400 kbit/s  
- **5V-tolerant GPIOs**, 21 external interrupt pins  
- **Max CPU Clock:** 60 MHz using on-chip PLL (lock time 100 µs)  
- **Crystal Frequency:** 1 MHz – 25 MHz  
- **Power modes:** Idle and Power-down with peripheral clock scaling  

---

### 🧭 **Procedure**

1. Open **STM32CubeIDE**.
   <img width="1920" height="1021" alt="I-1" src="https://github.com/user-attachments/assets/c43a1287-8f7a-4048-8c81-24a1a55795fc" />

2. Click **File → New STM32 Project**.
   <img width="1920" height="1110" alt="I-2" src="https://github.com/user-attachments/assets/e52db5cf-cc7d-41fc-952a-7388f0f18684" />


3. Select the **target microcontroller** or board and click **Next**.
   <img width="1920" height="1122" alt="I-3" src="https://github.com/user-attachments/assets/e547d901-0b95-462a-903b-2862c1640144" />



4. Name the project.
   <img width="590" height="634" alt="I-4" src="https://github.com/user-attachments/assets/afe07c01-6d7d-4e69-a9c9-6e789b29511d" />


5. The corresponding `.ioc` file will be generated automatically.
  ![I-5](https://github.com/user-attachments/assets/242e3b1b-4bca-4834-868b-24f2e51f4ae9)

6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
<img width="1920" height="1136" alt="I-6" src="https://github.com/user-attachments/assets/0adc98ce-a574-46ff-bd47-71e6ecd4f540" />

7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
   <img width="1920" height="1142" alt="I-7" src="https://github.com/user-attachments/assets/0d29f650-3b96-4581-963d-83bf05993868" />

 
8. Edit the generated main program as required.
   <img width="1920" height="1142" alt="I-8" src="https://github.com/user-attachments/assets/9fe9f5fb-487d-4316-bb43-991e694f0935" />

9. Click **Project → Build All**.
    ![I-9](https://github.com/user-attachments/assets/063ff855-1226-4f33-aaa0-6e26a29d0568)

10. Link the **HEX file** using the post-build process.
    <img width="1003" height="518" alt="I-10" src="https://github.com/user-attachments/assets/25b5fbaa-a42a-4f53-bdf9-4cb1b27a78e7" />


11. Click **Debug** and connect the **STM Nucleo Board**.
    <img width="870" height="764" alt="I-11" src="https://github.com/user-attachments/assets/bce1ae3a-33d1-4054-a2a0-75ecb02d0c53" />

13. Click **Run** to execute the program.
---

### 💻 **Program**


```c
#include "main.h"

void SystemClock_Config(void);
static void MX_GPIO_Init(void);

int main(void)
{
    HAL_Init();
    SystemClock_Config();
    MX_GPIO_Init();

    while (1)
    {
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);
        HAL_Delay(1000);
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_SET);
        HAL_Delay(1000);
    }
}
```
---
### OUTPUT
CASE 1: LED ON 
<img width="1280" height="576" alt="I-12" src="https://github.com/user-attachments/assets/1ace0210-387c-4fb9-ad74-2adeaa324aad" />


CASE 2: LED OFF
<img width="1280" height="576" alt="I-13" src="https://github.com/user-attachments/assets/a3a369c4-412f-4868-b6c9-a946371b2eeb" />

---
### RESULT
Interfacing a digital output with ARM microcontroller is executed and the results are verified.
