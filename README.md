# powershell-sus-activity-lab
## Overview
This lab simulates suspicious PowerShell activity on a Windows 11 endpoint and demonstrates how it is logged in Event Viewer and detected by Wazuh SIEM.

It’s designed as part of a broader cybersecurity home lab focused on learning how to detect malicious behavior in enterprise environments.

---

## Lab Environment

- **Endpoint**: Windows 11 (Test Machine)
- **SIEM**: Wazuh Server
- **Logging Sources**: Windows Event Viewer, Wazuh Alerts

---

## Simulation 1: Encoded PowerShell Command

### Command:
```powershell
powershell -EncodedCommand aABpAA==
