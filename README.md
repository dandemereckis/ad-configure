<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Installing and Configuring Active Directory in the Cloud</h1>
This tutorial outlines the implementation and deployment of Active Directory using virtual machines in Microsoft Azure.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 Version 21H2

<h2>High-Level Deployment and Configuration Steps</h2>

- Create two virtual machines in Microsoft Azure (DC-1 and Client-1)
- Install Active Directory on DC-1
- Create an admin and normal user account in Active Directory
- Join Client-1 to DC-1
- Use Powershell script to create 1,000 random users and add them to our Active Directory

<h2>Deployment and Configuration Steps</h2>

<p>
First, we will create two virtual machines using Microsoft Azure.  We'll use a virtual machine with Windows Server to act as our Domain Controller (DC-1) and we'll use the second virtual machine with Windows 10 to act as our client computer (Client-1). 
</p>
<p>
<img src="https://i.imgur.com/R0MYV3e.jpg" height="80%" width="80%" alt="Create Two Virtual Machines"/>
</p>
<br />
<hr>
<p>
Now we will use Remote Desktop Connection to log into Client-1.  We will test network connectivity between Client-1 and DC-1.  We will open Powershell and begin a continuous ping to DC-1 and see that our pings are not going through.  We will then log into DC-1 and enable ICMP traffic within the firewall settings.  Now we can see we are starting to get replies from DC-1.
</p>
<p>
<img src="https://i.imgur.com/fZSahJh.jpg" height="80%" width="80%" alt="Client-1 Pinging DC-1"/>
</p>
<p>
<img src="https://i.imgur.com/SJEi5LJ.jpg" height="80%" width="80%" alt="Enable ICMP"/>
</p>
<p>
<img src="https://i.imgur.com/qCbSm0u.jpg" height="80%" width="80%" alt="Client-1 Pinging DC-1"/>
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
