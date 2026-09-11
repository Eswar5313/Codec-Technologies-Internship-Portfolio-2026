# Codec Technologies Internship Portfolio 2026 — All Tracks in One Repo

**Author:** Eswar Mahalingam · Intern, Codec Technologies India (Aug 2026 – Present, Remote)
**Contact:** +91-9360548243 · eswarmba05313@gmail.com · Ghaziabad, UP, India

One repository for every Codec Technologies internship track I completed, kept deliberately compact: each track folder carries its results README, a clickable dashboard, one engineering-report PDF per project, and the complete source tree as a single zip archive that unpacks into standalone, runnable project folders. Nothing here is a mock-up — every figure in the READMEs and reports was produced by running the code in the archives, and every tool that was *not* available to me is named as a declared substitution rather than implied.

Open **[index.html](index.html)** for the landing dashboard.

## Tracks

| Track | Folder | Projects | Verification | Highlights (measured) |
|-------|--------|----------|--------------|-----------------------|
| Digital Electronics & VLSI | [Digital-Electronics-VLSI](Digital-Electronics-VLSI/) | 10 — traffic-light controller with emergency priority, low-power CMOS ALU, VHDL digital lock, FIR filter (3 architectures), UART, GSM energy meter, 4-bit CPU, RTL-to-GDSII flow, IoT home automation, digital voting machine | 10/10 `run_all.sh` PASS · Icarus Verilog / GHDL / Yosys / nextpnr-ice40 / icetime | ALU power −63.8 % · UART Fmax 135 MHz · FIR SNR 88.9 dB · 122/122 nets routed to a real GDSII · 12 real place-and-route runs |
| Robotics & Automation | [Robotics-Automation](Robotics-Automation/) | 10 — warehouse AMR (A*/Dijkstra), inspection arm (OpenCV + IK), voice-controlled home bot, self-balancing robot (PID + Kalman), surveillance drone, farming robot, gesture-controlled arm, SLAM search & rescue, automated parking, conveyor sorting | 10/10 `run_all.sh` PASS · 143 unit tests · pure-Python simulators + ROS 2 package skeletons | 0 collisions in every run · SLAM pose RMSE 0.34 m vs 1.41 m odometry · conveyor vision 99.7 % · irrigation water −77 % |
| Electric Vehicle | [Electric-Vehicle](Electric-Vehicle/) | 10 — BMS simulation, charging-station locator app, solar charging station, AI driving-efficiency optimiser, drivetrain model, IoT EV health dashboard, EV lifecycle analysis, EV-priority traffic light, wireless charging design, EV market forecast dashboard | 226 tests PASS (Python + Jest; firmware compile-checked) | EKF SOC RMSE 0.63 % · GradientBoosting R² 0.975 · real IEA GEO 2026 market data |
| Cyber Security | [Cyber-Security](Cyber-Security/) | 20 — two sets of ten defensive projects (IDS on NSL-KDD, phishing detection, ransomware-behaviour detector, SMS spam classifier, threat-intel k-anonymity monitor, and more) against self-contained lab targets | 226 tests PASS · defensive/educational only | Real datasets: NSL-KDD, URLhaus/Umbrella feeds, UCI SMS Spam |

## Why the compact layout

GitHub's web uploader accepts at most 100 files per upload, and the full source trees run to several hundred files per track. So each track folder is structured as:

```
<Track>/
├── README.md                     results table, how to run, declared substitutions (project names link to their report)
├── dashboard.html                clickable project cards (open in a browser)
├── reports/NN_ProjectName.pdf    one 2–4 page navy/gold engineering report per project
└── <Track>_source.zip            complete source tree: NN_*/ folders each with code, tests, sim outputs, Makefile, run_all.sh (report PDFs live in reports/)
```

To run anything: download the track's `*_source.zip`, unzip, `cd` into a project folder, `./run_all.sh`. Each track README lists the toolchain it needs (OSS CAD Suite for VLSI; Python 3.11 with numpy/scipy/OpenCV for Robotics; Node for the EV app).

## Declared substitutions (applies to every track)

Vivado, ModelSim, Cadence, Synopsys, MATLAB, Microwind, Magic, OpenROAD, KLayout, physical FPGA boards, GSM/MCU hardware, ROS/Gazebo, Webots, Unity, AirSim, RoboDK, CoppeliaSim, MediaPipe, cloud speech APIs and webcams were not available where this work was done. In every such case the engineering was implemented with open-source equivalents that actually ran, and ready-to-run files for the named tool are included and marked "provided, not run here". No result in this repository is claimed for a tool or device that did not execute it.

## Submission

Published for the Codec Technologies internship programme; the GitHub link together with the offer letter goes to vaishali@codectechnologies.in. Licence: MIT for my code; briefs and datasets belong to their respective owners.
