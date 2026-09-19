<div align="center">

# 🔐 Cybersecurity & Penetration Testing Lab

**Building a controlled virtual environment for cybersecurity, penetration testing, and ethical hacking practice**

</div>

<p align="center">
  <img src="https://img.shields.io/badge/Focus-Cybersecurity-C00000?style=flat-square&labelColor=404040" />
  <img src="https://img.shields.io/badge/VirtualBox-v7.2-0070C0?style=flat-square&labelColor=000000&logo=virtualbox&logoColor=white" />
  <img src="https://img.shields.io/badge/Kali%20Linux-v2026.2-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Host-Windows%2011-0078D4?style=flat-square&labelColor=000000&logo=windows&logoColor=white" />
  <img src="https://img.shields.io/badge/Linux-Kali%20Linux-404040?style=flat-square&labelColor=C00000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Network-10.0.0.0%2F24-238F89?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Nmap-v7.99-C00000?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Virtualization-VirtualBox-404040?style=flat-square&labelColor=C00000&logo=virtualbox&logoColor=white" />
  <img src="https://img.shields.io/badge/Penetration%20Testing-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Ethical%20Hacking-C00000?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/GitHub-404040?style=flat-square&labelColor=0070C0&logo=github&logoColor=white" />
  <img src="https://img.shields.io/badge/Week%2001-Lab%20Setup-404040?style=flat-square&labelColor=C00000" />
</p>

---

## Project Overview

This project focuses on setting up a virtual cybersecurity and penetration-testing laboratory using VirtualBox and Kali Linux on a Windows 11 computer.
The purpose of the laboratory is to create a controlled environment where cybersecurity tools, network reconnaissance, port scanning, vulnerability assessment, packet analysis, web-security testing, and other authorized security-testing activities can be performed safely.
The laboratory uses a dedicated VirtualBox NAT Network with the 10.0.0.0/24 subnet. Kali Linux is configured with a consistent static IP address of 10.0.0.2/24, allowing the environment to be documented and expanded with additional virtual machines in future cybersecurity exercises.

---

## Objectives

The main objectives of this project were to:
1. Install and configure VirtualBox.
2. Install and configure Kali Linux as the cybersecurity testing machine.
3. Create a dedicated NAT Network using the 10.0.0.0/24 subnet.
4. Configure Kali Linux with a static IPv4 address.
5. Configure the default gateway and DNS server.
6. Enable bidirectional clipboard and drag-and-drop functionality.
7. Configure a shared /downloads folder between the Windows host and Kali Linux.
8. Verify Internet connectivity and DNS resolution.
9. Verify that Nmap is installed and available.
10. Create a clean VirtualBox snapshot for recovery.
11. Document problems encountered during the setup and the solutions used.
12. Prepare the environment for future authorized cybersecurity exercises.

---

## Purpose of the Lab

The laboratory provides an isolated and controlled environment for cybersecurity education and authorized security testing.

The environment can be used for activities such as:
* Network reconnaissance
* Port scanning
* Vulnerability assessment
* Packet analysis
* Web-security testing
* Exploitation practice
* Security-tool experimentation
  
The laboratory is intended for systems that are owned by the student or for systems where explicit authorization to perform security testing has been provided.

**Important**: Cybersecurity tools must only be used against systems for which the tester has authorization. The lab should not be used to attack unauthorized systems or networks.

---

## Lab Architecture

The laboratory is based on a Windows 11 host computer running VirtualBox.
Kali Linux operates as the attacker/security-testing virtual machine and connects to the dedicated NatNetwork NAT Network.
The current architecture is:

```text
                    INTERNET
                       │
                       │
             ┌───────────────────────┐
             │   Windows 11 HOST     │
             │     32 GB RAM         │
             │  10 cores/12 logical  │
             └──────────┬────────────┘
                        │
                   VirtualBox
                        │
                ┌───────▼────────┐
                │   NAT Network  │
                │   NatNetwork   │
                │  10.0.0.0/24   │
                └───────┬────────┘
                        │
                 Gateway 10.0.0.1
                        │
                ┌───────▼────────┐
                │   Kali Linux   │
                │   10.0.0.2/24  │
                │   DNS 8.8.8.8  │
                └────────────────┘
                         |
                         |  
                  Security Testing

A shared folder is also configured between the Windows host and Kali Linux:
Windows Host
     |
     | Shared Folder
     |
 /downloads
     |
 Kali Linux
Additional virtual machines can be connected to the same NAT Network in future projects to create attacker, target, and supporting systems for authorized testing.

```

---

## Lab Configuration

|       Component        |         Configuration          |
|------------------------|--------------------------------|
| Host OS                | Windows 11                     |
| Host RAM               | 32 GB                         |
| Host CPU               | 10 cores/12 logical processors |
| Hypervisor             | Oracle VirtualBox              |
| Security VM            | Kali Linux 2026.2              |
| Kali CPU               | 2 CPUs                         |
| Kali RAM               | 2048 MB                        |
| Virtual Network        | NAT Network                    |
| Network Name           | `NatNetwork`                   |
| Network Address        | `10.0.0.0/24`                  |
| DHCP                   | Disabled                       |
| IPv6                   | Disabled                      |
| Kali IP Address        | `10.0.0.2/24`                  |
| Subnet Mask            | 255.255.255.0                  |
| Gateway                | `10.0.0.1`                     |
| DNS                    | `8.8.8.8`                      |
| Kali Network Interface | `eth0`                         |
| Nmap Version           | 7.99                           |
| Shared Folder          | `/downloads`                   |
| Snapshot               | `Clean Kali - Network Setup`   |

---

## VirtualBox Adapter Configuration

The Kali VM's Adapter 1 was configured as follows:


|       Setting           |         Configuration                 |
|-------------------------|---------------------------------------|
| Network Adapter         | `Enabled`                             |
| Attached To             | `NAT Network`                         |
| Name                    | `NatNetwork`                          |
| Adapter Type            | `Intel PRO/1000 MT Desktop (82540EM)` |
| Promiscuous Mode        | `Allow All`                           |
| Virtual Cable Connected | `Enabled`                             |

**Clipboard and Drag-and-Drop**
The VirtualBox VM settings were configured with:
* Shared Clipboard: Bidirectional
* Drag and Drop: Bidirectional

Windows-to-Kali drag-and-drop was functional. Kali-to-Windows drag-and-drop remained unreliable and produced a VirtualBox VERR_TIMEOUT error during testing. This issue is documented in the Problems Encountered & Solutions section.

---

# Lab Setup Procedure

## Step 1. Install 7-Zip

7-Zip was used to extract the Kali Linux virtual-machine package when required.

7-Zip is a file-archiving utility commonly used to extract compressed archives such as `.7z` files.

---

## Step 2. Install VirtualBox

VirtualBox was installed on the Windows 11 host computer and used as the hypervisor for the cybersecurity laboratory.

The Windows host provides:
* 32 GB RAM
* 10 CPU cores
* 12 logical processors

---

## Step 3. Create the NAT Network

A dedicated NAT Network named NatNetwork was configured in VirtualBox.

The network was configured with:

```text
Network Name: NatNetwork
IPv4 Prefix:  10.0.0.0/24
DHCP:         Disabled
IPv6:         Disabled
```

![]()

The DHCP service was disabled because Kali Linux was configured with a static IP address.

The NAT Network provides a private virtual network where multiple virtual machines can communicate with one another while allowing outbound Internet connectivity through NAT.

This design allows additional attacker and target virtual machines to be added to the laboratory in future projects.

---

## Step 4. Configure Kali Linux

Kali Linux was installed as the cybersecurity testing/attacking virtual machine.

The VM was allocated:
* RAM: 2048 MB
* CPU: 2

The first network adapter was configured as:
* Attached to: NAT Network
* Network:     NatNetwork

The adapter was configured with the Intel PRO/1000 MT Desktop (82540EM) virtual network adapter.

---
## Step 5. Configure the Kali Linux Network

Kali Linux was configured with the following IPv4 settings:

```text
IP Address:     10.0.0.2/24
Subnet Mask:    255.255.255.0
Gateway:        10.0.0.1
DNS:            8.8.8.8
```

The final ip -4 addr verification showed:

```text
eth0
inet 10.0.0.2/24
```

The routing table showed:

```text
default via 10.0.0.1 dev eth0
10.0.0.0/24 dev eth0
```

The DNS configuration showed:

```text
nameserver 8.8.8.8
```

---

## Step 6. Configure the Shared Folder

A shared folder was configured between the Windows host and Kali Linux.

The shared folder is mounted in Kali at:

```text
/downloads
```

The mount was verified using:

```text
mount | grep downloads
```

The result confirmed:

```text
Cybersecurity-Internship on /downloads type vboxsf (rw,nodev,relatime)
```

The directory was also accessible from Kali and contained test files and the project documentation.

---

## Step 7. Configure Clipboard and Drag-and-Drop

VirtualBox was configured with:

```text
Shared Clipboard: Bidirectional
Drag and Drop:    Bidirectional
```

```text
The Kali Guest Additions services were verified using ps, including:
VBoxClient --clipboard
VBoxClient --draganddrop
VBoxClient --seamless
VBoxClient --vmsvga-session
```

This confirmed that the VirtualBox guest integration services were running.

---

## Step 8. Create a Clean VM Snapshot

After the initial configuration was completed and verified, a VirtualBox snapshot was created.

Snapshot name:

```text
Clean Kali - Network Setup
```

The snapshot represents the known-good baseline of the cybersecurity laboratory.
This provides a recovery point before future cybersecurity exercises or experiments are performed.

---

# Lab Verification

The laboratory configuration was verified using several Linux commands and connectivity tests.

| ✅ Test               | 🧾 Command              | 🎯 Expected Result                 |
| ----------------------|--------------------------|------------------------------------|
| Check IP address      | `ip -4 addr`             | 10.0.0.2/24 displayed on eth0      |
| Check routing         | `ip route`               | Default gateway 10.0.0.1 confirmed |
| Check DNS             | `cat /etc/resolv.conf`   | 8.8.8.8 confirmed                  |             
| Test gateway//network | `ping -c 4 10.0.0.1`     | Successful during setup            |
| Test Internet IP      | `ping -c 4 8.8.8.8`      | 4/4 replies, 0% packet loss        |
| Test DNS + Internet   | `ping -c 4 google.com`   | 4/4 replies, 0% packet loss        |
| Test DNS resolution   | `nslookup google.com`    | Domain successfully resolved       |
| Verify Nmap           | `nmap --version`         | Nmap 7.99 displayed                |
| Verify shared folder  | `mount grep downloads` | /downloads mounted as vboxsf       |
| Snapshot              | VirtualBox Snapshots | Clean Kali - Network Setup created     |

### Example Results

```text
IP Address
The Kali Linux interface was successfully configured as:
Interface:    eth0
IP Address:   10.0.0.2/24
Subnet:       10.0.0.0/24

Default Gateway
The routing table confirmed:
default via 10.0.0.1 dev eth0

DNS
The DNS configuration confirmed:
nameserver 8.8.8.8

Internet Connectivity
The following test was successful:
ping -c 4 8.8.8.8

Result:
4 packets transmitted, 4 received, 0% packet loss

DNS Resolution
The following command successfully resolved Google:
nslookup google.com

The DNS server used was:
8.8.8.8

Multiple IPv4 and IPv6 addresses were returned for google.com, confirming successful DNS resolution.
Domain Connectivity
The following test was also successful:
ping -c 4 google.com

Result:
4 packets transmitted, 4 received, 0% packet loss

This confirmed both Internet connectivity and working DNS resolution.
Nmap
Nmap was verified using:
nmap --version

The installed version was:
Nmap version 7.99
```

---

# Problems Encountered & Solutions

Documenting problems encountered during the laboratory setup was an important part of the project.

## Problem 1. Static IP and Network Connectivity

During the initial configuration, Kali experienced a networking problem when the static IP configuration was being established.

The address `10.0.0.2` was detected as already occupied, which prevented the expected network configuration from activating correctly.

**Solution**

The VirtualBox NAT Network configuration was reviewed and the DHCP service was disabled because the lab uses a manually assigned static IP address.

After the network configuration was corrected, Kali was able to use: `10.0.0.2/24` with `Gateway: 10.0.0.1

The configuration was subsequently verified using ip addr and ip route.

---

## Problem 2. DNS Resolution

After basic network connectivity was restored, Kali could communicate with external IP addresses but initially had difficulty resolving domain names.

For example, direct connectivity to an IP address worked while domain-name connectivity did not.

**Solution**

The DNS configuration was corrected to use: `8.8.8.8`

The DNS configuration was then verified with: `cat /etc/resolv.conf`

which showed: `nameserver 8.8.8.8`

DNS resolution was subsequently confirmed using: `nslookup google.com` and `ping -c 4 google.com`

Both tests were successful.

---

## Problem 3. Virtualization Error

During the initial VM setup, the Kali virtual machine encountered a hardware virtualization/VT-x startup problem.

**Solution**

The computer was restarted and the system BIOS/UEFI settings were checked.

Hardware virtualization/Intel VT-x was enabled, after which the Kali virtual machine was able to start normally.

---

## Problem 4. Kali-to-Windows Drag-and-Drop Timeout

The VirtualBox Drag and Drop setting was configured as: `Bidirectional`

The VirtualBox Guest Additions version installed in Kali was: `7.2.16_Debian r174877`

The VBoxClient --draganddrop process was also confirmed to be running.
Windows-to-Kali drag-and-drop worked, but Kali-to-Windows drag-and-drop repeatedly failed with: `VERR_TIMEOUT` and `VBOX_E_DND_ERROR`

A small text file was used for testing to rule out file-size problems. The drag-and-drop client was also restarted, but the same error remained.

**Solution / Final Status**

The VirtualBox configuration was left with Drag and Drop set to Bidirectional, satisfying the requested VM configuration.

Because guest-to-host drag-and-drop remained unreliable, the configured VirtualBox shared folder was used as the dependable method for transferring files between Windows and Kali.

The issue was documented rather than changing the working network configuration or performing unnecessary reinstallation.

---

# What I Learned

Through this project, I learned how to create and configure a virtual environment for cybersecurity practice.

## 1. NAT vs. NAT Network

I learned that standard NAT and NAT Network configurations serve different purposes.

A NAT Network allows multiple virtual machines connected to the same virtual network to communicate with one another while also providing outbound connectivity through NAT.

This makes NAT Network useful for creating a multi-machine cybersecurity laboratory.

## 2. Virtual Machine Networking

I learned how VirtualBox virtual network adapters connect virtual machines to different network types and how IP addressing, gateways, DNS, and network configuration affect communication.

## 3. Static IP Configuration

I learned how to configure and verify:
* IPv4 addresses
* Subnet masks
* Default gateways
* DNS servers
* Routing tables

The Kali machine was successfully configured with: `10.0.0.2/24`

## 4. DNS Troubleshooting

I learned that Internet connectivity and DNS resolution are separate components.

A system may be able to reach an external IP address while still being unable to resolve domain names.

Testing both an IP address and a domain name helped identify and correct the DNS configuration.

## 5. Shared Folders

I learned how VirtualBox shared folders provide a reliable method for transferring files between the Windows host and Kali Linux.

The shared folder was successfully mounted at: `/downloads`

## 6. VM Snapshots

I learned that a clean snapshot should be created before beginning risky or experimental cybersecurity activities.

The snapshot:

Clean Kali - Network Setup

provides a known-good recovery point for future exercises.

## 7. Cybersecurity Tool Verification

I learned the importance of verifying that security tools are installed and working before beginning security exercises.

Nmap was successfully verified with: `nmap --version` and returned version: `7.99`

## 8. Documentation and Troubleshooting

I learned that documenting problems, commands, configuration changes, test results, and solutions is an important part of a professional cybersecurity project.

Rather than changing multiple settings at once, I learned to test individual components and use the results to identify the source of a problem.

---
# Security & Ethical Use

This laboratory is intended strictly for cybersecurity education, training, and authorized security testing.

All scanning, reconnaissance, vulnerability assessment, exploitation practice, and other security activities should only be performed against:
* Systems owned by the student
* Intentionally vulnerable laboratory systems
* Systems for which explicit authorization has been provided

The lab provides a controlled environment for learning cybersecurity concepts without intentionally targeting unauthorized systems.

---

# Tools & Resources

* **7-Zip** — used for extracting compressed virtual-machine packages.
* **VirtualBox** — used as the virtualization platform.
* **Kali Linux** — used as the cybersecurity testing/attacking operating system.
* **Nmap** — used for network discovery and security testing in authorized environments.
* **VirtualBox NAT Network** — used to create the private 10.0.0.0/24 laboratory network.

**Official resources:**
* 7-Zip: https://7-zip.org/
* VirtualBox: https://www.virtualbox.org/
* Kali Linux: https://www.kali.org/
* Nmap: https://nmap.org/

---

# Author / Project Information

**Author:** Chioma Fortress Evans Okay\
**Program:** Cybersecurity B083\
**Week:** 01\
**Project:** Cybersecurity & Penetration-Testing Lab Setup\
**Environment:** Windows 11 + VirtualBox + Kali Linux\
**Repository:** GitHub\

---

# Conclusion

The cybersecurity laboratory was successfully configured using Windows 11, VirtualBox, and Kali Linux.

The Kali Linux VM is connected to the `NatNetwork` NAT Network using the `10.0.0.0/24` subnet and has the static address: `10.0.0.2/24`

The default gateway and DNS server are:
```text
Gateway: 10.0.0.1
DNS:     8.8.8.8
```

Internet connectivity and DNS resolution were successfully verified. The /downloads shared folder is mounted and accessible, clipboard and drag-and-drop are configured as bidirectional, Nmap is installed and verified, and a clean VM snapshot has been created.

The remaining drag-and-drop issue from Kali to Windows was documented as a troubleshooting issue while retaining the working shared-folder solution.

The laboratory is now ready for future authorized cybersecurity exercises and for adding additional virtual machines to the private testing environment.
