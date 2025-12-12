# Week 4: Advanced Threat Detection & Web Security Enhancements

## 📌 Internship Program
**Organization:** DevelopersHub Corporation  
**Project Type:** Security Operations / Intrusion Detection  
**Week:** 4  
**Focus:** Real-time monitoring, intrusion detection, and automated alerting

---

## 🎯 Goal

Implement advanced security measures to:
- Detect SSH brute-force attacks in real time
- Automatically ban malicious IPs
- Generate forensic-ready CSV reports
- Send structured email alerts for incident response

This project fulfills the **Intrusion Detection & Monitoring** task using **Fail2Ban**.

---

## 🛠️ Technologies Used

- Fail2Ban
- SSH (sshd)
- nftables (default firewall backend)
- Bash scripting
- Sendmail (SMTP)
- Linux systemd / journald
- CSV-based incident reporting

---

## 📋 Task Requirements (Internship Mapping)

| Internship Requirement                    | Status     |
|------------------------------------------|------------|
| Real-time intrusion detection             | ✅ Completed |
| Multiple failed login detection           | ✅ Completed |
| Automated alert system                    | ✅ Completed |
| Advanced enhancement beyond basics        | ✅ CSV Reporting |
| GitHub documentation                      | ✅ Completed |

---

## 📂 Project Structure

```text
.
├── /etc/fail2ban/
│   └── jail.local
│
├── /usr/local/bin/
│   ├── f2b_ssh_csv.sh
│   └── f2b_mail_csv.sh
│
├── /tmp/
│   └── fail2ban_<IP>_<timestamp>.csv
│
└── README.md
```
⚙️ Configuration Highlights
🔐 Fail2Ban Jail Configuration
Ini, TOML
```
[sshd]
enabled = true
backend = systemd
maxretry = 3
findtime = 10m
bantime = 15m

action = nftables
         sendmail-whois-lines
         sendmail-ssh-csv[sender="alertsinternship1@gmail.com", dest="alertsinternship1@gmail.com"]
```
📎 Custom CSV Alert Action

    Triggered only when an IP is banned

    Extracts SSH log entries related to the offending IP

    Generates a timestamped CSV report

    Attaches the CSV directly to the alert email

📧 Email Alert Workflow

    SSH login failures detected

    Fail2Ban threshold reached

    Malicious IP is banned

    CSV report generated automatically

    Email sent with CSV attachment

    Admin receives structured incident evidence

🧪 Testing & Validation

    SSH brute-force attempts simulated using PuTTY

    IP ban verified using:
    Bash

    sudo fail2ban-client status sshd

    Email delivery verified in Gmail inbox

    CSV attachment confirmed with accurate log data

    Default Fail2Ban protections remained intact

🛡️ Stability & Safety

    No core Fail2Ban functionality removed

    Custom CSV alert runs alongside default actions

    Restart-safe configuration

    No impact on SSH availability or system performance

📚 Learning Outcomes

    Advanced Fail2Ban customization

    Secure SMTP alerting

    Log parsing and CSV report generation

    Real-world intrusion detection implementation

    Defensive security operations experience

🧑‍💻 Author

Internship Project – Muhammad Rehan Week 

✅ Conclusion

This project demonstrates a production-grade intrusion detection system with automated alerting and forensic-ready CSV reporting, fully aligned with modern security operations practices and internship requirements.
