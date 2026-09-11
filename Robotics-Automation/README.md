# Robotics & Automation Projects — Codec Technologies Internship 2026

**Author:** Eswar Mahalingam · Robotics & Automation Intern, Codec Technologies India (Aug 2026 – Present, Remote)
**Contact:** +91-9360548243 · eswarmba05313@gmail.com · Ghaziabad, UP, India

All ten simulation projects from the internship brief. Each folder is standalone: the algorithms (path planning, control, SLAM, kinematics, computer vision) are implemented from scratch in Python and exercised by a full simulation with a GIF/MP4 of the run, a `unittest` suite, a one-command `run_all.sh`, and a 2–4 page engineering report PDF. Every number below was produced by the code in this repository; the logs and `metrics.json` files sit next to each result.

**Compact layout:** this folder holds the 10 engineering-report PDFs (`reports/`), a clickable overview (`dashboard.html`) and the complete source tree as one archive — **`Robotics-Automation-Projects-Codec-2026_source.zip`** (unzip → each `NN_*/` project folder runs standalone with `./run_all.sh`). Project names in the table below link to their report PDF.

## Projects

| # | Folder | What I built | Measured results | Tests |
|---|--------|--------------|------------------|-------|
| 01 | [01_Autonomous_Warehouse_Robot](reports/01_Autonomous_Warehouse_Robot.pdf) | 40×30 warehouse grid, differential-drive robot, 72-beam ray-cast LiDAR, **A\* and Dijkstra** planners, pure-pursuit follower, LiDAR-triggered re-planning, OpenCV item recognition (HSV + contour + template), 6-order pick-and-place mission with task log | 6/6 picks · **0 collisions** · 147.2 m driven vs 150.3 m planned · 5 re-plans around 3 dropped boxes · recogniser 98 % on 50 items · A\* expands 97.8 vs Dijkstra 331.4 nodes for identical path lengths | 17/17 |
| 02 | [02_Robotic_Arm_Quality_Inspection](reports/02_Robotic_Arm_Quality_Inspection.pdf) | Synthetic PCB-tile conveyor with 5 injected defect types, ECC-aligned classical defect pipeline **and** HOG + colour SVM/RF classifiers (disjoint train/test), 4-DOF DH arm with analytic + damped-least-squares IK, trapezoidal trajectories, per-item JSON/CSV/HTML/PDF inspection reports | Classical 96.0 % · SVM 97.3 % · RF 90.0 % (scratch class is the weak spot, reported) · 0 false alarms · 24/24 cell verdicts · 21.5 items/min · IK error ≤ 1e-5 m | 15/15 |
| 03 | [03_Voice_Controlled_Home_Bot](reports/03_Voice_Controlled_Home_Bot.pdf) | Smart-home device state machines with power model, virtual robot moving between rooms, from-scratch MFCC + DTW keyword recogniser on synthetic speech, intent/slot **command parser** (synonyms, numbers, compound commands, negation, confirmations), actuator + feedback module; Google `speech_recognition` adapter | Isolated words 98.3 % @ 20 dB → 95.8 % @ 5 dB SNR · sentences 75–83 % raw / 98–99 % with grammar · 6/6 spoken commands executed · 32 parser cases | 14/14 |
| 04 | [04_Self_Balancing_Robot](reports/04_Self_Balancing_Robot.pdf) | Nonlinear two-wheeled inverted-pendulum dynamics + motor model (RK4 @ 1 kHz), IMU simulation, **complementary vs Kalman** fusion, **cascaded PID** (tilt / velocity) with anti-windup, scripted teleop, linearisation, pole analysis, gain sweep | Balances from 10° in 0.65 s · 0.4 m/s step: rise 0.96 s, overshoot 12.3 % · 0.4 N·s push → 7.6° max, recovered in 0.76 s · tilt RMSE accel 2.74° → KF+encoder **0.33°** · open-loop pole +10.6 s⁻¹, all closed-loop poles stable | 18/18 |
| 05 | [05_Surveillance_Drone](reports/05_Surveillance_Drone.pdf) | 6-DOF quadrotor with cascaded control, **WGS84 → ENU GPS waypoints**, geofence, return-to-home, battery model, rendered compound with 7 moving intruders, MOG2 + reference-map differencing + HOG-SVM detection, centroid tracker, alert engine with zones and snapshots | 12/12 waypoints (1.48 m mean error) · 0 fence breaches · 7/7 intruders · recall 97.7 % / precision 99.5 % · 12 alerts, 0 false · alert latency 1.23 s mean | 13/13 |
| 06 | [06_Smart_Farming_Robot](reports/06_Smart_Farming_Robot.pdf) | Field water-balance model, capacitive-moisture + DS18B20 sensor models, boustrophedon rover, synthetic canopy images → ExG/VARI/pseudo-NDVI + leaf-spot detection, hysteresis **irrigation controller** with daily water budget vs timer baseline, 30-day run, analytics dashboard | 96 plots × 3 days: **water 2 488 L vs 10 800 L timer (−77 %)** · stress-hours 15.0 vs 266.5 · zero drainage vs 500 L · crop-health classifier 96.0 % on 150 held-out canopy images (98.3 % in-sim) · moisture sensor RMSE 0.012 VWC with 3 % dropouts handled | 18/18 |
| 07 | [07_Gesture_Controlled_Arm](reports/07_Gesture_Controlled_Arm.pdf) | Classical gesture recogniser (YCrCb skin segmentation → convex hull / convexity defects → finger count, pointing direction, palm position) on 300 synthetic frames; 6-DOF DH arm with **Levenberg–Marquardt IK** + joint limits + null-space posture; One-Euro filtering and velocity/acceleration-limited trajectories; MediaPipe adapter | Recogniser **95.6 %** (confusion matrix) · IK 200/200 converged, 0.010 mm mean error · **jerk −97 %** after filtering · 7.6 ms/frame | 17/17 |
| 08 | [08_Search_Rescue_Robot](reports/08_Search_Rescue_Robot.pdf) | Rubble terrain with slope cost, skid-steer with slip, 2-D LiDAR, **log-odds occupancy SLAM with correlative scan matching + ICP**, frontier exploration + A\*, HSV vest detection fused with 2-mic **TDOA** bearing, coverage tracking, mission map report | 4/4 victims in 164 s · 97.0 % coverage · pose RMSE **0.34 m with SLAM vs 1.41 m odometry-only** · yaw RMSE 1.4° vs 22.6° · 60.6 m travelled | 10/10 |
| 09 | [09_Automated_Parking_System](reports/09_Automated_Parking_System.pdf) | 3-level structure as aisle graph, self-written discrete-event simulator with peak/off-peak Poisson arrivals, 4 **slot-allocation strategies** (incl. 2-wheeler / SUV / EV slots), A\*/Dijkstra + bicycle-model manoeuvres, car-following + level locks + merge yielding, independent SAT collision monitor, ₹ revenue dashboard GIF + static HTML | **0 collisions** over 4 strategies × 4 seeds (2 h peak, 114 vehicles) · closest approach 3.7 m · tiered strategy: 53 s avg wait, 69 % peak utilisation · M/M/1 Wq 13.2 s vs Erlang-C 12.0 s · manoeuvre end error 7 cm | 12/12 |
| 10 | [10_Conveyor_Sorting_Automation](reports/10_Conveyor_Sorting_Automation.pdf) | Belt + camera station renderer, HSV colour / contour shape / Hu-moment classification with mm calibration, two cascaded **SCARA arms** (FK/IK, pick windows from belt speed, EDF dispatch), discrete-event workflow with throughput, missed-pick and OEE metrics, belt-speed sweep | Vision **99.7 %** on 600 items, size error 0.29 mm mean · nominal run: 133 sorted / 16 true rejects / 0 mis-sorts / 0 missed · OEE 0.993 · first missed pick at 250 mm/s, two-arm ceiling ≈ 52 items/min | 9/9 |

## How to run

```bash
# Python 3.11 with numpy, scipy, matplotlib, opencv-python, scikit-image, scikit-learn, networkx, pandas, reportlab; ffmpeg for GIFs
cd 01_Autonomous_Warehouse_Robot && ./run_all.sh     # sim + tests + PASS/FAIL summary; exit code ≠ 0 on failure
python3 -m unittest discover -s tests -v             # tests only
make report                                          # regenerates docs/NN_Report.pdf
```

Each folder: `src/<pkg>/` (algorithms, imported unchanged by the simulator, the tests and the ROS 2 node) · `sim/` (run script, GIF/MP4, plots, logs, metrics JSON) · `tests/` · `ros2_ws/src/<pkg>/` (ROS 2 Humble package: `package.xml`, `setup.py`, `node.py`, launch file) · `worlds/` or vendor stubs · `docs/NN_Report.pdf` · `brief.md` · `README.md`.

## Tools used here vs. tools named in the brief (declared substitutions)

| Brief asks for | What actually ran in this repo | Ready-to-run artefacts shipped for the named tool |
|----------------|--------------------------------|---------------------------------------------------|
| ROS + Gazebo / Webots / Unity / AirSim | Pure-Python simulators (numpy / scipy / OpenCV / matplotlib) implementing the same robot models, sensors and algorithms | ROS 2 Humble packages (`ros2_ws/src/<pkg>/` — nodes wrap the identical algorithm modules; `py_compile`-checked only), Webots `.wbt` worlds + controller stubs, Gazebo `.sdf` worlds, PX4/MAVROS launch skeleton, AirSim client script, Unity C# controller stub — **not run here** |
| RoboDK / V-REP (CoppeliaSim) | Own DH-parameter arm models with FK / analytic + numeric IK and trajectory generation | RoboDK API scripts and CoppeliaSim ZMQ remote-API stubs — not run here |
| MediaPipe + webcam | Classical OpenCV hand pipeline on synthetic frames | `mediapipe_backend.py` adapter with the same interface, `webcam_demo.py` — not run here (no camera, no MediaPipe) |
| Speech-recognition API | From-scratch MFCC + DTW / k-NN recogniser on synthetic formant audio, plus typed-text fallback | Google `speech_recognition` adapter — not run here |
| SLAM packages (slam_toolbox / Nav2) | Own log-odds occupancy mapping, correlative scan matching, ICP, frontier exploration | slam_toolbox / Nav2 parameter and launch files — not run here |

Nothing in this repository claims to have run in ROS, Gazebo, Webots, Unity, AirSim, RoboDK or on a real robot. All "declared substitution" items are marked as such in each project's README and report.

## Repository map

```
Robotics-Automation-Projects-Codec-2026/
├── 01_Autonomous_Warehouse_Robot/ … 10_Conveyor_Sorting_Automation/
├── tools/            make_report.py (navy/gold report generator)
├── dashboard/        index.html — clickable project cards
├── PUSH_TO_GITHUB.md how to publish + submission e-mail template
└── README.md
```

Licence: MIT for my code; briefs belong to Codec Technologies.
