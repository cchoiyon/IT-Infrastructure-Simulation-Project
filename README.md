# IT Infrastructure Simulation Project

Welcome to my enterprise IT and security Simulation! This project is a documentation of my journey building a corporate IT environment from scratch. Designed to simulate real-world infrastructure, this lab serves as a dedicated space for practicing system administration, security engineering, and network deployment.


## Project Overview

The goal of this simulation is to bridge the gap between theory and practice by deploying a **fully functional Active Directory environment**, configuring network security policies, and managing endpoints just like a modern enterprise. This project serves as a comprehensive documentation of my progress in learning IT infrastructure and administration.

---

## Lab Specifications & Infrastructure

The environment consists of a hybrid architecture including Windows Server 2022 and Linux Debian distributions to simulate a real-world corporate network.

| Component | Operating System | Primary Role |
| :--- | :--- | :--- |
| **Server 01** | Windows Server 2022 | **Domain Controller (DC):** Responsible for managing Active Directory (AD) and handling authentication/authorization within the domain. |
| **Server 02** | Windows Server 2022 | **Utility Server:** Used for file storage, applications, or additional services required within the network. |
| **Server 03** | Linux (Debian 12.5) | **Monitoring Node:** Implemented to monitor the network and all devices within it. |
| **Workstations**| Windows Clients   | **Client Machines:** Four workstations joined to the domain to simulate end-user environments. |

---

## Naming Convention

To maintain organizational standards and ensure asset traceability, all client machines follow a strict naming convention.

* **Prefix:** `CHOIYONTECH` 
* **Client Identifier:** `PC`
* **Unique Sequence:** `01`, `02`, `03`, `04`

**Detailed Asset List:**
* `CHOIYONTECH-PC01`
* `CHOIYONTECH-PC02`
* `CHOIYONTECH-PC03`
* `CHOIYONTECH-PC04` 

---

---

## Phase 1: Laying the Foundation (Hyper-V Setup)

Before building the virtual domain, I needed a hypervisor to host it. I opted for Microsoft's native **Hyper-V** to manage the virtualization layer.

### 1.1 Unlocking Hyper-V
To get started, the built-in virtualization capabilities on the host machine needed to be awakened:
1. Navigated to **Control Panel > Programs > Programs and Features**.
2. Clicked on **Turn Windows features on or off**.
3. Checked the box for **Hyper-V**, hit OK, and rebooted the host machine to apply changes.
<img src="./images/Picture1.png" alt="hyper v" pic width="400">


### 1.2 Creating the Virtual Network (NAT)
To allow the lab environment to communicate internally while sharing the host’s internet connection, I configured a **NAT (Network Address Translation)** virtual switch via PowerShell.

1. **Initialize the Internal Switch:**
   Using an elevated PowerShell session, I created a new internal switch named `LabNAT`.
   ```powershell
   New-VMSwitch -Name "LabNAT" -SwitchType Internal
<img src="./images/pic2.png" alt="powershellpic" pic width="400">


---

## Phase 2: Virtual Machine Provisioning

With the networking foundation in place, the next phase involves deploying the core virtual machines that make up the infrastructure.

### 2.1 Provisioning the Domain Controller (DC01)
The first system deployed is the **Domain Controller (DC01)**, which will eventually manage Active Directory, DNS, and DHCP services for the `CHOIYONTECH` environment.

1. **Naming and Location:**
   I named the virtual machine `DC01` and designated a specific storage directory at `C:\Hyper-V\VMs\` to keep the project files organized and separate from the default system drive.
<img src="./images/pic3.png" alt="pic3" width="400">

2. **Specifying Generation:**
   I selected **Generation 1** for this virtual machine to ensure maximum compatibility with the legacy BIOS requirements often found in diverse lab environments and older software configurations.
<img src="./images/pic4.png" alt="pic4" width="400">

3. **Memory Allocation:**
   I allocated **4096 MB (4 GB)** of startup memory to ensure smooth performance during the Windows Server 2022 installation and subsequent Active Directory promotion. I also enabled **Dynamic Memory** to allow the host to reclaim unused RAM when the server is idle.
<img src="./images/pic5.png" alt="pic4" width="400">

---

## Progress Tracker & Next Steps

* [x] Unlocking Hyper-V & Virtualization
* [x] NAT Virtual Switch & Networking Foundation
* [x] **Initial VM Provisioning (DC01 Configured)**
* [ ] Configuring Virtual Hard Disk (VHDX)
* [ ] Windows Server 2022 OS Installation
* [ ] Static IP Configuration for DC01
* [ ] Domain Configuration & Active Directory Integration
