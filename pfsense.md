<h2>
  Objectives: <br>
  - Download and install pfSense system <br>
  - Set up 3 network interface cards; WAN, LAN and DMZ <br>
  - Configure each NIC. 
  - Implementing an Access Control List (ACL) using Pfblockerng <br>
</h2>

This is a network map of what the network looks like at the end of installation and configuration: <br>
   <img src="https://i.imgur.com/ndbAJ63.png" height="80%" width="80%" alt="firewall"/> <br>  


1. The firewall that I will be using for my SOC would be the open-source firewall and router: pfSense. Downloaded it from the website.

   <img src="https://i.imgur.com/Qrwi3A1.png" height="40%" width="40%" alt="firewall"/>

2. After the download is complete, I proceed with the installation of pfSense; similar to the installation of VMs.

   <img src="https://i.imgur.com/CnWlwva.png" height="40%" width="80%" alt="firewall"/>
   <img src="https://i.imgur.com/YDMQr4d.png" height="40%" width="40%" alt="firewall"/>
   <img src="https://i.imgur.com/4VB5mJF.png" height="40%" width="40%" alt="firewall"/>
   <img src="https://i.imgur.com/LpWltkd.png" height="40%" width="40%" alt="firewall"/>
   <img src="https://i.imgur.com/0KAvn89.png" height="40%" width="40%" alt="firewall"/>
   <img src="https://i.imgur.com/3Gmc9rH.png" height="40%" width="40%" alt="firewall"/>
   <img src="https://i.imgur.com/LpWltkd.png" height="40%" width="40%" alt="firewall"/>
   <img src="https://i.imgur.com/5VYebND.png" height="40%" width="40%" alt="firewall"/>
   <img src="https://i.imgur.com/Qg6iGRH.png" height="40%" width="40%" alt="firewall"/>
   
3. I added LAN segments; Network Adapter > LAN segments > Add.

   <img src="https://i.imgur.com/aoMA5hp.png" height="60%" width="60%" alt="firewall"/>
   <img src="https://i.imgur.com/QOscAO3.png" height="40%" width="80%" alt="firewall"/>
   <img src="https://i.imgur.com/pZsOmTm.png" height="40%" width="40%" alt="firewall"/>
   <img src="https://i.imgur.com/xIU6O29.png" height="40%" width="40%" alt="firewall"/>
   
4. Create a second LAN segment named DMZ.

   <img src="https://i.imgur.com/J8qJnLY.png" height="60%" width="60%" alt="firewall"/>
   
5. Closed the hardware window and finish the installation. Reboot after installation is completed.

   <img src="https://i.imgur.com/gS2gCM6.png" height="40%" width="40%" alt="firewall"/>
   <img src="https://i.imgur.com/sKoVk4V.png" height="40%" width="40%" alt="firewall"/>
   <img src="https://i.imgur.com/eqWfZdG.png" height="40%" width="40%" alt="firewall"/>
   <img src="https://i.imgur.com/Q63KUUq.png" height="40%" width="40%" alt="firewall"/>
   
6. After reboot, I set up the 3 different networks: WAN, LAN and DMZ; select option 1 (assign interfaces).

   <img src="https://i.imgur.com/KSx5F9z.png" height="40%" width="80%" alt="firewall"/>
   <img src="https://i.imgur.com/R7VCXXZ.png" height="40%" width="80%" alt="firewall"/>

7. Next would be to set the IP address for each interface manually; select option 2 (set interface(s) IP address). 

   <img src="https://i.imgur.com/jeH2P8J.png" height="40%" width="60%" alt="firewall"/>

8. IP for LAN subnet will be 172.16.50.0/24, with 172.16.50.1 as the default gateway.

   <img src="https://i.imgur.com/7JsRY9b.png" height="30%" width="50%" alt="firewall"/>
   <img src="https://i.imgur.com/uoiHJjO.png" height="30%" width="50%" alt="firewall"/>

9. Repeat the above steps for DMZ subnet. Current settings on pfSense.

   <img src="https://i.imgur.com/8R911tS.png" height="40%" width="80%" alt="firewall"/>

10. Move my current Win10 VM and Linux Server into LAN and DMZ network segment respectively; network adapter > LAN segments

   <img src="https://i.imgur.com/U0KdE7h.png" height="60%" width="60%" alt="firewall"/>

11. Win10: set static IP and use default gateway of LAN as DNS server.

   <img src="https://i.imgur.com/t3HU4iL.png" height="40%" width="80%" alt="firewall"/>

12. Linux Server: edit config.yaml file > set static IP and default gateway.

   <img src="https://i.imgur.com/91k3P2t.png" height="30%" width="80%" alt="firewall"/>
   <img src="https://i.imgur.com/Dn0n7il.png" height="40%" width="40%" alt="firewall"/>

13. Once done, I accessed the web interface to start the set up.

   <img src="https://i.imgur.com/eJDynym.png" height="40%" width="40%" alt="firewall"/>
   <img src="https://i.imgur.com/gRilk00.png" height="60%" width="60%" alt="firewall"/>
   <img src="https://i.imgur.com/SbW2Vhn.png" height="40%" width="40%" alt="firewall"/>

14. Created firewall rules; firewall > rules > edit, to allow access from WAN

   <img src="https://i.imgur.com/JujEVAY.png" height="60%" width="60%" alt="firewall"/>

15. Create rules to allow access from LAN to internet.

   <img src="https://i.imgur.com/CB9dhYi.png" height="60%" width="60%" alt="firewall"/>

16. Create port forwarding for Linux Web Server; firewall > NAT > port forward > edit > forward WAN IP port 8080 to web server port 80 in DMZ.

   <img src="https://i.imgur.com/18ysVmE.png" height="80%" width="60%" alt="firewall"/>
   <img src="https://i.imgur.com/L8l3ksD.png" height="40%" width="60%" alt="firewall"/>   

17. Create rule to allow access from DMZ to any that is not LAN.

   <img src="https://i.imgur.com/59HvpmW.png" height="60%" width="60%" alt="firewall"/>

18. I installed pfblockerng mainly for its DNSBL (DNS Block List), to block known malicious websites; System > Package Manager > Package Installer

   <img src="https://i.imgur.com/KSzxmIX.png" height="40%" width="50%" alt="firewall"/>

19. Firewall > pfblockerng > enable > enable DNSBL (DNS block list) > unbound mode > source definitions https://github.com/StevenBlack/hosts > force update > run to apply changes

   <img src="https://i.imgur.com/GB8VFec.png" height="40%" width="40%" alt="firewall"/>
   <img src="https://i.imgur.com/uUfmFiM.png" height="40%" width="40%" alt="firewall"/>

20. When trying to access a website that is blocked, user will be met with this alert

   <img src="https://i.imgur.com/CJgBh86.png" height="30%" width="60%" alt="firewall"/>
