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
<hr>
<p>
On DC-1 we will install Active Directory Domain Services through the Server Manager.  After installation is complete we will promote as a domain controller.
</p>
<p>
<img src="https://i.imgur.com/8tICw73.jpg" height="80%" width="80%" alt="Install Active Directory Domain Services"/>
</p>
<br />
<hr>
<p>
Then we will open Active Directory Users and Computers and add two Organizational Units (OUs): _EMPLOYEES, _ADMINS.  We will then create a user and add them to the _ADMINS OU.  We will also add them to the "Domain Admins" security group.
</p>
<p>
<img src="https://i.imgur.com/8vf4q2g.jpg" height="80%" width="80%" alt="Add to Organizational Units"/>
</p>
<p>
<img src="https://i.imgur.com/Bc78UmL.jpg" height="80%" width="80%" alt="Add User to OU and Security Group"/>
</p>
<br />
<hr>
<p>
Our next step will be the join Client-1 to DC-1.  In order to do this we need to set Client-1's DNS settings to DC-1 private IP address in Microsoft Azure (Microsoft Azure will automatically supply a DNS server by default, this DNS server will not allow us to find DC-1).
</p>
<p>
<img src="https://i.imgur.com/751hATB.jpg" height="80%" width="80%" alt="Join Client-1 to DC-1"/>
</p>
<br />
<hr>
<p>
Client-1 now shows up under Computers in Active Directory Users and Computers.  We created a new OU named _CLIENTS and moved Client-1 into there.
</p>
<p>
<img src="https://i.imgur.com/uY6Frqf.jpg" height="80%" width="80%" alt="Moved Client-1 into _CLIENTS"/>
</p>
<br />
<hr>
<p>
While logged into Client-1 as an administrator we will allow "Domain Users" to remote access this PC.
</p>
<p>
<img src="https://i.imgur.com/ZbyJPw3.jpg" height="80%" width="80%" alt="Allow "Domain Users" to Remote in"/>
</p>
<br />
<hr>
<p>
Back in DC-1 we will open Powershell ISE as an administrator.  We will add a script that will generate 1,000 random users and imput them into our Active Directory.  (Source to the script: <a href="https://github.com/joshmadakor1/AD_PS/blob/master/Generate-Names-Create-Users.ps1">Powershell Script</a>)
</p>
<p>
<img src="https://i.imgur.com/l7nGq2b.jpg" height="80%" width="80%" alt="Powershell Script"/>
</p>
<p>
<img src="https://i.imgur.com/aYNMnfg.jpg" height="80%" width="80%" alt="Powershell Script Running"/>
</p>
<br />
<hr>
<p>
Back in DC-1 we will open Powershell ISE as an administrator.  We will add a script that will generate 1,000 random users and imput them into our Active Directory.  (Source to the script: <a href="https://github.com/joshmadakor1/AD_PS/blob/master/Generate-Names-Create-Users.ps1">Powershell Script</a>)
</p>
<p>
<img src="https://i.imgur.com/l7nGq2b.jpg" height="80%" width="80%" alt="Powershell Script"/>
</p>
<p>
<img src="https://i.imgur.com/aYNMnfg.jpg" height="80%" width="80%" alt="Powershell Script Running"/>
</p>
<br />
<hr>
<p>
As we can see all randomly generate names are located in the _EMPLOYEES OU.
</p>
<p>
<img src="https://i.imgur.com/XbeBCWg.jpg" height="80%" width="80%" alt="All Users Added to OU"/>
</p>
<br />
<hr>
<p>
On Client-1 we attempted to login to a randomly generated name with the wrong password several times.  On DC-1 we can reset the user's password.  We can also unlock the account if the user is locked out.
</p>
<p>
<img src="https://i.imgur.com/HMP2bpu.jpg" height="80%" width="80%" alt="Failed Login"/>
</p>
<p>
<img src="https://i.imgur.com/aBScJM1.jpg" height="80%" width="80%" alt="Reset Password"/>
</p>
<p>
<img src="https://i.imgur.com/omoYzD4.jpg" height="80%" width="80%" alt="Reset Password"/>
</p>
<p>
<img src="https://i.imgur.com/tKC1C8k.jpg" height="80%" width="80%" alt="Unlock Account"/>
</p>
<br />
<p>
This is all for installing configuring Active Directory.  In the next section we will share files and edit permissions.
