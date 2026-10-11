# IT Service Desk Troubleshooting Lab

## Overview

This project documents hands-on IT support troubleshooting using a Windows 11 virtual machine. It demonstrates basic network diagnostics, system health checks, Windows service verification, and incident documentation.

## Objectives

- Troubleshoot basic network connectivity and DNS resolution.
- Review Windows system health and available disk space.
- Verify Windows Event Log service status.
- Document findings and recommended troubleshooting steps.

## Environment and Tools

- Windows 11
- Oracle VirtualBox
- Windows PowerShell
- Windows Task Manager
- Windows Services
- Windows System File Checker (SFC)
- CHKDSK

## Troubleshooting Activities

| Area | Tool or Command | Result |
|---|---|---|
| Network connectivity | `ping 8.8.8.8` | Successful; 0% packet loss in the recorded test |
| DNS resolution | `nslookup google.com` | Successfully resolved the hostname |
| Network path | `tracert -d 8.8.8.8` | Destination reached in the recorded test |
| Network configuration | `ipconfig /all` and `Get-NetIPConfiguration` | Reviewed adapter addresses, gateways, and DNS settings |
| Adapter status | `Get-NetAdapter` | Both listed Ethernet adapters were up at 1 Gbps |
| System file integrity | `sfc /verifyonly` | No integrity violations found |
| Disk file system | `chkdsk C: /scan` | No file system problems found |
| Memory usage | Task Manager | 2.4 GB of 4.0 GB in use at capture time |
| Disk activity | Task Manager | 0% active time at capture time |
| Storage capacity | File Explorer | 17.2 GB free of 58.6 GB |
| Windows Event Log | Services console | Running; startup type Automatic |

## Incident Documentation

The `tickets/` directory contains the Windows login failure incident ticket, `INC-001-windows-login-failure.md`.

The ticket documents the investigation, relevant authentication events, findings, and recommended response actions.

## Key Takeaways

- Used Windows tools and commands to investigate common IT support issues.
- Practiced interpreting network connectivity, DNS, and system health results.
- Verified that Windows system file and file system scans completed without reported errors.
- Documented findings and distinguished observed evidence from assumptions.

## Evidence

Screenshots of the troubleshooting activities are saved locally in the project's `screenshots/` folder. They can be added to this repository later.

## Scope and Limitations

This is a controlled home lab, not a production environment. Results reflect the system's state at the time of testing and do not establish the cause of every potential system issue. No root cause was confirmed for the previously observed unexpected shutdown.

## Skills Demonstrated

Windows Troubleshooting | PowerShell | Network Diagnostics | DNS | System Health Checks | Incident Documentation | Technical Writing
