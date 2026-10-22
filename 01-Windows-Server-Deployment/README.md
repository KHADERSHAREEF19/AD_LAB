# 🖥️ Lab 01: Windows Server 2016 Deployment

> **Project:** Active Directory Home Lab  
> **Lab 01:** Windows Server 2016 Deployment  
> **Status:** Completed

---

## 📌 Table of Contents

- [🎯 Objective](#-objective)
- [🧰 Lab Environment](#-lab-environment)
- [🛠️ Implementation Steps](#️-implementation-steps)
- [⌨️ Commands Used](#️-commands-used)
- [⚠️ Problems Faced and Solutions](#️-problems-faced-and-solutions)
- [📸 Screenshots](#-screenshots)
- [💡 Key Takeaways](#-key-takeaways)

---

## 🎯 Objective

Deploy a **Windows Server 2016 virtual machine** that will serve as the Domain Controller for the Active Directory Home Lab.

This server will later be used to configure Active Directory Domain Services (AD DS), manage domain users and computers, and practice centralized identity and access management.

## 🧰 Lab Environment

| Component | Configuration |
|---|---|
| Hypervisor | Oracle VirtualBox |
| Operating System | Windows Server 2016 Standard Evaluation |
| Installation Type | Desktop Experience (GUI) |
| RAM | 4 GB |
| CPU | 2 cores |
| Virtual Disk | 50 GB (VDI) |
| Network Adapter 1 | NAT |
| Network Adapter 2 | Internal Network (Lab Only) |

## 🛠️ Implementation Steps

### Step 1: Create the Virtual Machine

Created a new virtual machine in Oracle VirtualBox with the following configuration:

- Allocated 4 GB RAM.
- Assigned 2 CPU cores.
- Created a 50 GB virtual disk using the VDI format.

### Step 2: Configure the Installation Media

- Removed the VirtualBox unattended installation ISO.
- Attached the official Windows Server 2016 Evaluation ISO.
- Configured the VM to boot from the correct installation media.

### Step 3: Install Windows Server

- Started the Windows Server installation.
- Selected **Custom Installation**.
- Chose **Windows Server 2016 Standard Evaluation (Desktop Experience)**.
- Completed the installation process.

### Step 4: Configure the Administrator Account

- Set a password for the built-in Administrator account.
- Confirmed that the password met Windows Server's password complexity requirements.
- Kept the password out of the GitHub repository.

### Step 5: Install VirtualBox Guest Additions

Installed VirtualBox Guest Additions to improve the virtual machine experience, including display resizing and supported integration features.

### Step 6: Verify the Installation

Confirmed that Windows Server booted successfully and that the graphical desktop was accessible.

## ⌨️ Commands Used

No command-line commands were required for this lab.

The deployment was completed using the Windows Server installer and Oracle VirtualBox graphical interface.

## ⚠️ Problems Faced and Solutions

| Problem | Cause | Solution |
|---|---|---|
| `Windows cannot find the Microsoft Software License Terms` | The VirtualBox unattended installation ISO was attached. | Removed the unattended ISO and attached the correct Windows Server installation ISO. |
| Password rejected (`1234`) | The default password complexity requirements were enabled. | Set a stronger password containing uppercase and lowercase letters, numbers, and symbols. |
| `Ctrl + Alt + Delete` affected the host PC | The keyboard shortcut was sent to the host operating system. | Used **Input → Keyboard → Insert Ctrl+Alt+Del** in VirtualBox. |

## 📸 Screenshots

| Screenshot | Description |
|---|---|
| `assets/01-VM-Configuration.png` | Virtual machine hardware configuration, including RAM, CPU, and disk allocation. |

> **Note:** Store screenshots in the `assets/` directory and ensure that the filenames match the references above.

## 💡 Key Takeaways

- **Desktop Experience:** Choose this option when you need a graphical interface and tools such as Server Manager.
- **Installation Media:** Verify that the correct ISO is attached before starting the installation.
- **Password Security:** Use a strong Administrator password and never commit credentials to a public repository.
- **Virtualization:** Understand the VM's hardware allocation and network adapter configuration before deploying server roles.
- **Lab Isolation:** An Internal Network adapter allows communication between lab VMs without directly exposing that network to the external network.
- **Active Directory Preparation:** A working Windows Server installation is the foundation for configuring a Domain Controller in the next lab.

---

## 🚀 Next Steps

In the next lab, configure the server's hostname and static IP address, install **Active Directory Domain Services (AD DS)**, and promote the server to a Domain Controller.

