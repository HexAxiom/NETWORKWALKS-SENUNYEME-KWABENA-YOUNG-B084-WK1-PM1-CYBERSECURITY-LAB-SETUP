# NETWORKWALKS CYBERSECURITY INTERNSHIP 2026

**Building an isolated virtual lab for penetration testing and ethical hacking practice**

![Cybersecurity](https://img.shields.io/badge/Skill-Cybersecurity-red)
![VirtualBox](https://img.shields.io/badge/VirtualBox-7.2.22-blue?logo=virtualbox)
![Kali Linux](https://img.shields.io/badge/Kali_Linux-2026.3-557C94?logo=kalilinux\&logoColor=white)
![Linux](https://img.shields.io/badge/Skill-Linux-black?logo=linux)
![Network](https://img.shields.io/badge/Network-10.0.0.0%2F24-green)
![Virtualization](https://img.shields.io/badge/Skill-Virtualization-blue)
![Penetration Testing](https://img.shields.io/badge/Penetration-Testing-orange)
![Ethical Hacking](https://img.shields.io/badge/Ethical-Hacking-red)
![NetworkWalks](https://img.shields.io/badge/NetworkWalks-Cybersecurity_Internship-blue)
![GitHub](https://img.shields.io/badge/Platform-GitHub-black?logo=github)
![Project](https://img.shields.io/badge/Project-WK1--PM1-informational)
![Participant](https://img.shields.io/badge/Participant-Senunyeme_Kwabena_Young-success)

---

## Project Information

| Project Information     | Details                                    |
| :---------------------- | :----------------------------------------- |
| Participant Name        | SENUNYEME KWABENA YOUNG                    |
| Programme               | NetworkWalks Cybersecurity Internship 2026 |
| Batch                   | B084                                       |
| Project Code            | WK1-PM1                                    |
| Project Title           | Lab Setup VirtualBox and Kali Linux v4.2   |
| Virtualization Platform | Oracle VirtualBox 7.2.22                   |
| Attacking Machine       | Kali Linux 2026.3                          |

---

## 1. Project Overview

This project involved designing and setting up a virtual cybersecurity laboratory using Oracle VirtualBox and Kali Linux.

The objective was to establish a functional virtual environment for cybersecurity learning, ethical hacking practice, and future security testing exercises.

The laboratory uses a VirtualBox NAT Network with the required `10.0.0.0/24` subnet. Kali Linux was configured as the attacking machine with a static IP address, internet connectivity, shared-folder access, and bidirectional clipboard and drag-and-drop functionality.

## 2. Project Objectives

The main objectives were to:

* Install and configure Oracle VirtualBox.
* Create a NAT Network using the `10.0.0.0/24` subnet.
* Download and import a Kali Linux virtual machine.
* Configure Kali Linux with the required static IP address.
* Enable clipboard sharing and file drag-and-drop.
* Configure a shared folder between the host operating system and Kali Linux.
* Establish and verify internet connectivity.
* Create a VirtualBox snapshot after completing the initial setup.

## 3. Tools and Technologies Used

| Tool / Technology        | Purpose                                           |
| :----------------------- | :------------------------------------------------ |
| Oracle VirtualBox 7.2.22 | Virtualization platform                           |
| Kali Linux 2026.3        | Attacking and security testing machine            |
| 7-Zip                    | Extracting the Kali Linux virtual machine archive |
| VirtualBox NAT Network   | Virtual network configuration                     |
| NetworkManager (`nmcli`) | Network connection troubleshooting                |
| Windows                  | Host operating system                             |

## 4. Lab Architecture and Network Configuration

The laboratory was configured using a VirtualBox NAT Network.

### Network Configuration

| Configuration         | Value           |
| :-------------------- | :-------------- |
| Network Type          | NAT Network     |
| Network Name          | `NatNetwork`    |
| Network Subnet        | `10.0.0.0/24`   |
| DHCP                  | Enabled         |
| Kali Linux IP Address | `10.0.0.2/24`   |
| Subnet Mask           | `255.255.255.0` |
| Default Gateway       | `10.0.0.1`      |
| DNS Server            | `8.8.8.8`       |

### Virtual Machine Network Settings

The Kali Linux virtual machine was configured with:

* **Network Adapter:** Enabled
* **Attached to:** NAT Network
* **Network Name:** `NatNetwork`
* **Promiscuous Mode:** Allow All
* **Cable Connected:** Enabled

### Virtual Machine Integration Settings

The following integration settings were enabled:

* **Shared Clipboard:** Bidirectional
* **Drag'n'Drop:** Bidirectional

### Shared Folder Configuration

A shared folder was configured to allow file sharing between the Windows host and Kali Linux.

| Setting     | Configuration                |
| :---------- | :--------------------------- |
| Folder Name | `downloads`                  |
| Host Folder | `NetworkWalks-Lab/downloads` |
| Auto-mount  | Enabled                      |
| Read-only   | Disabled                     |

The shared folder was successfully mounted and appeared in the Kali Linux desktop environment.

## 5. Lab Setup Procedure

The following steps were completed during the setup.

### Step 1: Install 7-Zip

Downloaded and installed 7-Zip to extract the Kali Linux virtual machine archive.

### Step 2: Install Oracle VirtualBox

Installed Oracle VirtualBox 7.2.22 and the matching VirtualBox Extension Pack.

### Step 3: Configure the NAT Network

Created a NAT Network named `NatNetwork` with the IPv4 subnet:

`10.0.0.0/24`

DHCP was enabled.

### Step 4: Download and Import Kali Linux

Downloaded the Kali Linux 2026.3 prebuilt VirtualBox image, extracted the archive, and imported the virtual machine into VirtualBox.

### Step 5: Configure Kali Linux Networking

Configured the Kali Linux network interface with the required static IPv4 settings:

* **IP Address:** `10.0.0.2`
* **Netmask:** `255.255.255.0`
* **Gateway:** `10.0.0.1`
* **DNS:** `8.8.8.8`

### Step 6: Configure Virtual Machine Integration

Enabled bidirectional clipboard sharing, bidirectional drag-and-drop, and the shared `downloads` folder.

### Step 7: Verify Connectivity and Create Snapshot

Tested network connectivity and DNS resolution. After successful verification, shut down Kali Linux and created a VirtualBox snapshot named:

`Kali-Linux-Clean-Setup`

## 6. Network Configuration and Connectivity Verification

Network configuration was verified using the Kali Linux terminal.

### Verify IP Address

```bash
ip -4 addr show eth0
```

The interface was confirmed to be UP with the required address:

`10.0.0.2/24`

### Verify Default Gateway

```bash
ip route
```

The default route was confirmed to use:

`10.0.0.1`

### Test Internet Connectivity

```bash
ping -c 4 8.8.8.8
```

The test completed successfully with four packets received and 0% packet loss.

### Test DNS Resolution

```bash
ping -c 4 google.com
```

The domain resolved successfully, and all four packets were received with 0% packet loss.

These tests confirmed IP connectivity and DNS resolution.

## 7. Troubleshooting and Solutions

### Problem: Kali Linux Network Connection Issue

During the initial network configuration, the Kali Linux network connection did not become active after setting the required static IP address.

### Solution

Following the troubleshooting instructions in the project guide, I used the following commands to modify and restart the NetworkManager connection.

**1. Modify the connection settings:**

```bash
sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0
```

**2. Disconnect the network connection:**

```bash
sudo nmcli connection down "Wired connection 1"
```

**3. Reactivate the network connection:**

```bash
sudo nmcli connection up "Wired connection 1"
```

After executing the commands successfully, the network interface became active.

I subsequently verified the IP address, default gateway, internet connectivity, and DNS resolution.

### Lesson Learned

This troubleshooting experience improved my understanding of Linux network configuration and the use of NetworkManager to resolve virtual machine connectivity issues.

## 8. Project Evidence and Screenshots

The following screenshots document the configuration and verification of the virtual laboratory.

### 1. NAT Network Configuration

![NAT Network Configuration](01-nat-network.png)

### 2. Kali Linux Network Adapter

![Kali Network Adapter](02-kali-network-adapter.png)

### 3. Clipboard and Drag-and-Drop Settings

![Clipboard and Drag-and-Drop](03-kali-clipboard-dragdrop.png)

### 4. Shared Folder Configuration

![Shared Folder Configuration](04-kali-shared-folder.png)

### 5. Kali Linux IP Configuration

![Kali IP Configuration](05-kali-ip-configuration.png)

### 6. Internet Connectivity Verification

![Internet Connectivity](06-kali-internet-connectivity.png)

### 7. VirtualBox Snapshot

![Kali Snapshot](07-kali-snapshot.png)

## 9. Virtual Machine Snapshot

After completing the initial configuration and verifying connectivity, a VirtualBox snapshot named `Kali-Linux-Clean-Setup` was created.

The snapshot preserves the initial working laboratory configuration and provides a recovery point for future practical exercises.

## 10. Security and Ethical Considerations

This laboratory was established for educational purposes and authorized cybersecurity practice.

All security testing activities will be conducted only within systems and virtual environments that I own or have explicit permission to test.

## 11. Learning Outcomes

Through this project, I gained practical experience in:

* Installing and configuring virtualization software.
* Creating and configuring VirtualBox NAT Networks.
* Importing prebuilt Kali Linux virtual machines.
* Configuring static IPv4 addresses and default gateways.
* Using Linux NetworkManager for network troubleshooting.
* Enabling shared folders between host and guest operating systems.
* Configuring bidirectional clipboard and drag-and-drop.
* Testing IP connectivity and DNS resolution.
* Creating and managing virtual machine snapshots.
* Documenting technical configurations and troubleshooting procedures.

## 12. Conclusion

The initial cybersecurity laboratory was successfully established using Oracle VirtualBox and Kali Linux.

The required NAT Network, static IP configuration, shared folder, clipboard integration, internet connectivity, and virtual machine snapshot were configured and verified.

This laboratory provides a foundation for future cybersecurity practical exercises and security testing activities.

---

## Author Information

**Name:** SENUNYEME KWABENA YOUNG
**Programme:** NetworkWalks Cybersecurity Internship 2026
**Batch:** B084
**Project:** WK1-PM1 – Lab Setup VirtualBox and Kali Linux

**Project Repository:** NetworkWalks Cybersecurity Internship 2026 – Week 1
