# STM32 UART, EXTI Button & PWM LED Control
A simple STM32F411E Discovery project demonstrating:
- LED control via on-board button (PA0) using EXTI interrupt
- LED blinking using timer
- LED brightness control via PWM
- UART command interface for remote control

## Features
- Button interrupt with 250ms software debounce
- UART command parser (commands end with `;`)
  - `D12;` → Toggle LED1 (PD12)
  - `<number>s;` → Set blink period for LED3 (PD14) in seconds (e.g., `2s;`)
  - `<number>;` → Set PWM duty cycle for LED2 (PD13) in % (0–100)
- Periodic LED blinking using TIM2
- LED brightness control using TIM4 PWM

## Hardware
- **Board:** STM32F411E Discovery
- **Button:** On-board User Button (PA0)
- **LEDs:**
  - LED 1: Toggled by push-button using EXTI interrupt and via UART commands from PC.
  - LED 2: Brightness controlled by PWM, PWM value received from PC via UART.
  - LED 3: Toggles ON/OFF with interval time set through UART commands from PC.
- **UART:** USART2 TX/RX connected to PC

## Tools
- **IDE:** STM32CubeIDE (build, debug, flash)
- **Terminal:** PuTTY, Tera Term, or any serial monitor
- **Library:** STM32 HAL

## What I Learned
# STM32 UART, EXTI Button & PWM LED Control
A simple STM32F411E Discovery project to control LEDs using the on-board button (PA0) via EXTI interrupt, UART commands, and PWM for brightness adjustment.

## Features
- **EXTI (PA0):** Toggle LED1 (PD12) with software debounce (250 ms)
- **UART (USART2):** Receive commands ending with `;`
  - `D12;` → Toggle LED1 (PD12)
  - `2s;` → Blink LED3 (PD14) every 2 seconds
  - `75;` → Set LED2 (PD13) brightness to 75%
- **TIM2:** Periodic interrupt to blink LED3 at configurable intervals
- **TIM4 (PWM):** Adjust LED2 (PD13) brightness from 0–100%

## Hardware
- **Board:** STM32F411E Discovery, USB to TTL CP2102
- **Button:** On-board User Button (PA0, EXTI)
- **LEDs:**
  - PD12 → LED1 (Toggle via button/UART)
  - PD13 → LED2 (Brightness via PWM)
  - PD14 → LED3 (Blink via TIM2)
- **UART:** USART2 TX/RX to PC via USB Hercules

## Tools
- **IDE:** STM32CubeIDE (build, debug, flash)
- **Library:** STM32 HAL

## What I Learned
- Understanding how **EXTI registers** work (edge detection and interrupt triggering)
- Understanding how **UART registers** work (data transmission, reception, and status flags)
- Understanding how **TIM registers** work (timer counting, overflow events)
- Understanding how **PWM registers** work (duty cycle and period control)
- Implementing interrupt-based event handling for responsive LED control
- Structuring embedded code into modular, reusable functions

