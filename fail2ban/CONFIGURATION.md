# Fail2Ban Configuration  
Week 4 – Intrusion Detection & Monitoring

This section documents the complete configuration process of Fail2Ban, including installation, SSH setup, custom jail rules, and service verification.

---

## 🔧 Step 1 — Update the Server

Keeping the system updated ensures all security patches are applied.

```bash
sudo apt update && sudo apt upgrade -y

🛠 Step 2 — Install Fail2Ban
sudo apt install fail2ban -y
sudo systemctl status fail2ban


Expected output: active (running).

🛠 Step 3 — Install & Configure SSH

Fail2Ban monitors SSH logs to detect brute-force attacks. Ensure SSH is installed:

sudo apt install openssh-server -y
sudo systemctl enable ssh
sudo systemctl start ssh
sudo systemctl status ssh


SSH must be active before Fail2Ban can protect it.

🛠 Step 4 — Configure Fail2Ban Jail

Create the custom jail file:

sudo nano /etc/fail2ban/jail.local


Paste the following:

[sshd]
enabled   = true
port      = ssh
filter    = sshd
logpath   = /var/log/auth.log
findtime  = 10m
maxretry  = 3
bantime   = 15m
backend   = systemd

🔍 Parameter Explanation
Setting	Description
enabled	Turns on SSH protection
maxretry = 3	Only 3 failed attempts allowed
bantime = 15m	IP is blocked for 15 minutes
findtime = 10m	Attempts counted within a 10-minute window
logpath	Fail2Ban monitors /var/log/auth.log
backend = systemd	Uses modern log handling
🛠 Step 5 — Restart Fail2Ban
sudo systemctl restart fail2ban
sudo systemctl status fail2ban


This reloads your jail configuration.

🛠 Step 6 — Verify SSH Jail is Active
sudo fail2ban-client status sshd


Expected fields:

Currently failed

Total failed

Currently banned

Banned IP list

This confirms Fail2Ban is protecting SSH.

At this point, Fail2Ban is fully configured and ready for brute-force detection.
