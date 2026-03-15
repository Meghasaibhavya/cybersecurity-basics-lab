# 🔍 Network Traffic Analysis (Wireshark)

## Overview
This folder documents my hands-on analysis of network traffic during reconnaissance. By capturing raw data with **Wireshark**, I examined how specific discovery activities—like DNS resolution and TCP port scanning—look at the packet level.

## 🛠️ Environment 
- **OS:** Kali Linux
- **Analysis Tool:** Wireshark
- **Interface:** eth0
- **Traffic Source:** Local machine

## 🚀 Lab Analysis & Observations

### 1. DNS Resolution
Before a network scan can reach its destination, the system must resolve the domain name. I isolated the outbound DNS queries to observe the system identifying the target's IP infrastructure.
- **Display Filter:** `dns && dns.flags.response == 0`

<img width="900" alt="DNS Queries in Wireshark" src="https://github.com/user-attachments/assets/ae6c5d69-a591-445c-8b48-f57de9d26189" />

### 2. Identifying TCP SYN Stealth Scans
I examined the signature of a "Stealth Scan" (SYN scan). By filtering for packets where only the SYN flag is set, I identified the rapid sequence of connection attempts used to probe for open services.
- **Display Filter:** `tcp.flags.syn == 1`

<img width="900" alt="TCP SYN Packet Analysis" src="https://github.com/user-attachments/assets/cd4d0497-c2e4-4f21-9314-5df4e34fe0cd" />

### 3. Service Verification (SYN-ACK Responses)
To confirm which ports were identified as active and "Open," I filtered for the target's response. A `[SYN, ACK]` packet indicates that the server is listening and willing to complete the connection.
- **Display Filter:** `tcp.flags.syn == 1 && tcp.flags.ack == 1`

<img width="900" alt="SYN-ACK Response Verification" src="https://github.com/user-attachments/assets/a1ef7d13-1be7-4fff-a9b9-44c3f32ed396" />

---

## 📑 Display Filter Reference

| **Filter** | **Security Significance** |
| :--- | :--- |
| `dns` | General inspection of name resolution traffic. |
| `dns && dns.flags.response == 0` | Isolates requests to identify target domain lookup attempts. |
| `tcp.flags.syn == 1` | Primary indicator of automated port scanning behavior. |
| `tcp.flags.syn == 1 && tcp.flags.ack == 1` | Identifies live services and successful TCP handshakes. |

---

## 💡 Key Takeaways
- **Protocol Insights:** Gained a deeper understanding of the TCP 3-way handshake and how it is manipulated for reconnaissance.
- **Traffic Fingerprinting:** Learned to distinguish automated scanning "bursts" from normal network noise.
- **Incident Response:** Mastering these filters is a fundamental skill for detecting early-stage network probing and unauthorized activity.
