# Network Mapping & Enumeration (Nmap)

## Overview
This laboratory documents the use of **Nmap** to map the attack surface of a remote target. The focus was on identifying active hosts, open ports, and the specific versions of running services.

## Environment
- **OS:** Kali Linux
- **Target:** `scanme.nmap.org`
- **Tool:** Nmap 7.98

---

## Lab Activities

### 1. Host Discovery (Pre-Scan Validation)

Before performing a full scan, I verified that the target host was reachable using a host discovery scan. This reduces unnecessary traffic and ensures the target is active before deeper enumeration.

- **Command:** `nmap -sn scanme.nmap.org`
- **Purpose:** Confirms target availability before deeper enumeration.
<img width="663" height="122" alt="Image" src="https://github.com/user-attachments/assets/63a9d6a1-c2fc-44d5-9537-073fc64edd32" />

### 2. TCP Port Enumeration

A default Nmap scan (SYN scan on top 1000 TCP ports) was performed to identify commonly exposed services and potential entry points.

- **Command:** `nmap scanme.nmap.org`
- **Findings:**
  - Port 22 → SSH (remote access)
  - Port 80 → HTTP (web service)
  - Port 9929 → nping-echo service
  - Port 31337 → Elite service
- **Security Interpretation:** Each open port represents a potential attack surface. Services such as SSH are high-value targets for credential-based attacks (brute force, credential stuffing), while unknown or non-standard services may indicate misconfiguration or niche exposure requiring further investigation.

<img width="666" height="323" alt="Image" src="https://github.com/user-attachments/assets/b54a5081-9fed-499f-b38b-f1e51258c928" />

### 3. Service & Version Detection

To assess exploitability, I performed service version detection on all open ports.

- **Command:** `nmap -sV scanme.nmap.org`
- **Findings:**
  - SSH → OpenSSH 6.6.1p1
  - HTTP → Apache 2.4.7
- **Security Interpretation:** Version fingerprinting enables mapping services to known vulnerabilities (CVEs). Older service versions may contain publicly documented weaknesses, including authentication flaws, information disclosure issues, or remote code execution vulnerabilities. This step is essential for vulnerability assessment and prioritization.

<img width="775" height="349" alt="Image" src="https://github.com/user-attachments/assets/906f1f6c-2db8-4837-b61d-0fe092e00794" />

---
## Security Takeaways
- Reconnaissance is layered: Start with host discovery **(-sn)** before escalating to full service enumeration.
- Attack surface equals exposure: Every open port increases potential entry vectors and should be evaluated based on service criticality.
- Version intelligence enables vulnerability mapping: Service fingerprinting is a prerequisite for CVE correlation and risk assessment.
- Operational relevance: This workflow mirrors real-world penetration testing and SOC reconnaissance analysis used to identify externally exposed assets and prioritize risk.
