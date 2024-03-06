
![image](https://github.com/CamdenBodden/Configuring-Active-Directory-within-Azure-VMs/assets/114665835/56782445-1ae1-4000-ae1b-42ace8dfd8fc)


<h1>Active Directory Project</h1>





<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory

<h2>Operating Systems Used </h2>

- Windows 11 and Windows Server 2022

<h2>Project Overview</h2>
Active directory is used to centrally manage thousands of user accounts, manage devices, and provides a way to control access to resources on a large scale. I will demonstrate experience in Active Directory by using Azure to create two virtual machines. One will be the domain controller with an on-premise version of Active Directory and the other will be a client computer that I will join to the domain controller. I will run a PowerShell script that creates thousands of users. I will then select one of those users to sign in on the client computer. In real life there would be multiple computers connected to the domain controller and multiple users across the network that could sign in to those computers. 
<p>

![image](https://github.com/CamdenBodden/Configuring-Active-Directory-within-Azure-VMs/assets/114665835/30046287-46ac-4ae6-a1d3-f24b8e1c2833)

</p>

<h2>Setup Resources in Azure</h2>
I created the domain controller and client computer and ensured they were in the same network. I set the Domain Controller’s NIC Private IP address to be static. Ideally, when you have a server that manages thousands of computers you don’t want to have the IP of the server to be dynamic.
<p>

![image](https://github.com/CamdenBodden/Configuring-Active-Directory-within-Azure-VMs/assets/114665835/e9a15a78-69be-41c6-87d2-433c2e0ede51)

</p>
--------------------------------------------------------------------------------------------------------------------------------------------------------
<p>

![image](https://github.com/CamdenBodden/Configuring-Active-Directory-within-Azure-VMs/assets/114665835/a68db684-2069-4341-a43d-ec27a288d797)

</p>

<h2>Ensure Connectivity between the Client and Domain controller</h2>
I remote desktoped into the client computer and pinged the domain controller’s private IP address with a perpetual ping.
<p>

![image](https://github.com/CamdenBodden/Configuring-Active-Directory-within-Azure-VMs/assets/114665835/9e240446-8b90-4f80-a023-46e6f17ba8eb)

</p>

<p>

![image](https://github.com/CamdenBodden/Configuring-Active-Directory-within-Azure-VMs/assets/114665835/b1673836-4a17-4900-9981-d7011058e9d3)

</p>
The pings failed because the domain controller's firewall was blocking the ICMPv4 ping. So I remote desktoped into the domain controller's computer and enabled the ICMPv4 in the Windows Firewall.
<p>

![image](https://github.com/CamdenBodden/Configuring-Active-Directory-within-Azure-VMs/assets/114665835/e06233fa-9d4e-45a4-be88-f2934302d53e)

</p>

<p>

![image](https://github.com/CamdenBodden/Configuring-Active-Directory-within-Azure-VMs/assets/114665835/d5107bc1-b606-4e82-8cd3-8084e7e3f668)

</p>
I was then able to ping successfully due to the Firewall on the domain controller allowing ICMPv4 traffic

<h2>Install Active Directory</h2>
The domain controller's virtual machine was not yet a domain controller. Once I installed Active Directory I had to promote the virtual machine by creating a new forest.

<p>

![image](https://github.com/CamdenBodden/Configuring-Active-Directory-within-Azure-VMs/assets/114665835/fbc22ff6-9095-4036-90e9-c6f08e0994a6)

</p>
---------------------------------------------------------------------------------------------------------------------------------------------------------------
<p>

![image](https://github.com/CamdenBodden/Configuring-Active-Directory-within-Azure-VMs/assets/114665835/eaeae98a-9a21-4467-afb8-a1886ecc6b14)

</p>
---------------------------------------------------------------------------------------------------------------------------------------------------------------
<p>

![image](https://github.com/CamdenBodden/Configuring-Active-Directory-within-Azure-VMs/assets/114665835/d26ad677-378f-4fce-996f-d9394b6ab43a)

</p>

<h2>Create an Admin Account in Active Directory</h2>

<p>



</p>

<h2>Join the Client Computer to the Domain Controller</h2>

<p>



</p>

<h2>Setup Remote Desktop for Non- administrative Users on the Client Computer</h2>

<p>



</p>

<h2>Creation of many users and attempt to log in to the client computer with one of the users</h2>

<p>



</p>
