
# Cybersecurity Lab Environment Setup
### Setting Up an Isolated Virtual Laboratory for Ethical Hacking and Penetration Testing

**Skill Area:** Cybersecurity  
**Network:** `10.0.0.0/24`  
**Hypervisor:** Oracle VirtualBox 7.2  
**Security Platform:** Kali Linux 2026.2  
**Author:** Olagunju Olakiitan Esther  

---

## 1. Project Overview
This project involves setting up a virtual cybersecurity and penetration-testing laboratory using Oracle VirtualBox and Kali Linux. 

The aim is to create a safe and controlled environment where cybersecurity skills can be practiced, including network scanning, reconnaissance, vulnerability assessment, and other authorized security-testing activities without affecting real-world systems. 

The laboratory is connected through a private virtual network, making it possible to expand the environment in the future by adding more virtual machines that can serve as authorized target systems for testing, analysis, and practical cybersecurity exercises.

---

## 2. Project Objectives
The main objectives of this project are to:
- Install and properly configure Oracle VirtualBox.
- Install or import Kali Linux as a virtual machine.
- Create a private NAT Network for the cybersecurity laboratory.
- Configure and test network connectivity on the Kali Linux virtual machine.
- Assign a consistent IP address to the Kali Linux VM.
- Verify that network connectivity and DNS resolution are working correctly.
- Create a clean virtual machine snapshot for recovery when required.
- Document the laboratory setup process clearly for future reference.
- Build a reliable environment that can be expanded for future cybersecurity projects and practical exercises.

---

## 3. Purpose of the Laboratory
The laboratory provides an isolated and controlled environment for cybersecurity learning and authorized security testing. The activities that can be performed within the laboratory include:
- Network reconnaissance
- Port scanning
- Vulnerability assessment
- Packet analysis
- Web security testing
- Exploitation practice
- Security-tool experimentation

### ⚠️ Ethical and Security Consideration
This laboratory and its tools must only be used for educational purposes and authorized security testing. Testing should be conducted only on systems that are personally owned or where explicit permission has been granted by the system owner.

---

## 4. Laboratory Architecture
The laboratory architecture consists of a Kali Linux virtual machine connected to a private NAT Network within Oracle VirtualBox. The network is designed so that additional target machines can be added to the same virtual network in future projects.

> ![Laboratory Architecture](LAB%20ARCHITECTURE%20(1).jpeg)


### Proposed Network Structure
- **Kali Linux:** `10.0.0.2`
- **Future Target Machines:** `10.0.0.3 – 10.0.0.99`
- **Network Subnet:** `10.0.0.0/24`
- **Gateway:** `10.0.0.1`

---

## 5. Laboratory Configuration

| Component | Configuration |
| :--- | :--- |
| **Host Operating System** | Windows 11 |
| **Host RAM** | 8 GB |
| **Processor** | Intel Core i5 |
| **Hypervisor** | Oracle VirtualBox 7.2 |
| **Security Operating System** | Kali Linux 2026.2 |
| **Kali Linux RAM** | 2048 MB |
| **Virtual Network** | NAT Network |
| **Network Address** | 10.0.0.0/24 |
| **Kali Linux IP Address** | 10.0.0.2/24 |
| **Default Gateway** | 10.0.0.1 |
| **DNS Server** | 8.8.8.8 |
| **Future VM Address Range** | 10.0.0.3 – 10.0.0.99 |

---

## 6. Laboratory Setup Procedure

### Step 1: Download and Install 7-Zip
7-Zip was downloaded and installed to extract the compressed Kali Linux virtual machine files. The software was required because the downloaded Kali Linux virtual machine package was highly compressed and needed to be extracted before it could be imported and used in Oracle VirtualBox.
![7-Zip Installation](DOWNLOAD%20%26%20INSTALL%20OF%207-ZIP(2).jpeg)


### Step 2: Download and Install Oracle VirtualBox
Oracle VirtualBox 7.2 was downloaded and installed as the hypervisor for creating and managing the virtual cybersecurity laboratory. VirtualBox provides the virtualization environment required to run Kali Linux and other virtual machines on the host computer.
![VirtualBox Installation](./Install%20Virtual%20box%20(3).jpeg)



### Step 3: Create the NAT Network
A standalone NAT Network was configured inside Oracle VirtualBox for the cybersecurity laboratory.

| Setting | Configuration |
| :--- | :--- |
| **Network Name** | NAT Network |
| **IPv4 Prefix** | 10.0.0.0/24 |
| **DHCP** | Enabled |
| **IPv6** | Disabled |




A NAT Network was selected because it provides a controlled virtual environment where multiple virtual machines can communicate with one another while also allowing external network access. This makes it suitable for building a multi-machine cybersecurity laboratory.

### Step 4: Import Kali Linux
Kali Linux version 2026.2 was downloaded from the official Kali Linux website and imported into Oracle VirtualBox 7.2. 

* **Virtual Machine Architecture:** Kali Linux 2026.2 – VirtualBox – AMD64

#### Kali Linux Network Adapter Configuration

| Setting | Configuration |
| :--- | :--- |
| **Adapter** | Adapter 1 |
| **Network Adapter** | Enabled |
| **Attached To** | NAT Network |
| **Network Name** | NAT Network |
| **Adapter Type** | Intel PRO/1000 MT Desktop (82540EM) |
| **Promiscuous Mode** | Allow All |

> 🖼️ *[INSERT KALI NETWORK ADAPTER IMAGE HERE]*

The virtual machine was allocated 2048 MB of RAM.

> 🖼️ *[INSERT KALI RAM CONFIGURATION IMAGE HERE]*

A shared folder was also configured to allow the transfer of required files between the host operating system and the Kali Linux virtual machine.

### Step 5: Configure the Kali Linux Network
The Kali Linux network settings were verified and configured with a static IPv4 address.

#### Network Configuration

| Setting | Configuration |
| :--- | :--- |
| **IPv4 Address** | 10.0.0.2 |
| **Subnet Mask** | 255.255.255.0 |
| **Default Gateway** | 10.0.0.1 |
| **DNS Server** | 8.8.8.8 |

> 🖼️ *[INSERT IP CONFIGURATION IMAGE HERE]*

Using a static IP address provides a consistent network address for the Kali Linux machine. This makes the laboratory easier to document, troubleshoot, and use during future cybersecurity exercises.

### Step 6: Create a Clean Virtual Machine Snapshot
After completing the initial configuration, a VirtualBox snapshot was created. The snapshot provides a recovery point that allows the virtual machine to be restored to its clean, working state if a configuration change or future cybersecurity exercise causes problems.

* **Snapshot Name:** `Set Up My Kali Linux`

> 🖼️ *[INSERT SNAPSHOT IMAGE HERE]*

---

## 7. Laboratory Verification
After completing the configuration, several tests were performed to confirm that the laboratory was functioning correctly.

| Test | Command Used | Result |
| :--- | :--- | :--- |
| Check IP Address | `ip a` | IP address displayed as 10.0.0.2 |
| Test Gateway | `ping 10.0.0.1` | Successful |
| Test Internet Connectivity | `ping 8.8.8.8` | Successful reply |
| Test DNS Resolution | `nslookup networkwalks.com` | Domain successfully resolved |
| Verify Nmap Installation | `nmap --version` | Nmap version 7.99 displayed |

> 🖼️ *[INSERT LAB VERIFICATION SCREENSHOT HERE]*

The successful results confirmed that the Kali Linux virtual machine was correctly connected to the virtual network, could communicate with the gateway, access the internet, resolve domain names, and use Nmap for network-security activities.

---

## 8. Problems Encountered and Solutions

### ❌ Problem 1: Virus Detection During 7-Zip Installation
During the installation of 7-Zip, Windows Security detected the MSI installer as a potential threat, which prevented the installation from proceeding.
* **✔️ Solution:** The issue was resolved by using the recommended 64-bit EXE installer instead of the MSI version.
> 🖼️ *[INSERT SCREENSHOT OF THE SECURITY WARNING HERE]*

### ❌ Problem 2: Unable to Open Kali Linux in VirtualBox
Kali Linux could not initially be opened in VirtualBox because the virtual machine files had been extracted using WinZip, which resulted in compatibility issues.
* **✔️ Solution:** The problem was resolved by extracting the Kali Linux files using 7-Zip. After the files were properly extracted, the virtual machine opened successfully in Oracle VirtualBox.

### ❌ Problem 3: Difficulty Accessing the Wired Network Connection
The wired network connection was initially inaccessible, which made it difficult to configure the network settings in Kali Linux.
* **✔️ Solution:** The issue was resolved by opening the Applications menu and navigating to Advanced Network Configuration. The connection permission was changed from *Deny* to *Allow All*. 

The following terminal command was also executed to resolve the network connection issue:
```bash
sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0
```
After applying these changes, the wired connection became accessible and functioned properly.

---

## 9. What I Learned
Through this project, I gained practical experience in setting up and configuring a cybersecurity laboratory for safe and controlled security practice.

1. **Proper Software Installation & Security Awareness:** I learned the importance of paying attention to security warnings during software installation and using trusted paths.
2. **Proper Extraction of VM Files:** I learned that file extraction tools matter, switching from WinZip to 7-Zip for proper compatibility.
3. **Network Configuration Troubleshooting:** Gained hands-on experience adjusting settings and changing network adapter permissions inside Kali.
4. **Using Command-Line Tools for Troubleshooting:** Learned to utilize `nmcli` in the Linux terminal to programmatically fix configuration timeouts.
5. **Understanding NAT vs. NAT Network:** Understood that standard NAT only gives the guest external internet, while a NAT Network allows peer-to-peer virtual environment communication.
6. **Manual IP Address Configuration:** Mastered configuring static configurations (`IP`, `Subnet`, `Gateway`, `DNS`) inside Linux environments.
7. **Virtual Machine Snapshots:** Learned how to save machine states as restore points before attempting risky security testing.
8. **Cybersecurity Documentation:** Understood that capturing commands, errors, and fixes is critical for tracking work and proving professional completions.

---

## 10. Security and Ethical Use
This laboratory was created for educational purposes and authorized cybersecurity testing. All security-testing activities carried out within the laboratory must follow ethical and legal requirements. 

The laboratory and its security tools must only be used against systems that are personally owned or where explicit authorization has been provided by the system owner.

### Tools & Resources
* [7-Zip Official Download Page](https://7-zip.org)
* [Oracle VirtualBox Official Download Page](https://virtualbox.org)
* [Kali Linux Official Download Page](https://kali.org)

---

## 11. Project Details
* **Program:** Cybersecurity at Networkwalks (Week 01)
* **Author:** Olagunju Olakiitan Esther
* **LinkedIn:** [Your LinkedIn Profile Link Here]

