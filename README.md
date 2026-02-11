# 🐧 Virtual Lab Setup: Ubuntu & VirtualBox

## 1. Project Overview
**Objective:** To create a safe, isolated environment (Sandbox) for testing Linux commands, analyzing logs, and practicing network configurations without risking my main computer.
**Role:** System Administrator / Junior Analyst.

## 2. Tools Used
* **Host Machine:** Windows 10/11
* **Virtualization Software:** Oracle VM VirtualBox (Type 2 Hypervisor)
* **Guest OS:** Ubuntu 22.04 LTS (Long Term Support)

## 3. Implementation Steps

### Step A: Configuration
I allocated specific resources to ensure the VM runs smoothly while keeping the Host stable:
* **RAM:** 4 GB (Allocated to handle future GUI tools)
* **Storage:** 60 GB (Dynamically allocated)
* **Network Adapter:** NAT (To allow internet access for updates)

### Step B: Installation Process
1.  Downloaded the official ISO from Ubuntu.com.
2.  Mounted the ISO in the Virtual Optical Drive.
3.  Followed the installation wizard, creating a root user and a standard user (`yasser`).

### Step C: First "Hardening" & Commands
Once the system was live, I opened the terminal to verify the installation:

```bash
# 1. Checking the system kernel version
uname -a

# 2. Verifying IP configuration
ip addr show

# 3. Updating the package repositories (Security Best Practice)
sudo apt update && sudo apt upgrade -y
```
## 4. Challenges & Troubleshooting
Building this lab wasn't plug-and-play. I encountered specific hurdles that helped me understand the relationship between Hardware and Software:

* **BIOS Virtualization (VT-x/AMD-V):**
    * *Issue:* The VM refused to start initially.
    * *Solution:* I had to reboot my physical machine, access the BIOS/UEFI settings, and manually enable Hardware Virtualization technology.
* **Guest Additions & Resolution:**
    * *Issue:* The Linux screen was tiny and copy-paste between Windows and Ubuntu didn't work.
    * *Solution:* I mounted the "Guest Additions" ISO and installed the necessary drivers to enable Full-Screen mode and Bidirectional Clipboard.
* **Resource Management:**
    * *Learning:* I learned to balance RAM allocation (4GB) so that my host Windows machine remains stable while Ubuntu runs smoothly.

## 5. Key Learnings & Next Steps
**What I have mastered:**
* **Package Management:** Understanding that Linux uses repositories (`apt update`) instead of downloading `.exe` files.
* **Root Privileges:** The critical importance of `sudo` for administrative tasks and security.
* **CLI Comfort:** Overcoming the initial intimidation of the terminal to perform system updates.

**Future Roadmap (Step 3 & 4):**
1.  **Networking:** Configure Network Adapters (Bridge vs NAT) to simulate a real LAN and make VMs communicate.
2.  **Traffic Analysis:** Install **Wireshark** on this VM to visualize packets, linking my Cisco CCNA theory to practice.
