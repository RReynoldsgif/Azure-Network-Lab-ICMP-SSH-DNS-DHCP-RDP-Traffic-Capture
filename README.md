# Azure-Network-Lab-ICMP-SSH-DNS-DHCP-RDP-Traffic-Capture

# Azure Network Lab – ICMP, SSH, DNS, DHCP, RDP Traffic Capture

This project demonstrates the deployment of two Azure Virtual Machines (Windows 10 & Ubuntu) in the same Virtual Network to observe, filter, and analyze network traffic using Wireshark.

---

## ⚙️ Lab Setup

- **Resource Group:** `hiphop-lab-rg`
- **Virtual Machines:**
  - `windows-vm` (Windows 10 Pro)
  - `ubuntu-vm` (Ubuntu 22.04 LTS)
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

> 📸 `Firewall_Blocked_Ping.png`  
> *“Ping blocked via NSG - ICMP echo requests observed without replies.”*

---

### 🔐 SSH
- SSH session initiated from Windows to Ubuntu.
- Traffic filtered via port 22 in Wireshark.
- Verified encrypted communication packets.

> 📸 `Wireshark_SSH_Traffic.png`  
> *“SSH traffic over port 22 captured using Wireshark.”*

---

### 🌐 DNS
- Used `nslookup` to resolve domains.
- Observed DNS request/response packets.

> 📸 `Wireshark_DNS_Traffic.png`  
> *“DNS queries to google.com and disney.com observed in Wireshark.”*

---

### 📶 DHCP
- Renewed IP in Windows with `ipconfig /renew`.
- Captured DHCP broadcast/acknowledgment.

> 📸 `Wireshark_DHCP_Traffic.png`  
> *“Dynamic IP address renewal captured in Azure via DHCP.”*

---

### 🖥️ RDP
- Observed continuous RDP traffic on port 3389.
- Explained constant data stream due to session streaming.

> 📸 `Wireshark_RDP_Traffic.png`  
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

## 🎧 Why “Hip-Hop Lab”?

Because IT should be dope too. Just like a hip-hop beat—everything in sync, flowing through the network with rhythm. This project blends structure, creativity, and control—just like a good track.

---

## 📁 Screenshots

Screenshots included in `/screenshots` folder with filenames like:
- `Azure_VM_Deployment.png`
- `Wireshark_ICMP_Filter.png`
- `SSH_Traffic_Capture.png`
- `DNS_Query_Traffic.png`
- `Firewall_Rule_Example.png`

---

## 📚 Notes

This lab was created as part of my hands-on portfolio to showcase real-world IT and cloud networking skills in action. All traffic was captured in a secure, controlled test environment.
