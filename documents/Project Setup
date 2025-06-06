# 🛡️ Active Directory HomeLab Setup Guide

*Author: Habeeb Haliru*  
*Date: May 27th, 2025*

---

## 📌 Project Overview

This project is a home lab simulation of a real-world Active Directory environment, using VirtualBox and various virtual machines to emulate a domain setup, Windows server, attacker machine, and Splunk logging server. This type of setup is ideal for learning threat detection, logging, and network security.

---

## 🧠 Important Notes

- Always **start with a diagram** of your environment. Interviewers may ask for this.
- Use [draw.io](https://draw.io) to create diagrams.

---

## 🔧 Lab Environment

- **Domain**: MyDFIR  
- **Network**: 192.168.10.0/24  
- **Splunk Server**: 192.168.10.10  
- **Active Directory**: 192.168.10.7  
- **Attacker (Kali)**: 192.168.10.250  

---

## 🖥️ Virtual Machines Setup

### ✅ Target Windows Machine

- Download **Windows 10 (22H2)**
- Machine name: `asura`

### ✅ Kali Linux Machine

- Download **Kali Linux**
- Requires **7-Zip** to extract
- Default credentials: `kali:kali`

### ✅ Windows Active Directory Server

- Download **Windows Server 2022 ISO**
- Add ISO to a new VM
- Use **Server Manager** to install Active Directory

---

## 🧩 Installing Splunk Server (Ubuntu)

1. Download **Ubuntu Server** from [ubuntu.com](https://ubuntu.com)
2. Username: `asurafeng`
3. Password: `Capricorn3012`
4. Run:  
   ```bash
   sudo apt-get update && sudo apt-get upgrade -y
   ```

---

## 🌐 Setting Up Static IP on Ubuntu (Splunk)

1. Run:
   ```bash
   ip a
   ```
   to get current IP.
2. Edit config:
   ```bash
   sudo nano /etc/netplan/50-cloud-init.yaml
   ```
3. Update with:
   ```yaml
   dhcp4: no
   addresses: [192.168.10.10/24]
   nameservers:
       addresses: [8.8.8.8]
   routes:
       - to: default
         via: 192.168.10.1
   ```
4. Save and apply:
   ```bash
   sudo netplan apply
   ```

---

## 📦 Installing Splunk (on Host Ubuntu)

1. Sign up & download `.deb` package from Splunk site
2. Install VirtualBox guest additions:
   ```bash
   sudo apt-get install virtualbox-guest-additions-iso
   sudo reboot
   ```
3. Create shared folder:
   ```bash
   mkdir share
   sudo mount -t vboxsf -o uid=1000,gid=1000 Active-Directory-HomeLab share/
   ```
4. Install Splunk:
   ```bash
   sudo dpkg -i splunk*.deb
   ```

---

## 📥 Installing Sysmon & Splunk Forwarder (Windows Target)

1. Set VM **Network to NAT Network**
2. Create your own NAT network
3. Download:
   - Splunk Universal Forwarder
   - Sysmon from Sysinternals
4. Configure **Sysmon** via `Olaf` config:
   ```powershell
   .\Sysmon64.exe -i sysmonconfig.xml
   ```
5. Create `inputs.conf` file in `local` folder with:
   ```
   [WinEventLog://Application]
   [WinEventLog://Security]
   [WinEventLog://System]
   [WinEventLog://Microsoft-Windows-Sysmon/Operational]
   ```
6. Restart Splunk Forwarder:
   - Open Services → `SplunkForwarder`
   - Log on as local system account
   - Restart service

---

## 🧠 Create Splunk Index & Receiver

1. Visit: `http://192.168.10.10:8000`
2. Go to:
   - `Settings` → `Indexes` → Create index: `endpoint`
   - `Settings` → `Forwarding and Receiving` → `Configure Receiving` → Add Port `9997`

---

## 🧠 Repeat Splunk Forwarder + Sysmon Setup on Windows Server

- Follow the exact same process as the target Windows machine

---

## ⚙️ Setup Active Directory & Promote Domain Controller

1. Set Static IP: `192.168.10.7`
2. In **Server Manager**:
   - Add Roles & Features → **AD Domain Services**
   - Promote to domain controller
   - Add new forest: `asura.local`
   - Set password
3. Database paths:
   - `ntds.dit`
   - `SYSVOL`, etc.
4. Restart → Now Domain Controller

---

## 👤 Create Users in Active Directory

1. Open `Active Directory Users and Computers`
2. Organize users via **Organizational Units**
3. Use `Builtin` groups cautiously — they are system-reserved

---

## 🔗 Join Windows 10 Target to Domain

1. Change DNS in `IPv4 Settings` to: `192.168.10.7`
2. Verify with:
   ```cmd
   ipconfig /all
   ```
3. Now join the domain: `asura.local`

---

## ✅ Summary

By following this guide, you've:

- Built a full domain environment
- Installed and configured Splunk for SIEM logging
- Set up endpoint monitoring with Sysmon
- Joined a Windows client to your custom AD domain

Great job building a foundational cybersecurity lab! 🧠🔥
