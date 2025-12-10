Week 4 – Intrusion Detection & Monitoring

This section documents the complete configuration process of Fail2Ban, including installation, SSH setup, custom jail rules, and service verification.

🔧 Step 1 — Update the Server

Keeping the system updated ensures all security patches are applied.

Commands
sudo apt update && sudo apt upgrade -y

🔧 Step 2 — Install Fail2Ban

Fail2Ban is available in Ubuntu’s official repositories.

Commands
sudo apt install fail2ban -y
sudo systemctl status fail2ban

Expected output: active (running).

🔧 Step 3 — Install & Configure SSH

Fail2Ban monitors SSH logs to detect brute-force attacks.

Commands
sudo apt install openssh-server -y
sudo systemctl enable ssh
sudo systemctl start ssh
sudo systemctl status ssh

SSH must be running before Fail2Ban can protect it.

🔧 Step 4 — Configure Fail2Ban Jail

Commands
sudo nano /etc/fail2ban/jail.local

Paste the following configuration:

[sshd]
enabled   = true
port      = ssh
filter    = sshd
logpath   = /var/log/auth.log
findtime  = 10m
maxretry  = 3
bantime   = 15m
backend   = systemd

🔧 Step 5 — Restart Fail2Ban

Commands
sudo systemctl restart fail2ban
sudo systemctl status fail2ban

🔧 Step 6 — Verify SSH Jail Status

Commands
sudo fail2ban-client status sshd

You should see:

Currently failed attempts

Total failed

Currently banned

List of banned IPs

🚀 Fail2Ban is now fully configured and protecting your server.
