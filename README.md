# Active Directory Home Lab Project

This repository contains resources, guides, and configuration files to set up an Active Directory-based home lab environment. The project simulates real-world scenarios for both Blue Team (defensive security) and Red Team (offensive security) practices using tools like Splunk, Sysmon, Kali Linux, and Atomic Red Team.

---

## **1. Overview**

The project covers:
- Setting up Active Directory on a Windows Server and promoting it to a domain controller.
- Configuring Splunk for monitoring and telemetry.
- Installing and configuring Sysmon for detailed event logging.
- Simulating attacks with Kali Linux and Atomic Red Team.
- Troubleshooting common issues.

---

## **2. Folder Structure**

### **Configuration Files**
- **[Sysmon Configuration File](configurations/sysmon-config.xml)**: Sysmon rules for monitoring malicious behaviors.
- **[Splunk Inputs.conf](configurations/splunk-inputs.md)**: Configuration for event log ingestion.

### **Guides and Documentation**
- **[Project-Setup](documents/Project-Setup.md)**: Step-by-step instructions for setting up the home lab environment, Splunk on an Ubuntu Server, installing and configuring Sysmon as well as Splunk Universal Forwarder, and configuring Active Directory and joining client machines to the domain.
- **[Kali Linux Attack using Atomic Red Team](documents/Kali%20Linux%20Attack%20using%20Atomic%20Red%20Team.md)**: Steps for simulating attacks using Atomic Red Team and analyzing telemetry.

### **Network Diagram**
**![Active Directory Network Diagram](https://github.com/asurafeng3012/Active-Directory-Home-Lab/blob/main/documents/Active%20Directory%20HomeLab.jpg)**

---

## **3. Key Features**
- **Blue Team Focus**:
  - Configure Splunk and Sysmon for monitoring.
  - Analyze telemetry from simulated attacks.
- **Red Team Focus**:
  - Simulate brute force attacks and persistence techniques using Kali Linux and Atomic Red Team.
- **Hands-On Learning**:
  - Experiment in a safe, controlled lab environment.
  - Practice troubleshooting real-world issues.

---

## **4. Setup Instructions**
1. Follow the **[Project-Setup](documents/Project-Setup.md)** to install virtual machines and configure the network.
2. Install and configure Splunk by referencing the **[Project-Setup](documents/Project-Setup.md)**.
3. Configure Sysmon and Splunk Universal Forwarder using the **[Project-Setup](documents/Project-Setup.md)**.
4. Set up and use Kali Linux for attack simulations as described in the **[Kali Linux Attack using Atomic Red Team](documents/Kali%20Linux%20Attack%20using%20Atomic%20Red%20Team.md)**.
5. Configure Active Directory and join client machines using the **[Project-Setup](documents/Project-Setup.md)**.

---

## **5. Inspiration**
This project was inspired by the following YouTube tutorial series:
- **[Active Directory Project Tutorial](https://www.youtube.com/watch?v=5OessbOgyEo&t=55s)**  
  Special thanks to the **MyDFIR** for providing detailed guidance on setting up an Active Directory lab environment.
  
---
