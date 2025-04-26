<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How to Deploy on-premises Active Directory within Azure Compute](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

![image](https://github.com/user-attachments/assets/8af1cad8-d2d5-42dc-9d35-e45d8076e468)

First we are going to create two virtual machines. One is titled "DC-1" and the other is "Client-1". While creating this you will want them both to be under the same vnet other known as virtual network. This imoproves the communication between the two, as well as keeps the performance consistent. 

![image](https://github.com/user-attachments/assets/571eec7b-f7f6-452b-8023-ed86ac1ed3aa)
![image](https://github.com/user-attachments/assets/0851324c-52b0-443a-992b-bc19c5f3a94c)

Next, we’ll set a static (fixed) IP address on the domain controller (DC-1) instead of using a dynamic one. This is important because a static IP makes sure the domain controller’s address doesn’t change. That way, the client computers can always find DC-1 when they need to join the domain or look up names using its DNS service.




