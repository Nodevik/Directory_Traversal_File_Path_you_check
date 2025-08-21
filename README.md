# 🕵️ Linux Directory Traversal Pentesting Cheat Sheet

When you discover **Directory Traversal (Path Traversal)** on a Linux target, here are the most valuable files and directories to check for sensitive information, credentials, and potential escalation.

---

## 🔑 System & User Information
- `/etc/passwd` → list of system users
- `/etc/shadow` → password hashes
- `/etc/group` → groups users belong to
- `/etc/sudoers` → sudo privileges
- `/etc/hostname` → system hostname
- `/etc/issue` → distro banner
- `/etc/os-release` → distribution info

---

## 📦 Configuration Files
- `/etc/ssh/sshd_config` → SSH settings
- `/root/.ssh/id_rsa` & `/home/<user>/.ssh/id_rsa` → private SSH keys
- `/root/.ssh/authorized_keys`, `/root/.ssh/known_hosts`
- `/etc/hosts` → local host mappings
- `/etc/resolv.conf` → DNS config
- `/etc/network/interfaces` or `/etc/netplan/*` → network setup

---

## 🌐 Web Application Files
- `/var/www/html/config.php`
- `/var/www/html/db.php`
- `/var/www/html/.env` → environment variables (Laravel/Django/NodeJS)
- `/var/www/html/wp-config.php` → WordPress DB creds
- `/var/www/html/*/settings.py` → Django settings
- `/var/www/html/*/config/*` or `/var/www/html/*/include/*`

---

## 🛢️ Database Credentials
- `/etc/mysql/my.cnf`
- `/root/.my.cnf`
- `/home/<user>/.my.cnf`
- Application configs (`config.php`, `.env`, etc.)

---

## 🔐 Security & Auth
- `/var/log/auth.log` → authentication logs
- `/var/log/secure` → (CentOS/RHEL)
- `/etc/krb5.conf` → Kerberos config
- `/etc/pam.d/*` → PAM configs

---

## 📜 Logs
- `/var/log/apache2/access.log`
- `/var/log/apache2/error.log`
- `/var/log/httpd/access_log`
- `/var/log/httpd/error_log`
- `/var/log/nginx/access.log`
- `/var/log/nginx/error.log`
- `/var/log/mysql/error.log`
- `/var/log/messages`
- `/var/log/syslog`
- `/var/log/dmesg`

---

## 👤 User Files
- `/home/<user>/.bash_history` → command history
- `/home/<user>/.profile`, `.bashrc`, `.zshrc`
- `/home/<user>/.git/config` → Git repo config
- `/home/<user>/.docker/config.json` → Docker tokens

---

## 🐳 Container & Cloud
- `/root/.docker/config.json`
- `/var/run/docker.sock` → Docker socket (RCE if writable)
- `/etc/kubernetes/admin.conf` → kubeconfig
- `/var/lib/cloud/instances/*/user-data.txt` → cloud-init data
- AWS: `/home/<user>/.aws/credentials`
- GCP: `/home/<user>/.config/gcloud/credentials.db`
- Azure: `/home/<user>/.azure/*`

---

## ⚙️ Cron Jobs
- `/etc/crontab`
- `/etc/cron.daily/`
- `/etc/cron.weekly/`
- `/var/spool/cron/crontabs/*`

---

## 🎯 Other High-Value Files
- `/proc/self/environ` → environment variables
- `/proc/self/cmdline` → running process commands
- `/proc/net/tcp` → open connections
- `/proc/mounts` → mounted filesystems
- `/etc/fstab` → storage config

---

## 🚀 Pentest Tips
1. Start with `/etc/passwd` to confirm traversal works.
2. Move to **web app configs** like `.env`, `wp-config.php`, `config.php` for DB creds.
3. Check logs for internal paths, tokens, and errors.
4. Grab SSH keys, API keys, or DB passwords for **lateral movement or RCE**.

---
