# MITT-PRACTICUM

Quick Overview
This repository documents my hands-on IT practicum work in a real school lab environment (Winnipeg, MB). Key deliverables include endpoint deployment runbooks, network device inventory/audit notes, and infrastructure build documentation.
Highlights:

Audited and documented 30 Cisco switches (model/serial/ports/IOS/image) for asset lifecycle planning.

Built a workstation for console access (BIOS/USB install, PuTTY) and improved efficiency by batching device processing.

Documented server deployment work including RAID provisioning (Dell PERC / HP Smart Array) and KVM integration.

Key Deliverables 

Switch inventory audit 

PXE deployment & domain join summary

Windows PDQ deployment notes

RJ45 termination technique

Inventory classification notes

---

## Inventory Audit of 30 Cisco Switches in a Real-World School IT Environment

As part of my practicum training in a live school IT infrastructure environment, I was assigned the task of auditing and recording essential information from 30 Cisco switches. The objective was to collect and document each device's model number, serial number, number of ports, IOS version, and software image—critical details for asset management and lifecycle planning.

The process began with preparing a workstation. I located an unused desktop, installed RAM and a hard drive, connected a monitor, and tested power-up functionality. When the initial machine failed to boot, I applied a standard hardware troubleshooting method—**component substitution**—by selecting a different machine and repeating the test sequence. Once a stable system was identified, I created a bootable USB with Rufus, updated the BIOS to boot from USB, installed Windows OS, and configured PuTTY for CLI operations.

To increase efficiency, I requested six power cables from the instructor, enabling me to power up six switches simultaneously. I accessed each device through the console and used the `show version` command to extract the required information. I carefully documented all results in Excel and performed a **manual double-check** after each batch of six to prevent errors.

After completing the data collection, I returned all switches to a **physically secure, access-controlled storage location** designed for equipment protection, following standard ESD and inventory protocols.

---

### Team Context and Personal Contribution

This switch inventory task was completed as part of a team-based practicum assignment. Each group member was responsible for completing the full device recording process on a subset of Cisco switches.

In addition to my assigned group work, I also collaborated with a student from another group to prepare the shared workstation used for accessing the switches. This included hardware verification, BIOS configuration, Windows installation, and tool setup (Rufus and PuTTY).

The tasks outlined above reflect my direct contribution, including:
- Physical workstation setup (in collaboration)
- Efficient switch boot-up planning (6 at a time)
- Data collection from 30 switches (CLI access and `show version`)
- Manual double-check after each batch
- Final secure return of all switches to designated storage

While the overall project was shared among team members, this version highlights the portion I personally completed and managed.

---

### Professional Insight

This task gave me hands-on experience in operational network administration within a functioning school environment. It reinforced my technical skills in BIOS setup, CLI interaction, and device documentation, while also building confidence in troubleshooting, task efficiency, and hardware handling. These are directly transferable skills for entry-level roles in network and system administration, and this experience has strengthened my readiness for professional IT positions.

---

## Server Deployment, RAID Provisioning, and KVM Integration

### Overview

As part of my practicum at MITT, I participated in deploying, configuring, and troubleshooting enterprise servers in a real-world IT environment. My responsibilities included hardware preparation, RAID storage implementation (Dell & HP), and the integration of a hardware KVM switch for efficient rack management. The project also covered data center-level cabling, network device setup, and collaborative teamwork.

---

### Process Summary

#### 1. Server Hardware Preparation

- Assembled and verified the physical setup of Dell and HP enterprise servers.
- Checked RAM, drive installation, and completed all power and data cable connections.
- Created a **Proxmox VE bootable installation USB** using Rufus for OS deployment.

#### 2. RAID Configuration

- **Dell PowerEdge:**
  - Accessed the PERC RAID controller during boot (`Ctrl+R`).
  - Verified SAS/SATA disk recognition, troubleshot missing drives as needed.
  - Created new Virtual Disks (VDs) with RAID levels (0/1/5/10), named and initialized each group.
- **HP ProLiant:**
  - Entered RAID configuration utility with `Ctrl+C`.
  - Detected and troubleshot disk recognition, created and initialized logical drives using proper RAID levels.

#### 3. KVM Switch Integration

- Integrated a **Belkin 4-port USB+VGA KVM switch** for multi-host console access.
- Connected each server's VGA and USB ports to the color-coded KVM cables.
- Verified seamless keyboard, mouse, and display switching between up to four physical servers.

#### 4. Network & Rack Awareness

- Worked with a topology including Dell/HP servers, Fortinet switches, and a SonicWall router (WAN uplink).
- Gained hands-on experience with structured cabling, rack layout, and logical port planning.

---

### Team Context & Personal Contribution

- **Proxmox bootable USB creation** and OS installation preparation.
- **Full RAID configuration** on both Dell and HP servers (including troubleshooting all disk/initialization issues).
- **KVM switch integration** for centralized management of multiple hosts.
- **Documentation** of all configuration steps and encountered issues.
- Collaborated with team members on hardware compatibility and cable management, while independently handling the key configuration tasks.

---

### Professional Insight

This project provided real-world experience in enterprise server deployment, RAID provisioning, and KVM integration. I developed practical skills in hardware configuration, BIOS/RAID setup, and device documentation. These competencies are directly applicable to roles in network and system administration.


---

### Key Skills & Technologies

- Proxmox VE Installation
- Dell PERC & HP Smart Array RAID Configuration (`Ctrl+R`, `Ctrl+C`)
- RAID Levels 0/1/5/10 Implementation
- Belkin USB+VGA KVM Switch Integration
- Structured Cabling & Rack Management
- Troubleshooting (Disk Detection, Initialization, Cable Mapping)
- Documentation & Collaboration

---

### Cognitive Effort and Problem-Solving Log

During this project, significant time and energy were dedicated not just to executing tasks, but to understanding complex issues, troubleshooting unexpected hardware/software behaviors, and iteratively refining solutions. For example:

- Spent over 1 hour diagnosing RAID disk detection issues, including consulting instructor, swapping drives, and verifying controller settings.
- Invested multiple cycles in understanding KVM switch integration, testing various connection combinations, and confirming multi-host control functionality.
- Engaged in peer discussions and online research to validate network topology plans and hardware compatibility.

This cognitive investment enabled rapid adaptation and resilient problem-solving, contributing directly to my professional growth—even when the visible 'output' seemed limited.


> *This practicum reinforced my confidence and technical readiness for professional roles in system and network administration.*
