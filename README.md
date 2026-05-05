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

![Lab Architecture](docs/screenshots/Lab_01.png)

---

## 🔧 Installation

> ⚠️ **Note for Ubuntu 26.04 users:** Most online guides target Ubuntu 22.04. The package names below have been updated and verified for Ubuntu 26.04 (Resolute).

### Step 1 — Update the system

```bash
sudo apt update && sudo apt upgrade -y
```

### Step 2 — Install prerequisites

```bash
sudo apt install -y \
  build-essential g++ gcc cmake \
  libpcap-dev libpcre2-dev \
  zlib1g-dev liblzma-dev \
  libluajit-5.1-dev libhwloc-dev \
  libdumbnet-dev bison flex \
  openssl libssl-dev libnghttp2-dev \
  autoconf automake libtool pkg-config \
  libunwind-dev libfl-dev \
  libgoogle-perftools-dev
```

> 💡 **Ubuntu 26.04 fix:** `libpcre3-dev` is no longer available — use `libpcre2-dev` instead. `libdnet-dev` is also removed; `libdumbnet-dev` covers it.

### Step 3 — Install LibDAQ from source

Snort 3 requires LibDAQ (Data Acquisition library), which is not available via apt:

```bash
cd /tmp
git clone https://github.com/snort3/libdaq.git
cd libdaq
./bootstrap
./configure
make
sudo make install
sudo ldconfig
```

### Step 4 — Install Snort 3 from source

```bash
cd /tmp
git clone https://github.com/snort3/snort3.git
cd snort3
./configure_cmake.sh --prefix=/usr/local --enable-tcmalloc
cd build
make -j$(nproc)
sudo make install
sudo ldconfig
```

### Step 5 — Verify installation

```bash
snort -V
```

Expected output:
```
   ,,_     -*> Snort++ <*-
  o"  )~   Version 3.12.2.0
   ''''  
```

Snort successfully validated the configuration (with 0 warnings).

![Snort Version](docs/screenshots/snort-version.png)

---
