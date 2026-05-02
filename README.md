# snort-ids-lab-vmware
Practical Snort IDS lab demonstrating rule tuning, packet analysis, and intrusion detection in a controlled environment.

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
- OS: Ubuntu 26.04 LTS
- Role: Snort IDS (Intrusion Detection System)

### 🧠 Lab Architecture
- Kali Linux acts as the attacker
- Ubuntu runs Snort to monitor and detect malicious traffic
- Both machines are connected within an isolated virtual network (VMware Fusion)
<img width="1920" height="1080" alt="Screenshot 2026-05-02 at 11 06 26 AM" src="https://github.com/user-attachments/assets/b95951a8-55ac-49e8-be54-074e5746815d" />
