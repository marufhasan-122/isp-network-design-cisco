# 🌐 ISP Network Design & Static Routing Project

This project demonstrates **network design, IP addressing, and static routing** using **Cisco Packet Tracer**.  
It was built based on an addressing table and connectivity requirements.

---

## 📋 Problem Statement
1. Connect Network Devices and Hosts  
2. Configure Devices with IPv4 Addressing, and Static Routing  
3. Verify the End Device Configuration and Connectivity  
4. Use Networking Commands to View Host Information  

---

## 🗂️ Addressing Table

| Device   | Interface/Port | Network         | IPv4 Address      | Connected To   |
|----------|----------------|-----------------|------------------|----------------|
| PC0      | NIC/Fa0/0      | 192.168.1.0/24  | 192.168.1.x      | Switch    |
| PC1      | NIC/Fa0/0      | 192.168.1.0/24  | 192.168.1.x      | Switch    |
| PC2      | NIC/Fa0/0      | 192.168.2.0/24  | 192.168.2.x      | Switch    |
| PC3      | NIC/Fa0/0      | 192.168.2.0/24  | 192.168.2.x      | Switch    |
| PC4      | NIC/Fa0/0      | 172.16.10.0/24  | 172.16.10.x      | Switch   |
| PC5      | NIC/Fa0/0      | 172.16.10.0/24  | 172.16.10.x      | Switch   |
| Router0  | Serial         | 64.103.211.0/30 | 64.103.211.1/30  | Router1        |
| Router0  | Serial         | 209.165.10.0/30 | 209.165.10.1/30  | Router2        |
| Router1  | Serial         | 64.103.211.0/30 | 64.103.211.2/30  | Router0        |
| Router1  | Serial         | 209.165.11.0/30 | 209.165.11.1/30  | Router2        |
| Router2  | Serial         | 209.165.10.0/30 | 209.165.10.2/30  | Router0        |
| Router2  | Serial         | 209.165.11.0/30 | 209.165.11.2/30  | Router1        |

---

## ⚙️ Configuration Steps

### ✅ PC Configuration
Example for **PC0**:
```
IP Address: 192.168.1.10
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.1.1
```

---

### ✅ Router0 (Example)
```bash
Router> enable
Router# configure terminal

! LAN interface
Router(config)# interface g0/0
Router(config-if)# ip address 192.168.1.1 255.255.255.0
Router(config-if)# no shutdown

! Serial to Router1
Router(config)# interface s0/0/0
Router(config-if)# ip address 64.103.211.1 255.255.255.252
Router(config-if)# clock rate 64000
Router(config-if)# no shutdown

! Serial to Router2
Router(config)# interface s0/0/1
Router(config-if)# ip address 209.165.10.1 255.255.255.252
Router(config-if)# clock rate 64000
Router(config-if)# no shutdown
```

---

### ✅ Static Routes Example
Router0:
```bash
ip route 192.168.2.0 255.255.255.0 64.103.211.2
ip route 172.16.10.0 255.255.255.0 209.165.10.2
```

Router1:
```bash
ip route 192.168.1.0 255.255.255.0 64.103.211.1
ip route 172.16.10.0 255.255.255.0 209.165.11.2
```

Router2:
```bash
ip route 192.168.1.0 255.255.255.0 209.165.10.1
ip route 192.168.2.0 255.255.255.0 209.165.11.1
```

---

## 🖧 Verification
- `ping` between PCs in different networks (e.g., PC0 → PC2, PC1 → PC4, PC5 → PC0)  
- `show ip route` to verify routing tables  
- `show ip interface brief` to verify interfaces  

---

## 📸 Screenshots
![4](https://github.com/user-attachments/assets/e2ee006e-fc75-45b0-a91b-ea8eb5bb08e1)


---

## 🎯 Learning Outcomes
- Subnetting & Addressing  
- Router Configuration  
- Static Routing  
- Connectivity Verification  

---

## 🛠 Tools Used
- Cisco Packet Tracer  
- Networking Commands (`ping`, `ipconfig`, `tracert`, etc.)  

---

## 👨‍💻 Author
**Ruhul Amin Maruf**  
📧 ruhulamin43416@gmail.com  
🔗 [LinkedIn](www.linkedin.com/in/ruhulamin-ece)
