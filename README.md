# SOC-Home-Lab Attack-Chain-Detection-with-Wazuh-SIEM-and-Sysmon


# 📑  Overview 

 My Main SOC Home Lab features an attack chain detection using Sysmon telemetry and Wazuh. The objective was to simulate an adversary's full attack, to correlate and detect fileless malware activity, validate the Wazuh alerts with Sysmon for forensic evidence and reconstruct the attack-chain by using MITRE ATT&CK mapping. 

 # 📍 Project Objectives

 - Deploy a Wazuh SIEM environment
 - Configure Sysmon telemetry
 - Simulate post-compromise attack behaviour
 - Map detections to MITRE ATT&CK
 - Correlate SIEM alerts with endpoint telemetry (Sysmon)

# 🛠 SOC Lab Architecture

<img width="3456" height="2304" alt="SOC Lab Architecture" src="https://github.com/user-attachments/assets/8a294c56-f309-4cf6-b096-49889f667bb7" />

# 💻 Technologies Used

| Technology                 | Purpose               |
| -------------------------- | ---------------------------- |
| Ubuntu                     | Wazuh Server                |
| Wazuh                      | SIEM                    |
| Sysmon                     | Endpoint Telemetry          |
| Windows 10                 | Target Endpoint                  |
| PowerShell                 | Attack Simulation |
| MITRE ATT&CK               | Technique Mapping  |


# 🎥  Demonstration Video

A full walkthrough of the attack simulation, Wazuh detections, Sysmon forensic and MITRE ATT&CK mapping is available in the video below.

<a href=https://youtu.be/HJdtREMMGxU>Watch Demonstration Video.

# ⚔️ Attack Scenario 

###  Assumption 
The atacker has already gained access to the Windows Endpoint. This project focuses on post-compromise detection using Wazuh and Sysmonn.

MITRE ATT&CK T1059.001 - PowerShell

### Execution
The adversary spawns Command Prompt in PowerShell to execute additional native Windows commands : PowerShell --> cmd.exe

MITRE ATT&CK T1059.003 – Windows Command Shell

### Discovery
The attacker perfroms reconnaissance to gather information about the compromised environment by using :

- whoami - identifies the current user
- netuser - enumerates local  account(s)
- ipconfig - retrieves network configuration
- systeminfo - gathers operating system information

### Defense Evasion
The adversary performs defense evasion techniques such as : 

- launching SecEdit.exe : a legitimate Windows utility, commonly used as a Living off the Land BIN (LOLBIN)
- modifying Registry using 'reg add'
  
MITRE ATT&CK T1112 - Modify Registry

### Persistence
The adversary implements persistence by creating a registry key that automatically starts up after user logon.

MITRE ATT&CK T1547.001 - Registry Run Keys

# ❗️ Detection

### PowerShell execution detected
<img width="1208" height="519" alt="image" src="https://github.com/user-attachments/assets/a5b08773-085d-4855-b069-a77af36c5f03" />

### Binary launched in a suspicious location detected 
<img width="1170" height="531" alt="image" src="https://github.com/user-attachments/assets/1a69c722-61bd-4139-ab5e-680cd5bf13f9" />

### Discovery Execution detected
<img width="1221" height="69" alt="image" src="https://github.com/user-attachments/assets/6ac9156c-a2f1-4c49-9841-3cfb4e274df3" />


### Registry key modification detected 
<img width="1256" height="104" alt="image" src="https://github.com/user-attachments/assets/8240aa2d-a3e6-4272-98ad-443a171959b9" />

# 🔍 Investigation

### Parent-Child Relationship (PowerShell - Command Prompt)
<img width="1152" height="779" alt="CMD" src="https://github.com/user-attachments/assets/8eec2b74-810a-4065-b6ec-840ee4b7092a" />

### PowerShell suspicious encoded command line
<img width="1686" height="783" alt="whomai" src="https://github.com/user-attachments/assets/5010d046-dffa-493d-b751-76525d864767" />

### Timeline validation between Wazuh & Sysmon
<img width="1491" height="383" alt="secedit" src="https://github.com/user-attachments/assets/1d51d1ad-3d25-4701-89ed-e35d846ef0d1" />

# ‼️ Alert Correlation

| Wazuh Alert           | Sysmon Evidence  |
| --------------------- | ---------------- |
| PowerShell execution  | Event ID 1       |
| Discovery activity    | Process Creation |
| Registry modification | Registry Event   |
| Persistence           | Registry Run Key |


# 📚 Lessons Learned 
During this project I gained hands-on experience with a SIEM environment, troubleshooting agent communication, investigating a full attack-chain through Sysmon and Wazuh. One of the most valuable aspects of this project was troubleshooting real-world deployment issues, including agent communication, service dependecies, OpenSearch indexing, Filebeat configuration, Linux permissions, port conflicts, memory constrains and log ingestion. Solving these problems significantly improved my understaing of Linux system administration and enterprise SIEM deployments.

# 📈 Future Improvements

- Implement custom Wazuh Detection Rules
- Integrate Sigma rules
- Expand to multi-host environments
- Include automated response using Wazuh Active Response

# 📎 Conclusion
This project demonstrates how endpoint telemetry and SIEM can be combined to correlate, detect, investigate and reconstruct incidents. By having both, security analysts gain both behavioral detection and visibility into adversary activity.






















