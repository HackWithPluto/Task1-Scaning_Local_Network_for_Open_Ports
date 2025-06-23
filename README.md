 Task 1: Local Network Port Scanning

## Objective
Perform a local network port scan using **Nmap** to identify open ports and potential risks. Additionally, capture and analyze traffic using **Wireshark** to understand how SYN scans work at the packet level.

---

## Tools Used


**Nmap** Port scanning and host discovery
**Wireshark** Packet-level analysis of Nmap SYN scan traffic

## Scanned IP Ranges

| Range              | Description                             |
|--------------------|-----------------------------------------|
| 10.0.2.0/24       | NAT network (3 hosts detected)          |


## Nmap Scan Results

# 10.0.2.2
- `135/tcp` → **msrpc**
- `445/tcp` → **microsoft-ds**
- `902/tcp` → **iss-realsecure**
- `912/tcp` → **apex-mesh**
- `2869/tcp` → **icslap**

# 10.0.2.3
- `53/tcp` → **domain (DNS)**

# 10.0.2.15
- All ports closed (no open ports detected)

## Risk Analysis

| Port | Service       | Risk Description                                       |
|------|---------------|--------------------------------------------------------|
| 135  | MSRPC         | May expose RPC vulnerabilities used in remote exploits |
| 445  | SMB           | Exploitable via EternalBlue, used in WannaCry attacks  |
| 902  | VMware Service| May reveal virtualization environment details          |
| 53   | DNS           | May be abused for DNS tunneling or poisoning attacks   |


## Wireshark Analysis (TCP SYN Scan)

# Purpose
Captured real-time Nmap scan traffic using Wireshark to validate and understand how SYN scanning works on the network level.

# Filter Applied:
tcp.flags.syn == 1 && tcp.flags.ack == 0

## Included Files
- scan_results.html – raw output of Nmap
- wireshark_result.pcapng – raw output of wireshaark
- nmap_scan.png – screenshot of terminal output
- wireshark_scan.png – screenshot of terminal output

## Outcome
Learned to scan a network, identify open ports, analyze services, and recognize potential vulnerabilities.  improve this readme and add part of wireshark
