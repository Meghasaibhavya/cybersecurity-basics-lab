# 🌐 Network Mapping & Enumeration (Nmap)

## Overview
This laboratory documents the use of **Nmap** to map the attack surface of a remote target. The focus was on identifying active hosts, open ports, and the specific versions of running services.

## 🛠️ Environment
- **OS:** Kali Linux
- **Target:** `scanme.nmap.org`
- **Tool:** Nmap 7.98

---

## 🚀 Lab Activities

### 1. Passive Host Discovery
I performed a "ping scan" to verify the target was active before committing to a more intensive service scan.
- **Command:** `nmap -sn scanme.nmap.org`

<img width="663" height="122" alt="Image" src="https://github.com/user-attachments/assets/63a9d6a1-c2fc-44d5-9537-073fc64edd32" />

### 2. Basic Port Scanning
I identified the top 1000 common ports to determine the available entry points.
- **Command:** `nmap scanme.nmap.org`
- **Key Findings:** Identified active services on ports 22 (SSH), 80 (HTTP), and 9929.

<img width="666" height="323" alt="Image" src="https://github.com/user-attachments/assets/b54a5081-9fed-499f-b38b-f1e51258c928" />

### 3. Service Version Detection
I used version detection to identify the specific software and versions running on the open ports. This is critical for vulnerability research.
- **Command:** `nmap -sV scanme.nmap.org`
- **Results:** Identified **Apache 2.4.7** and **OpenSSH 6.6.1p1**.

<img width="775" height="349" alt="Image" src="https://github.com/user-attachments/assets/906f1f6c-2db8-4837-b61d-0fe092e00794" />

---

## 💡 Technical Takeaways
- **Reconnaissance Strategy:** Established that a stealthier approach (Host Discovery first) is essential for avoiding detection.
- **Version Analysis:** Learned how to cross-reference service versions (e.g., Apache 2.4.7) with known CVEs to identify potential vulnerabilities.
- **Data Persistence:** Integrated both raw `.txt` logs and visual screenshots for thorough documentation.
