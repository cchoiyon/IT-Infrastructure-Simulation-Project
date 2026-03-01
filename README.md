# IT Infrastructure Simulation Project

Welcome to my enterprise IT and security Simulation! This project is a documentation of my journey building a corporate IT environment from scratch. Designed to simulate real-world infrastructure, this lab serves as a dedicated space for practicing system administration, security engineering, and network deployment.


## Project Overview

The goal of this simulation is to bridge the gap between theory and practice by deploying a fully functional Active Directory environment, configuring network security policies, and managing endpoints just like a modern enterprise.

Lab Specs/Notes
Three Servers
One server (Windows Server 2022) will act as the Domain Controller (DC), responsible for managing the Active Directory (AD) and handling authentication and authorization within the domain. 
The second server (Windows Server 2022) will be used for other purposes such as file storage, applications, or additional services required within the network. 
Additionally, a Linux server (Debian 12.5) will be implemented for monitoring purposes. This server will monitor the network and all devices within it. 
Four Client Machines 
These machines will be used to simulate end-user workstations within the network. Each machine will be joined to the domain controlled by the Domain Controller. 
Naming Convention 
Prefix: CHOIYONTECH
Client Identifier: PC 
Unique Number: 01, 02, 03, 04 
Detailed Naming List 
CHOIYONTECH-PC01 
CHOIYONTECH-PC02 
CHOIYONTECH-PC03 
CHOIYONTECH-PC04

---

## Phase 1: Laying the Foundation (Hyper-V Setup)

Before building the virtual domain, I needed a hypervisor to host it. I opted for Microsoft's native **Hyper-V** to manage the virtualization layer.

### 1.1 Unlocking Hyper-V
To get started, the built-in virtualization capabilities on the host machine needed to be awakened:
1. Navigated to **Control Panel > Programs > Programs and Features**.
2. Clicked on **Turn Windows features on or off**.
3. Checked the box for **Hyper-V**, hit OK, and rebooted the host machine to apply changes.

### 1.2 Architecting the Virtual Network
A lab is no good if the machines can't communicate.
1. Opened **Hyper-V Manager**.
2. Launched the **Virtual Switch Manager** from the Actions pane.
3. Created a new **External virtual switch** linked to my primary network adapter.
   * *Purpose:* This acts as the bridge, allowing VMs to securely access the physical network and the internet.
![Hyper V setup pic](./images/Picture1.png)





### Next Steps (in progress)
* [ ] Domain Configuration & Active Directory Integration
* [ ] DHCP & DNS Setup
* [ ] User & Group Policy Management
* [ ] Security Hardening
