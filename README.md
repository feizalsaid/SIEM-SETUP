# Wazuh SIEM Homelab

A complete security monitoring homelab built with Wazuh — deployed on Ubuntu Server with agents on Arch Linux and Windows 11. Includes file integrity monitoring, active response rules, and CIS hardening with OpenSCAP.

## Architecture

```
┌─────────────────────────┐
│   Wazuh Manager (Ubuntu) │
│   192.168.217.131        │
│   ┌──────────┐           │
│   │ Indexer  │           │
│   │ Server   │           │
│   │ Dashboard│           │
│   └──────────┘           │
└──────────┬──────────────┘
           │
    ┌──────┴──────┐
    │             │
┌───▼────┐  ┌────▼────┐
│ Arch   │  │Windows 11│
│ Linux  │  │  Agent   │
│ Agent  │  │          │
└────────┘  └─────────┘
```

## What's Included

- **Wazuh Manager** — All-in-one deployment (Indexer + Server + Dashboard) on Ubuntu
- **Agent Deployment** — Automated installation scripts for Windows (PowerShell) and Arch Linux (AUR)
- **File Integrity Monitoring** — Real-time detection of file changes with configurable monitoring rules
- **Active Response** — Custom rules for automatic threat blocking (e.g., SSH brute force detection)
- **CIS Hardening** — OpenSCAP compliance scanning and remediation

## Components

| Component | Description |
|-----------|-------------|
| `wazuhinstallationandsetup.md` | Full installation guide for the 3-node lab (with screenshots) |
| `FILEINTEGRITYMGMT.md` | File integrity monitoring configuration and testing (with screenshots) |
| `images/` | Screenshots extracted from the original documentation |

> The original Word documentation (`FILEINTEGRITYMANAGEMENT.docx`) was extracted to
> `images/` so the screenshots render directly in the markdown guides.

## Quick Start

1. Deploy Wazuh Manager on Ubuntu Server:
   ```bash
   curl -sO https://packages.wazuh.com/4.12/wazuh-install.sh
   sudo bash ./wazuh-install.sh -a
   ```

2. Install agent on Windows 11 (Admin PowerShell):
   ```powershell
   .\install-agent.ps1
   ```

3. Install agent on Arch Linux:
   ```bash
   git clone https://github.com/mranv/wazuh-agent-archlinux
   cd wazuh-agent-archlinux && makepkg -si
   ```

4. Access the dashboard at `https://<manager-ip>:443`

## What I Learned

- Deploying and configuring SIEM infrastructure from scratch
- Writing custom detection rules mapped to MITRE ATT&CK (T1110 - Brute Force)
- File integrity monitoring with real-time alerting
- CIS benchmark compliance with OpenSCAP automation
- Agent management across heterogeneous OS environments

## Tech Stack

`Wazuh` `OpenSCAP` `Linux` `Windows` `Ansible` `SIEM` `CIS Hardening`
