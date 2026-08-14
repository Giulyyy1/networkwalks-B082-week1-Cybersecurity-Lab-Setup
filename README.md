# networkwalks-B082-week1-Cybersecurity-Lab-Setup
**Installation and Setup of Kali Linux on VirtualBox**


![Kali Linux](https://img.shields.io/badge/Kali%20Linux-2026.1-557C94?style=for-the-badge&logo=kalilinux&logoColor=white)




![VirtualBox](https://img.shields.io/badge/VirtualBox-7.x-183A61?style=for-the-badge&logo=virtualbox&logoColor=white)




![Linux](https://img.shields.io/badge/Linux-111827?style=for-the-badge&logo=linux&logoColor=white)




![Networking](https://img.shields.io/badge/Networking-0891B2?style=for-the-badge&logo=cisco&logoColor=white)




![NAT Network](https://img.shields.io/badge/NAT%20Network-10.0.0.0%2F24-0891B2?style=for-the-badge)




![Virtualization](https://img.shields.io/badge/Virtualization-183A61?style=for-the-badge&logo=virtualbox&logoColor=white)
# Week 1 Lab: Kali Linux Installation & Setup

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
**Step 1: Download & Install 7-Zip**

7-Zip is a free file archiver used to extract compressed files (like .7z or .zip) that Kali Linux images are often packaged in. It's needed before you can unpack the downloaded VM files.
https://7-zip.org/download.html  

![image alt](https://github.com/Giulyyy1/networkwalks-B082-week1-Cybersecurity-Lab-Setup/blob/42bca5b38bbea1889fddb74049e3272ac6a74e90/Screenshot%202026-08-13%20085044.png)

**Step 2: Download & Install VirtualBox**

VirtualBox is a free hypervisor (virtualization software) that lets you run a full operating system, like Kali Linux, inside a virtual machine on your existing PC without affecting your main OS.
 https://virtualbox.org/wiki/Downloads

![image alt](https://github.com/Giulyyy1/networkwalks-B082-week1-Cybersecurity-Lab-Setup/blob/42bca5b38bbea1889fddb74049e3272ac6a74e90/Screenshot%202026-08-13%20085141.png)

**Step 3: Configure Network Settings (NAT Network, 10.0.0.0/24)**

A NAT Network in VirtualBox creates an isolated internal network for your VM(s) that still allows outbound internet access through the host machine. Setting it to the 10.0.0.0/24 range defines the pool of private IP addresses (10.0.0.1 to 10.0.0.254) available to any VM connected to it, keeping the VM separated from your actual home/office network for safer testing.

![image alt](https://github.com/Giulyyy1/networkwalks-B082-week1-Cybersecurity-Lab-Setup/blob/42bca5b38bbea1889fddb74049e3272ac6a74e90/Screenshot%202026-08-12%20223935.png)

**Step 4: Download & Import Kali Linux VM**

Instead of installing Kali from an ISO, this step uses a pre-built VirtualBox VM image from Kali's official site (https://kali.org/get-kali). This is a faster path since the OS is already configured and just needs to be imported into VirtualBox.

![image alt](https://github.com/Giulyyy1/networkwalks-B082-week1-Cybersecurity-Lab-Setup/blob/4a3feba94d2809d769d4e882b0221e942ab33baf/Screenshot%202026-08-13%20092054.png)

After selecting the kali Linux VM for VirtualBox and installing it, I opened the virtual machine(Kali Linux) to ensure it was properly installed 

![image alt](https://github.com/Giulyyy1/networkwalks-B082-week1-Cybersecurity-Lab-Setup/blob/144129f7ac42d6247af50bcdd07e647871a3b048/Screenshot%202026-08-12%20222652.png)

**Step 5: Setup IP Configuration**

This is where the Kali VM is connected to the NAT Network created in Step 3 and assigned an IP address within that range, so it can communicate on the virtual network and reach the internet.

![image alt](https://github.com/Giulyyy1/networkwalks-B082-week1-Cybersecurity-Lab-Setup/blob/24b56cc8c82af553682b8412630f79541fd96564/Screenshot%202026-08-12%20124525.png)

**Step 6: Take Snapshot of the VM**

A snapshot saves the exact state of the VM at that point in time. Taking one after a clean, working setup means you can always roll back to this baseline if something breaks in a later lab, without having to reinstall from scratch.

![image alt](https://github.com/Giulyyy1/networkwalks-B082-week1-Cybersecurity-Lab-Setup/blob/144129f7ac42d6247af50bcdd07e647871a3b048/Screenshot%202026-08-12%20235953.png)


## Verification Commands and Results

To confirm the VM was correctly installed and networked, the following commands were run inside the Kali terminal:

```bash
uname -a
```
Confirms the kernel version and system architecture.

![image alt](https://github.com/Giulyyy1/networkwalks-B082-week1-Cybersecurity-Lab-Setup/blob/70f0578124443a414946c5359de0cdefc107b189/Screenshot%202026-08-13%20102018.png)

```bash
cat /etc/os-release
```
Confirms the installed OS is Kali Linux 2026.1.

![image alt](https://github.com/Giulyyy1/networkwalks-B082-week1-Cybersecurity-Lab-Setup/blob/70f0578124443a414946c5359de0cdefc107b189/Screenshot%202026-08-13%20102202.png)


```bash
ip a
```
Confirms the VM received an IP address (10.0.0.2) from the NAT gateway (10.0.0.1), verifying network connectivity.

![image alt](https://github.com/Giulyyy1/networkwalks-B082-week1-Cybersecurity-Lab-Setup/blob/70f0578124443a414946c5359de0cdefc107b189/Screenshot%202026-08-13%20101924.png)

```bash
sudo apt update && sudo apt upgrade -y
```
Confirms the system can reach package repositories and applies the latest updates.

![image alt](https://github.com/Giulyyy1/networkwalks-B082-week1-Cybersecurity-Lab-Setup/blob/920e066f3c02f51ac92aaa2929bbc4add30173f6/Screenshot%202026-08-13%20104214.png)

## Problems Faced
My virtual machine didn't have internet access after adding it to the NAT network and this was the command i used to resolve it

```bash
sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0
```
Aside from that, the setup went smoothly. The main point worth noting was deciding on NAT rather than Bridged networking. 
**Reason For NAT:**
NAT was chosen because it keeps the VM isolated from the rest of the local network while still allowing outbound internet access, which is a safer default for a machine that will later run offensive security tools.

## What I Learned
- How VirtualBox's NAT mode routes VM traffic through the host, and why this is a safer default than Bridged mode for a security lab machine.
- The difference between minimal resource allocation (1 vCPU, 2 GB RAM) being sufficient for basic Kali usage versus what would be needed for heavier tasks like packet capture or password cracking.
- How to verify a Linux installation from the command line rather than relying only on the GUI, using tools like `uname`, `ip`, and `/etc/os-release`.
- The importance of documenting environment configuration clearly, since this VM will be the base environment for future labs in this internship.
- Taking a **snapshot** before hacking or making changes teaches you about system restoration and disaster recovery
- Modern OS require **UEFI** while older OS require **Legacy BIOS**
- We use a **Type 2 Hypervisor** because Kali Linux is an OS that focuses on **Offensive** and less of defensive measures, meaning its more vulnerable to attack, so that ensures a safe space for kali
