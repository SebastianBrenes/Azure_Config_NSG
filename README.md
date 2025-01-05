<p align="center">
<img src="https://i.imgur.com/M0pY7CY.png" alt="Network Security Groups and Wireshark Logo"/>
</p>

# Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines using Wireshark

This guide walks you through observing various network traffic between Azure Virtual Machines using Wireshark and experimenting with Network Security Groups (NSGs). The tutorial is structured to help you understand how NSGs control traffic and how to analyze it using Wireshark.

---

## Environments and Tools Used

- **Platforms**: Microsoft Azure (Virtual Machines/Compute), Remote Desktop
- **Technologies**: Network Security Groups (NSGs), Wireshark (Protocol Analyzer)
- **Protocols**: ICMP, SSH, DHCP, DNS, RDP
- **Operating Systems**: Windows 10 (21H2), Ubuntu Server 20.04

---

## Overview of Steps

1. **Set Up Your Virtual Environment**
   - Create a Resource Group.
   - Deploy a Windows Virtual Machine and an Ubuntu Virtual Machine.
   - Configure a Virtual Network (VNet) and Subnet.

2. **Observe ICMP Traffic**
   - Use Wireshark to filter and monitor ICMP traffic.
   - Experiment with enabling/disabling ICMP traffic via NSGs.

3. **Inspect SSH Traffic**
   - Filter for SSH traffic and analyze it during an SSH session.

4. **Analyze DHCP Traffic**
   - Renew the IP address on the Windows VM and observe DHCP traffic.

5. **Monitor DNS Traffic**
   - Use `nslookup` to resolve domain names and observe DNS traffic.

6. **Observe RDP Traffic**
   - Filter for RDP traffic and analyze the constant data stream.

7. **Clean Up Resources**
   - Delete Azure resources to avoid additional charges.

---

## Detailed Steps

### Step 1: Set Up Your Virtual Environment
- Create a Resource Group in your Azure subscription.
  ![Resource Group](https://i.imgur.com/dOAeXqs.png)

- Deploy a Windows Virtual Machine (VM) and an Ubuntu VM within the same Resource Group and Virtual Network (VNet). Use the password option for the administrator account.
  ![Windows VM](https://i.imgur.com/PHOwjLh.png)
  ![Ubuntu VM](https://i.imgur.com/N5zwQUH.png)

- Verify the virtual network configuration using Azure Network Watcher.
  ![Network Watcher](https://i.imgur.com/Pn02GXF.png)

### Step 2: Observe ICMP Traffic
- Install Wireshark on the Windows VM and filter for ICMP traffic.
- Ping the Ubuntu VM from the Windows VM and observe the requests/replies in Wireshark.
  ![ICMP Traffic](https://i.imgur.com/3h9QSEY.png)

- Disable ICMP inbound traffic via the NSG and observe how pings fail in real-time.
  ![ICMP Blocked](https://i.imgur.com/ovGk5dq.png)

- Re-enable ICMP traffic and verify functionality.
  ![ICMP Re-enabled](https://i.imgur.com/nZbl2sA.png)

### Step 3: Inspect SSH Traffic
- Filter for SSH traffic in Wireshark.
- SSH into the Ubuntu VM from the Windows VM and observe the encrypted data packets.
  ![SSH Traffic](https://i.imgur.com/6YEDJKu.png)

### Step 4: Analyze DHCP Traffic
- Filter for DHCP traffic in Wireshark.
- Renew the IP address on the Windows VM (`ipconfig /renew`) and observe the DHCP handshake.
  ![DHCP Traffic](https://i.imgur.com/mKyAHFr.png)

### Step 5: Monitor DNS Traffic
- Filter for DNS traffic in Wireshark.
- Use `nslookup` to resolve domain names like `google.com` and `disney.com`, then observe the DNS query/response packets.
  ![DNS Traffic](https://i.imgur.com/mYZ8CAK.png)

### Step 6: Observe RDP Traffic
- Filter for RDP traffic in Wireshark (`tcp.port==3389`).
- Observe the constant data stream due to the live RDP session.
  ![RDP Traffic](https://i.imgur.com/hNlhTVp.png)

### Step 7: Clean Up Resources
- Close your RDP session and delete the Resource Group from the Azure portal.
- Verify resource deletion to avoid unnecessary charges.

---

By completing this tutorial, you gain practical experience in configuring NSGs and analyzing network traffic with Wireshark, which are essential skills for network and cloud administration.
