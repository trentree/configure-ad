# configure-ad
<p align="center"> 
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/> 
</p> 

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1> 
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br /> 


<h2>Environments and Technologies Used</h2> 

- Microsoft Azure (Virtual Machines/Compute) 
- Remote Desktop 
- Active Directory Domain Services 
- PowerShell 

<h2>Operating Systems Used </h2> 

- Windows Server 2022 
- Windows 10

<h2>High-Level Deployment and Configuration Steps</h2> 

- Setup Resources by creating Domain Controller and Client VM (Virtual Machine)
- Ensure connectivity between the resources stated above
- Install Active Directory 
- Create Admin and Normal User Account
- Join Client to Domain
- Setup Remote Desktop for non-admin users on Client
- Create additional users and log into the client VM with a created user

<h2>Deployment and Configuration Steps</h2> 

<p> 
  
![Screenshot 2023-07-17 113431](https://github.com/trentree/configure-ad/assets/129711900/fd644ea4-1a01-428e-b285-06f8ed3d6137)

</p> 
To start off, we created two virtual machines as our resource. One will be the Domain Client and the other will be the Client.
<p> 

![Screenshot 2023-07-17 113820](https://github.com/trentree/configure-ad/assets/129711900/f922dcae-7ef0-4d57-9749-09059a19550c)
 
</p> 
<p> 
Next, we set the Domain Client as "Static" so the private IP will NOT change.
</p> 
<br /> 

<p> 
  
![CGBeRXrk jpg_large](https://github.com/trentree/configure-ad/assets/129711900/b4463800-f774-40ea-9ed7-bacc3dbd6942)
 
</p> 
<p>
Here we load up Domain Client to open Windows Defender Firewall and enable Core Network Diagnostics.
</p> 
<br />
<p> 
  
![KxM7HIDO](https://github.com/trentree/configure-ad/assets/129711900/8fee3cc3-dfdf-4b6d-8f5b-7a3f492eb437)

</p> 
<p>
We launch "Server Manager" to download Active Directory by clicking "Add Roles and Features".
</p> 
<br />
<p> 
  
![w59PbxUK](https://github.com/trentree/configure-ad/assets/129711900/724cf8c0-56a8-43a0-a195-df17e2d2add8)

</p> 
<p>
As Active Directory is finished downloading, we open the software to create an "_ADMIN" and "_EMPLOYEES" folder.
</p> 
<br />
<p>
  
![9zt26m-U](https://github.com/trentree/configure-ad/assets/129711900/08baaba7-7389-4e12-a8ac-b7b43ed0e8db)
 
</p> 
<p>
In the admin folder, we want to create an admin and their domain.
</p> 
<br />
<p> 
  
![Screenshot 2023-07-17 121059](https://github.com/trentree/configure-ad/assets/129711900/70ee44bb-b3fa-41c6-9b69-3c6c71927636)

</p> 
<p>
Here, we will boot up the "Client" Virtual Machine and set a domain there too in system properties.
</p> 
<br />
<p> 
  
![n3yvTbsx](https://github.com/trentree/configure-ad/assets/129711900/a8639775-c0a0-4ec4-bb86-99f0020b11ce)

</p> 
<p>
Once that is done, we will close out the "Client" VM and copy our private IP from the "Domain Client" to the "Client" VM
</p> 
<br />
<p> 
  
![77LFkLNL](https://github.com/trentree/configure-ad/assets/129711900/3aa00cdf-5acd-422c-a3fe-0cd73cccdc66)

</p> 
<p>
Now, we log back into the "Client" VM, open PowerShell, and create a code to generate however many employees you desire.  
</p> 
<br />
<p> 
  
![d8YxkfQR](https://github.com/trentree/configure-ad/assets/129711900/3192d289-401e-49b3-8ca7-9fe0152bfab4)

</p> 
<p>
While the employees are being created, you can go back to your "Domain Client" VM and open up the "_EMPLOYEES" folder we created. We pick a random employee from the folder and use their credentials to log into the "Client" VM.
</p> 
<br />
<p> 
  
![R6s8cOZv](https://github.com/trentree/configure-ad/assets/129711900/bec5828d-58e0-441e-8a7c-125b1d2659d7)

</p> 
<p>
Finally. We created a folder on our driver with different types of access (No-Access, Read/Write, Read Only, Accounting) for specific employees.
</p> 
<br />
