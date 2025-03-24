# 🧰 Incident Response Case Study: SplunkServer Recovery (Disk Full)

## 🧩 Problem Summary
While building a home cybersecurity lab and installing Splunk on a virtualized Ubuntu Server, the system became unresponsive and inaccessible due to **100% disk usage**. 

This caused:
- Login failures (GUI would not accept credentials)
- Inability to access terminal
- Inability to restart or repair Splunk

## ⚙️ Root Cause
- Ubuntu root volume was only ~12GB
- Downloaded packages, logs, XFCE GUI, and Splunk installers consumed all available space
- Splunk log/temp data caused volume to hit **100% full**

## 🚑 Recovery Procedure (via Live ISO)
### 1. Booted into Ubuntu Live ISO:
- Launched the system using a mounted Ubuntu Live ISO environment
- Verified disk layout using `fdisk -l`
- Mounted the LVM root volume:
  ```bash
  sudo mkdir /mnt/recovery
  sudo mount /dev/mapper/ubuntu--vg-ubuntu--lv /mnt/recovery
  ```

### 2. Cleanup to Regain Space:
Removed or cleared the following to free disk space:
- `/home/flipxcrsp/splunk-9.2.1.deb`
- `/opt/splunk/var/run/splunk/*`
- `/var/cache/apt/archives/*`
- `/var/log/*`
- `/home/flipxcrsp/Downloads/*`

### 3. Reclaimed ~1GB space to regain OS access

---

## 📦 Filesystem Expansion (LVM)

### Extended Logical Volume:
```bash
sudo lvextend -l +100%FREE /dev/mapper/ubuntu--vg-ubuntu--lv
```

### Resized Filesystem:
```bash
sudo resize2fs /dev/mapper/ubuntu--vg-ubuntu--lv
```

✅ Result: Disk space expanded from **12G ➜ 23G**

### Verified Expansion:
```bash
df -h /mnt/recovery
# Filesystem      Size  Used Avail Use%
# /dev/mapper/...  23G   11G   11G  51%
```

---

## 🔁 System Boot & Validation
- Detached ISO from VirtualBox
- Set boot priority to Hard Disk
- Successfully booted into native OS GUI
- Login successful

---

## 📊 Splunk Service Recovery
```bash
sudo /opt/splunk/bin/splunk restart
```
- Splunk started successfully
- Access confirmed at: [http://localhost:8000](http://localhost:8000)

---

## 💡 Lessons Learned / Skills Demonstrated
- Linux recovery via Live ISO and chroot
- LVM volume management and on-the-fly resizing
- Filesystem cleanup and log auditing under disk pressure
- VirtualBox boot and device management
- Splunk troubleshooting and operational recovery

---

## 📝 Additional Notes
- Clipboard support (Guest Additions) still functional post-reboot
- Full-screen and drag-and-drop integration available via VBox additions
- Splunk should be monitored for volume growth; recommend separate `/opt` partition in future

---

## ✅ Final Outcome
**System fully recovered. SplunkServer running with 11GB free disk space and clean boot process.**

**flipxcrsp**  
March 2025
