# AUTOMATIC-LED-CONTROL-USING-IR-SENSOR
##  AIM
To design and implement a system using the **STM32 microcontroller** where an LED automatically turns ON or OFF based on the input from an **IR sensor**.

---

##  Components Required
- STM32 Nucleo or Discovery Board (e.g., **Nucleo-G071RB**)
- IR Sensor Module
- LED (5mm Green or any color)
- Jumper wires
- Breadboard

---

##  Theory
An **IR sensor** detects the presence of an object by emitting and receiving infrared light.

### IR Sensor Behavior
- When an **object is detected**, the IR sensor output goes **LOW (0V)**.
- When **no object is detected**, the output stays **HIGH (3.3V)**.

### Microcontroller Response
- If **IR output = LOW** → **LED ON**
- If **IR output = HIGH** → **LED OFF**
### **Procedure**

1. Open **STM32CubeIDE**.

   <img width="1670" height="1088" alt="Screenshot 2025-11-08 071818" src="https://github.com/user-attachments/assets/e695c6a8-537c-4b7f-835a-017e3108eb42" />


2. Click **File → New STM32 Project**.
   
  <img width="1910" height="1145" alt="Screenshot 2025-11-08 071839" src="https://github.com/user-attachments/assets/a2a38df5-39bc-4673-b68c-4c2cfc004d44" />

  <img width="1917" height="1128" alt="Screenshot 2025-11-08 071923" src="https://github.com/user-attachments/assets/5470343a-790f-476d-8d2e-0e39ec554539" />


4. Select the **target microcontroller** or board and click **Next**.

  <img width="1915" height="1127" alt="Screenshot 2025-11-08 072027" src="https://github.com/user-attachments/assets/fb927827-9f38-433e-875c-1bfb0a519419" />


5. Name the project.

<img width="1891" height="1122" alt="Screenshot 2025-11-08 072127" src="https://github.com/user-attachments/assets/6b7643bc-e59b-4673-bda7-cc38cf9ccd0b" />


6. The corresponding `.ioc` file will be generated automatically.

  <img width="1861" height="1024" alt="Screenshot 2025-11-08 072643" src="https://github.com/user-attachments/assets/531b247f-01c0-47bc-9814-b19f1866ca49" />


7. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.

  <img width="1906" height="1098" alt="Screenshot 2025-11-08 072808" src="https://github.com/user-attachments/assets/89a4d81f-3e94-40ca-8363-5702500fb883" />

  <img width="1861" height="1024" alt="Screenshot 2025-11-08 072643" src="https://github.com/user-attachments/assets/37406077-976c-4632-9553-8472250d14cf" />



8. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
   
  <img width="1861" height="1024" alt="Screenshot 2025-11-08 072643" src="https://github.com/user-attachments/assets/a612230e-9d7d-4762-bc1c-0ebf49e3ffce" />

10. Edit the generated main program as required.
    
  <img width="1882" height="1117" alt="Screenshot 2025-11-08 072846" src="https://github.com/user-attachments/assets/cbf6625a-edb6-4735-88c3-e99f018819d5" />

<img width="1874" height="1090" alt="Screenshot 2025-11-08 072934" src="https://github.com/user-attachments/assets/49408e62-1c12-40d0-8073-77de19262346" />

11. Click **Project → Build All**.
   <img width="1919" height="1115" alt="Screenshot 2025-11-08 073300" src="https://github.com/user-attachments/assets/ca01aec5-6077-4898-9838-91c0fb14c758" />

12. Link the **HEX file** using the post-build process.

   <img width="609" height="404" alt="Screenshot 2025-11-08 073320" src="https://github.com/user-attachments/assets/f4013af0-0308-4ff0-ac92-79054a2febb6" />


13. Click **Debug** and connect the **STM Nucleo Board**.
    <img width="1903" height="1102" alt="Screenshot 2025-11-08 074040" src="https://github.com/user-attachments/assets/5936b41a-8409-411d-9b02-5b9706308c86" />

14. Click **Run** to execute the program.
    
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
        GPIO_PinState ir = HAL_GPIO_ReadPin(GPIOA, GPIO_PIN_10); // IR OUT at PA10 (D2)

	      if (ir == GPIO_PIN_RESET)  // IR sensor HIGH = object detected
	      {
	          HAL_GPIO_WritePin(GPIOB, GPIO_PIN_3, GPIO_PIN_SET); // Turn ON LED
	      }
	      else
	      {
	          HAL_GPIO_WritePin(GPIOB, GPIO_PIN_3, GPIO_PIN_RESET); // Turn OFF LED
	      }

	      HAL_Delay(100);
    }
}
```
---
### OUTPUT
CASE 1: LED ON 

<img width="436" height="799" alt="image" src="https://github.com/user-attachments/assets/53cb73fa-7f24-4b21-8ca0-da861ff1ec57" />


CASE 2: LED OFF

<img width="609" height="624" alt="image" src="https://github.com/user-attachments/assets/77e230d4-7ef7-4d55-a6ed-53c3570d6b2d" />


---
### RESULT

The experiment on IR Sensor-Based Automatic LED Control using STM32 was successfully carried out. The STM32 microcontroller accurately read the IR sensor output and controlled the LED based on object detection. When an object was detected, the LED glowed (ON) and when no object was present, the LED remained OFF. Thus, the objective of the experiment was achieved.




