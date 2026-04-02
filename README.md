# 👁️ OInjectEye

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Linux-informational?style=flat-square&logo=linux&logoColor=white&color=0a0c10"/>
  <img src="https://img.shields.io/badge/Category-OForensics%20%2F%20Memory%20Analysis-cyan?style=flat-square"/>
  <img src="https://img.shields.io/badge/Dependencies-psutil%20(optional)-yellow?style=flat-square"/>
  <img src="https://img.shields.io/badge/License-Proprietary-green?style=flat-square"/>
  <img src="https://img.shields.io/badge/Part%20of-OwlSec%20Toolkit-7b5ea7?style=flat-square"/>
  <img src="https://img.shields.io/badge/Version-v2.1-cyan?style=flat-square"/>
</p>

> **OInjectEye** is a fileless malware signature builder and memory forensics tool. It scans live process memory (`/proc/<pid>/mem`) or raw memory dumps for fileless IOCs and automatically generates tiered YARA rules.

---

## 📌 Overview

OInjectEye specializes in detecting **fileless malware** techniques commonly used by advanced threats:
- AMSI bypass
- Reflective PE/DLL loading
- PowerShell obfuscation & encoded commands
- WMI persistence & execution
- .NET assembly loading & injection
- In-memory PE headers (Mini-PE)
- High-entropy Base64 payloads

It outputs structured JSON reports and ready-to-use tiered YARA rules (high/medium/hunting confidence).

---

## 🖥️ Modules

| # | Module               | Description |
|---|----------------------|-------------|
| **[1]** | **Live Scan**        | Scan all or suspicious running processes (Linux) |
| **[2]** | **PID Scan**         | Target specific process IDs |
| **[3]** | **Dump Scan**        | Analyze raw memory dump files |
| **[4]** | **YARA Builder**     | Generate tiered YARA rules from last scan |
| **[5]** | **View Report**      | Display detailed last scan results |
| **[6]** | **Settings**         | Configure scan limits, entropy thresholds, YARA parameters |

---

## 📊 Key Features

- **Live Memory Scanning** — Direct access to `/proc/<pid>/mem` and maps
- **Mini-PE Detection** — Finds in-memory PE headers with valid sections
- **Pattern Matching** — AMSI, ReflectiveLoader, IEX, WMI, .NET injection APIs
- **Entropy-Gated Base64** — High-entropy Base64 with decoded payload analysis
- **Risk Scoring Engine** — Weighted scoring (0-100) with category bonuses and noise penalties
- **Tiered YARA Generation** — High confidence (proximity), medium, and broad hunting rules
- **Context Awareness** — Suppresses legitimate Defender/PS contexts
- **Structured Export** — JSON reports + ready-to-use `.yar` files

---

## ⚙️ Requirements

- **Linux** (for live process memory scanning)
- **Root / sudo** recommended for full `/proc/<pid>/mem` access
- **Optional**: `pip install psutil` (for easier process enumeration)

---

## 🚀 Usage

```bash
sudo ./OInjectEye

📁 Output

Live Results — Color-coded risk scores per process with IOC count
Detailed Findings — Category, pattern, context (ASCII + hex), region info
Score Breakdown — Base score, entropy bonus, structural bonus, proximity, noise penalty
JSON Report — ofileless_YYYYMMDD_HHMMSS.json (full structured data)
YARA Rules — ofileless_YYYYMMDD_HHMMSS.yar with high/medium/hunting tiers


📦 Part of OwlSec Toolkit
This tool is part of the OwlSec suite — a collection of 300+ security and privacy tools.
🔗 owlsec.org

©️ License
Proprietary — © Khaled S. Haddad
Tools are distributed as pre-built executables. Source code is proprietary.

AUTHORISED MEMORY FORENSICS AND FILELESS MALWARE ANALYSIS USE ONLY
