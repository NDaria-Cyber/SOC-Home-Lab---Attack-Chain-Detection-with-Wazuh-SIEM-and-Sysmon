# SOC-Home-Lab Attack-Chain-Detection-with-Wazuh-SIEM-and-Sysmon


# Overview 

 My Main SOC Home Lab features an attack chain detection using Sysmon telemetry and Wazuh. The objective was to simulate an adversary's full attack, to correlate and detect fileless malware activity, validate the Wazuh alerts with Sysmon for forensic evidence and reconstruct the attack-chain by using MITRE ATT&CK mapping. 

 # Project Objectives

 - Deploy a Wazuh SIEM environment
 - Configure Sysmon telemetry
 - Simulate post-compromise attack behaviour
 - Map detections to MITRE ATT&CK
 - Correlate SIEM alerts with endpoint telemetry (Sysmon)

# SOC Lab Architecture

<img width="3456" height="2304" alt="SOC Lab Architecture" src="https://github.com/user-attachments/assets/8a294c56-f309-4cf6-b096-49889f667bb7" />

# Technologies Used

| Technology                 | Purpose               |
| -------------------------- | ---------------------------- |
| Ubuntu                     | Wazuh Server                |
| Wazuh                      | SIEM                    |
| Sysmon                     | Endpoint Telemetry          |
| Windows 10                 | Target Endpoint                  |
| PowerShell                 | Attack Simulation |
| MITRE ATT&CK               | Technique Mapping  |


# Demonstration Video

A full walkthrough of the attack simulation, Wazuh detections, Sysmon forensic and MITRE ATT&CK mapping is available in the video below.

<a href=https://youtu.be/HJdtREMMGxU>Watch Demonstration Video.

# Attack Scenario 












