# Changelog

All notable changes to the **Active Directory Attack Lab** project will be documented in this file.

This project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html) and the format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

---

## [Unreleased]

### Planned
- ADCS (Active Directory Certificate Services) attack module
- Azure AD / Hybrid AD attack techniques
- Automated lab health-check script
- Docker-based alternative to Vagrant setup
- Video walkthrough links for each attack module

---

## [1.0.0] — 2025-05-15

### 🎉 Initial Release

#### Added
- Full project structure and documentation framework
- `lab-setup/` — Vagrant-based lab provisioning
  - `Vagrantfile` for automated VM creation (DC01, WS01, WS02, Kali)
  - PowerShell provisioning scripts for AD configuration
  - AD user and group creation scripts
  - GPO baseline configuration
- `attacks/01-recon/` — Reconnaissance module
  - Nmap AD scanning guide
  - Enum4linux enumeration walkthrough
  - LDAP enumeration techniques
  - BloodHound data collection and analysis
- `attacks/02-credential-attacks/` — Credential attacks module
  - Password spraying walkthrough
  - Kerberoasting end-to-end guide
  - AS-REP Roasting techniques
  - Pass-the-Hash attack
- `attacks/03-lateral-movement/` — Lateral movement module
  - Pass-the-Ticket walkthrough
  - WinRM lateral movement
  - WMI remote execution
  - PsExec-based movement
- `attacks/04-privilege-escalation/` — Privilege escalation module
  - ACL/DACL abuse techniques
  - GPO abuse for privilege escalation
  - Constrained and unconstrained delegation attacks
  - AD CS (Certificate Services) abuse
- `attacks/05-persistence/` — Persistence module
  - Golden Ticket creation and use
  - Silver Ticket attacks
  - Skeleton Key backdoor
  - DCSync attack walkthrough
- `defense/detections/` — Detection and alerting
  - Sigma rules for all covered attack techniques
  - Splunk SPL queries for threat hunting
  - Windows Event ID reference guide
- `defense/hardening/` — Hardening guidelines
  - AD tiering model implementation guide
  - Privileged Access Workstation (PAW) setup
  - GPO hardening templates (LLMNR disable, SMB signing)
- `defense/monitoring/` — Monitoring and visibility
  - SIEM integration guide
  - Honeypot account configuration
- `reporting/` — Report templates
  - Professional pentest report template
  - Individual finding template
  - Sample completed report
- `resources/` — Supporting materials
  - Common AD password wordlist
  - Service account name wordlist
  - Tools reference list
  - AD attack cheatsheet
  - External references and reading list
- `scripts/` — Automation scripts
  - `ad-enum.py` — Automated AD enumeration script
  - `auto-pwn.py` — Lab scenario automation
  - `report-generator.py` — Markdown report generator
- Root files: `README.md`, `DISCLAIMER.md`, `LICENSE`, `.gitignore`
- Network topology diagram
- Lab architecture documentation

---

## [0.1.0] — 2025-04-01

### 🧪 Pre-release / Planning Phase

#### Added
- Initial project planning and structure design
- Research and tool evaluation
- Lab environment prototype testing
- Documentation framework selection

---

## Version History Summary

| Version | Date | Description |
|---------|------|-------------|
| 1.0.0 | 2025-05-15 | Full initial release with all core modules |
| 0.1.0 | 2025-04-01 | Project planning and prototype |

---

## How to Read This Changelog

Each release entry uses the following change categories:

- **Added** — New features, modules, or files
- **Changed** — Updates to existing content or functionality
- **Deprecated** — Features that will be removed in a future release
- **Removed** — Features or content that have been removed
- **Fixed** — Bug fixes or corrections to documentation
- **Security** — Security-related changes or advisories

---

[Unreleased]: https://github.com/YOUR_USERNAME/Active-Directory-Attack-Lab/compare/v1.0.0...HEAD
[1.0.0]: https://github.com/YOUR_USERNAME/Active-Directory-Attack-Lab/releases/tag/v1.0.0
[0.1.0]: https://github.com/YOUR_USERNAME/Active-Directory-Attack-Lab/releases/tag/v0.1.0
