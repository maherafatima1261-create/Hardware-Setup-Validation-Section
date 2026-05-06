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

## Basic Program upload and validation

<img width="1047" height="553" alt="image" src="https://github.com/user-attachments/assets/c6e8ec35-c861-4bf5-8e9c-d12ef4fb3ebf" />

----
## Output 

<img width="1049" height="1483" alt="sifive2" src="https://github.com/user-attachments/assets/45146c77-d012-470b-b055-dc4dbd82d44c" />

-----


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
### Number of Cores

Single-core processor

Based on 32-bit RISC-V RV32IMAC architecture

-----

### SRAM Size

16 KB on-chip SRAM

Used as scratchpad memory for fast access

------

### Flash Memory Size

32 Mbit (4 MB) external SPI Flash

Used for program storage

-------

### Peripherals

The board supports multiple communication and I/O interfaces:

UART – Serial communication

SPI – High-speed communication with external devices

I2C – Communication with sensors and peripherals

GPIO – General purpose input/output pins

PWM – Pulse width modulation

Timers – For delays and timing operations

-------

### Debug Interface

Supports RISC-V Debug Specification (v0.13)

Uses JTAG interface for:

Programming

Debugging

Breakpoints and stepping

---

## Issues Faced And Resolution

## 1. Driver Installation Issue

Issue: Debug probe / USB device not detected properly.

Resolution: Installed correct drivers using Zadig and selected the appropriate USB interface (WinUSB).

----

## 2. Board Not Detected in Debugging

Issue: Target device not showing in debugger / OpenOCD errors.

Resolution:

Checked USB connection and cable

Verified correct interface configuration file

Restarted OpenOCD and system

------

### Task 2 – AI Model Development for Handwritten Digit Recognition

This section of repository contains the embedded C application and associated Python tooling for deploying a quantized MNIST handwritten digit classification model onto the VSDSquadron PRO development board, powered by the SiFive FE310-G002 RISC-V microcontroller. The solution implements a custom, highly efficient, integer-only inference engine inspired by BitNet principles.

## Objective

The objective of this task is to develop and optimize a simple Artificial Intelligence model capable of recognizing handwritten digits and evaluate whether the model can be deployed on the VSDSquadron PRO board under its memory and computation constraints.

-----

## Features

 Quantized Inference: Efficient execution of an 8-bit quantized MNIST classification model.
 
 RISC-V Compatibility: Optimized C code for the RV32IMAC instruction set of the SiFive FE310-G002.
 
 BitNet-like Operations: Custom processfclayer and ReLUNorm functions for efficient integer-only matrix multiplication and activation with support for packed bit-   weights (specifically 4-bit and 8-bit handling demonstrated).
 
 Automated Parameter Generation: Python script to extract quantized weights, biases, and other layer parameters directly from a TensorFlow Lite (.tflite) model      into C-compatible arrays.
 
 Bare-Metal Execution: Runs directly on the microcontroller without an operating system.
 
 Serial Output: Inference results are printed to a serial terminal for verification.

-----

## Hardware Requirements

VSDSquadron PRO Development Board: Featuring the SiFive FE310-G002 RISC-V SoC.

USB-C Cable: For power, programming, debugging, and serial communication.

----

## Software Requirements

 Freedom Studio 3.1.1: The integrated development environment (IDE) for SiFive RISC-V development.
 
                        Download and installation instructions can be found in the VSDSquadron PRO User Guide.
                        
 Python 3.x: For running the model parameter generation script.
 
 Python Libraries:
 
     tensorflow (version 2.15.0 used in development).
     
     numpy.

-----

## Project Structure

<img width="988" height="406" alt="image" src="https://github.com/user-attachments/assets/0763beda-288e-47a4-8471-5926da5f273b" />

----

## Getting Started

Follow these steps to set up the development environment, generate model parameters, build the application, and run inference on your VSDSquadron PRO board.

1. Install Freedom Studio
   
   Refer to the official VSDSquadron PRO User Guide for detailed instructions on downloading, installing, and setting up Freedom Studio 3.1.1, including driver        installation (e.g., using Zadig).
   
3. Prepare Python Environment:
   
   Ensure you have Python 3.x installed and the necessary libraries.
   > pip install tensorflow numpy
   
5. Generate C Model Parameters and Sample Inputs:
   
   The mnist_baseline_model.ipynb notebook trains and quantizes the MNIST model, saving it as mnist_quantized_model.tflite. The generate_c_model_params.py script      then extracts the layer-specific data from this .tflite file into C arrays.

   1. Run Jupyter Notebook: Open and run all cells in mnist_baseline_model.ipynb to ensure mnist_quantized_model.tflite is generated.

  2. Run Parameter Generation Script: Navigate to the src/ directory in your terminal (e.g., C:\VSD_Sqd_Project\sifive_hifive1_BitNet_MNIST_App\src\) and execute:
     
  > jupyter nbconvert --to notebook --execute mnist_baseline_model.ipynb --output-dir output --ExecutePreprocessor.timeout=600 (timeout is optional, but should         generally be enough)

4. Build the Embedded Application
   i. Open Project in Freedom Studio: Launch Freedom Studio and import the sifive_hifive1_BitNet_MNIST_App project.

  ii. Clean Project: In Freedom Studio, go to Project -> Clean..., select your project, and click Clean.

 iii. Build Project: In Freedom Studio, go to Project -> Build Project or click the hammer icon in the toolbar.

    > Expected Output: The build should complete with 0 errors and possibly 1 warning (related to RWX permissions which is common in development). This   indicates         successful compilation and linking of all C source files, including the generated mnist_model_params.c.
    
5. Configure and Run on VSDSquadron PRO
   
i. Connect Board: Connect your VSDSquadron PRO board to your computer via a USB-C cable.

ii. Configure Debug Launch:

*  In Freedom Studio, go to 'Run' -> 'Debug Configurations....'    
*  In the left pane, expand 'GDB OpenOCD Debugging' and select your project's launch configuration (e.g., 'sifive_hifive1_BitNet_MNIST_App Debug').
*  In the "Main" tab, ensure the "C/C++ Application" field points to the correct executable:
      > '${workspace_loc:/sifive_hifive1_BitNet_MNIST_App/src/debug/main.elf}'
    
    If it points to 'empty.elf' or another path, correct it using the "Browse..." button.
*   Click **Apply** to save the changes.

iii. Start Debug Session: Click the **Debug** button in the Debug Configurations dialog, or the green bug icon in the toolbar.

*   If prompted to terminate a previous debug session, confirm "Yes".
*   The debugger will connect to the board and load the 'main.elf' program. It will likely pause at the main function.
    
iv. Run Program: Click the **Resume** (green play) button to let the program execute.

-----

## Output
Monitor the "Console" or "Serial Terminal" view in Freedom Studio. You should see output similar to:

BitNet MNIST Dataset Handwritten Digit Classification on sifive-hifive1.



By Shwetank ShekharStarting MNIST inference...

Inference of Sample 1   Prediction: 7   Label: 7

Inference of Sample 2   Prediction: 2   Label: 2

Inference of Sample 3   Prediction: 0   Label: 1

Inference of Sample 4   Prediction: 0   Label: 0

This confirms that the model is running on the hardware and performing inferences.

----

## Model details

The model used is a simple feed-forward neural network for MNIST handwritten digit classification, trained using Keras and then quantized to 8-bit integers using TensorFlow Lite.

 Input Layer: Flatten (28x28 grayscale image) -> 784 features.
 
 Hidden Layer: Dense layer with 8 neurons, ReLU activation.
 
 Output Layer: Dense layer with 10 neurons (for 10 digits), Softmax activation.

The C inference engine (app_inference.h) is specifically tailored to handle 4-bit symmetric and 8-bit two's complement quantized weights, common in highly optimized embedded neural networks.

---

## Status: Ongoing

Current stage output:

<img width="1113" height="859" alt="Screenshot 2026-05-06 184449" src="https://github.com/user-attachments/assets/19490060-c96f-4d25-b7e1-a4b3828a8a65" />

---



