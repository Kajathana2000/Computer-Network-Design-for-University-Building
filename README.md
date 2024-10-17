# University Computer Network Design Project 🌐🏢

This project focuses on designing a computer network for the new **IT Centre** and **Department Building** at the university. The goal is to provide a reliable, secure, and well-structured network with optimal use of IP addresses. The project includes subnetting, VLANs, Wi-Fi configurations, and router and switch setup.

---

## 🏛️ Project Overview

The IT Centre and Department Building consist of multiple floors, lecture halls, offices, labs, and meeting rooms requiring both wired and wireless connections. The IP address range provided is `10.20.0.0/16`.

### **Buildings and Data Points Summary**

#### IT Centre Block (164 Data Points)
- **Director Office:** 2 desktops  
- **Network Manager Room:** 1 desktop  
- **2 Technical Officers Rooms:** 1 computer each  
- **Staff Office:** 5 computers  
- **Meeting Room:** 2 data points (for video conference and computer) + Wi-Fi coverage  
- **Lobby Area:** Wi-Fi coverage  
- **Computer Lab 1:** 60 computers  
- **Computer Lab 2:** 60 computers  
- **Digital Learning and Media Centre:** 30 computers + 1 printer  
- **Printing Room:** 2 printers  

#### Department Block (203 Data Points)
- **4 Lecture Halls:** 1 desktop + 1 multimedia projector each  
- **14 Staff Rooms:** 1 desktop per room  
- **4 Technical Officers Rooms:** 1 desktop per room  
- **Department Meeting Room:** 2 data points (for video conference and computer) + Wi-Fi coverage  
- **Computer Lab 1:** 50 computers  
- **Computer Lab 2:** 50 computers  
- **Network Engineering Lab:** 10 computers  
- **Microprocessor Lab:** 12 computers  
- **Computer Vision and Machine Learning Lab:** 50 computers  
- **Department Office:** 2 computers + 1 printer  

---

## 📋 Network Requirements

1. **Network Isolation:**  
   - Staff room computers are isolated from other department rooms and labs for security.  
   - Department office computers are isolated from staff rooms, labs, and other spaces.

2. **Printer Access Restrictions:**  
   - IT Centre printers are accessible only by IT Centre staff.  
   - Department office printer is accessible only by department staff.

3. **Administrator Access Control:**  
   - All network nodes are only accessible by the administrator.

---

## 🛠️ Network Setup and Configuration

### 1. **Subnetting Plan**
The given IP address range is `10.20.0.0/16`. Subnets and VLANs will be created based on logical groups to isolate different sections of the network for security and performance.

- **IT Centre:**  
  - VLAN 10: Director and Staff Offices  
  - VLAN 20: Technical Officers and Labs  
  - VLAN 30: Wi-Fi and Meeting Rooms  

- **Department Block:**  
  - VLAN 40: Lecture Halls  
  - VLAN 50: Staff Rooms  
  - VLAN 60: Labs (Network, Microprocessor, CV/ML Labs)  
  - VLAN 70: Department Office and Meeting Room  

### 2. **Router and Switch Configuration**
Below are the general steps to configure the router and switches:

#### Router Configuration Example:
```bash
# Assign IP address to interfaces
interface GigabitEthernet0/1
  ip address 10.20.1.1 255.255.255.0
  no shutdown

# Enable routing between VLANs
ip routing

# Configure static routes if needed
ip route 10.20.2.0 255.255.255.0 10.20.1.2

#### **Switch Configuration Example:**
vlan 10
  name Director_Staff

interface GigabitEthernet0/2
  switchport mode access
  switchport access vlan 10
