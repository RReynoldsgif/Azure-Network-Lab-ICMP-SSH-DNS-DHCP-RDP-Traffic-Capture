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

> 📸 ![image](https://github.com/user-attachments/assets/e5e791b8-d350-49a5-9fd7-15a3b8cd800d)Captured a successful ping from the Windows VM to the Ubuntu VM (10.0.0.5) using PowerShell. Wireshark confirms bidirectional ICMP traffic with echo requests and replies, verifying network connectivity and NSG rule configuration. This test validated end-to-end communication over ICMP protocol.

> ![image](https://github.com/user-attachments/assets/40d26f0d-9843-465d-8847-fc623f49dc57)Captured successful internal ping between two virtual machines (Windows to Ubuntu) using ICMP, and verified DNS functionality by resolving and pinging google.com. Wireshark confirmed packet transmission and response, validating both internal network communication and external DNS resolution.

> ![image](https://github.com/user-attachments/assets/59cc5367-8411-46d0-b008-3f1fa33d0433)Captured fluctuating ICMP traffic between two VMs using Wireshark and PowerShell. The PowerShell window displays a sequence of timeouts followed by restored replies, illustrating how network policy or firewall changes affected communication and how recovery was verified in real time.

---

### 🔐 SSH
- SSH session initiated from Windows to Ubuntu.
- Traffic filtered via port 22 in Wireshark.
- Verified encrypted communication packets.

> 📸> ![image](https://github.com/user-attachments/assets/1bfd7f64-13c0-4c0a-8d75-be11e54c0e21)This screenshot captures a secure SSH connection from a Windows VM to an Ubuntu VM within an Azure virtual network. The PowerShell terminal shows successful authentication, while Wireshark displays encrypted SSHv2 traffic (port 22), confirming secure remote access over the network.
 
> *“SSH traffic over port 22 captured using Wireshark.”*

---

### 🌐 DNS
- Used `nslookup` to resolve domains.
- Observed DNS request/response packets.

> 📸 ![image](https://github.com/user-attachments/assets/56dea127-d809-4e30-a5b7-6668be6d9d4b)In this screenshot, I demonstrated DNS resolution functionality within a virtualized Azure lab environment. After exiting an SSH session from the Windows VM to the Ubuntu VM, I used PowerShell to:
	•	Run ipconfig /renew to refresh the network configuration.
	•	Use nslookup to query domain names like google.com and disney.com.
	•	Successfully resolved the domains to their respective IP addresses.

Simultaneously, Wireshark captured DNS query and response packets between the VM (10.0.0.4) and DNS server (168.63.129.16) over UDP port 53, confirming that DNS name resolution was working as expected.

This test validated DNS communication paths and showed how to inspect real-time name resolution traffic in a cloud-based network lab.
> *“DNS queries to google.com and disney.com observed in Wireshark.”*

---

### 📶 DHCP
- Renewed IP in Windows with `ipconfig /renew`.
- Captured DHCP broadcast/acknowledgment.

> 📸 ![image](https://github.com/user-attachments/assets/b506dedc-08da-4abb-a36c-f747c401d4de)This screenshot shows a successful Dynamic Host Configuration Protocol (DHCP) exchange between a Windows VM and the Azure-provided DHCP server (168.63.129.16). After logging out of an SSH session to the Ubuntu VM, I ran ipconfig /renew in PowerShell to trigger a DHCP request.

Wireshark captured:
	•	A DHCP Request from the client (10.0.0.4) to the DHCP server.
	•	A DHCP ACK confirming the IP address assignment.

This verified that DHCP was functioning correctly in the Azure virtual network, and that the VM dynamically obtained its IP address through proper client-server communication.

> *“Dynamic IP address renewal captured in Azure via DHCP.”*

---

### 🖥️ RDP
- Observed continuous RDP traffic on port 3389.
- Explained constant data stream due to session streaming.

> 📸 ![image](https://github.com/user-attachments/assets/e5e3632a-f8de-4eab-ba7b-99cd4a021a71)
This screenshot demonstrates a successful Remote Desktop Protocol (RDP) connection from a client (99.90.208.51) to a Windows VM (10.0.0.4) over TCP port 3389, captured in Wireshark.

Key details:
	•	The filter tcp.port == 3389 isolates RDP traffic.
	•	The capture includes application data and TCP handshakes (SYN/ACK).
	•	The data flow confirms an active RDP session used to remotely access the VM.

This verifies that RDP is enabled, NSG rules are properly configured, and that remote administration of the VM is functioning securely.
 
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
