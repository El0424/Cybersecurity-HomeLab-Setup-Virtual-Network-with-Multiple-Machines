# Cybersecurity HomeLab Set-up: Virtual Network with Multiple Machines

## Table of Contents
1. [Overview](#overview)
2. [Features](#features)
3. [Tools and Technologies](#tools-and-technologies)
4. [Lab Environment Setup](#lab-environment-setup)
    - [Prerequisites](#prerequisites)
    - [Network Diagram](#network-diagram)
    - [Installation and Setup](#installation-and-setup)
5. [Results](#results)
6. [Contributing](#contributing)
7. [Conclusion](#conclusion)
8. [Contact](#contact)

---

## Overview

This project focuses on creating a Cybersecurity Home Lab utilizing VirtualBox to establish a virtual network configured as a NAT Network. The lab consists of multiple virtual machines, including Kali Linux for penetration testing, Ubuntu/CentOS for server configurations, and Windows for testing Windows-specific vulnerabilities. The NAT Network allows seamless internet access for the VMs while keeping them isolated from the host network, enhancing security and preventing unintended exposure. Within this environment, key security tools such as Metasploit, Nmap, and Wireshark are installed to facilitate hands-on learning experiences. The lab also can incorporates automation tools like Ansible and monitoring solutions like Zabbix to streamline operations and track network activities. 

  This setup provides an ideal platform for experimenting with real-world scenarios, including vulnerability assessments, threat detection, and incident response.



## Features

- **Multi-Machine Setup:** Deploy multiple virtual machines with different operating systems for comprehensive testing and learning.
- **Network Segmentation:** Utilize VLANs and firewalls to create isolated environments for secure testing of vulnerabilities and attacks.
- **Vulnerable Applications:** Implement intentionally vulnerable applications for hands-on practice in exploitation and remediation techniques.
- **Realistic Scenarios:** Create and simulate real-world cyber threats and incidents to develop incident response skills and improve security posture.


## Tools and Technologies

This project leverages the following tools and technologies:

- **Operating Systems:** Kali Linux, Ubuntu, CentOS, Windows Server 2022
- **Penetration Testing Tools:** Nmap
- **Security Tools:** Firewall
- **Virtualization Platform:** VirtualBox, VMware Workstation
- **Languages:** Bash, Powershell, Python

## Lab Environment Setup

### Prerequisites

- **Basic Knowledge of Computer Networking**
- **Virtualization Platform:** VirtualBox or VMware Workstation
- **Minimum Hardware:**
  - 16 GB RAM
  - 200 GB Disk space
  - Quad-core CPU

### Network Diagram

![Network Diagram](path/to/your/network-diagram.png)

The lab consists of:

- **Attack VM:** Kali Linux
- **Target VM:** Ubuntu Server with vulnerable web applications
- **Firewall:** pfSense configured between the attacker and target network
- **IDS/IPS:** Snort/Suricata monitoring traffic between segments

### Installation and Setup


**Step 1: Install Virtualization Software**
   
1. **Install VirtualBox**

Open the link [Download Virtualbox](https://www.virtualbox.org/wiki/Downloads) and download your OS installer (VirtualBox for MacOS/WindowsOS/Linux)

2. **Install VirtualBox:**

- **Windows:** Double-click the downloaded `.exe` file and follow the on-screen instructions.
- **macOS:** Double-click the downloaded `.dmg` file, then move the VirtualBox icon to your Applications folder.
- **Linux:** Use your system's package manager to install VirtualBox. For example, on Ubuntu, you would run:


  ```bash
  sudo apt update
  sudo apt install virtualbox

3. **Install VirtualBox Extension Pack:**
    - **Download the Extension Pack:** Go to the [Download VirtualBox](https://www.virtualbox.org/wiki/Downloads) and find the Extension Pack.
   - **Open VirtualBox:** Launch the VirtualBox software.
   - **Access Preferences:** Go to `File > Preferences > Extensions`.
   - **Add New Package:** Click the **Add New Package** button, select the downloaded Extension Pack, and install it.


**Step 2: Create Virtual Machines (VMs)**

1. **Download OS Images:**
   - **Ubuntu:** Download the Ubuntu desktop image from [Download Ubuntu](https://ubuntu.com/download/desktop).
   - **Kali Linux:** Download Kali Linux from [Download Kali Linux](https://www.kali.org/downloads/).
   - **Windows(optional): Download Windows Evaluation Versions from [Download Windows Evaluation Versions](https://www.microsoft.com/en-us/evalcenter)

2. **Create a New Virtual Machine**
   - **Open VirtualBox**: Launch the VirtualBox software.
   - **Click New**: Click the New button to create a new virtual machine.
   - **Name and Configure**:
   - **Name**: Give your VM a name (e.g., "Ubuntu", "Kali").
   - **Type and Version**: Select Linux as the type and choose the appropriate version (Ubuntu or Debian for Kali).
   - **Memory**: Allocate at least 2GB of RAM (4GB or more recommended if possible).
   - **Hard Disk**: Create a new virtual hard disk with at least 20GB of storage.

3. **Install the Operating System**
   -**Start the VM**: Start the newly created VM.
   -**Select ISO File**: Choose the downloaded ISO image of your desired operating system (Ubuntu or Kali Linux) as the startup disk.
   -**Follow Installation Instructions**:
   - **Language and Keyboard**: Select your preferred language and keyboard layout.
   - **Partitioning**: Choose the default partitioning scheme unless you have specific requirements.
   - **User Account**: Create a user account and set a password.
   - **Installation Completion**: Complete the installation process and reboot the VM.


**Step 3: Set Up Networking**

1. **Configure Network Settings**:
   - **Open Settings**: Go to `Settings > Network`.
   - **Attach to Network**: For direct access to your home network, choose a Bridged Adapter. For a private network, select NAT Network. We'll use NAT Network for this tutorial.
   
2. **Create a NAT Network**:
   - **Open Preferences**: Go to `File > Preferences > Network`.
   - **Add NAT Network**: Click the NAT Networks tab, then click Add.
   - **Configure Settings**: Configure the NAT network settings (e.g., 10.0.2.0/24).
   
3. **Connect VM to NAT Network**:
   - **Open VM Settings**: Go to the settings of each VM (`Settings > Network > Adapter 1`).
   - **Select NAT Network**: Choose Attached to: NAT Network and select the created NAT network.


**Step4 4: Install and Configure Tools**

1. **Ubuntu  Virtual Machine**
   - **Update the system:** Ensure your system is up-to-date using:
   
```bash
      sudo apt update && sudo apt upgrade -y
   ```
   - **Install essential tools:**

```bash
    sudo apt install -y build-essential git curl wget
```
2. **Kali Linux Virtual Machine**
   - **Update the system:**
     
```bash
    sudo apt update && sudo apt upgrade -y
```
   - **Install additional tools (optional):**

```bash
    sudo apt install -y nmap wireshark metasploit-framework
```

**Step 5: Simulate Network Attacks and Defenses**

1. **Simulate an Attack**
   - Use Kali Linux: On your Kali Linux VM, perform a basic network scan against the Ubuntu VM:
     
 ```bash
     nmap -A 10.0.2.15
```
***(replace 10.0.2.15 with the actual IP of your Ubuntu VM)***

2. **Defend Against Attacks**
   
 ```bash
   sudo apt install ufw
   sudo ufw enable
   sudo ufw allow ssh
   sudo ufw allow from 10.0.2.16
```
3. **Analyze Network Traffic**
   - **Install Wireshark**
On your Ubuntu VM, install Wireshark using the following command:
```bash
sudo apt install wireshark
sudo wireshark
```

**Step 6: Document Your Setup**

1. **Network Diaagram**
   - **Create a visual representation of your virtual network using a diagramming tool like [draw.io](https://www.draw.io).**
   - **Include IP addresses and machine names for clarity.**

2. **Configuration Details**
   - **Record the configurations and settings for each VM, including network settings, installed tools, and any specific changes made.**


## Results

This project successfully demonstrates:

- The ability to exploit various vulnerabilities and simulate attacks in a secure, isolated environment.
- Deployment of defense mechanisms that effectively detect, block, and log malicious activities.
- Automated scripts that enhance both offensive and defensive cybersecurity capabilities.

The results include detailed reports on vulnerabilities found and how they were mitigated, as well as lessons learned from improving network security.

## Contributing

Contributions are welcome! If you'd like to contribute to this project, please follow the steps below:

1. Fork the repository.
2. Create a new branch:
```bash
    git checkout -b feature-branch
```
3. Commit your changes:
 ```bash
    git commit -m "Add your message"
 ```
4. Push the branch:
 ```bash
    git push origin feature-branch
 ```
5. Open a Pull Request.

Please make sure your code follows the project's coding standards and passes all tests.

## Conclusion

**Setting up a cybersecurity home lab with a virtual network and multiple machines offers a robust platform for enhancing your cybersecurity skills in a controlled environment. This project allows you to experiment with various operating systems, security tools, and network configurations, enabling hands-on experience with real-world scenarios. By engaging in penetration testing, incident response exercises, and network monitoring, you'll gain invaluable insights and practical knowledge that will prepare you for a successful career in cybersecurity. Whether you're a beginner or an experienced professional, this home lab serves as a versatile and flexible space for continuous learning and skill development.**

## Contact

If you have any questions or feedback, feel free to reach out:

- GitHub: [yourusername](https://github.com/yourusername)
- Email: youremail@example.com
