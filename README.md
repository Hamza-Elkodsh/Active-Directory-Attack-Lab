# 🛡️ Active Directory Attack Lab

> A structured, hands-on lab environment for learning, practicing, and understanding Active Directory attack techniques and their corresponding defensive countermeasures.

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Platform](https://img.shields.io/badge/platform-Windows%20Server%202019-blue)
![Status](https://img.shields.io/badge/status-active-brightgreen)
![Offensive Security](https://img.shields.io/badge/category-Offensive%20Security-red)
![Defensive Security](https://img.shields.io/badge/category-Defensive%20Security-blue)

---

## ⚠️ Legal Disclaimer

> **This project is strictly for educational and authorized testing purposes only.**
> Unauthorized use of these techniques against systems you do not own or have explicit written permission to test is **illegal** and **unethical**.
> The author assumes no liability for any misuse of the information provided in this repository.
> See [DISCLAIMER.md](./DISCLAIMER.md) for full details.

---

## 📌 Table of Contents

- [Overview](#overview)
- [Lab Architecture](#lab-architecture)
- [Prerequisites](#prerequisites)
- [Quick Start](#quick-start)
- [Project Structure](#project-structure)
- [Attack Modules](#attack-modules)
- [Defense Modules](#defense-modules)
- [Tools Used](#tools-used)
- [Contributing](#contributing)
- [References](#references)
- [License](#license)

---

## 🔍 Overview

This lab simulates a realistic corporate Active Directory environment vulnerable to common misconfigurations and attack techniques used in real-world red team engagements and penetration tests.

The project is divided into two pillars:

| Pillar | Description |
|--------|-------------|
| 🔴 **Offensive** | Step-by-step attack walkthroughs covering recon, credential attacks, lateral movement, privilege escalation, and persistence |
| 🔵 **Defensive** | Detection rules (Sigma/Splunk), hardening guides, GPO templates, and monitoring strategies for every attack covered |

This dual approach ensures the lab is useful for:
- Penetration testers preparing for OSCP, CRTE, or CRTO certifications
- Blue teamers building detection capabilities
- Security engineers learning AD hardening
- Students exploring offensive security in a safe environment

---

## 🏗️ Lab Architecture

```
┌─────────────────────────────────────────────────────────┐
│                    LAB NETWORK (192.168.56.0/24)        │
│                                                         │
│  ┌──────────────────┐      ┌───────────────────────┐   │
│  │  DC01             │      │  WS01 (Windows 10)    │   │
│  │  Domain Controller│◄────►│  Workstation 1        │   │
│  │  192.168.56.10    │      │  192.168.56.20        │   │
│  │  lab.local        │      └───────────────────────┘   │
│  └──────────────────┘                                   │
│           ▲               ┌───────────────────────┐     │
│           │               │  WS02 (Windows 10)    │     │
│           └──────────────►│  Workstation 2        │     │
│                           │  192.168.56.21        │     │
│  ┌──────────────────┐     └───────────────────────┘     │
│  │  Kali Linux       │                                   │
│  │  Attacker Machine │◄──── All attack traffic          │
│  │  192.168.56.100   │                                   │
│  └──────────────────┘                                   │
└─────────────────────────────────────────────────────────┘
```

**Domain:** `lab.local`
**Forest Functional Level:** Windows Server 2016
**Domain Functional Level:** Windows Server 2016

---

## ✅ Prerequisites

### Software Requirements

| Tool | Version | Purpose |
|------|---------|---------|
| [VirtualBox](https://www.virtualbox.org/) | 7.0+ | Virtualization platform |
| [Vagrant](https://www.vagrantup.com/) | 2.3+ | VM provisioning |
| [Git](https://git-scm.com/) | Latest | Clone this repo |
| Windows Server 2019 ISO | - | Domain controller |
| Windows 10 ISO | - | Workstations |
| Kali Linux | 2024+ | Attacker machine |

### Hardware Requirements

| Resource | Minimum | Recommended |
|----------|---------|-------------|
| RAM | 8 GB | 16 GB |
| CPU Cores | 4 | 8 |
| Disk Space | 60 GB | 100 GB |

### Knowledge Requirements
- Basic networking (TCP/IP, DNS, DHCP)
- Familiarity with Windows environments
- Basic Linux command line

---

## 🚀 Quick Start

```bash
# 1. Clone the repository
git clone https://github.com/YOUR_USERNAME/Active-Directory-Attack-Lab.git
cd Active-Directory-Attack-Lab

# 2. Install Vagrant plugins
vagrant plugin install vagrant-reload

# 3. Spin up the lab environment
cd lab-setup
vagrant up

# 4. Verify all VMs are running
vagrant status

# 5. Start with the first attack module
cd ../attacks/01-recon
cat README.md
```

> ⏱️ Initial setup takes approximately **20–40 minutes** depending on your internet speed and hardware.

---

## 📁 Project Structure

```
Active-Directory-Attack-Lab/
│
├── README.md               ← You are here
├── DISCLAIMER.md           ← Legal disclaimer
├── LICENSE                 ← MIT License
├── CHANGELOG.md            ← Version history
├── .gitignore              ← Git ignore rules
│
├── lab-setup/              ← VM provisioning and configuration
├── attacks/                ← Offensive attack modules (01–05)
├── defense/                ← Detection, hardening, and monitoring
├── reporting/              ← Pentest report templates
├── resources/              ← Wordlists, cheatsheets, references
└── scripts/                ← Automation and utility scripts
```

---

## ⚔️ Attack Modules

| # | Module | Techniques Covered |
|---|--------|--------------------|
| 01 | [Reconnaissance](./attacks/01-recon/) | Nmap, BloodHound, Enum4linux, LDAP Enumeration |
| 02 | [Credential Attacks](./attacks/02-credential-attacks/) | Kerberoasting, AS-REP Roasting, Password Spraying, Pass-the-Hash |
| 03 | [Lateral Movement](./attacks/03-lateral-movement/) | Pass-the-Ticket, WinRM, WMI, PsExec |
| 04 | [Privilege Escalation](./attacks/04-privilege-escalation/) | ACL Abuse, GPO Abuse, Constrained Delegation, AD CS |
| 05 | [Persistence](./attacks/05-persistence/) | Golden Ticket, Silver Ticket, Skeleton Key, DCSync |

---

## 🛡️ Defense Modules

| Module | Coverage |
|--------|----------|
| [Detections](./defense/detections/) | Sigma rules, Splunk queries, Windows Event IDs |
| [Hardening](./defense/hardening/) | AD Tiering Model, PAW, GPO templates |
| [Monitoring](./defense/monitoring/) | SIEM integration, honeypot accounts |

---

## 🧰 Tools Used

### Offensive Tools
- [BloodHound](https://github.com/BloodHoundAD/BloodHound) — AD relationship visualization
- [Impacket](https://github.com/fortra/impacket) — Python classes for network protocols
- [CrackMapExec](https://github.com/byt3bl33d3r/CrackMapExec) — Swiss army knife for AD pentesting
- [Mimikatz](https://github.com/gentilkiwi/mimikatz) — Credential extraction
- [Rubeus](https://github.com/GhostPack/Rubeus) — Kerberos interaction and abuse
- [Evil-WinRM](https://github.com/Hackplayers/evil-winrm) — WinRM shell

### Defensive Tools
- [Sigma](https://github.com/SigmaHQ/sigma) — Generic SIEM detection rules
- [Splunk](https://www.splunk.com/) — Log analysis and SIEM
- [Sysmon](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon) — Windows event monitoring

---

## 🤝 Contributing

Contributions are welcome! Please read the guidelines below before submitting a pull request.

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/new-attack-module`
3. Commit your changes: `git commit -m "Add: DCSync attack walkthrough"`
4. Push to the branch: `git push origin feature/new-attack-module`
5. Open a Pull Request

Please ensure all new attack modules include a corresponding **detection section** in `defense/detections/`.

---

## 📚 References

- [Microsoft AD Documentation](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/)
- [SpecterOps BloodHound Docs](https://bloodhound.readthedocs.io/)
- [The Hacker Recipes](https://www.thehacker.recipes/)
- [HackTricks — Active Directory](https://book.hacktricks.xyz/windows-hardening/active-directory-methodology)
- [PayloadsAllTheThings — AD Attacks](https://github.com/swisskyrepo/PayloadsAllTheThings)
- [MITRE ATT&CK — Enterprise](https://attack.mitre.org/)

---

## 📄 License

This project is licensed under the MIT License — see [LICENSE](./LICENSE) for details.

---

<p align="center">
  Built for learning. Use responsibly. 🔐
</p>
