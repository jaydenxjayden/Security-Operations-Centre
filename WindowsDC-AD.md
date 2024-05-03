<h1>Domain Controller & Active Directory</h1>

<h2>Work in Progress... :construction_worker:</h2>

<h2>
  Objectives: <br>
  - Download and install Windows Server 2016 <br>
  - Turn the Windows Server into a Domain Controller (DC) by installing Active Driectory Domain Services <br>
  - Configuring Group Policy Management for DC <br>
</h2>

This is a network map of what the network looks like at the end of installation and configuration: <br>
   <img src="https://i.imgur.com/kFTjyc2.png" height="80%" width="80%" alt="DCAD"/> <br>  


1. After downloading and installing the Windows 2016 Server VM, I placed it into the LAN segment in VM settings.

   <img src="https://i.imgur.com/aTjrQxL.png" height="20%" width="20%" alt="DCAD"/>
   <img src="https://i.imgur.com/U15DMGc.png" height="53%" width="53%" alt="DCAD"/>
   
2. Once the VM is powered up, I am able to see the Server Manager GUI. I selected the local server > Ethernet0 to configure IP address, subnet mask, default gateway etc.

   <img src="https://i.imgur.com/hoU3snE.png" height="60%" width="60%" alt="DCAD"/>
   <img src="https://i.imgur.com/x2Bfvmh.png" height="40%" width="60%" alt="DCAD"/>   
   
3. Enabled Remote Desktop Protocol (RDP) and changed computer name to DC.

   <img src="https://i.imgur.com/S2eZ9IZ.png" height="60%" width="60%" alt="DCAD"/>
   <img src="https://i.imgur.com/5B4eTEg.png" height="60%" width="60%" alt="DCAD"/>

4. Proceed to install Active Directory Domain Service. Server Manger > Manage > add roles and features > ADDS > Add feature.

   <img src="https://i.imgur.com/aTjrQxL.png" height="40%" width="60%" alt="DCAD"/>
   <img src="https://i.imgur.com/U15DMGc.png" height="40%" width="30%" alt="DCAD"/>

1. After downloading and installing the Windows 2016 Server VM, I placed it into the LAN segment in VM settings.

   <img src="https://i.imgur.com/aTjrQxL.png" height="20%" width="20%" alt="DCAD"/>
   <img src="https://i.imgur.com/U15DMGc.png" height="53%" width="53%" alt="DCAD"/>
   
1. After downloading and installing the Windows 2016 Server VM, I placed it into the LAN segment in VM settings.

   <img src="https://i.imgur.com/aTjrQxL.png" height="20%" width="20%" alt="DCAD"/>
   <img src="https://i.imgur.com/U15DMGc.png" height="53%" width="53%" alt="DCAD"/>
         
