# Cybersecurity HomeLab Set-up: Virtual Network with Multiple Machines

## Table of Contents
1. [Overview](#overview)
2. [Features](#features)
3. [Tools and Technologies](#tools-and-technologies)
4. [Lab Environment Setup](#lab-environment-setup)
    - [Requirements](#requirements)
    - [Network Diagram](#network-diagram)
    - [Installation](#installation)
6. [Usage](#usage)
6. [Results](#results)
7. [Contributing](#contributing)
8. [Conclusion](#license)
9. [Contact](#contact)

---

## Overview

This project focuses on creating a Cybersecurity Home Lab utilizing VirtualBox to establish a virtual network configured as a NAT Network. The lab consists of multiple virtual machines, including Kali Linux for penetration testing, Ubuntu for server configurations, and Windows for testing Windows-specific vulnerabilities. The NAT Network allows seamless internet access for the VMs while keeping them isolated from the host network, enhancing security and preventing unintended exposure. Within this environment, key security tools such as Metasploit, Nmap, and Wireshark are installed to facilitate hands-on learning experiences. The lab also can incorporates automation tools like Ansible and monitoring solutions like Zabbix to streamline operations and track network activities. 

  This setup provides an ideal platform for experimenting with real-world scenarios, including vulnerability assessments, threat detection, and incident response.



## Features

- **Multi-Machine Setup:** Deploy multiple virtual machines with different operating systems for comprehensive testing and learning.
- **Network Segmentation:** Utilize VLANs and firewalls to create isolated environments for secure testing of vulnerabilities and attacks.
- **Vulnerable Applications:** Implement intentionally vulnerable applications for hands-on practice in exploitation and remediation techniques.
- **Realistic Scenarios:** Create and simulate real-world cyber threats and incidents to develop incident response skills and improve security posture.


## Tools and Technologies

This project leverages the following tools and technologies:

- **Operating Systems:** Kali Linux, Ubuntu, Windows Server 2019
- **Penetration Testing Tools:** Metasploit, Nmap, Burp Suite, Aircrack-NG
- **Security Tools:** Snort, Suricata, pfSense Firewall, Fail2Ban
- **Monitoring Tools:** Zabbix, ELK Stack (Elasticsearch, Logstash, Kibana)
- **Vulnerability Scanners:** OpenVAS, Nikto, Nessus
- **Virtualization Platform:** VirtualBox, VMware Workstation
- **Languages:** Bash, Python

## Lab Environment Setup

### Requirements

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

### Installation

1. **Clone the repository:**
    ```bash
    git clone https://github.com/yourusername/projectname.git
    cd projectname
    ```

2. **Deploy Virtual Machines:**
    - Follow the instructions in the `setup/` folder to import the pre-configured VMs.
    - Alternatively, use Vagrant to automate the setup:
      ```bash
      vagrant up
      ```

3. **Configure Networking:**
    - Set up a virtual network as per the network diagram, with the firewall, internal network, and DMZ zones.

4. **Install Required Tools:**
    - Run the `install.sh` script in the `tools/` folder to install necessary penetration testing and defense tools on each machine.

    ```bash
    bash tools/install.sh
    ```

## Project Components

### Attack Vectors

- **Network Scanning:** Nmap and Zenmap were used to discover open ports and vulnerabilities in services.
- **Web Application Exploits:**
  - **SQL Injection:** Exploiting vulnerable web apps to bypass authentication.
  - **Cross-Site Scripting (XSS):** Injecting malicious scripts to hijack sessions.
- **Wireless Attacks:** Cracking WPA/WPA2 passwords using Aircrack-NG.

### Defense Mechanisms

- **Firewall Rules:** Configured pfSense with strict traffic rules between network zones.
- **IDS/IPS:** Implemented Snort/Suricata to detect suspicious activities in real-time.
- **Log Monitoring:** Deployed ELK stack to collect and analyze logs for threat detection.
- **Patch Management:** Automated security patches using Ansible for regular updates.

## Usage

Once the lab is set up, you can begin penetration testing and applying security measures:

1. **Launch the Attack:**
    - Run automated penetration testing scripts:
      ```bash
      bash attack/auto_attack.sh
      ```

2. **Monitor Defenses:**
    - Watch Snort or Suricata alerts in real-time:
      ```bash
      sudo tail -f /var/log/snort/alerts
      ```

3. **Analyze Logs:**
    - View collected logs in Kibana (access through your browser at `http://localhost:5601`).

4. **Generate Reports:**
    - Generate detailed vulnerability assessment reports using OpenVAS.

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

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact

If you have any questions or feedback, feel free to reach out:

- GitHub: [yourusername](https://github.com/yourusername)
- Email: youremail@example.com
