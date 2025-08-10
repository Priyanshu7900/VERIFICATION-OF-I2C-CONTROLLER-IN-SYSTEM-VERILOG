# Project Title

# Verification of the I2C Controller in SystemVerilog

## Project Overview

This project implements and verifies an **Inter-Integrated Circuit (I2C) Controller** using SystemVerilog. The design includes separate **Master** (`i2c_master.sv`) and **Slave** (`i2c_slave.sv`) modules, integrated into a top-level system (`top.sv`), with a testbench (`top_tb.sv`) verifying end-to-end communication and protocol compliance.

## Features

- Fully synthesizable I2C Master and Slave modules  
- Supports **read** and **write** transactions according to the I2C protocol  
- Top-level integration connecting `i2c_master` and `i2c_slave` for direct communication  
- Testbench that verifies functionality, logs results, and captures pass/fail status  
- `verification_results` providing simulation outputs and waveform evidence of correct operation

## Architecture
The project comprises modules including:
- **i2c_master.sv** – I2C Master module that initiates communication, generates the clock (`SCL`), and transmits or receives data over `SDA` according to the I2C protocol.  
- **i2c_slave.sv** – I2C Slave module that responds to the master’s requests, receives/transmits data, and generates acknowledgments (`ACK`).  
- **top.sv** – Top-level module instantiating both master and slave, wiring them together for protocol verification.  
- **top_tb.sv** – Testbench that applies reset and clock, initiates transactions, and monitors responses to verify the complete communication path.  
- **verification_results/** – Contains logs, waveforms, or textual outputs confirming that transmitted data matches expected results and protocol timing is met.

---

## Run Locally

Clone the project

```bash
git clone https://github.com/Priyanshu7900/VERIFICATION-OF-I2C-CONTROLLER-IN-SYSTEM-VERILOG.git
```

Go to the project directory

```bash
cd VERIFICATION-OF-I2C-CONTROLLER-IN-SYSTEM-VERILOG
```

Install a Verilog/SystemVerilog Simulator

```bash
Download (Free with Intel FPGA tools): https://www.intel.com/content/www/us/en/software-kit/705184/modelsim-intel-fpgas.html
```

How to check the results on ModelSim

```bash
. Open ModelSim and Create a Project
. vlib work
. vmap work work 
. vlog *.sv 
. vlog top_tb.sv
. vsim top_tb 
. run -all
```

---

## Run on EDA Playground

1. **Open** [EDA Playground](https://www.edaplayground.com/)  
2. **Set language** to **SystemVerilog / Verilog** in the left sidebar.  
3. In the **Design pane** (right), click the **+** and add these files from your GitHub repo:  
   - `i2c_master.sv`  
   - `i2c_slave.sv`  
   - `top.sv`  
4. In the **Testbench pane** (left), either:  
   - Paste your `top_tb.sv` code into the default testbench tab, **or**  
   - Create a new file `top_tb.sv` and paste it there.  
5. At the **very top** of your testbench file, add:

```verilog
`include "i2c_master.sv"
`include "i2c_slave.sv"
`include "top.sv"
```
*(This ensures files are compiled in the correct order.)*

6. In the **Tools & Simulators** section:  
   - For full SystemVerilog features → select **Siemens Questa** or **Aldec Riviera**.  
   - For a lighter option → select **Icarus Verilog** (limited SV support).  
7. *(Optional)* Check **Open EPWave after run** to automatically open the waveform viewer.  
8. Click **Run** (or press `Ctrl+Enter`). 
