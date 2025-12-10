Fail2Ban – SSH Intrusion Detection & Prevention
1. Overview

Fail2Ban monitors authentication logs and bans IPs that show malicious behavior such as repeated failed login attempts.

This implementation protects SSH (port 22) on Ubuntu.

2. Installation
sudo apt update && sudo apt upgrade -y
sudo apt install fail2ban -y
sudo systemctl status fail2ban

3. Configure SSH Jail

Create jail.local:

sudo nano /etc/fail2ban/jail.local


Paste:

[DEFAULT]
bantime = 10m
findtime = 10m
maxretry = 3
backend = systemd

[sshd]
enabled = true
port = ssh
logpath = /var/log/auth.log


Restart Fail2Ban:

sudo systemctl restart fail2ban
sudo systemctl status fail2ban

4. Verify Jail
sudo fail2ban-client status sshd


Expected output:

Currently failed attempts

Total failed

Banned IP list

5. Testing (Brute Force Simulation)

Open terminal A:

sudo tail -f /var/log/auth.log


Open terminal B and intentionally fail SSH login:

ssh internship@localhost


After 3 failed attempts, Fail2Ban bans the attacker.

6. Result

SSH brute-force attempts detected

IP banned successfully

Logs and jail status verified
