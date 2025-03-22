# 🔍 Splunk Free Setup & Use

This file documents how I installed and configured Splunk (Free) for local SIEM-style log collection and analysis in my lab.

## 🛠️ Installation
- Host OS: Ubuntu Server (VM)
- Downloaded from: https://www.splunk.com/en_us/download/splunk-enterprise.html
- Version: Splunk Enterprise Free (500MB/day limit)
- Installed via `.deb` package

## 🔐 Login
- Default URL: `http://<vm-ip>:8000`
- Admin user/password set during first run

## 📥 Log Sources
- Local syslog from Ubuntu server
- Forwarded logs from Kali using `Splunk Universal Forwarder`
- Apache web logs for simulated attacks

## 📊 Use Cases
- Created dashboards showing:
  - SSH login attempts
  - Port scans
  - Apache 404s and 500s
- Used search queries to:
  - Detect brute-force patterns
  - Correlate logs between machines
  - Visualize nmap scans

## 📝 Notes
- Splunk service runs on boot using `systemctl`
- Regularly clean test logs to stay under the daily ingest limit
- Planning to add Zeek logs as next integration
