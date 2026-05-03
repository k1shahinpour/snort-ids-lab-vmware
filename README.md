# snort-ids-lab-vmware

Practical Snort 3 IDS lab demonstrating installation, rule writing, packet analysis, and intrusion detection in a controlled virtual environment. Built as a hands-on portfolio project.

---

## 📋 Table of Contents

- [Objectives](#-objectives)
- [Lab Environment](#️-lab-environment)
- [Lab Architecture](#-lab-architecture)

---

## 🎯 Objectives

- Deploy Snort 3 as a Network Intrusion Detection System (NIDS) on Ubuntu
- Write and tune custom Snort 3 rules to detect real attack patterns
- Simulate attacks from Kali Linux and validate detection accuracy

---

## 🖥️ Lab Environment

### Hardware

- Apple MacBook Pro (2021)
- Apple M1 Pro Chip
- 16 GB RAM

### Virtualization Platform

- VMware Fusion 25H2U1

### Virtual Machines

#### 🔴 Attacker Machine

- OS: Kali Linux 2026.1
- Role: Attack simulation (scanning, probing, traffic generation)

#### 🟢 Victim / Detection Machine

- OS: Ubuntu 26.04 LTS (Resolute)
- Snort Version: **3.12.2.0**
- Role: Snort IDS (Intrusion Detection System)

---

## 🧠 Lab Architecture

```
┌─────────────────────────┐        Isolated Virtual Network        ┌──────────────────────────┐
│   🔴 Kali Linux          │ ─────────────────────────────────────► │   🟢 Ubuntu 26.04        │
│   Attacker               │        (VMware Host-Only Network)      │   Snort 3.12.2.0 IDS     │
│   Attack Tools:          │                                        │   Monitors & Alerts on   │
│   nmap, hping3, etc.     │                                        │   all incoming traffic   │
└─────────────────────────┘                                        └──────────────────────────┘
```

Both machines are connected within an isolated virtual network (VMware Fusion) with no external internet exposure.

<img width="1920" height="1080" alt="Screenshot 2026-05-02 at 11 06 26 AM" src="https://github.com/user-attachments/assets/b95951a8-55ac-49e8-be54-074e5746815d" />
