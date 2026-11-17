# 🦅 Eagle-Eye: Automated Perimeter Reconnaissance Pipeline

**Eagle-Eye** is a robust, menu-driven Bash reconnaissance framework developed in **Void Labs** designed to automate the outer perimeter discovery phase for web application penetration testing and bug bounty hunting. 

It implements a structured first-principles methodology—separating human-readable audit logs from machine-readable clean input streams for seamless tool chaining.

---

## 🚀 Key Features

* **Interactive Scan Intensity Selector**: Upfront configuration menu allowing operators to choose scan scopes with built-in safety controls.
* **15-Second Safety Countdown & Visual Loading Bar**: Prevents accidental heavy scans against unauthorized targets by incorporating a warning timer and visual progress bar with `Ctrl+C` abort functionality.
* **Dual-Mode Output Architecture**:
  * *Human-Readable Logs*: Captures full HTTP status codes, server technologies, and WAF headers (`live_web_assets.txt`).
  * *Machine-Readable Streams*: Strips all unnecessary metadata into a clean URI list (`live_domains_for_harvest.txt`) built specifically to feed downstream tools like **Project 2 (`deep_harvest`)**.
* **Multi-Stage Reconnaissance Flow**: Fully automates passive subdomain harvesting (`subfinder`), active DNS resolution (`dnsx`), HTTP probing (`httpx`), and targeted port scanning (`nmap`).

---

## 🛠️ Pipeline Architecture & Workflow

```text
 [Target Domain] 
        │
        ├──► Phase 1: Passive Discovery (subfinder) ──► subdomains_passive.txt
        │
        ├──► Phase 2: DNS Resolution (dnsx) ─────────► hosts_for_nmap.txt / subdomains_resolved.txt
        │
        ├──► Phase 3: HTTP Probing (httpx) ──────────► live_web_assets.txt (Audit Log)
        │                                            └─► live_domains_for_harvest.txt (Project 2 Input)
        │
        └──► Phase 4: Port Scanning (nmap) ──────────► nmap_scan_results.txt

## 🚀 Installation & Usage

### 1. Setup
```bash
git clone [https://github.com/lishanthan-shrihari/eagle-eye-recon.git](https://github.com/lishanthan-shrihari/eagle-eye-recon.git)
cd eagle-eye-recon
chmod +x eagle_eye
sudo cp eagle_eye /usr/local/bin/eagle_eye
