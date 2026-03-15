# 🌐 Network Mapping & Reconnaissance

This module documents the use of **Nmap** (Network Mapper) to perform discovery and security auditing on a remote host. The goal was to understand how a scanner identifies the "attack surface" of a target and interprets the states of various network ports.

## 🛠️ Environment
- **OS:** Kali Linux
- **Target:** `scanme.nmap.org` (An authorized Nmap project host for testing)
- **Primary Tool:** Nmap

## 🚀 Lab Activities

### 1. Basic Service Enumeration
I initiated a standard scan to identify which ports were responding to connection attempts. This is the first step in understanding what services (like web servers or SSH) are exposed to the internet.

<img width="696" height="328" alt="Nmap Basic Scan" src="https://github.com/user-attachments/assets/706d82cd-046c-41aa-b54b-225766c23a4c" />
<br>

### 2. Port State & Service Identification
By analyzing the scan results, I identified specific open ports. 
* **Technical Detail:** An "Open" state indicates that an application on the target machine is actively listening for connections on that port, providing a potential entry point for communication.
* **Key Findings:** Identified active services including **SSH (22)**, **HTTP (80)**, and **Nping-echo (9929)**.

<img width="688" height="378" alt="Open Ports Identification" src="https://github.com/user-attachments/assets/fd24a180-dbe6-4a26-9d1f-602d56ee6a33" />
<br>

### 3. Host Discovery & IP Analysis
I practiced host discovery to verify the reachability of the target. This confirms that the host is active and responding to probes (such as ICMP echo requests or TCP SYN packets) before committing to a deeper scan.

<img width="687" height="302" alt="Host Discovery" src="https://github.com/user-attachments/assets/2da160e3-0327-48b9-ad4c-42b788b8e1f4" />
<br>

---

## 💡 Technical Takeaways
- **Service Fingerprinting:** Identifying exact service versions is crucial for vulnerability research, as it allows a researcher to cross-reference versions with known CVEs (Common Vulnerabilities and Exposures).
- **Scan Efficiency:** Learned that different scan types (e.g., Stealth SYN vs. Comprehensive) offer different balances between speed and the amount of data returned.
- **Reconnaissance Logic:** Established a methodical workflow for mapping a network: Host Discovery → Port Scanning → Service Identification.

---
