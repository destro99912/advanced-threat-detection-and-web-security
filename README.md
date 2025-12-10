# Advanced Threat Detection & Web Security Enhancements

This repository contains my Week 4 internship work for **DevelopersHub Corporation**.  
The goal is to implement advanced security measures, detect threats in real-time, and secure web/API endpoints.

---

## 🎯 Goal

> Implement advanced security measures, detect threats in real-time, and secure API endpoints.

---

## ✅ Tasks Covered in This Repository

1. **Intrusion Detection & Monitoring**
   - Configure real-time monitoring using **Fail2Ban**.
   - Detect and block IPs after multiple failed SSH login attempts.
   - Review security logs and understand brute-force detection.

2. **API Security Hardening**
   - Apply **rate limiting** to protect APIs from brute-force & abuse.
   - Configure **CORS** safely to restrict unauthorized origins.
   - Secure APIs using **API keys** and an introduction to **OAuth-style** protection.

3. **Security Headers & Content Security Policy (CSP)**
   - Add important **security headers** to mitigate common web attacks.
   - Implement a **Content Security Policy (CSP)** to reduce the risk of script injection (XSS).

---

## 📂 Repository Structure

```text
.
├── README.md
├── fail2ban/
│   ├── INTRO.md
│   ├── CONFIGURATION.md
│   └── VERIFICATION.md
├── api-security/
│   ├── RATE_LIMITING.md
│   ├── CORS.md
│   └── API_KEYS_OAUTH.md
└── security-headers/
    ├── SECURITY_HEADERS_OVERVIEW.md
    └── CSP.md

Each folder contains detailed, step-by-step documentation of how the task was implemented, along with commands, explanations, and verification steps.

🛠 Environment

OS: Ubuntu (VM on VMware Workstation)

Tools: Fail2Ban, Node.js (Express), HTTP client (curl/Postman), browser dev tools

Access: SSH from host (PuTTY)

🔐 Learning Outcomes

By the end, I will have:

Set up real-time intrusion detection using Fail2Ban.

Hardened API endpoints with rate limiting, CORS, and API keys.

Implemented modern security headers and a basic CSP policy.

Understood how these layers work together to improve overall security posture.
