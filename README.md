# 🦅 Eagle Eye: Automated Reconnaissance & Attack Surface Mapping Pipeline

[![Bash](https://img.shields.io/badge/Language-Bash-blue.svg)](https://www.gnu.org/software/bash/)
[![Security](https://img.shields.io/badge/Domain-Web%20Application%20Penetration%20Testing-red.svg)]()
[![Void Labs](https://img.shields.io/badge/Created%20By-Void%20Labs%20%2F%20Knull-purple.svg)]()

> *An automated, modular reconnaissance framework designed to eliminate manual overhead during initial target scoping, combining passive intelligence gathering with active HTTP probing and safety-engineered port scanning.*

---

## 🛠️ Architecture & Workflow
Eagle Eye operates on a disciplined 4-phase reconnaissance lifecycle:
1. **Passive Subdomain Enumeration (`subfinder`):** Queries Certificate Transparency (CT) logs (`crt.sh`) to harvest historical asset records without touching the target's perimeter infrastructure.
2. **DNS Hygiene & Resolution (`dnsx`):** Validates raw records against active resolvers, eliminating wildcard DNS traps and returning strictly live IPv4/IPv6 endpoints.
3. **HTTP Probing & Fingerprinting (`httpx`):** Probes live assets to extract HTTP status codes, page titles, and backend technology stacks (e.g., Nginx, React, WordPress).
4. **Targeted Port Mapping (`nmap`):** Translates live web hosts into clean target lists, feeding them into a tiered Nmap engine with built-in safety controls.

---

## ⚙️ Key Technical Features
* **Tiered Intensity Menu:** Built-in safety selection allowing operators to choose between standard web ports (`80, 443, 8080, 8443, 3000`), top 1000 common ports (`1-1000`), or a full ultra scan (`-p-`).
* **Safety-Engineered Abort Window:** Features a dynamic 15-second animated countdown warning on heavy scans, giving operators a critical window to abort (`Ctrl+C`) before triggering client IDSs or rate limits.
* **Modular Artifact Management:** Automatically organizes scan outputs into dedicated, structured directories (`recon_<target>/`) for clean reporting.

---

## 🚀 Installation & Usage

### 1. Setup
```bash
git clone [https://github.com/lishanthan-shrihari/eagle-eye-recon.git](https://github.com/lishanthan-shrihari/eagle-eye-recon.git)
cd eagle-eye-recon
chmod +x eagle_eye
sudo cp eagle_eye /usr/local/bin/eagle_eye
