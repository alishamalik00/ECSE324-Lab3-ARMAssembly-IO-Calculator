# ECSE 324 — Lab 3: ARM Assembly I/O Drivers and Calculator

This lab focuses on ARMv7 assembly programming for the Altera DE1-SoC board.  
It is divided into three main tasks:

- **Task 1:** Slider switch & LED driver  
- **Task 2:** Pushbutton driver  
- **Task 3:** Stack-based calculator using polling and memory-mapped I/O  

---

## Task 1 — Slider Switch & LED Driver

**Description:**  
This task implements an ARM assembly driver to read the state of the DE1-SoC board’s slider switches and control the corresponding LEDs.  
The program uses memory-mapped I/O addresses to directly interface with hardware registers.

The driver:
- Reads the binary value from the slider switches (SW0–SW9).
- Outputs the same binary value to the LEDs (LEDR0–LEDR9).
- Loops continuously to provide real-time updates.

**Example:**  
If switches SW0, SW3, and SW5 are ON, the binary value `00101001` is sent to the LED register, turning on LEDs 0, 3, and 5.

---

## Task 2 — Pushbutton Driver

**Description:**  
This section implements polling-based input handling for the board’s pushbuttons (KEY0–KEY3).  
The driver reads pushbutton edge capture registers to detect presses and clears them after processing.

The driver supports:
- Reading specific button presses (e.g., KEY0 for “start”).
- Responding to multiple buttons in one loop.
- Clearing edge capture to avoid repeated detection.

**Example:**  
Pressing KEY2 could trigger a specific action (like pausing an operation), while KEY0 might resume it.

---

## Task 3 — Stack-Based Calculator

**Description:**  
This task combines the I/O drivers from previous tasks into a functional stack-based calculator.  
It uses:
- Slider switches for numeric input.
- Pushbuttons for operations (push, add, subtract, multiply, divide).
- HEX displays for showing results.

**Functionality:**
1. **Push:** Read the current switch value and push onto the stack.
2. **Arithmetic:** Perform the operation on the top elements of the stack.
3. **Display:** Update HEX displays to show the result.
4. **Polling loop:** Continuously checks inputs and updates outputs.

**Example:**  
If the switches are set to `5` and pushed twice, pressing the multiply button will result in `25` displayed on the HEX displays.

---
