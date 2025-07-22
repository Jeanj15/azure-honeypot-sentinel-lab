# azure-honeypot-sentinel-lab
# 🛡️ Azure Honeypot + Microsoft Sentinel SIEM Lab

This project simulates a real-world cyber threat detection environment using **Microsoft Azure**, a **Windows 10 honeypot**, and **Microsoft Sentinel SIEM** to collect, analyze, and visualize attack data.

## 📌 Overview

Built a honeypot in Azure, simulated brute-force attacks, centralized event logs, enriched with geolocation data, and visualized threats in a live attack map using Microsoft Sentinel Workbooks.

---

## 🧰 Tools & Technologies

- Microsoft Azure (Virtual Machines, Network Security Groups, Log Analytics Workspace)
- Microsoft Sentinel (SIEM)
- Windows Event Viewer
- Kusto Query Language (KQL)
- GeoIP Threat Intelligence (via Watchlist)
- RDP Honeypot Simulation
- Cyber Range Lab Environment (optional)

---

## ⚙️ Lab Setup

### Part 1: Azure Subscription Setup
- Created free Azure account: [azure.microsoft.com](https://azure.microsoft.com/en-us/pricing/purchase-options/azure-account)
- Accessed portal: [portal.azure.com](https://portal.azure.com)

### Part 2: Deploy Honeypot VM
- Deployed Windows 10 VM
- Enabled all inbound traffic via Network Security Group (NSG)
- Disabled Windows Firewall for traffic visibility (`wf.msc`)

### Part 3: Simulated Attack
- Failed 3 login attempts as user “employee”
- Opened Event Viewer ➝ Security Logs ➝ Verified Event ID 4625 (Failed Logon)

---

## 🔍 Log Analysis & SIEM Integration

### Part 4: Forwarding Logs to Sentinel
- Created Log Analytics Workspace (LAW)
- Created Sentinel instance and linked it to LAW
- Connected “Windows Security Events via AMA” data connector
- Queried failed login events using KQL:

```kql
SecurityEvent
| where EventID == 4625
