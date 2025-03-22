# 🧱 Metasploitable 2 Setup

Metasploitable 2 is a vulnerable Linux VM intentionally designed for penetration testing practice. This file documents how I use it within my isolated lab network.

## 🔧 Configuration
- Imported into VirtualBox as an OVA file
- Network mode: Bridged Adapter (connected to `Lab_Net`)
- Default credentials:
  - `msfadmin:msfadmin`
  - `user:user`

## 🎯 Purpose in Lab
- Act as the primary vulnerable target for:
  - nmap scanning
  - Metasploit exploitation
  - Web app fuzzing (DVWA)
  - SSH brute force attacks
  - SQL injection practice

## 🧪 Services to Explore
- FTP
- SSH
- Telnet
- Apache (Web Server)
- PostgreSQL & MySQL
- Samba (SMB)

## 🔐 Security Notes
- Do **not** expose this VM to the internet.
- Keep it isolated to `Lab_Net` or host-only mode for safety.
