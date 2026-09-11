# EV Internship Projects — Codec Technologies India (2026)
> **Compact layout:** this folder holds one engineering-report PDF per project (`reports/`), a clickable overview (`dashboard.html`) and the complete source tree as one archive — **`EV-Internship-Projects-Codec-2026_source.zip`** (unzip → each `NN_*/` project folder runs standalone). Project names in the table link to their report PDF.

**Intern:** Eswar Mahalingam · **Track:** Electric Vehicle Internship · **Submission:** Part 01 — all 10 projects

> **Interactive dashboard:** open [`dashboard.html`](dashboard.html) in a browser for a clickable overview — each card opens the matching project. (Enable GitHub Pages to view it as a live site.)

This repository holds my completed work for every project on the Codec Technologies EV internship project list. Each project lives in its own numbered folder and is fully standalone (own `README.md`, `requirements.txt`, entry point, automated tests and generated results), so any folder can be cloned or reviewed on its own. Where the brief names a licensed tool that I did not have (MATLAB/Simulink, HOMER/PVsyst, COMSOL/ANSYS Maxwell, SimaPro), I built the equivalent model in open-source Python and the README of that project maps my modules to the tool's blocks. Where the brief needs hardware (NodeMCU, Arduino, RFID, GPS), the firmware is complete and compile-checked with `arduino-cli`, and the same control logic is proven in a software simulation — but nothing has run on a physical board, which each README states plainly.

| # | Project | Stack | Entry point | Tests |
|---|---------|-------|-------------|-------|
| 1 | [Battery Management System (BMS) Simulation](reports/01_BMS_Simulation.pdf) — 96s2p pack on a 2-RC cell model, Coulomb-counting vs Extended Kalman Filter SOC, capacity/resistance SOH over 500 cycles, lumped thermal model with coolant/heater control, fault detection, passive balancing | Python · NumPy · SciPy · Matplotlib | `python main.py` | 23 passed |
| 2 | [EV Charging Station Locator App](reports/02_EV_Charging_Station_Locator_App.pdf) — Expo / React Native (TypeScript) app with Google Maps (`react-native-maps`, `PROVIDER_GOOGLE`), expo-location, Open Charge Map client with declared-synthetic fallback data, real-time availability (Firebase RTDB / ThingSpeak / simulated), charging-stop route optimiser (greedy corridor + Dijkstra), Leaflet web demo built from the same logic | React Native · Expo · TypeScript · Jest | `npx expo start` (in `app/`), `web-demo/index.html` | 55 passed, `tsc` 0 errors |
| 3 | [Solar-Powered EV Charging Station Design](reports/03_Solar_Powered_EV_Charging_Station.pdf) — HOMER-style 8760-hour techno-economic simulation for Ghaziabad on real NASA POWER irradiance, stochastic EV demand, LiFePO4 storage dispatch, 247-point PV × battery sizing grid, NPC/LCOE/payback, Excel workbook with live formulas | Python · Pandas · openpyxl | `python main.py` | 11 passed |
| 4 | [AI-Powered Driving Efficiency Optimizer](reports/04_AI_Driving_Efficiency_Optimizer.pdf) — physics-based trip simulator (declared synthetic), 19 behaviour features, Ridge vs RandomForest vs GradientBoosting Wh/km prediction (R² 0.975), driver-style classifier (95 % accuracy), counterfactual driving-tip recommender | Python · Scikit-learn · Pandas · Jupyter | `python main.py` | 13 passed |
| 5 | [EV Drivetrain Modeling and Simulation](reports/05_EV_Drivetrain_Modeling_Simulation.pdf) — Simulink-equivalent Python model: PMSM / induction / brushed-DC motors with loss maps, IGBT vs SiC inverter, single-speed gearbox with ratio sweep, Rint pack, backward + forward-PI simulation on WLTP- and MIDC-like cycles, AC vs DC efficiency comparison | Python · NumPy · SciPy · Matplotlib | `python main.py` | 15 passed |
| 6 | [IoT-Based EV Health Monitoring System](reports/06_IoT_EV_Health_Monitoring_System.pdf) — NodeMCU firmware (INA219 + DS18B20 + 12 V divider → ThingSpeak or Firebase, compile-checked), Raspberry Pi alternative, seeded pack simulator, offline ThingSpeak-compatible mock cloud, single-file responsive web dashboard | C++ (ESP8266) · Python · Flask · HTML/JS | `python run_demo.py` | 17 passed |
| 7 | [Lifecycle Analysis of an Electric Vehicle](reports/07_EV_Lifecycle_Analysis.pdf) — screening-level cradle-to-grave LCA (materials, battery, use phase on India/EU/RE grids, maintenance, end-of-life with recycling credit) for a compact EV vs petrol car and e-scooter vs petrol scooter, break-even km, tornado sensitivity, fully-sourced Excel workbook | Python · Matplotlib · openpyxl | `python main.py` | 11 passed |
| 8 | [Smart Traffic Light with EV Priority](reports/08_Smart_Traffic_Light_EV_Priority.pdf) — Arduino Uno controller with MFRC522 RFID whitelist, ETA-aware pre-emption state machine with fairness/starvation guards (compile-checked), NEO-6M + HC-12 GPS variant, Wokwi circuit, SimPy intersection simulation (120 runs) | C++ (AVR) · Python · SimPy | `python simulation/run_experiments.py` | 26 passed |
| 9 | [Wireless Charging System Design](reports/09_Wireless_Charging_System_Design.pdf) — analytical + numerical (Neumann filament, Biot–Savart) model in place of COMSOL/Maxwell: SAE J2954 WPT2 7.7 kW coil pair, SS and LCC-S compensation at 85 kHz, efficiency vs gap/misalignment/load, loss breakdown, B-field map vs ICNIRP limit | Python · NumPy · SciPy | `python main.py` | 15 passed |
| 10 | [EV Market Forecast Dashboard](reports/10_EV_Market_Forecast_Dashboard.pdf) — real IEA Global EV Data Explorer data (GEO 2026, CC BY 4.0), 20 sourced government policies, logistic / Bass / CAGR growth models to 2035, interactive Plotly Dash app (Overview · Forecast · Map · Policies · Data & Sources) plus offline static HTML | Python · Pandas · Plotly · Dash | `python src/app.py` | 40 passed |

**Total: 226 automated tests across 10 projects, all passing.**

## Quick start

```bash
git clone https://github.com/<your-username>/EV-Internship-Projects-Codec-2026.git
cd EV-Internship-Projects-Codec-2026/01_BMS_Simulation      # or any project folder
pip install -r requirements.txt
python main.py            # regenerates everything under results/
python -m pytest tests    # verification suite
```

Python 3.10+ covers the nine Python projects; project 2 needs Node 18+ (`cd app && npm install && npx jest`). Regenerating every result takes under five minutes on a laptop. Firmware in projects 6 and 8 builds with `arduino-cli` (cores `esp8266:esp8266` 3.1.2 and `arduino:avr` 1.8.8).

## Data integrity statement

Real, downloaded data: NASA POWER hourly irradiance (project 3), the IEA Global EV Data Explorer (project 10), and the cited ICCT / CEA / MNRE / UPERC factors in projects 3 and 7 — each with a source URL in that project's README. Everything else (drive cycles, battery telemetry, trips, charging sessions, station lists, traffic arrivals) is **simulated or declared-synthetic** data generated by the models in the code, and every figure and data file says so. No hardware measurement is claimed anywhere; the firmware is compile-checked only. Nothing in this repository is presented as a measurement that was not actually obtained.

## Highlights

- **BMS (1):** EKF SOC RMSE 0.63 % vs −6.6 % Coulomb-counting drift; thermal manager holds a 1.5C fast charge at 34 °C where the unmanaged pack hits 50.9 °C; SOH 90.1 % after 500 cycles.
- **Locator app (2):** Dijkstra charging-stop planner beats greedy by 19 min on a Modinagar → Pari Chowk trip at 20 % SOC; whole app type-checks under strict TypeScript.
- **Solar station (3):** 70 kWp + 125 kWh LiFePO4 serves 96 % of a 152 kWh/day load; LCOE ₹17.20/kWh — honestly ~40 % dearer than the ₹12.24/kWh grid-tied alternative.
- **Driving optimizer (4):** aggressive drivers average 178.7 Wh/km vs 134.3 for eco; recommender predicts a 19.9 % combined saving for aggressive trips.
- **Drivetrain (5):** PMSM 90.4 % cycle efficiency / 142.6 Wh/km vs brushed DC 80.1 % / 166.4 Wh/km; SiC inverter cuts inverter loss by 54 %.
- **IoT monitor (6):** 960 simulated uploads round-trip through the mock cloud to a live dashboard; both firmware variants compile at 370 kB flash.
- **LCA (7):** compact EV 31.5 t CO₂e vs petrol 41.6 t over 150,000 km on today's Indian grid (−24 %), break-even at 12,163 km; −69 % on the EU grid.
- **EV-priority signals (8):** at 5 % EV share the ETA-aware controller halves EV delay (16.8 → 8.1 s) for +4 % non-EV delay, with non-green time per approach capped at 60 s.
- **Wireless charging (9):** k = 0.221 at 175 mm gap, system efficiency 96.5 % at 7.7 kW, 96.3 % at 75 mm misalignment; bystander field 11.9 µT vs the 27 µT ICNIRP reference.
- **Market dashboard (10):** 21.0 M electric cars sold in 2025 (25 % share, China 62 % of volume, India 4.0 %); fixed-ceiling logistic model gives ~66 % world share by 2030.

## Licence

Code: MIT. IEA data: CC BY 4.0; NASA POWER data: public domain (attribution in the project READMEs).
