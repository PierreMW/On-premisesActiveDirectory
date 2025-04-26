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

![image](https://github.com/user-attachments/assets/e2d869e6-0ec6-4e07-b888-d5b38e06e832)
![image](https://github.com/user-attachments/assets/a6e925b7-2f00-44c6-bc59-605f7c8f27c3) 
![image](https://github.com/user-attachments/assets/d90ed389-7704-42c5-9bd6-bde6d5e689fe)

Next we will use the remote desktop to disable the firewall using the IP address of "DC-1". Once you sign in through the remote desktop you will roight click the microsoft windows and choose run. Once prompted for a code you will enter "wf.msc". For the firewall state of private, domain and public you will switch them to off. This insures that the firewall have been taken down.

![image](https://github.com/user-attachments/assets/bb882120-b66d-4adc-8119-a0a26dcfd1bd)

Then we will go to "client-1" and switch the DNS-server to the private IP address of "dc-1". You will do so by going to virtual machines, client-1, network settings and clicking on "client 1723_z1". Once you have completed those steps you will restart client-1 to insure it is working properly with the new settings.

![image](https://github.com/user-attachments/assets/87144b00-f555-424c-a869-07abb0950765)
![image](https://github.com/user-attachments/assets/4c375099-f4eb-400f-a40f-457b80b0518d)

Next you will open the remote desktop using client-1 public ip address. You will then open Powershell through remote desktop. Once opened you will type "ping 10.0.0.4". 10.0.0.4 is the private IP address for dc-1. If you receive back "destination host unreachable". It means dc-1's firewall is still up or your in a different network. 

![image](https://github.com/user-attachments/assets/035e1cea-c4c9-4f8c-a571-86145f765659)

If you see that everything is correct you will then type "ipconfig /all". The output should show dc-1's ip private address "10.0.0.4" next to DNS servers. If you've received a different output go over said steps.

















