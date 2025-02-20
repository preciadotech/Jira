<h1>Active Directory Domain Services Home Lab</h1>



<h2>Description</h2>
In my home lab, I set up an Active Directory Domain Services environment on Azure by creating two virtual machines: one running Windows Server 2022 as the domain controller and another running Windows 10 as a client machine. I installed and configured AD DS on the Server 2022 VM, promoted it to a domain controller, and created user accounts. On the Windows 10 VM, I configured network settings to communicate with the domain controller and joined the machine to the domain. After restarting, I successfully logged into the Windows 10 VM using domain credentials, ensuring the domain environment was fully functional for testing and learning purposes.
<br />


<h2>Languages and Utilities Used</h2>

- <b>Microsoft Azure</b>
- <b>Active Directory</b>

<h2>Environments Used </h2>

- <b>Windows 10</b>
- <b>Server 2022</b> 

<p align="center">
<h2>Step 1: Create Server 2022 and Windows VMs on Azure: </h2>
One VM is running Windows Server 2022 to serve as the Domain Controller. <br/>
The second VM is a Windows 10 VM, which will act as a domain member client. <br/>
I ensured both VMs were placed in the same Virtual Network (VNet) to ensure they could communicate with each other over the internal network. <br/>
<img src="https://i.imgur.com/5he8UZQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<h2>Step 2: Install Active Directory Domain Services (AD DS) on the Server 2022 VM:  </h2>
After creating the Server 2022 VM, I used Remote Desktop Protocol (RDP) to connect to it and started configuring it. <br/>
I opened Server Manager, went to Add Roles and Features, and selected Active Directory Domain Services (AD DS) for installation. <br/>
<img src="https://i.imgur.com/spnc4ZB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<h2>Step 3: Promote Server 2022 to Domain Controller: </h2>
I selected Add a new forest and entered a domain name (e.g., example.local). <br/>
After completing the wizard, I allowed the server to reboot, which promoted it to the Domain Controller for my new domain (example.local). <br/>
<img src="https://i.imgur.com/i61hL98.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<h2>Step 4: Create Users in Active Directory:  </h2>
I opened the Active Directory Users and Computers tool from Server Manager to start managing users. <br/>
I created a few test user accounts by right-clicking on the domain (example.local), selecting New → User, and providing details for each user. <br/>
<img src="https://i.imgur.com/eCbaBMB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<h2>Step 5: Change Network Adapter Settings on Windows 10 VM: </h2> 
I connected to the Windows 10 VM using RDP and navigated to the Network and Sharing Center. <br/>
From there, I clicked on Change adapter settings to modify the network adapter configuration. <br/>
In Internet Protocol Version 4 (TCP/IPv4), I selected Use the following DNS server addresses and entered the IP address of my Domain Controller (the Server 2022 VM) as the DNS server, so the Windows 10 VM can communicate with the domain. <br/>
<img src="https://i.imgur.com/wftTI5o.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<h2>Step 6: Join the Windows 10 VM to the Domain: </h2>
On the Windows 10 VM, I opened System Properties (by right-clicking on This PC and choosing Properties → Change settings). <br/>
I clicked on Change, entered the domain name (example.local), and provided the domain admin credentials to join the domain. <br/>
After the domain join was successful, I was prompted to restart the VM to apply the changes. I restarted the Windows 10 VM. <br/>
<img src="https://i.imgur.com/NmSsgN8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<h2>Step 7: Verify Domain Membership:  </h2>
After the restart, I logged into the Windows 10 VM using a domain user account (e.g., example.local\username). <br/>
I ensured the Windows 10 VM could successfully communicate with the Domain Controller and access domain resources like shared folders or printers. <br/>
<img src="https://i.imgur.com/2HlLThq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
