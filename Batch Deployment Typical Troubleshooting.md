# MITT-PRACTICUM

## Batch Deployment Typical Troubleshooting

### 1. Background

In this VMware Workstation and system batch deployment project, I was responsible for deploying applications to multiple physical workstations. During the process, I encountered several common failures that are highly representative of real-world troubleshooting and remediation. This document summarizes the main issue types, troubleshooting methods, operational commands, security awareness, and personal reflections, serving as a reference for future automation and IT operations improvements.

---

## 2. Major Issues and Troubleshooting Procedures

### 1. The Network Path Was Not Found

#### Cause Analysis

- Physical network connection errors (e.g., network cable plugged into the wrong NIC, mismatched workstation numbering and physical location)
- Target device not joined to the domain or file/printer sharing not enabled
- DNS resolution errors or hostname typos
- Physical cable loose or not properly connected

#### Troubleshooting & Steps

1. **Check if the target device is online**

    ```cmd
    ping <target-hostname-or-IP>
    ```
    - If unreachable, check power/network cable/switch port first.

2. **Check DNS resolution**

    ```cmd
    nslookup <target-hostname>
    ```
    - If failed, verify DNS configuration and hostname spelling.

3. **Test shared path accessibility**

    ```cmd
    net use \\<target-hostname>\C$
    ```
    - If authentication or access fails, check sharing status and permissions.

4. **Enable file and printer sharing (manual GUI steps)**

    - Control Panel → Network and Sharing Center → Change advanced sharing settings
    - Only enable the following in **Domain network**:
      - Network discovery
      - File and printer sharing
    - Keep all options in Public network **disabled** to avoid unnecessary exposure.

5. **Check firewall settings**

    ```cmd
    netsh advfirewall firewall show rule name=all | findstr "File and Printer Sharing"
    ```
    - If the rule is not enabled, temporarily allow or disable the firewall for testing.

#### Practical Notes

- During this internship, I only had local manual GUI privileges, so all configurations were performed one by one. After deployment, I promptly disabled unnecessary sharing for security.

---

### 2. The Target Account Name Is Incorrect

#### Cause Analysis

- Trust relationship between target machine and AD domain controller lost
- System reinstalled without rejoining the domain
- VM restore or physical machine replacement causing computer account issues

#### Troubleshooting & Fix

1. **Check domain status**

    ```cmd
    systeminfo | findstr /i "Domain"
    ```
    - Confirm whether the device is a domain member.

2. **“Leave and rejoin domain” if necessary**

    - Use “This PC → Properties → Change settings” to leave and rejoin the domain to restore trust.

3. **Verify hostname, IP, and DNS consistency**

    - Ensure that AD, DNS, and the actual device state are synchronized.

#### Practical Notes

- For a workstation with a trust failure, I scheduled a **leave and rejoin domain** operation to re-establish deployment access.

---

### 3. Installation Process Conflict (Error 1618)

#### Cause Analysis

- Windows Installer (MSI engine) occupied by another installation process
- Concurrent deployment tasks causing msiexec.exe process to hang
- Antivirus, patching, or system repair processes occupying the installer

#### Troubleshooting & Fix

1. **Check processes in Task Manager**

    - Look for msiexec.exe or any long-running installation tasks.

2. **Check installation logs**

    ```powershell
    Get-WinEvent -LogName Application | findstr MSIInstaller
    ```

3. **Handling**

    - If the process is stuck for a long time, **restart the target machine** to release the MSI engine.
    - Wait for current installation tasks to finish before re-deploying.

#### Practical Notes

- On the affected device, with multiple issues present, I restarted the machine and continued deployment after the reboot.

---

### 4. Special Application Errors (e.g., Packet Tracer command returns 1)

- This type of error mainly affects Packet Tracer, which can be downloaded and installed manually. It was not a troubleshooting priority in this project.

---

## 3. Security Awareness and Operations Mindset

- **Principle of least exposure:** Only enable sharing and network discovery in Domain networks; keep Public network settings closed to reduce attack surface.
- Promptly roll back or clean up permissions after configuration to avoid leftover vulnerabilities.
- Although I could only operate manually, I have accumulated ideas for automation scripts and Group Policy (GPO) bulk management.
- In future scenarios with more privileges, I will implement standardized batch processes via PowerShell or remote GPO to improve efficiency and consistency.

---

## 4. Self-Reflection and Recommendations

- Due to lack of domain GPO and remote management rights, all work was performed manually via GUI, which was inefficient.
- I proactively summarized and accumulated knowledge of automation and scripting for bulk management, so I can respond more quickly to similar situations in the future.
- Most batch deployment failures fundamentally stem from inconsistencies in basic network, sharing, domain accounts, and system environment configuration.
- For similar future projects, I would calibrate network, DNS, AD domain, and workstation states in advance and perform unified checks and remediation before mass deployment.

---

## 5. Summary

This batch deployment internship systematically addressed typical issues such as **network path not found, target account name incorrect, and installation process conflicts**. Through standardized network checks, sharing service configuration, domain account, and process management, most deployment failures can be identified and resolved. Even with manual-only privileges, I maintained clear security principles and a proactive mindset for automation. When granted higher-level rights in the future, I will prioritize scripted and GPO-based batch management to ensure deployment security and efficiency.

---
