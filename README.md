# 🛡️ Wazuh SIEM Homelab

**Security Information and Event Management (SIEM) | Endpoint Monitoring | File Integrity Monitoring (FIM)**

A hands-on cybersecurity homelab project focused on deploying **Wazuh SIEM**, monitoring a Windows endpoint, and detecting file integrity changes in a controlled virtualized environment.

This project demonstrates practical experience in SIEM deployment, Windows endpoint monitoring, Linux administration, log collection, and basic security event analysis.

---

## 📌 Project Overview

The purpose of this project is to build a functional Security Information and Event Management (SIEM) environment using Wazuh.

The homelab consists of an Ubuntu Linux virtual machine running the Wazuh SIEM platform and a Windows 11 host running the Wazuh Agent.

The Windows endpoint communicates with the Wazuh Manager, allowing endpoint security events and file integrity changes to be collected and monitored through the Wazuh Dashboard.

### Project Objectives

- Set up an Ubuntu virtual machine using VMware Workstation.
- Deploy and configure Wazuh SIEM.
- Install and configure the Wazuh Agent on Windows 11.
- Establish communication between the Windows Agent and Wazuh Manager.
- Implement File Integrity Monitoring (FIM).
- Detect file creation, modification, and deletion activities.
- Document the implementation process and detection results.

---

## 🏗️ Lab Architecture

```text
             WINDOWS 11 HOST
       +--------------------------+
       |                          |
       |       Wazuh Agent        |
       |                          |
       |  File Integrity          |
       |  Monitoring (FIM)        |
       |                          |
       +------------+-------------+
                    |
                    | TCP 1514 / 1515
                    |
       +------------v-------------+
       |                          |
       |     VMware Workstation   |
       |                          |
       |    Ubuntu 24.04.5 LTS    |
       |                          |
       |      Wazuh Manager       |
       |      Wazuh Indexer       |
       |      Filebeat            |
       |      Wazuh Dashboard     |
       |                          |
       +--------------------------+
```

### Architecture Description

1. **Windows 11 Host:** Acts as the monitored endpoint.
2. **Wazuh Agent:** Collects endpoint security information and monitors selected files and directories.
3. **Ubuntu Virtual Machine:** Hosts the Wazuh SIEM infrastructure.
4. **Wazuh Manager:** Receives and analyzes endpoint security events.
5. **Wazuh Dashboard:** Provides a centralized interface for reviewing endpoint status and security alerts.

---

## 🛠️ Technologies & Tools

| Technology | Purpose |
|---|---|
| Wazuh SIEM 4.14.8 | Security monitoring and event analysis |
| Ubuntu 24.04.5 LTS | Wazuh server operating system |
| Windows 11 | Monitored endpoint |
| VMware Workstation | Virtualization platform |
| Wazuh Agent | Endpoint monitoring |
| Windows PowerShell | Agent installation and testing |
| File Integrity Monitoring | Detection of file changes |
| GitHub | Project documentation |

---

## 🚀 Project Implementation

### Phase 1 — VMware & Ubuntu Setup

Configured an Ubuntu virtual machine using VMware Workstation to host the Wazuh SIEM environment.

**Activities:**

- Installed Ubuntu 24.04.5 LTS.
- Configured virtual machine resources.
- Verified network connectivity.
- Installed Wazuh SIEM components.
- Prepared the environment for endpoint monitoring.

**Documentation:** [01 — VMware Setup](docs/01-vmware-setup.md)

### Phase 2 — Windows Wazuh Agent Deployment

Installed and configured the Wazuh Agent on the Windows 11 host.

**Activities:**

- Verified network connectivity between Windows and Ubuntu.
- Tested TCP ports 1514 and 1515.
- Installed the Windows Wazuh Agent using PowerShell.
- Configured the Wazuh Manager connection.
- Verified the Wazuh Agent service.
- Confirmed successful agent registration through the Wazuh Dashboard.

**Agent Information:**

| Field | Result |
|---|---|
| Agent Name | Windows-Host |
| Agent ID | 001 |
| Operating System | Windows 11 |
| Wazuh Version | 4.14.8 |
| Connection Status | Active |

**Documentation:** [02 — Windows Agent Deployment](docs/02-windows-agent.md)

### Phase 3 — File Integrity Monitoring (FIM)

Implemented File Integrity Monitoring to detect changes in a dedicated Windows testing directory.

**Monitored Directory:**

`C:\Wazuh-FIM-Lab`

**FIM Configuration:**

```xml
<directories realtime="yes" check_all="yes">C:\Wazuh-FIM-Lab</directories>
```

The monitoring configuration enables Wazuh to track file system changes within the selected directory.

**Detection Experiments:**

| Experiment | Activity | Result |
|---|---|---|
| Test 1 | File Creation | Detected |
| Test 2 | File Modification | Detected |
| Test 3 | File Deletion | Detected |

The Wazuh File Integrity Monitoring dashboard displayed three events categorized as added, modified, and deleted.

These experiments were performed in a controlled environment to validate the FIM detection capability.

**Documentation:** [03 — File Integrity Monitoring](docs/03-file-integrity-monitoring.md)

---

## 📊 Detection Results

### File Integrity Monitoring Dashboard

The following screenshot shows the File Integrity Monitoring results collected from the Windows endpoint.

The dashboard displays three categories of file integrity events:

- **Added:** A new file was created.
- **Modified:** An existing file was changed.
- **Deleted:** A monitored file was removed.

![Wazuh FIM Detection Dashboard](screenshots/after-detection.png)

The results demonstrate that Wazuh successfully recorded file system changes during the controlled monitoring experiment.

---

## 📁 Repository Structure

```text
Wazuh-SIEM-Homelab/
│
├── README.md
│
├── docs/
│   ├── 01-vmware-setup.md
│   ├── 02-windows-agent.md
│   └── 03-file-integrity-monitoring.md
│
└── screenshots/
    └── after-detection.png
```

The `docs` directory contains step-by-step technical documentation, while the `screenshots` directory stores supporting evidence from the homelab.

---

## 🧠 Skills Demonstrated

### Security Operations

- SIEM Deployment and Configuration
- Endpoint Security Monitoring
- File Integrity Monitoring
- Security Event Collection
- Basic Security Alert Analysis

### System Administration

- Ubuntu Linux Administration
- Windows PowerShell
- VMware Virtualization
- Windows Service Management
- Network Connectivity Troubleshooting

### Documentation

- Technical Documentation
- Security Testing
- Evidence Collection
- GitHub Repository Management

---

## 📈 Future Improvements

The following enhancements are planned for future development:

- [x] Ubuntu VMware Setup
- [x] Wazuh SIEM Deployment
- [x] Windows Wazuh Agent Installation
- [x] File Integrity Monitoring
- [ ] Windows Failed Login Detection (Event ID 4625)
- [ ] Security Alert Investigation
- [ ] Custom Wazuh Detection Rules
- [ ] SOC Incident Investigation Report

---

## 🎯 Project Outcome

Successfully deployed a Wazuh SIEM homelab integrating an Ubuntu-based Wazuh server with a Windows 11 endpoint.

The Windows Agent was registered and connected to the Wazuh Manager, enabling centralized endpoint monitoring.

File Integrity Monitoring was configured and tested through controlled file creation, modification, and deletion experiments.

This project provides practical exposure to **SIEM deployment, endpoint monitoring, Linux administration, and defensive cybersecurity fundamentals**.

---

## 📚 References

- [Wazuh Official Website](https://wazuh.com/)
- [Wazuh Documentation](https://documentation.wazuh.com/current/)
- [MITRE ATT&CK Framework](https://attack.mitre.org/)

---

**Project Type:** Cybersecurity Homelab  
**Focus Area:** Blue Team / Security Operations Center (SOC)  
**Platform:** Wazuh SIEM  
**Environment:** Windows 11, Ubuntu Linux, VMware Workstation
