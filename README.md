# STM32F4 Bare-Metal: Precision Polling & SysTick

https://github.com/user-attachments/assets/e680de91-cc68-48c6-9034-9b83012c3f8b

![WhatsApp Image 2026-03-28 at 18 40 16](https://github.com/user-attachments/assets/349f4d87-721d-486d-8676-b5a644ff334e)

## Overview
This repository documents the foundational milestone of translating the STM32F401RE Reference Manual into functional bare-metal C code. It demonstrates the ability to power silicon registers and control peripheral hardware without relying on external libraries (HAL).

## Hardware Platform
* **Development Board:** STMicroelectronics NUCLEO-F401RE
* **Microcontroller:** STM32F401RE (ARM Cortex-M4)
* **Onboard Peripherals Utilized:**
  * User LED (Green) mapped to GPIO PA5.
  * User Button (Blue) mapped to GPIO PC13.

## Core Competencies Achieved
* **Datasheet Navigation:** Mapped physical pins to memory addresses.
* **Peripheral Clocking (RCC):** Powered silicon logic.
* **Core Peripherals:** Configured the 24-bit System Tick (SysTick) Timer for precise millisecond generation.
* **GPIO Configuration:** Configured MODER (Mode Register) for Output (LED) and Input (Push Button)

## Known Limitations & Technical Debt (To be fixed in v2.0)
1. **CPU Paralysis:** The SysTick `delay_ms()` function is a blocking loop. The CPU cannot process other sensor data while waiting.
2. **Missed Inputs:** Because the system uses a Polling Superloop, button presses that occur during a `delay_ms()` cycle are completely ignored.

## Next Version Roadmap
* **v2.0 Upgrade:** Implement **Hardware Interrupts (EXTI/NVIC)** to eliminate the need for polling, allowing the button to asynchronously wake the CPU even during a delay.
