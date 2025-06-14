# Azure-Network-Lab-ICMP-SSH-DNS-DHCP-RDP-Traffic-Capture

# Azure Network Lab – ICMP, SSH, DNS, DHCP, RDP Traffic Capture

This project demonstrates the deployment of two Azure Virtual Machines (Windows 10 & Ubuntu) in the same Virtual Network to observe, filter, and analyze network traffic using Wireshark.

---

## ⚙️ Lab Setup

- **Resource Group:** `hiphop-lab-rg`
- **Virtual Machines:**
  - ![image](https://github.com/user-attachments/assets/9c9de06c-ce7d-4baf-8da4-7714fffa341c)
 (Windows 10 Pro)
  - ![image](https://github.com/user-attachments/assets/add20a16-78c0-448d-8a1d-c5040e7a7cad)
 (Ubuntu 22.04 LTS)
- **Networking:**
  - Both VMs deployed on the same VNet/Subnet (`hiphop-vnet/default`)
  - RDP access enabled for Windows VM
  - SSH enabled for Ubuntu VM

---

## 🔬 Tools Used

- **Microsoft Azure** (Cloud Infrastructure)
- **Wireshark** (Network packet capture)
- **PowerShell & CMD** (Ping/SSH/NSLookup commands)
- **Remote Desktop (RDP)**

---

## 🧪 Traffic Types Observed

### ✅ ICMP (Ping)
- Captured successful ping between Windows and Ubuntu VM.
- Blocked ICMP using NSG, verified with packet loss and no replies.
- Re-enabled ICMP, confirmed restored communication.

> 📸 `Firewall_Blocked_Ping.png`  ![image](https://github.com/user-attachments/assets/e5e791b8-d350-49a5-9fd7-15a3b8cd800d)
> ![image](https://github.com/user-attachments/assets/40d26f0d-9843-465d-8847-fc623f49dc57)
> ![image](https://github.com/user-attachments/assets/fb4b50f3-9e4c-4fb5-a1d2-a914f9a8e276)
> ![image](https://github.com/user-attachments/assets/59cc5367-8411-46d0-b008-3f1fa33d0433)




> *“Ping blocked via NSG - ICMP echo requests observed without replies.”*

---

### 🔐 SSH
- SSH session initiated from Windows to Ubuntu.
- Traffic filtered via port 22 in Wireshark.
- Verified encrypted communication packets.

> 📸 ![image](https://github.com/user-attachments/assets/1b164e57-8ee1-466d-9b63-f340d4d0bd84)
> ![image](https://github.com/user-attachments/assets/1bfd7f64-13c0-4c0a-8d75-be11e54c0e21)

`Wireshark_SSH_Traffic.png`  
> *“SSH traffic over port 22 captured using Wireshark.”*

---

### 🌐 DNS
- Used `nslookup` to resolve domains.
- Observed DNS request/response packets.

> 📸 ![image](https://github.com/user-attachments/assets/56dea127-d809-4e30-a5b7-6668be6d9d4b)
`Wireshark_DNS_Traffic.png`  
> *“DNS queries to google.com and disney.com observed in Wireshark.”*

---

### 📶 DHCP
- Renewed IP in Windows with `ipconfig /renew`.
- Captured DHCP broadcast/acknowledgment.

> 📸 `Wireshark_DHCP_Traffic.png`  ![image](https://github.com/user-attachments/assets/b506dedc-08da-4abb-a36c-f747c401d4de)

> *“Dynamic IP address renewal captured in Azure via DHCP.”*

---

### 🖥️ RDP
- Observed continuous RDP traffic on port 3389.
- Explained constant data stream due to session streaming.

> 📸 ![image](https://github.com/user-attachments/assets/e5e3632a-f8de-4eab-ba7b-99cd4a021a71)
`Wireshark_RDP_Traffic.png`  
> *“Nonstop RDP data flow showing live screen sharing traffic between client and host.”*

---

## 🧹 Lab Cleanup
- Deleted resource group and all Azure assets to avoid billing.

---

## 🔥 Skills Demonstrated

- Azure VM provisioning and networking
- Remote desktop and SSH connectivity
- Custom firewall (NSG) configuration
- Network protocol filtering and packet analysis
- Real-world troubleshooting using Wireshark

---

## 📚 Notes

This lab was created as part of my hands-on portfolio to showcase real-world IT and cloud networking skills in action. All traffic was captured in a secure, controlled test environment.
