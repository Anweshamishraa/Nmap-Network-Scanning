# 🔍 Network Scanning Using Nmap

![Nmap](https://img.shields.io/badge/Tool-Nmap-blue) ![Kali Linux](https://img.shields.io/badge/Platform-Kali%20Linux-purple) ![Cybersecurity](https://img.shields.io/badge/Domain-Cybersecurity-red)

## 📌 Project Overview

This project demonstrates network reconnaissance using Nmap in a controlled cybersecurity lab environment. It covers host discovery, port scanning, service and version detection, operating system detection, NSE vulnerability scanning, and firewall-filtering analysis.

**Target:** `192.168.204.129`  
**Attacker Machine:** Kali Linux  
**Tool:** Nmap 7.99  
**Lab:** Metasploitable 2 (intentionally vulnerable VM)

> ⚠️ Educational use only. Scan systems you own or have explicit permission to test.

---

## 🎯 Objectives

- Discover active hosts on the network.
- Identify open TCP ports.
- Detect running services and software versions.
- Estimate the target operating system.
- Check for potential vulnerabilities using NSE scripts.
- Examine network filtering behaviour.
- Generate scan reports.

---

## 🛠️ Tools Used

- Kali Linux
- Nmap 7.99
- VMware
- Nmap Scripting Engine (NSE)

---



## 1️⃣ Host Discovery

### Command

```bash
nmap -sn 192.168.204.0/24
```

### Screenshot

![Host Discovery](./HOST%20DISCOVERY.png)
### Explanation

The `-sn` option performs host discovery without a standard port scan. The supplied lab output shows four responsive hosts.

### Target Availability Check

```bash
ping 192.168.204.129
```

### 1. Target IP Status
![Target IP Status](./CHECK%20THE%20TARGET%20IP%20STATUS.png)

The screenshot documents the target's response to ICMP ping requests.

---

## 2️⃣ Port Scanning

### Command

```bash
nmap 192.168.204.129
```

![Port Scanning](./PORT%20SCANNING.png)

### Explanation

Nmap checks its default set of 1,000 TCP ports. The supplied output identifies multiple open services, including FTP, SSH, Telnet, HTTP, SMB, MySQL, and PostgreSQL.

---

## 3️⃣ Service and Version Detection

### Command

```bash
nmap -sV 192.168.204.129
```

### Screenshot

![Service and Version Detection](./SERVICE%20VERSION.png)

### Explanation

The `-sV` option attempts to identify services and their software versions. These results help identify potentially outdated software that may require further assessment.

---

## 4️⃣ Operating System Detection

### Command

```bash
nmap -O 192.168.204.129
```

### Screenshot

![Operating System Detection](./OS%20DETECTION.png)

### Explanation

The `-O` option attempts to identify the target operating system through network fingerprinting. The supplied output estimates that the target runs Linux.

---

## 5️⃣ NSE Vulnerability Scanning

### Command

```bash
nmap --script vuln 192.168.204.129
```

### Screenshot

![NSE Script Scanning](./NSE%20SCRIPT%20SCANNING.png)
### Explanation

Nmap's vulnerability scripts reported potential issues associated with legacy services, including a vsftpd 2.3.4 backdoor and an SSLv3 POODLE-related finding.

Findings should be verified before concluding that a vulnerability is exploitable.

---

## 6️⃣ Firewall and Filtering Analysis

### Command

```bash
nmap -sA 192.168.204.129
```

### Screenshot

![Firewall Detection](./FIREWALL%20DETECTION.png)

### Explanation

The `-sA` option uses TCP ACK probes to examine network filtering behaviour. An `unfiltered` result does not, by itself, prove that no firewall exists.

---

## 7️⃣ Scan Report Generation

### Command
![Scan Report](./SCAN%20REPORT.png)
```bash
nmap -sV -oN nmap_scan_report.txt 192.168.204.129
```

To view the saved report:

```bash
cat nmap_scan_report.txt
```

The report records detected services, versions, and scan results for documentation and further analysis.

---

## 📊 Project Summary

| Practical | Tool/Command | Purpose |
|---|---|---|
| Host Discovery | `nmap -sn` | Discover responsive hosts |
| Target Check | `ping` | Check ICMP response |
| Port Scanning | `nmap` | Identify open ports |
| Service Detection | `nmap -sV` | Identify services and versions |
| OS Detection | `nmap -O` | Estimate operating system |
| NSE Scanning | `nmap --script vuln` | Identify potential vulnerabilities |
| Filtering Analysis | `nmap -sA` | Examine packet-filtering behaviour |

---

## 🛡️ Security Recommendations

- Disable unnecessary network services.
- Update outdated and vulnerable software.
- Prefer SSH over Telnet for remote administration.
- Restrict access to sensitive ports.
- Review firewall configurations.
- Validate vulnerability findings.
- Repeat scans after remediation.

---

## 📚 Learning Outcomes

- Network reconnaissance
- Host discovery and TCP port scanning
- Service and version enumeration
- OS fingerprinting
- Vulnerability assessment fundamentals
- Network filtering analysis
- Technical documentation

---

## ✅ Conclusion

This project demonstrates how Nmap can help identify active hosts, exposed services, software versions, and potential security weaknesses in a controlled lab environment.

The findings highlight the importance of reducing unnecessary service exposure, maintaining updated software, and validating vulnerabilities through authorized security assessments.

---

## ⚠️ Disclaimer

This project is intended for educational purposes and authorized security testing only.
