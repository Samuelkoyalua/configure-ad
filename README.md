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

- Step 1
- Step 2
- Step 3
- Step 4

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/ABRQyLY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Sign in to Azure Portal.
Create a Resource Group.
Create a Virtual Network (VNet) within the resource group.
Create a Virtual Machine (VM) named "DC-1" using Windows Server 2022.
Note the Resource Group and VNet created during VM setup.</p>
<br />

Set the Domain Controller's NIC private IP address to be static.
Create a Windows 10 client VM named "Client-1" in the same Resource Group and Vnet as created in Step 1.a.
Verify that both VMs are in the same Vnet using Network Watcher.

<p>
<img src="https://i.imgur.com/IcfUgG7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Verify connectivity between the client and Domain Controller.
Remote Desktop into Client-1 and start a continuous ping to DC-1's private IP using: ping -t <ip address>.
Access the Domain Controller, enable ICMPv4 in the Windows Firewall.
Confirm successful pings on Client-1.</p>
<br />

<p>
<img src="https://i.imgur.com/4kr2Lvj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Install Active Directory.
Login to DC-1 and install Active Directory Domain Services.
Promote DC-1 as a domain controller, setting up a new forest with the domain name mydomain.com.
After setup, restart DC-1.
Log back into DC-1 as the user mydomain.com\labuser.</p>
<br />





<p>
<img src="https://i.imgur.com/NUnq6LE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>


Open Active Directory Users and Computers (ADUC) and navigate to the domain where you want to create the accounts.
Create a new Organizational Unit (OU) named "_EMPLOYEES".
Inside the "_EMPLOYEES" OU, create a new user named "Jane Doe" with the username "jane_admin" and assign the same password.
Create another OU named "_ADMINS" at the same level as "_EMPLOYEES".
Add the "jane_admin" user to the "Domain Admins" Security Group.
Logout or close the Remote Desktop connection to the domain controller.
Log back in using the credentials "mydomain.com\jane_admin".
From now on, use the "jane_admin" account as your admin account for administrative tasks.
