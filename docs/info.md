<!---

This file is used to generate your project datasheet. Please fill in the information below and delete any unused
sections.

You can also include images in this folder and reference them in the markdown. Each image must be less than
512 kb in size, and the combined size of all images must be less than 1 MB.
-->

## How it works

This chip is a simple, combinational logic padlock designed to teach basic digital logic concepts. It uses a hardcoded 3-bit password (`1-0-1`) to unlock a vault. 

The circuit is built using fundamental logic gates:
* **Inputs:** Three switches act as the password entry. Switch 1 and Switch 3 are wired directly to the final AND logic. Switch 2 is wired through a **NOT gate**. 
* **Logic:** The inputs feed into a cascade of **AND gates**. The final AND gate will only output a `1` (High) if the exact sequence `1`, `0`, `1` is entered on the switches.
* **Display Output:** Instead of a complex binary-to-7-segment decoder, this chip uses direct wiring to create letters. Segments D, E, and F are hardwired to VCC to permanently form the shape of an "L" (Locked). The master unlock signal from the AND gates is wired to segments A, B, and C. 

When the correct password is provided, segments A, B, and C light up, joining the "L" to form a complete "O" (Open)!

## How to test

To test this chip on the physical Tiny Tapeout demo board:

1. Turn on the board and select this project using the DIP switches.
2. Look at the 7-segment display. By default, with all input switches set to `0`, the display should show the letter **"L"** (Locked).
3. Try flipping various combinations on input switches 1, 2, and 3 (`ui_in[0]`, `ui_in[1]`, `ui_in[2]`). Notice that the display remains an **"L"**.
4. Enter the secret password: Flip **Switch 1 UP**, **Switch 2 DOWN**, and **Switch 3 UP** (`1-0-1`).
5. Watch the display! The moment the correct sequence is entered, the top segments will illuminate, turning the "L" into an **"O"** (Open). 
6. Flip any switch away from the `1-0-1` sequence, and the display will instantly snap back to **"L"**.
