# Cyber Security Projects — Codec Technologies India (2026)

**Intern:** Eswar Mahalingam · **Track:** Cyber Security Internship · **Submission:** all 20 projects (both project sets)

> **Interactive dashboard:** open [`dashboard/index.html`](dashboard/index.html) in a browser for a clickable overview with search and category filters — each card opens the matching project. (Enable GitHub Pages to view it as a live site.)

This repository holds my completed work for every project on the Codec Technologies Cyber Security internship list — the 10 core projects and the 10 advanced projects — built into one repo. Each project is its own numbered, standalone folder with a `README.md` (first person), `requirements.txt`, a runnable entry point, a `tests/` suite, and generated `results/`. Everything is **defensive and educational**: every project builds its own self-contained lab targets or synthetic data and is designed to run only against those or systems you own. **226 automated tests pass across the 20 projects** (223 Python + a Jest note where applicable).

## Responsible-use and scope

I built this as a learning portfolio, so a few briefs are delivered as the *defensive* version, which is the stronger thing to demonstrate and the safe thing to publish:

- **#13 "Custom Ransomware Simulation"** is built as a **ransomware-behaviour detector**, not ransomware. It never encrypts or harms real files — a benign, sandboxed workload writes throwaway high-entropy files inside a `/tmp` directory the project creates, purely so the detector (canary files, entropy-spike and mass-modification monitoring) has activity to catch. A test asserts nothing outside the sandbox is ever touched.
- **#04 Phishing** and **#14 "Dark-Web Monitoring"** are built as **detection + safe internal awareness** and **credential-exposure threat intelligence on lawful/simulated sources**. No credential-harvesting pages, no real-organisation impersonation, no scraping of illegal marketplaces; the awareness page is asserted by test to contain no password field, and the exposure checker only ever transmits a 5-character hash prefix (k-anonymity).
- Every other project (VAPT lab, firewall, IDS, secure web app, cryptography, password hashing/cracking, traffic analysis, IR playbook, honeypot, mobile/IoT labs, email gateway, browser-exploit detection, forensics, secure file sharing, insider-threat, CTF platform) targets **only bundled lab objects on localhost or synthetic data**. Each folder's README carries an "Ethics & scope" note.

Use any of this only against systems and data you own or are explicitly authorised to test.

## Project index — Set A (core)

| # | Project | Focus | Entry point | Tests |
|---|---------|-------|-------------|-------|
| 1 | [VAPT Lab](01_VAPT_Lab/) | Bundled vulnerable Flask app + scanner (nmap/socket, header check, web-vuln probe) + CVSS report | `python main.py` | 11 |
| 2 | [Personal Firewall](02_Personal_Firewall/) | scapy packet monitor + pure rule engine (IP/CIDR/port/proto/direction), iptables translation | `python main.py` | 11 |
| 3 | [IDS with ML](03_IDS_ML/) | RandomForest + IsolationForest on real NSL-KDD; PCAP→flow scoring | `python main.py` | 7 |
| 4 | [Phishing Detection & Awareness](04_Phishing_Detection_and_Awareness/) | URL + email phishing classifiers (real feeds) + safe awareness simulator | `python main.py` | 8 |
| 5 | [Secure Web Application](05_Secure_Web_Application/) | Flask app demonstrating the OWASP Top 10 defenses (argon2, JWT, RBAC, CSRF, headers) | `python -m pytest tests` | 10 |
| 6 | [Cryptography Algorithms](06_Cryptography_Algorithms/) | AES-GCM + from-scratch AES-128, RSA OAEP/PSS, SHA/HMAC, secure-channel demo, NIST vectors | `python main.py` | 12 |
| 7 | [Password Hashing & Cracking](07_Password_Hashing_and_Cracking/) | MD5→bcrypt/argon2 timing, dictionary/brute-force on self-made hashes, strength meter | `python main.py` | 8 |
| 8 | [Network Traffic Analysis](08_Network_Traffic_Analysis/) | scapy PCAP analysis: SYN-scan, beacon/C2, DNS burst, exfil, plaintext creds | `python main.py` | 8 |
| 9 | [Incident Response Playbook](09_Incident_Response_Playbook/) | NIST 800-61r2 plan + 6 ATT&CK-mapped playbooks (PDF) + log-triage mini-SIEM | `python main.py` | 8 |
| 10 | [Honeypot](10_Honeypot/) | Low-interaction SSH/HTTP/Telnet honeypot, credential capture, analytics dashboard | `python main.py` | 7 |

## Project index — Set B (advanced)

| # | Project | Focus | Entry point | Tests |
|---|---------|-------|-------------|-------|
| 11 | [Mobile App Security Testing Framework](11_Mobile_App_Security_Testing_Framework/) | Static analysis of a self-made insecure Android app → OWASP Mobile Top 10 / MASVS | `python main.py` | 8 |
| 12 | [IoT Device Pentest Lab](12_IoT_Device_Pentest_Lab/) | Simulated vulnerable IoT services on localhost + assessment toolkit + firmware triage | `python main.py` | 9 |
| 13 | [Ransomware Behaviour Detection](13_Ransomware_Behaviour_Detection/) | **Defensive:** canary + entropy/mass-modification monitor; sandboxed benign workload | `python main.py` | 17 |
| 14 | [Threat-Intel Credential-Leak Monitor](14_Threat_Intel_Credential_Leak_Monitor/) | **Defensive:** k-anonymity breach check, synthetic leak feed, IOC enrichment | `python main.py` | 13 |
| 15 | [Email Security Gateway](15_Email_Security_Gateway/) | SPF/DKIM/DMARC, URL/attachment scanning, ML spam/phish classifier → ALLOW/QUARANTINE/REJECT | `python main.py` | 23 |
| 16 | [Browser Exploit Detection Toolkit](16_Browser_Exploit_Detection_Toolkit/) | Detects XSS sinks, clickjacking, weak CSP, obfuscation, cookie flags in sample pages | `python main.py` | 16 |
| 17 | [Digital Forensics Toolkit](17_Digital_Forensics_Toolkit/) | Hashing/chain-of-custody, JPEG carving, EXIF/PDF metadata, timeline, memory triage | `python main.py` | 12 |
| 18 | [Secure File Sharing Platform](18_Secure_File_Sharing_Platform/) | AES-256-GCM envelope encryption, RSA/scrypt key wrap, expiring links, audit log | `python demo.py` | 15 |
| 19 | [Insider Threat Detection](19_Insider_Threat_Detection/) | UBA on synthetic CERT-style logs: z-scores + IsolationForest + peer groups, precision@K 1.0 | `python main.py` | 9 |
| 20 | [CTF Platform](20_CTF_Platform/) | Flask CTF: 8 solvable challenges, hashed-flag submission, scoreboard, first-blood, Docker stack | `python run.py` | 11 |

**Total: 226 automated tests, all passing.**

## Quick start

```bash
git clone https://github.com/<your-username>/Cyber-Security-Projects-Codec-2026.git
cd Cyber-Security-Projects-Codec-2026/01_VAPT_Lab      # or any project folder
pip install -r requirements.txt
python main.py            # regenerates that project's results/
python -m pytest tests    # verification suite
```

Python 3.10+ covers every project. A few use optional system tools (nmap for #1, Playwright/Chromium for screenshots in #5/#16/#18/#20) and degrade gracefully with a note in the README when a tool is absent.

## Data integrity statement

Real, public data used (and cited in the project READMEs): the **NSL-KDD** intrusion dataset (#3), abuse.ch **URLhaus** + Cisco Umbrella URL feeds (#4), the UCI **SMS Spam Collection** (#15). Standard cryptographic **test vectors** (FIPS-197, NIST CAVP, RFC 4231) are used in #6. Everything else — packet captures, honeypot events, IoT/mobile targets, forensic evidence, insider-activity logs, leak feeds, CTF flags — is **synthetic or self-made lab data, declared as such** in the files and READMEs. No real host, account, device, or network is ever contacted, and no measurement is presented that was not actually produced by the code.

## Licence

MIT (see `LICENSE`). Third-party datasets retain their own licences, noted in each project's README.
