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

   <img src="https://i.imgur.com/Zpg0Vr4.png" height="70%" width="70%" alt="DCAD"/>
   <img src="https://i.imgur.com/ol4I2t5.png" height="30%" width="30%" alt="DCAD"/>

5. Installed the service with default configurations and promote the server to a DC. 

   <img src="https://i.imgur.com/0s6xwnw.png" height="40%" width="40%" alt="DCAD"/>
   <img src="https://i.imgur.com/l37E5oi.png" height="60%" width="60%" alt="DCAD"/>
   
6. I added a new forest and named the root domain 'mydomain.local'.

   <img src="https://i.imgur.com/5HKtWxt.png" height="40%" width="40%" alt="DCAD"/>
         
7. Setting passwords and configurations for new domain.

   <img src="https://i.imgur.com/2p3ICvu.png" height="40%" width="40%" alt="DCAD"/>
   <img src="https://i.imgur.com/pWGd8He.png" height="40%" width="40%" alt="DCAD"/>

8. Complete the pre-requisite checks and install. Ensure that 'workgroup' has changed to 'mydomain.local'.

   <img src="https://i.imgur.com/KZ1ZjFP.png" height="40%" width="40%" alt="DCAD"/>
   <img src="https://i.imgur.com/K2Coivg.png" height="40%" width="40%" alt="DCAD"/>
   <img src="https://i.imgur.com/j6Y9zFf.png" height="40%" width="40%" alt="DCAD"/>

9. Aside from promoting it to DC, I also installed the DHCP server, to make the DC the DHCP of the LAN segment.

   <img src="https://i.imgur.com/qyDvlUM.png" height="40%" width="60%" alt="DCAD"/>
   <img src="https://i.imgur.com/muyQp0P.png" height="40%" width="60%" alt="DCAD"/>
         
10. After making the DC the DHCP server, we put in place some rules so that certain IP addresses are reserved.

   <img src="https://i.imgur.com/NYZGr4q.png" height="60%" width="60%" alt="DCAD"/>
   <img src="https://i.imgur.com/KN212G2.png" height="40%" width="40%" alt="DCAD"/>
   <img src="https://i.imgur.com/eRRbBiQ.png" height="40%" width="40%" alt="DCAD"/>
   <img src="https://i.imgur.com/u09UXhV.png" height="40%" width="40%" alt="DCAD"/>
   <img src="https://i.imgur.com/Lj62gIK.png" height="40%" width="40%" alt="DCAD"/>
   <img src="https://i.imgur.com/abw5lAE.png" height="40%" width="40%" alt="DCAD"/>

11. I placed my kali VM into the LAN segment to verify. It was assigned the IP 172.16.50.51!

   <img src="https://i.imgur.com/Ur4a3SX.png" height="80%" width="80%" alt="DCAD"/>

12. I moved my Win10 VM into the new domain, and set the DNS server of Win10 to DC.

   <img src="https://i.imgur.com/phyNYNT.png" height="60%" width="60%" alt="DCAD"/>
         
13. Change the workgroup of the Win10 to mydomain.local, key in the credentials and restart the VM.

   <img src="https://i.imgur.com/GVxOtmu.png" height="60%" width="60%" alt="DCAD"/>
   <img src="https://i.imgur.com/J5rzxoV.png" height="60%" width="60%" alt="DCAD"/>

14. Going back to Server Manager, I proceed to create a Group Policy Object (GPO) under mydomain.local named 'FrontDesk' as an example.

   <img src="https://i.imgur.com/aKGWyXu.png" height="30%" width="30%" alt="DCAD"/>
   <img src="https://i.imgur.com/4B4UNnK.png" height="30%" width="30%" alt="DCAD"/>
   <img src="https://i.imgur.com/n1u9BSj.png" height="20%" width="20%" alt="DCAD"/>

15. Creating a user 'soc1' in AD Users and Computers. 

   <img src="https://i.imgur.com/7FVy9y9.png" height="60%" width="60%" alt="DCAD"/>
   <img src="https://i.imgur.com/9a2gj2H.png" height="40%" width="40%" alt="DCAD"/>
   <img src="https://i.imgur.com/9aJo3IC.png" height="40%" width="40%" alt="DCAD"/>
         
16. Add 'soc1' as the user to be affected by the new GPO 'FrontDesk'.

   <img src="https://i.imgur.com/44qunuh.png" height="50%" width="50%" alt="DCAD"/>

17. Proceed to configure policies that affect 'FrontDesk' GPO by going to Group Policy Management (GPM) editor.

   <img src="https://i.imgur.com/ImnX3U1.png" height="40%" width="60%" alt="DCAD"/>
   
18. Restrict the use of command prompt by 'FrontDesk'. Enable the rule.

   <img src="https://i.imgur.com/3nrjWsK.png" height="40%" width="40%" alt="DCAD"/>
   <img src="https://i.imgur.com/2zfr3yw.png" height="40%" width="40%" alt="DCAD"/>
   <img src="https://i.imgur.com/ev8Tx0Q.png" height="40%" width="60%" alt="DCAD"/>

19. Login to soc1 user and verify that command prompt is disabled. It works!

   <img src="https://i.imgur.com/D6VWZyg.png" height="40%" width="40%" alt="DCAD"/>

20. Configure audit policies for computer for logging of the following; Account Logon, Account Management, Logon/Logoff, Object Access, Policy Change and System.

   <img src="https://i.imgur.com/YtjZT8L.png" height="60%" width="60%" alt="DCAD"/>
   <img src="https://i.imgur.com/SS6s0eC.png" height="40%" width="40%" alt="DCAD"/>
   <img src="https://i.imgur.com/bFuoxSA.png" height="40%" width="40%" alt="DCAD"/>
   <img src="https://i.imgur.com/RViHjl4.png" height="40%" width="40%" alt="DCAD"/>
   <img src="https://i.imgur.com/oMzT5pA.png" height="40%" width="40%" alt="DCAD"/>
   <img src="https://i.imgur.com/UAvSY6d.png" height="40%" width="40%" alt="DCAD"/>
   <img src="https://i.imgur.com/EOLnckx.png" height="40%" width="40%" alt="DCAD"/>

21. Test if events do get logged by creating a new user and checking if its logged in security log. It works!
    
   <img src="https://i.imgur.com/flS53YD.png" height="40%" width="40%" alt="DCAD"/>
   <img src="https://i.imgur.com/AWhoBWQ.png" height="40%" width="40%" alt="DCAD"/>
   

