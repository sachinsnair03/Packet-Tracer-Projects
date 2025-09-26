# 🏢 Enterprise Network Project – Accounts & Delivery Departments (Packet Tracer)

This project implements a simple real-world networking case study using **Cisco Packet Tracer**.  
It covers **subnetting, IP addressing, router configuration, VLAN separation, and end-to-end testing** between two departments.

---

## 📌 Case Study
> **Requirement:**  
Design a network in Cisco Packet Tracer to connect **Accounts** and **Delivery** departments with the following conditions:
- Each department should contain at least **two PCs**.
- Each department should also have a **printer**.
- Appropriate number of **switches and routers** should be used.
- All interfaces must be configured with **IP addresses, subnet masks, and default gateways**.
- Devices should be connected with the correct cables.
- Verify communication between devices across departments.

---

## 🖼️ Network Topology


*(Insert Packet Tracer topology screenshot here)*

---

## 📊 Subnetting

- **Given network:** `192.168.40.0/24`  
- **Requirement:** 2 subnets (for Accounts & Delivery)

| Subnet | Network ID         | CIDR | Subnet Mask       | Valid Host Range            | Broadcast   |
|--------|--------------------|------|------------------|-----------------------------|-------------|
| 1 (Accounts) | 192.168.40.0   | /25 | 255.255.255.128 | 192.168.40.1 – 192.168.40.126 | 192.168.40.127 |
| 2 (Delivery) | 192.168.40.128 | /25 | 255.255.255.128 | 192.168.40.129 – 192.168.40.254 | 192.168.40.255 |

---

## ⚙️ Configuration

### Router Configuration
```bash
enable
configure terminal

# Enable interfaces
interface range gig0/0-1
 no shutdown
exit

# Accounts dept. (Subnet 1)
interface gig0/0
 ip address 192.168.40.1 255.255.255.128
 no shutdown
exit

# Delivery dept. (Subnet 2)
interface gig0/1
 ip address 192.168.40.129 255.255.255.128
 no shutdown
exit

end
write memory
