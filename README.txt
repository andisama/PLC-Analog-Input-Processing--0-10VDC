"Processing Analog Input, 0-10VDC" in Industrial Automation
Towards Industry 4.0.

See the article at ...


Siemens PLC: SIMATIC S7-1200 Compact PLC, DC/DC/DC
===================================================

- CPU 1214C, compact CPU
- DC/DC/DC
- Onboard I/O: 14 DI 24 V DC; 10 DO 24 V DC; 2 AI 0-10 V DC
- Power supply: DC 20.4-28.8V DC
- Program/data memory 100 KB


Hardware, Software & Wiring Configuration
=========================================

Hardware
- Power Supply
  * 1x External Siemens PSU (Input 220VAC 1 Phase, Output 24VDC).
- CPU
  * 1x Siemens Compact PLC 1200 DC/DC/DC.
- Digital Input
  * 1x Start Push Button(NO) %I0.1.
  * 1x STOP Push Button (NC) %I0.0.
- Analog Input
  * channel 0, %IW64.
- Signal Generator
  * 1x Signal Generator to Analog Input Channel 0.
  * only use signal ground (GND) and AVo (output, voltage).
  * powered by an external USB cable.
  * set the mode on Signal Generator to Voltage (press the mode button to switch between voltage & current).
- Digital Output
  * 5x 24VDC Lamps %Q0.0 (Blue), %Q0.4 (Red), %Q0.5 (Yellow), %Q0.6 (Green), %Q0.7 (White).
- Cabling
  * AWG 16 with ferrules.
- Cabling (color)
  * 220VAC Live: brown, 220VC Neutral: blue.
  * 24VDC+: red, 24VDC common: black.
  * 24VDC Digital Input: white.
  * 24VDC Digital Output: orange.
  * 24VDC Common: black.
  * Analog Input: yellow.
- PLC Firmware level (updated from base 4.5)
  * 4.6.0.
Hardware Configuration change in PLC
- Utilize Realtime Clock (RTC).
  * through TIA portal, devices & network -> system & clock memory -> enable the use of clock memory byte.
  * download to PLC (hardware configuration).
Connectivity
- Laptop to PLC
  * RJ45.
  * straight cable wiring as Siemens 1200 PLC can autocross on the ethernet cable.
Application Software
- Siemens TIA Portal v17 on Windows 11.


Programming Logic
=================
- If the Start Push Button (NO) is pressed, the program runs, and the Start Push Button is latched.
- It continuously monitors the analog input, normalizes and scales the analog input appropriately, and energizes the programmed output ports based on the normalized and scaled values.
 * Red: if the analog signal is between 0.0–2.5VDC.
 * Yellow: if the analog signal is between 2.5–5VDC.
 * Green: if the analog signal is between 5–7.5VDC.
 * White: if the analog signal is between 7.5–10.0VDC.
- If the Stop Push Button (NC) is pressed, the Start Push Button is un-latched, and the program stops.