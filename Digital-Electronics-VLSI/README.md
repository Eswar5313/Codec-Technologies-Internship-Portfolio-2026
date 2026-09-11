# VLSI & Digital Electronics Projects — Codec Technologies Internship 2026

**Author:** Eswar Mahalingam · Digital Electronics & VLSI Intern, Codec Technologies India (Aug 2026 – Present, Remote)
**Contact:** +91-9360548243 · eswarmba05313@gmail.com · Ghaziabad, UP, India

All ten projects from the internship brief, each in a standalone folder with RTL, a self-checking testbench, waveform PNGs, synthesis / place-and-route / timing reports, a Makefile, a one-command `run_all.sh`, and a 2–4 page engineering report PDF. Every number quoted below was measured by running the design in this repository — the raw logs sit next to each result.

**Compact layout:** this folder holds the 10 engineering-report PDFs (`reports/`), a clickable overview (`dashboard.html`) and the complete source tree as one archive — **`VLSI-Digital-Electronics-Projects-Codec-2026_source.zip`** (unzip → each `NN_*/` project folder runs standalone with `./run_all.sh`). Project names in the table below link to their report PDF.

## Projects

| # | Folder | What I built | Verification (measured) | Implementation (measured) |
|---|--------|--------------|-------------------------|---------------------------|
| 01 | [01_FPGA_Traffic_Light_Priority](reports/01_FPGA_Traffic_Light_Priority.pdf) | 4-way intersection FSM with pedestrian phase, debounced + synchronised emergency-vehicle override per approach (safe yellow → all-red hand-over), 1 Hz divider, 7-segment countdown | 6 scenarios · 39 checks · 0 errors · 3 always-on no-conflicting-green assertions never fired | iCE40 HX8K: 318/7680 LCs · **Fmax 109.4 MHz** (nextpnr + icetime) · Xilinx-style 109 LUT / 128 FF |
| 02 | [02_LowPower_8bit_ALU_CMOS](reports/02_LowPower_8bit_ALU_CMOS.pdf) | 8-bit ALU (11 ops, Z/C/N/V flags) in baseline and low-power variants — clock gating, operand isolation, one-hot decode — mapped to a CMOS std-cell library, gate-level simulated with identical stimulus | 4 × 590/590 results match RTL ↔ gate level | **Power 390.8 → 141.3 µW (−63.8 %)** at 29 % activity · area +0.2 % · Tcrit 2.13 → 2.70 ns · 2 460 vs 2 450 transistors |
| 03 | [03_Smart_Digital_Lock_VHDL](reports/03_Smart_Digital_Lock_VHDL.pdf) | VHDL-2008 4×4 keypad scanner with debounce, 4-digit PIN FSM, change-PIN mode, 3-strike lockout + alarm + timeout, master reset, dual 7-segment status | 88 key presses · 38 checks · PASS (GHDL) | iCE40: 439 LCs · **Fmax 97.2 MHz** · Xilinx-style 180 LUT / 182 FF |
| 04 | [04_FIR_Filter_DSP_VLSI](reports/04_FIR_Filter_DSP_VLSI.pdf) | 15-tap low-pass FIR (scipy firwin → Q1.15; Octave/MATLAB script provided) in direct, transposed and pipelined-symmetric Verilog architectures | All 3 bit-exact vs integer model · **SNR 88.9 dB** vs float · 10 kHz tone −26.3 dB measured = design | LCs 3171 / 1616 / 1973 · Fmax 38.7 / 99.1 / 90.7 MHz · CMOS area 56.6k / 44.8k / 48.3k µm² · power 9.4 / 8.3 / 7.2 mW |
| 05 | [05_UART_Protocol_VHDL](reports/05_UART_Protocol_VHDL.pdf) | VHDL-2008 UART TX/RX FSMs, 16× oversampling, parity + 1/2 stop bits, framing/parity/overflow flags, 8-deep RX FIFO, loopback top, PC terminal script | 46 frames · 68 checks · 9600 / 115200 / 921600 baud · injected parity + framing errors flagged · FIFO overflow · baud-mismatch tolerance 4.5 % ok / 13 % errors | iCE40: 378 LCs · **Fmax 135.0 MHz** · Xilinx-style 107 LUT / 101 FF / 2 RAM32M |
| 06 | [06_Smart_Energy_Meter_GSM](reports/06_Smart_Energy_Meter_GSM.pdf) | Verilog metering DSP (SPI ADC front-end, Vrms/Irms/P/Wh fixed-point MAC, imp/kWh pulse), portable C MCU firmware with SIM800L AT state machine (host-built + mocked), Indian slab-tariff billing simulation | 6 load scenarios · 37/37 registers bit-exact vs Python (P error < 0.02 %) · firmware 20/20 host checks incl. modem time-outs/retries | iCE40: 2393/7680 LCs · **Fmax 44.7 MHz** @ 16 MHz · Xilinx-style 769 LUT / 612 FF / 3 DSP48 |
| 07 | [07_4bit_Processor_Design](reports/07_4bit_Processor_Design.pdf) | 4-bit CPU with custom 16-opcode ISA, 4×4 register file, ALU with Z/C, 3-cycle FSM control unit, ROM/RAM, Python assembler + golden ISA simulator | 3 programs (add + I/O, JZ countdown, Fibonacci to 13) — every OUT matches the golden model · 4/4 unit tests | iCE40: 317 LCs · **Fmax 115.9 MHz** · CMOS 826 cells / 6 205 µm² / 2.35 ns |
| 08 | [08_ASIC_RTL_to_GDSII_OpenSource](reports/08_ASIC_RTL_to_GDSII_OpenSource.pdf) | Counter + RCA/CLA adders through Yosys → CMOS liberty → gate-level equivalence → my own Python physical-design flow (floorplan, SA placement, 2-layer maze routing, DEF, real GDSII writer + reader, DRC-lite); ORFS sky130 + KLayout configs | RTL ↔ gate checksum identical · 7/7 unit tests · GDS re-parsed record-by-record | Util 69.2 % · **HPWL −47 %** after annealing · 122/122 nets routed · 0 DRC-lite violations · GDS 96.7 kB (1 067 BOUNDARY, 589 PATH) |
| 09 | [09_IoT_Home_Automation_Digital_Logic](reports/09_IoT_Home_Automation_Digital_Logic.pdf) | Sensor blocks (PIR, LDR hysteresis, ultrasonic timer), relay interlock, PWM fan/RGB, register-mapped UART command interface for ESP8266/HC-05, clock-gated sleep controller with wake-on-PIR; ESP8266 bridge firmware + Python mock bridge | 40/40 checks · mock Wi-Fi bridge 16/16 replies match | Sleep mode: toggles −53.8 %, **P_dyn −23.6 %**, total −16.1 % · iCE40 968 LCs · Fmax 43.3 MHz |
| 10 | [10_Digital_Voting_Machine_Secure_Memory](reports/10_Digital_Voting_Machine_Secure_Memory.pdf) | 4 candidates + NOTA, debounced switches, officer-gated ballot FSM, I²C master writing CRC-8 sequenced vote records to a 24LC256 EEPROM model with write-verify, tamper seal, PIN-gated results on 7-segment and HD44780 LCD driver | 32/32 checks · LCD init sequence matches datasheet · 4 EEPROM records with valid CRC · double-press and tamper cases | iCE40: 1467 LCs · **Fmax 88.3 MHz** · Xilinx-style 612 LUT / 723 FF |

## How to run

```bash
# toolchain: OSS CAD Suite (yosys, iverilog, ghdl, nextpnr-ice40, icetime) + Python 3.11 (numpy, scipy, matplotlib, reportlab)
export PATH=/path/to/oss-cad-suite/bin:$PATH
cd 01_FPGA_Traffic_Light_Priority && ./run_all.sh     # sim + synth + tests + PASS/FAIL summary; exit code ≠ 0 on failure
make report                                            # regenerates docs/NN_Report.pdf
```

Each folder: `rtl/` (or `src/`) · `tb/` · `sim/` (logs, VCDs, waveform PNGs) · `synth/` (Yosys scripts, nextpnr/icetime reports, .pcf/.xdc) · `docs/NN_Report.pdf` · `brief.md` (original task text) · `README.md` (design notes, results, how to run).

## Tools used here vs. tools named in the brief (declared substitutions)

| Brief asks for | What actually ran in this repo | Ready-to-run artefacts shipped for the named tool |
|----------------|--------------------------------|---------------------------------------------------|
| Vivado / ModelSim simulation | Icarus Verilog 14, GHDL 7 (`--std=08`), self-checking testbenches, VCD → PNG waveforms | `vivado/create_project.tcl` + `.xdc` (Basys-3 / Spartan-7), `modelsim/run.do` — not run here |
| Xilinx Spartan FPGA implementation | Yosys `synth_ice40` + **nextpnr-ice40** real place-and-route + **icetime** timing on iCE40 HX8K; Yosys `synth_xilinx` for Spartan-style LUT/FF/DSP counts | `.xdc` pin constraints; no physical board was programmed |
| Cadence Virtuoso / Synopsys, Microwind / Magic | Yosys + ABC mapping to an educational CMOS liberty (`tools/cmos_cells.lib`), gate-level sim, activity-based power (`tools/power_estimate.py`), path-based STA (`tools/mini_sta.py`), matplotlib CMOS schematic/stick diagrams | ngspice-compatible full-adder SPICE deck; Microwind/Magic how-to — not run here |
| MATLAB coefficient generation | Python/scipy `firwin` | `scripts/gen_coeffs.m` (Octave/MATLAB) — not run here |
| OpenROAD / KLayout RTL-to-GDSII | Yosys synthesis + my own Python floorplan / placement / routing / GDSII writer | OpenROAD-flow-scripts `config.mk` (sky130hd) + `.sdc` + Docker run script, KLayout `.lyp` + viewer — not run here |
| Microcontroller + GSM / ESP8266 hardware | Portable C firmware compiled and unit-tested on the host against mock SPI / mock SIM800L; Python mock Wi-Fi bridge | Arduino `.ino` ports and wiring diagrams — not compiled for a target, no hardware run |

The CMOS library values are representative of a 180 nm-class process and are used for relative comparison only; they are not a foundry PDK. Nothing in this repository claims to have run on hardware or on a tool that was not available.

## Repository map

```
VLSI-Digital-Electronics-Projects-Codec-2026/
├── 01_FPGA_Traffic_Light_Priority/ … 10_Digital_Voting_Machine_Secure_Memory/
├── tools/            shared helpers: make_report.py, vcd2png.py, cmos_cells.lib/.v/_timing.json, mini_sta.py, power_estimate.py
├── dashboard/        index.html — clickable project cards
├── PUSH_TO_GITHUB.md how to publish + submission e-mail template
└── README.md
```

Licence: MIT for my code; tool outputs and briefs belong to their respective owners.
