# MITT-PRACTICUM

## PXE Deployment & Domain Join – Field Task Summary

##  Overview

This document summarizes the steps I personally completed during a PXE-based operating system deployment and domain integration task conducted in a classroom lab environment.  
Although this was a group assignment, the following actions strictly reflect my individual contributions.

---

##  Tasks Completed

### 1. Hardware Setup and Cable Management

- Connected **workstations, monitors, keyboards, mouses, power cords, and Ethernet cables**.
- Ensured all machines were correctly connected to the designated switch ports and power sources.
- Verified physical readiness for network deployment.

---

### 2. FOG Deployment Task Preparation

- Logged into the **FOG server web interface**.
- Created Windows 11 deployment tasks for the assigned machines.
- Mapped each machine with correct **MAC address and hostname** records.

---

### 3. BIOS Boot Configuration

- Restarted machines and entered BIOS using `F2`.
- Navigated to **Boot Configuration** settings.
- Enabled **PXE boot** as the first boot option.
- Saved and exited BIOS to trigger PXE-based image deployment.

---

### 4. PXE Boot & Image Deployment

- Monitored PXE boot sequence.
- Waited for FOG server to initiate automated deployment of **Windows 11**.
- Confirmed successful installation on all relevant machines.

---

### 5. Active Directory Domain Join

- Logged into the freshly imaged Windows 11 system.
- Joined the machine to the school’s **Active Directory domain**.
- Validated:
  - Correct `hostname`
  - Domain registration via `System Properties`
  - IP/DNS configuration using `ipconfig`, `hostname`, and `ping` tests

---

##  Reflection & Takeaways

- Consistency across BIOS boot configuration is critical for network-based imaging.
- Proper MAC and hostname registration is a prerequisite for successful task mapping in FOG.
- Domain integration demands accurate DNS resolution and correct network settings.
- This task reinforced my understanding of the full deployment pipeline from hardware setup to system identity registration.



---

##  Project Tags

`PXE Boot` `Windows Deployment` `FOG Server` `Active Directory`  
`Domain Join` `BIOS Configuration` `IT Internship` `Network Imaging`

---

##  Skills Used

- **Hardware Setup & Troubleshooting**: Power, monitor, keyboard, mouse, NIC port coordination.
- **FOG Imaging Platform**: Task creation, MAC-to-hostname mapping, image pushing.
- **BIOS Navigation**: Boot priority configuration for PXE deployment.
- **PXE Boot Process**: Network-based OS installation and system boot validation.
- **Windows 11 System Setup**: Initial login, hostname/IP/DNS verification.
- **Active Directory Integration**: Manual domain join, system verification with AD tools.
- **Command-line Diagnostics**: `ipconfig`, `hostname`, `ping`, system properties.
- **Deployment Workflow Understanding**: End-to-end automation pipeline from hardware to identity management.

---

##  Conclusion

This deployment activity demonstrated hands-on experience with enterprise deployment tools and domain-based authentication environments.  
By personally managing both the physical and logical layers of deployment, I practiced a complete system provisioning process aligned with IT administrative workflows.

