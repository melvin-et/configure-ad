<p align="center">
  <img src="https://github.com/user-attachments/assets/b7b4f74a-9292-44cb-be62-51027570cc9d" alt="Microsoft Active Directory Logo" width="200"/>
</p>

<h1 align="center">🏢 On-Premises Active Directory in the Azure Cloud</h1>

<p align="center"><i>A hands-on lab deploying Active Directory Domain Services (AD DS) in a simulated enterprise cloud environment using Microsoft Azure.</i></p>

---

## 🧠 Project Overview

This project demonstrates how to deploy and configure a fully operational **on-premises-style Active Directory** setup in Microsoft Azure. It includes:

- Virtual Network and Subnet Configuration
- Domain Controller Setup
- Client Machine Configuration
- DNS Integration
- User/Group Organizational Units
- Bulk User Creation with PowerShell
- Domain Join and RDP Access Validation

Perfect for learning enterprise-level IT infrastructure concepts hands-on — fully replicable in a free-tier Azure account.

---

## 🛠️ Step-by-Step Deployment

### 1. 🔧 Virtual Network Setup

<p align="center">
  <img src="https://github.com/user-attachments/assets/e55d8a59-3ecc-4126-bd61-f6a72605d711" alt="Network Diagram" width="500"/>
</p>

- Create a **Virtual Network** in Azure
- Add a subnet with IP range `192.168.0.0/24`

![Subnet creation](https://github.com/user-attachments/assets/6f508a04-f6c9-4e1a-8b18-8e0fa1b53ec7)

---

### 2. 🖥️ Domain Controller Deployment

- Create a **Windows Server VM** in the VNet
- Set a **static private IP** via NIC settings
- (Optional) Enable **Public IP** for RDP access

![Create domain controller](https://github.com/user-attachments/assets/018cd269-9e54-4072-a622-9a09714c3b59)

---

### 3. 💻 Client VM Configuration

- Create a **Windows 10/11 Pro VM**
- Use the same virtual network and subnet
- Set the **client's DNS** to the DC's static IP

![Client NIC config](https://github.com/user-attachments/assets/7e528fbb-81b9-4b51-a3f4-33b59ea9b548)

- Verify connectivity using `ping` and `ipconfig /all`

---

### 4. 🧩 Install & Configure Active Directory

- On the domain controller:
  - Install **Active Directory Domain Services**
  - Promote server to **Domain Controller** and create a **new forest**

![AD install](https://github.com/user-attachments/assets/9115468c-b6f3-4878-a4c4-08ecd091e93b)
![Forest](https://github.com/user-attachments/assets/72918066-f944-4dcd-a554-dd5be3c3cc91)

---

### 5. 🗂️ Organizational Units & User Setup

- In Active Directory Users and Computers:
  - Create 2 **OUs**: `Admins`, `Employees`
  - Create user `jane_admin` in `Admins`
  - Add Jane to the **Domain Admins** group

![Create user](https://github.com/user-attachments/assets/4fee8d28-a945-45e3-8787-fbf2486877a5)

---

### 6. 🔐 Join Domain from Client

- Log into client with local user
- Go to **System Settings > Join Domain**
- Use **Jane's credentials** to authenticate

![Join domain](https://github.com/user-attachments/assets/bd7c1522-b2a8-40c9-b0b3-7e3fc220f397)

- Allow RDP access to **Domain Users**

![RDP](https://github.com/user-attachments/assets/0570d4af-72c9-433d-ae90-2f5bf3c1493a)
---

## ⚡ Automate User Creation

Use my custom PowerShell script to generate **1,000+ test users** inside the `Employees` OU.

- 📄 [Generate-Names-Create-Users.ps1](https://github.com/melvin-et/configure-ad/blob/main/Generate-Names-Create-Users.ps1)

Steps:
1. Open **PowerShell ISE as Administrator** on the DC
2. Paste and run the script

![ISE as Admin](https://github.com/user-attachments/assets/02ef3b6f-fa56-4e5d-b2a6-edca566bd16d)
![Run script](https://github.com/user-attachments/assets/93ecf464-dfea-40d3-80d2-bb19fb002a93)

---

## ✅ Final Test

Select a newly created domain user and **log in via RDP** to the client machine.

- Confirm successful authentication and session start

![Logging In](https://github.com/user-attachments/assets/e6f13ae3-45bf-4615-9cb5-9362fb194137)
![RDP login success](https://github.com/user-attachments/assets/9c0b663c-adff-4a86-986d-c7861ca7a649)

---

## 📦 Skills Demonstrated

- Azure IaaS: Virtual Network, VM Deployment
- Active Directory Domain Services
- Windows Server Administration
- DNS & Networking Fundamentals
- PowerShell Scripting for Automation
- Enterprise IT Infrastructure Simulation

