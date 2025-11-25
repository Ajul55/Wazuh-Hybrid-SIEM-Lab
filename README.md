# Hybrid Cloud SIEM Lab: SSH Brute Force Detection 🛡️

## Project Overview
This project demonstrates the deployment of a **Hybrid Cloud Security Operations Center (SOC)** using **Wazuh**. The goal was to simulate a real-world cyber attack (SSH Brute Force) and detect it in real-time using a SIEM solution.

## 🏗️ Architecture
* **SIEM Manager:** Wazuh Cloud (SaaS)
* **Endpoint (Victim):** Linux Mint (Physical Machine)
* **Threat Actor:** Kali Linux (Virtual Machine)

## 🛠️ Tools Used
* **Wazuh:** For Log Analysis, File Integrity Monitoring, and Threat Detection.
* **Hydra:** For executing the brute force attack.
* **Linux (Debian/Ubuntu):** Operating system management and CLI.

## 🚀 The Process

### Phase 1: Environment Setup
1.  Deployed a Wazuh Cloud instance to serve as the Manager.
2.  Installed the Wazuh Agent on a Linux Mint host.
3.  Configured the Agent to communicate with the Cloud Manager via authenticated TCP.
4.  Ensured visibility between the Kali VM (Attacker) and Linux Mint (Victim) via Bridged Networking.

### Phase 2: The Attack (Red Team)
Used `Hydra` to simulate an unauthorized access attempt via SSH.
Command used:
```bash
hydra -l admin -P /usr/share/wordlists/rockyou.txt ssh://<VICTIM_IP> -t 4
