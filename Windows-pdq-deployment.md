# PDQ Bulk Deployment Exception: End-to-End Troubleshooting & Resolution

## Problem Background

During a batch deployment using PDQ Deploy, only one target machine (Workstation 11) remained stuck in the "Queued" state, while all other devices completed successfully.

---

## Detailed Troubleshooting and Resolution Process

### 1. Physical Network and IP Configuration Check

- **Inspected the physical network cabling** on the affected workstation.
- Noticed that the machine had two **network interface cards (NICs)** (also: Ethernet ports/LAN ports).
- Discovered the Ethernet cable was plugged into a different wall network jack compared to other workstations.  
- **Key point:** The cable was connected to the incorrect NIC/port, resulting in the wrong IP address and VLAN (Virtual LAN) assignment.

### 2. IP Address and Hostname Verification

- Logged into the workstation and used the `ipconfig` and `hostname` commands to check its current IP address and hostname.
- Compared with Active Directory (AD) and PDQ registration records.  
- Found that the machine was assigned an incorrect address (`X.X.X.193`) while, as workstation 11, it should have been `X.X.X.111`.
- After reconnecting the cable to the correct port, the machine received the proper IP address.

### 3. DNS and AD Synchronization Check

- On the PDQ Deploy server, ran `ping` and `nslookup` to test the target computer's hostname.
- Confirmed that DNS now resolved the hostname to the correct, updated IP.

### 4. Task Manager: Process Status Check

- Opened **Task Manager** on the workstation.
- Looked for `PDQDeployRunner.exe` or related processes to see if deployment jobs were executing locally.
- No such process was running, confirming the PDQ job had not been received by the workstation.

### 5. Service and Registry Check

- Used `services.msc` to confirm that core remote management services—**Remote Procedure Call (RPC)** and **Windows Management Instrumentation (WMI)**—were running and set to **Automatic**.
- Checked the **Remote Registry** service:  
  - *Note:* While not always required, starting this service can help PDQ perform inventory and registry-related tasks.
- Verified the **ADMIN$ share**:
  - In **Command Prompt**, ran:
    ```cmd
    net share
    ```
    - Checked for `ADMIN$` (points to C:\Windows).
    - *If missing, re-enable with (admin rights needed):*
      ```cmd
      net share ADMIN$=C:\Windows
      ```
    - The `ADMIN$` share is used by remote deployment tools for copying files to the target system.
- Confirmed deployment credentials had local administrator privileges.

### 6. Reboot and Configuration Synchronization

- After fixing the physical connection, IP address, and hostname, **restarted the workstation** to ensure all changes took effect and old network data was cleared.

### 7. PDQ Console Refresh and Redeployment

- Refreshed the machine list in the PDQ Deploy console.
- Confirmed that the problematic workstation now showed as **Online**.
- Redeployed the software package—this time, it completed successfully.

---

## Lessons Learned & Reflection

- **Multi-layer troubleshooting is essential**:  
  Covered the physical (network cables, switch ports, NIC/VLAN), system (services, processes), management (hostname, IP, registry, admin shares), and platform (PDQ config, credentials) layers.
- **Root cause**: The problem was resolved by correcting the network interface connection, which restored IP and VLAN assignment. However, thoroughly checking system services, registry settings, and administrative shares ensured there were no compounded issues.
- **Single-point failures in batch jobs**: Always check both the physical/configuration basics and higher-level system or platform causes.

---

## Conclusion 

This practicum troubleshooting exercise demonstrates a systematic, multi-level approach:  
From physical network cable inspection and endpoint addressing, to system service, registry, and admin share validation, then up to console/platform diagnostics.  
The core issue was traced to a simple network interface misconnection, which resulted in mismatched IP and device identity.  
Once the connection was corrected and the system rebooted, PDQ bulk deployment returned to normal.  
**Key takeaway:** Consistent physical and logical identity is fundamental for automation at scale.  
Comprehensive troubleshooting should always address the entire stack, from hardware to platform.


