# VSDSquadron PRO Internship
## Task 1 – Hardware Setup & Validation (VSDSquadron PRO)

## Objective
The objective of this task is to:
- Install and configure the RISC-V development environment
- Validate hardware functionality using the VSDSquadron PRO board
- Upload and execute a basic program
- Understand hardware specifications
- Document the entire setup process clearly

This task forms the foundation for further Edge AI and embedded systems development.

---

## System Configuration

- OS: (e.g., Ubuntu 22.04 / Windows 10)
- Processor: (e.g., Intel i5 / Ryzen 5)
- RAM: (e.g., 8GB / 16GB)
- Storage: (e.g., 256GB SSD)

---
## Step-by-Step Installation Guide
Step 1: Install Drivers using Zadig
1. Go to the website: https://zadig.akeo.ie/
2. Download and open Zadig.
3. In Zadig:
- Click on Options → select List All Devices
- From the dropdown, choose: Dual RS-232-HS (Interface 0)
4. On the right side, select the driver: libusb-win32
5. Click on: Install Driver (or Reinstall Driver)

✅ This step ensures your board is detected properly by your system.

Step 2: Extract Freedom Studio
1. Download Freedom Studio (preferably save in C drive or D drive).
2. Locate the downloaded file: VSDSquadronPRO.tar
3. Right-click on it and select: Extract All
4. Choose a destination folder and click: Extract

✅ Now your software files are ready to use.

Step 3: Open Freedom Studio
1. Go to the extracted folder.
2. Find and double-click: FreedomStudio-3-1-1
3. If a warning popup appears: Click More Info
Then click Run Anyway

✅ Freedom Studio will now launch.

Step 4: Create Workspace
1. A window will appear asking for workspace location.
2. Choose or create a folder (example: D:\projects)
3. Click on: Launch

✅ This workspace will store all your projects.

Step 5: Create New Project
1. Inside Freedom Studio:
2. Create a New Project
3. Select:
   - SDK
   - Target: sifive-hifive1
   - Choose an example project
4. Create a Debug Configuration

✅ Your project setup is now complete.

Step 6: Run Debug (Connect Board)
1. Click on the Debug button.
2. A Debug Configuration window will open.
3. Connect your VSDSquadron PRO board to your laptop.
4. Go to the OpenOCD tab.
5. Click on: Debug

✅ This starts the debug session and runs the program on the board.

Step 7: Run Another Debug Session
1. In Freedom Studio, go to the top menu.
2. Click on: Debug
3. Then select: Debug Configurations
4. In the left panel, click on: OpenOCD
5. Now click on: Debug

✅ This will start a new debug session.

Step 8: Run the Program
1. After debugging starts, a Debug Window will open.
2. Look for the Run button.
3. Click on: Run

✅ This executes your program on the board.

Step 9: Handle Debug Warning (If It Appears)
1. While starting a new session, you might see a popup message:
 “You have an active OpenOCD debug launch. Would you like to terminate that one and continue this one?”
2. Simply click: Yes

✅ This will stop the previous session and start a new one.

Step 10: Verify Output
1. Check the COM Terminal in Freedom Studio.
2. You should see the output: “SiFive”
3. Also check your VSDSquadron PRO board:
   -The blue LED should start blinking

✅ This confirms everything is working correctly 🎉

## Commands
### Build
**```bash**

make clean

make all

--------
If your project uses a specific target:

**```bash**

make TARGET=vsd_squadron_pro


---
### Flash
**```bash**

openocd -f interface/ftdi.cfg -f target/riscv.cfg


Inside GDB:

**```bash**

target remote localhost:3333

load

continue

----

## Hardware Specifications Summary

### Processor Core Specifications:
Processor Type:

32-bit RISC-V architecture (open-source ISA)

SoC / Microcontroller:
SiFive FE310-G002

-----

Core Type:

RV32IMAC

RV32I → Base integer instruction set

M → Multiply/Divide support

A → Atomic instructions

C → Compressed instructions (improves code size)

-----

CPU Core:

SiFive E3 Core (embedded processor core)

----





