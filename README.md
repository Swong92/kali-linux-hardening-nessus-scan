# kali-linux-hardening-nessus-scan
Kali Linux hardening lab using Nessus Essentials vulnerability scanning and before/after security comparison.


# Kali Linux Hardening & Nessus Vulnerability Scan

## Project Overview

This project documents a vulnerability scanning and hardening lab completed as part of my cybersecurity internship/cohort. The goal was to perform a baseline vulnerability scan, apply system hardening steps, run a post-hardening scan, and compare the results.

Although the original project instructions focused on Windows 11 hardening, Kali Linux was used as the scan target with instructor approval due to faster performance and better functionality in my lab environment.

## Lab Environment

| Component | Details |
|---|---|
| Host Machine | Windows laptop |
| Virtualization Platform | Oracle VirtualBox |
| Target VM | Kali Linux 2025.4 |
| Scanner | Nessus Essentials |
| Network Setup | NAT + Host-Only Adapter |
| Target IP | 192.168.56.101 |

## Tools Used

- Nessus Essentials
- Oracle VirtualBox
- Kali Linux Terminal
- Linux networking commands
- `ip addr`
- `ping`
- `sysctl`
- `apt`
- `ss`
- `systemctl`

## Scan Results

| Severity | Pre-Hardening Count | Post-Hardening Count |
|---|---:|---:|
| Critical | 0 | 0 |
| High | 0 | 0 |
| Medium | 0 | 0 |
| Low | 1 | 1 |
| Informational | 4 | 6 |

## Hardening Steps Completed

### 1. Verified Network Configuration

I confirmed the Kali Linux VM was connected using both NAT and Host-Only networking. The Host-Only adapter allowed Nessus on my Windows laptop to scan the Kali Linux VM.

### 2. Resolved Connectivity Issues

The first scan attempt failed because Nessus could not reach the VM. I restarted NetworkManager in Kali Linux and confirmed successful connectivity using ping from the Windows host machine.

### 3. Restricted ICMP Broadcast Responses

I modified `/etc/sysctl.conf` to reduce unnecessary ICMP responses and limit network information disclosure.

```bash
net.ipv4.icmp_echo_ignore_broadcasts = 1
