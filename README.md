# networkwalks-B082-week1-Cybersecurity-Lab-Setup
**Installation and Setup of Kali Linux on VirtualBox**
# Week 1 Lab – Kali Linux Installation & Setup

## Project Overview
This project documents the installation and configuration of Kali Linux as a virtual machine using Oracle VirtualBox. The goal of this lab was to build a working, isolated environment for security-focused coursework and self-directed practice, including network traffic analysis and social engineering defense research later in the internship.

**Objectives:**
- Install Kali Linux inside VirtualBox on a Windows host
- Configure networking so the VM can reach the internet without exposing it directly to the host network
- Verify the installation is functional and up to date
- Document the setup process for reference in future labs

## Configuration

| Setting        | Value                               |
|----------------|-------------------------------------|
| Host OS        | Windows                             |
| Hypervisor     | Oracle VirtualBox                   |
| Guest OS       | Kali Linux 2026.1                   |
| Install Image  | kali-linux-2026.1-virtualbox-amd64  |
| vCPUs          | 1                                   |
| RAM            | 2 GB                                |
| Disk Size      | 80 GB                               |
| Network Mode   | NAT NETWORK                         |
| Network Range  | 10.0.0.0/24                         |
| Gateway        | 10.0.0.1                            |
| VM IP Address  | 10.0.0.2                            |

## Setup Steps
1. Downloaded the official Kali Linux VirtualBox image from the Kali website.

![image alt]({https://github.com/Giulyyy1/networkwalks-B082-week1-Cybersecurity-Lab-Setup)

2. Created a new VM in VirtualBox and allocated resources as listed in the configuration table above.
3. Attached the Kali image and completed the guided installation, setting up disk partitioning and a local user account.
4. Powered on the VM and confirmed it booted into the Kali desktop environment.

![image alt](https://github.com/Giulyyy1/networkwalks-B082-week1-Cybersecurity-Lab-Setup/blob/df466b0052b6138dc9384b6fbf87a40ecb8adac5/Screenshot%202026-08-12%20222652.png)

5. Set the network adapter to NAT so the VM could reach the internet through the host without being directly reachable from the local network.

![image alt](https://github.com/Giulyyy1/networkwalks-B082-week1-Cybersecurity-Lab-Setup/blob/df466b0052b6138dc9384b6fbf87a40ecb8adac5/Screenshot%202026-08-12%20223935.png)

6. Updated the package lists and upgraded installed packages to bring the system fully up to date.

![image alt](https://github.com/Giulyyy1/networkwalks-B082-week1-Cybersecurity-Lab-Setup/blob/df466b0052b6138dc9384b6fbf87a40ecb8adac5/Screenshot%202026-08-12%20125857.png)


## Verification Commands and Results

To confirm the VM was correctly installed and networked, the following commands were run inside the Kali terminal:

```bash
uname -a
```
Confirms the kernel version and system architecture.

```bash
cat /etc/os-release
```
Confirms the installed OS is Kali Linux 2026.1.

```bash
ip a
```
Confirms the VM received an IP address (10.0.0.2) from the NAT gateway (10.0.0.1), verifying network connectivity.

```bash
sudo apt update && sudo apt upgrade -y
```
Confirms the system can reach package repositories and applies the latest updates.

*(Insert screenshots here: output of each command above.)*

## Problems Faced
The installation and initial setup went smoothly overall. The main point worth noting was deciding on NAT rather than Bridged networking — NAT was chosen because it keeps the VM isolated from the rest of the local network while still allowing outbound internet access, which is a safer default for a machine that will later run offensive security tools.

## What I Learned
- How VirtualBox's NAT mode routes VM traffic through the host, and why this is a safer default than Bridged mode for a security lab machine.
- The difference between minimal resource allocation (1 vCPU, 2 GB RAM) being sufficient for basic Kali usage versus what would be needed for heavier tasks like packet capture or password cracking.
- How to verify a Linux installation from the command line rather than relying only on the GUI, using tools like `uname`, `ip`, and `/etc/os-release`.
- The importance of documenting environment configuration clearly, since this VM will be the base environment for future labs in this internship.
