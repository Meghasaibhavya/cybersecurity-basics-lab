# Overview

This folder contains my initial hands-on practice with Wireshark to understand how network traffic looks during basic reconnaissance activities such as DNS resolution and TCP port scanning.

## Environment 

- **OS:** Kali Linux
- **Tool:** Wireshark
- **Interface Used:** eth0
- **Traffic Source:** Local machine (Nmap)

## What I practiced

I explored commonly used Wireshark display filters to analyze network behavior during reconnaissance:

  - **DNS queries** to resolve domain names
  - **TCP SYN packets** generated during port scanning
  - **TCP SYN-ACK responses** indicating open ports

These filters help identify scanning activity and understand how clients and servers communicate at the packet level.

## Filters Used

| **Filter** | **Purpose** |
| :--- | :--- |
| `dns` | View all DNS traffic |
| `dns && dns.flags.response == 0` | Show DNS queries only |
| `tcp.flags.syn == 1` | Identify TCP connection attempts |
| `tcp.flags.syn == 1 && tcp.flags.ack == 1` | Identify open port responses |
