# MITT-PRACTICUM
My individual submission for the practicum.
## Inventory Audit of 30 Cisco Switches in a Real-World School IT Environment

As part of my practicum training in a live school IT infrastructure environment, I was assigned the task of auditing and recording essential information from 30 Cisco switches. The objective was to collect and document each device's model number, serial number, number of ports, IOS version, and software image—critical details for asset management and lifecycle planning.

The process began with preparing a workstation. I located an unused desktop, installed RAM and a hard drive, connected a monitor, and tested power-up functionality. When the initial machine failed to boot, I applied a standard hardware troubleshooting method—**component substitution**—by selecting a different machine and repeating the test sequence. Once a stable system was identified, I created a bootable USB with Rufus, updated the BIOS to boot from USB, installed Windows OS, and configured PuTTY for CLI operations.

To increase efficiency, I requested six power cables from the instructor, enabling me to power up six switches simultaneously. I accessed each device through the console and used the `show version` command to extract the required information. I carefully documented all results in Excel and performed a **manual double-check** after each batch of six to prevent errors.

After completing the data collection, I returned all switches to a **physically secure, access-controlled storage location** designed for equipment protection, following standard ESD and inventory protocols.

### Professional Insight

This task gave me hands-on experience in operational network administration within a functioning school environment. It reinforced my technical skills in BIOS setup, CLI interaction, and device documentation, while also building confidence in troubleshooting, task efficiency, and hardware handling. These are directly transferable skills for entry-level roles in network and system administration, and this experience has strengthened my readiness for professional IT positions.

---

## Team Members
- Aiwei Tu
- Prabhjot Kaur
- Arshdeep Kaur

---

## References
- Cisco CLI command reference: https://www.cisco.com/c/en/us/td/docs/
- Rufus bootable USB creation: https://rufus.ie/en/
- PuTTY terminal client: https://www.putty.org/

---
