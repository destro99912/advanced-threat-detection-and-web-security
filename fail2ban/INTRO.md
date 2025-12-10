# Fail2Ban – Introduction  
Week 4: Intrusion Detection & Monitoring

Fail2Ban is a host-based intrusion detection and prevention tool used to protect Linux servers from brute-force attacks.  
It works by **monitoring log files** (such as `/var/log/auth.log`) and automatically **blocking IPs** that show malicious behavior.

---

## 🔍 Why Fail2Ban Is Used in Threat Detection

Brute-force attacks attempt thousands of username/password combinations to gain unauthorized access.  
Fail2Ban automatically detects these attempts and:

- Identifies repeated failed login attempts  
- Bans the attacking IP for a specific time  
- Logs all activity for auditing  
- Reduces server load by stopping attackers early  

Fail2Ban acts as a **defensive layer**, preventing attackers from repeatedly abusing SSH or API endpoints.

---

## 🎯 What This Section Covers

This Week 4 component focuses on:

1. Installing Fail2Ban  
2. Creating custom jail rules for SSH  
3. Monitoring authentication logs  
4. Simulating brute-force attacks  
5. Observing how Fail2Ban detects and blocks malicious IPs  
6. Unbanning and managing blocked hosts  

---

## 🛡 Real-World Importance

Fail2Ban is widely used by:

- Cloud servers (AWS, Azure, DigitalOcean)
- DevOps engineers  
- Security engineers  
- Penetration testers  
- Linux administrators  

It provides **first-line intrusion detection** and helps secure systems exposed to the internet.

---

## 📄 Output You Will See Later In This Documentation

During this Week 4 task, you will see:

- Failed SSH attempts  
- IP bans  
- Fail2Ban logs  
- Verification using `fail2ban-client`

This file serves as the foundation for understanding the configuration steps in the next sections.
