# 🔌 Arduino UNO Flash Read & Write using AVRDUDE
This guide explains how to **read** and **write** the Arduino UNO (ATmega328P) flash memory using **AVRDUDE** directly from the command line — without the Arduino IDE.

---

## 🧰 Requirements

- **Arduino UNO** (ATmega328P)
- **USB cable** (connected to your PC)
- **avrdude.exe** and **avrdude.conf** (included in this repository)
- **COM Port** of your Arduino (check in Device Manager → Ports)

---

## ⚙️ Command Format Reference

AVRDUDE basic structure:
avrdude -C config_file -p part_no -c programmer -P port -U memtype:op:filename:format

Where:
- `-C` → Path to `avrdude.conf`
- `-p` → MCU type (e.g. `atmega328p`)
- `-c` → Programmer type (e.g. `arduino`)
- `-P` → COM port (e.g. `COM6`)
- `-U` → Memory operation  
  - `flash:w:file.hex:i` → Write hex file to flash  
  - `flash:r:file.hex:i` → Read flash to hex file  

---

## 📝 Write (Upload) HEX file to Arduino UNO

Use this command to **upload a compiled HEX file** (example: Blink.ino.hex) to your Arduino UNO.
# Syntax
```
avrdude -C config_file -p part_no -c programmer -P Port -U flash:w:file.hex:i
```
# Example

```bash
"C:\Users\kr\Downloads\AVR_Files\avrdude" "-C C:\Users\kr\Downloads\AVR_Files\avrdude.conf" -p atmega328p -c arduino -P COM6 -U flash:w:"C:\Users\kr\AppData\Local\Temp\arduino_build_808068\Blink.ino.hex:i"
```
Explanation:

-p atmega328p → Microcontroller used in Arduino UNO

-c arduino → Programmer type

-P COM6 → Port number (change if your UNO uses a different COM port)

-U flash:w: → Write operation to flash memory

"file.hex:i" → File path and format (i = Intel HEX)

---
## 💾 Read (Backup) HEX file from Arduino UNO

Use this command to read the current flash memory from your Arduino and save it as a .hex file.
```
"C:\Users\kr\Downloads\AVR_Files\avrdude" "-C C:\Users\kr\Downloads\AVR_Files\avrdude.conf" -p atmega328p -c arduino -P COM6 -U flash:r:"C:\Users\kr\Desktop\AfterRead.ino.hex:i"
```
# Explanation:

Reads the program from the UNO’s flash memory

Saves it to C:\Users\kr\Desktop\AfterRead.ino.hex

---

##🧩 Notes

Make sure Arduino IDE is closed before running avrdude (to avoid port conflicts).

Run Command Prompt as Administrator if permission errors occur.

Always check that the COM port number is correct.

You can modify paths as per your folder locations.

---

## 🧠 Example Workflow

Upload program using Arduino IDE (e.g., Blink)

Read flash → backup HEX

Erase or reflash Arduino using write command

Verify both files using a HEX compare tool

---

## Author 
[karthickrajathedeveloper](https://github.com/karthickrajathedeveloper)

## LICENSE
[MIT LICENSE](LICENSE)


