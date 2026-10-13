# Phase 3: File Integrity Monitoring (FIM)

## 1. Overview

This phase focuses on implementing File Integrity Monitoring (FIM) on a Windows endpoint using Wazuh.

The purpose is to monitor changes to selected files and directories and identify file creation, modification, and deletion activities.

## 2. Objectives

- Configure File Integrity Monitoring on the Windows endpoint.
- Monitor a dedicated testing directory.
- Generate file creation, modification, and deletion events.
- Verify FIM alerts through the Wazuh Dashboard.
- Develop practical skills in security event monitoring.

## 3. Lab Environment

| Component            | Technology         |
| -------------------- | ------------------ |
| SIEM Platform        | Wazuh 4.14.8       |
| Wazuh Manager        | Ubuntu 24.04.5 LTS |
| Monitored Endpoint   | Windows            |
| Virtualization       | VMware Workstation |
| Monitoring Directory | `C:\Wazuh-FIM-Lab` |

## 4. FIM Configuration

A dedicated directory was selected for File Integrity Monitoring.

The following configuration is added within the existing `<syscheck>` section of the Windows Wazuh Agent configuration file:

```xml
<directories realtime="yes" check_all="yes">C:\Wazuh-FIM-Lab</directories>
```

The configuration enables real-time monitoring of the specified directory.

## 5. Detection Experiments

Three experiments are planned to test the FIM functionality.

### Experiment 1: File Creation

```powershell
Set-Content "C:\Wazuh-FIM-Lab\test.txt" "Initial file content"
```

**Expected Result:** Wazuh detects a newly created file.

### Experiment 2: File Modification

```powershell
Add-Content "C:\Wazuh-FIM-Lab\test.txt" "Modified file content"
```

**Expected Result:** Wazuh detects changes to the monitored file.

### Experiment 3: File Deletion

```powershell
Remove-Item "C:\Wazuh-FIM-Lab\test.txt"
```

**Expected Result:** Wazuh detects the deletion of the monitored file.

## 6. Detection Results

| Experiment        | Expected Event | Actual Result |
| ----------------- | -------------- | ------------- |
| File Creation     | File added     | Pending       |
| File Modification | File modified  | Pending       |
| File Deletion     | File deleted   | Pending       |

## 7. Screenshots

Screenshots will be added after successful verification:

- FIM configuration
- File creation alert
- File modification alert
- File deletion alert
-[Evidence](../screenshots/after detection.png)

## 8. Learning Outcomes

This lab aims to strengthen practical understanding of:

- File Integrity Monitoring
- Endpoint security monitoring
- SIEM alert generation
- Security event investigation
- Windows endpoint configuration

## 9. Next Phase

**Phase 5: FIM Detection Analysis**

The next phase will focus on investigating the generated alerts and documenting the detection results.

## Project Status

**Phase 4: In Progress — Awaiting Detection Verification**
