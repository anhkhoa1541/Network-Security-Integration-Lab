# Integrated Enterprise Network: Routing, Switching & AAA Security
## (Hệ thống Mạng Doanh nghiệp Tích hợp: Định tuyến, Chuyển mạch & Bảo mật AAA)

### 1. Project Overview (Tổng quan dự án)
* **English**: This project is a comprehensive network simulation developed using **Cisco Packet Tracer**. [cite_start]It demonstrates the integration of dynamic routing, VLAN segmentation, and centralized security management using the AAA framework and RADIUS protocol[cite: 1, 2, 22].
* **Tiếng Việt**: Dự án này là một bài mô phỏng mạng chi tiết được thực hiện trên **Cisco Packet Tracer**. [cite_start]Bài Lab minh chứng việc tích hợp định tuyến động, phân đoạn mạng ảo VLAN và quản lý bảo mật tập trung sử dụng mô hình AAA và giao thức RADIUS[cite: 1, 2, 22].

---

### 2. Key Technical Implementations (Các tính năng kỹ thuật chính)

#### A. Dynamic Routing - RIP (Định tuyến động)
* [cite_start]Implemented **RIP (Routing Information Protocol)** across routers R1, R2, and R3 to ensure full network reachability[cite: 23, 171].
* [cite_start]Configured `no auto-summary` to support proper subnet advertisement across the `192.168.x.x`, `10.0.0.0`, `20.0.0.0`, and `30.0.0.0` networks[cite: 173, 179, 219].

#### B. VLAN & Inter-VLAN Routing (VLAN & Định tuyến liên VLAN)
* [cite_start]Segmented the server farm into **VLAN 10** (Web/DNS Server - C3) and **VLAN 20** (RADIUS Server - C4)[cite: 17, 18, 24].
* [cite_start]Configured **Router-on-a-Stick** using sub-interfaces (e.g., `FastEthernet0/0.10` and `0/0.20`) on the gateway router to enable communication between different VLANs[cite: 241, 351, 354].

#### C. Centralized AAA Security - RADIUS (Bảo mật tập trung AAA)
* [cite_start]Implemented **AAA (Authentication, Authorization, and Accounting)** using the **RADIUS** protocol[cite: 27, 424].
* [cite_start]**Router R2** acts as the **AAA Client**, delegating authentication to the **Cisco Secure ACS Server (C4)** at IP `20.20.0.36` with shared key `123456`[cite: 4, 429, 443].
* [cite_start]Verified the implementation by capturing and analyzing **Access-Request**, **Access-Accept**, and **Accounting** packets[cite: 477, 481, 486].

#### D. Traffic Filtering - Standard ACL (Kiểm soát lưu lượng)
* [cite_start]Deployed a **Standard Access Control List (ACL)** on Router R3 to enforce security policies[cite: 26, 408].
* [cite_start]**Policy**: Successfully blocked the `10.0.0.0/8` subnet from accessing the Web Server while permitting the `30.0.0.0/8` subnet[cite: 26, 409, 415].

---

### 3. Address Table (Bảng địa chỉ IP)

| Device | Interface | IP Address | Subnet Mask | Default Gateway |
| :--- | :--- | :--- | :--- | :--- |
| **R1** | F0/0 | 10.0.0.36 | 255.0.0.0 | [cite_start]N/A [cite: 21] |
| **R1** | F0/1 | 30.0.0.36 | 255.0.0.0 | [cite_start]N/A [cite: 21] |
| **R1** | S1/0 | 192.168.1.30 | 255.255.255.0 | [cite_start]N/A [cite: 21] |
| **R2** | S1/0 | 192.168.1.36 | 255.255.255.0 | [cite_start]N/A [cite: 21] |
| **R2** | S1/1 | 192.168.2.30 | 255.255.255.0 | [cite_start]N/A [cite: 21] |
| **R3** | F0/0 | 20.0.0.30 | 255.0.0.0 | [cite_start]N/A [cite: 21] |
| **C1** | NIC | 10.0.0.30 | 255.0.0.0 | [cite_start]10.0.0.36 [cite: 21] |
| **C3 (Web/DNS)**| NIC | 20.10.0.36 | 255.0.0.0 | [cite_start]20.10.0.30 [cite: 21] |
| **C4 (RADIUS)** | NIC | 20.20.0.36 | 255.0.0.0 | [cite_start]20.10.0.30 [cite: 21] |

---

### 4. Verification Results (Kết quả kiểm tra)
* [cite_start]**Connectivity**: Full connectivity verified via Ping between R1, R2, and R3 after RIP convergence[cite: 228, 229].
* [cite_start]**Web Access**: C2 can access `http://www.demo.com` successfully[cite: 160, 418]. [cite_start]C1 is denied access after ACL application[cite: 415, 420].
* [cite_start]**RADIUS Auth**: Remote access to R2 is authenticated through the user `Hutech` created on the ACS Server[cite: 461, 471].

---

### 5. Tools Used (Công cụ sử dụng)
* [cite_start]**Cisco Packet Tracer**: Network simulation and configuration[cite: 236, 407].
* [cite_start]**Cisco Secure ACS**: RADIUS/AAA Server management[cite: 431, 434].
* [cite_start]**Wireshark**: Packet analysis for RADIUS protocol verification[cite: 476, 479].
