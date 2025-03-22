# 💉 SQL Injection Attack - DVWA

This scenario demonstrates a SQL injection attack using OWASP DVWA (Damn Vulnerable Web Application). It's designed to test input validation, generate logs, and demonstrate how injection attacks work.

## 🎯 Target
- App: DVWA (running on Metasploitable or Ubuntu VM)
- URL: `http://192.168.x.x/dvwa/vulnerabilities/sqli/`
- Required: Login to DVWA and set security level to "Low"

## 🛠️ Tools Used
- Web browser (Firefox, Chromium)
- DVWA interface
- (Optional) Burp Suite for deeper analysis

## 🔍 Steps
1. Login to DVWA:
   - Username: `admin`
   - Password: `password`

2. Navigate to **SQL Injection** module:
   ```
   http://192.168.x.x/dvwa/vulnerabilities/sqli/
   ```

3. Test basic injection in the ID input:
   ```sql
   1' OR '1'='1
   ```

4. Submit and observe if all user records are shown.
   - Try additional injections like:
     ```sql
     1' OR 1=1 --
     1' UNION SELECT null, version() #
     ```

## 📝 Notes
- Use browser dev tools or Burp Suite to intercept and modify requests
- Monitor HTTP requests and responses to understand how injection works
- Capture traffic with Wireshark if desired

## 📊 Log & Detection Ideas
- Analyze Apache logs via Splunk for suspicious query strings
- Build detection rules for common SQLi patterns
- Practice input validation and WAF simulation

## 🧠 Learning Points
- Understand how SQLi works at the application and database layer
- Learn how to test and detect injection attempts in logs
- Gain familiarity with DVWA as a training tool
