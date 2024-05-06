<h1>SIEM - ELK</h1>

<h2>
  Objectives: <br>
  - Download and install ELK stack <br>
  - Placing it within LAN segment, creating port forwarding rule to Kibana dashboard <br>
  - Configuration of ELK, downloading integrations to use ELK effectively as a SIEM <br>
</h2>

This is a network map of what the network looks like at the end of installation and configuration: <br>
   <img src="https://i.imgur.com/Zxh10q6.png" height="80%" width="80%" alt="SIEM"/> <br>  


1. Installed ELK stack on an Ubuntu server (VM). Add the VM into the LAN segment using VM settings.

   <img src="https://i.imgur.com/ohuL56L.png" height="40%" width="80%" alt="SIEM"/>

2. Power up the ELK VM, and ensure that elasticsearch, logstash and kibana services are running. 

   <img src="https://i.imgur.com/5MVNnGO.png" height="40%" width="80%" alt="SIEM"/>
   <img src="https://i.imgur.com/pr5Dzfj.png" height="40%" width="80%" alt="SIEM"/>
   <img src="https://i.imgur.com/XrknTfQ.png" height="40%" width="80%" alt="SIEM"/>  
   
4. Configured their respective configuration (yaml) files.

   <img src="https://i.imgur.com/4YXb0qK.png" height="40%" width="80%" alt="SIEM"/>
   <img src="https://i.imgur.com/nzxwXAm.png" height="40%" width="80%" alt="SIEM"/>
   <img src="https://i.imgur.com/XzAEVrx.png" height="40%" width="80%" alt="SIEM"/>

5. Checking that the ELK is part of the LAN segment and has been assigned the correct IP.

   <img src="https://i.imgur.com/Bbn2T8N.png" height="40%" width="40%" alt="SIEM"/>

6. Created a port forwarding rule in pfsense to allow access from main machine to Kibana (WAN to ELK) over port 5601.

   <img src="https://i.imgur.com/LbScMH2.png" height="80%" width="80%" alt="SIEM"/>
   <img src="https://i.imgur.com/VlIrfjU.png" height="50%" width="50%" alt="SIEM"/>
   
7. Installing beats on DC so that logs from DC are sent to ELK.

   <img src="https://i.imgur.com/TA7YryW.png" height="40%" width="60%" alt="SIEM"/>
   <img src="https://i.imgur.com/uNNUpvj.png" height="40%" width="60%" alt="SIEM"/>
   <img src="https://i.imgur.com/OpOKtem.png" height="40%" width="40%" alt="SIEM"/>
   
8. Changing the username and password accordingly in the yml file.

   <img src="https://i.imgur.com/E7gvpk7.png" height="40%" width="80%" alt="SIEM"/>

9. Installed elasticagent using PowerShell, and replaced the elastic-agent.yml file with the one that was edited (with correct credentials).

   <img src="https://i.imgur.com/9JLn47D.png" height="40%" width="60%" alt="SIEM"/>
   <img src="https://i.imgur.com/9RprpkI.png" height="40%" width="60%" alt="SIEM"/>
   <img src="https://i.imgur.com/5ZaqSon.png" height="40%" width="60%" alt="SIEM"/>

10. Finding the elastic agent in services.msc. Actions such as clearing security logs in DC will be sent to ELK.

   <img src="https://i.imgur.com/Ta9WJus.png" height="40%" width="80%" alt="SIEM"/>
   <img src="https://i.imgur.com/X7SYemA.png" height="40%" width="80%" alt="SIEM"/>
   <img src="https://i.imgur.com/lpCiyq7.png" height="40%" width="80%" alt="SIEM"/>

11. Next would be installing an agent on the linux web server in DMZ. Similar process as steps 8 & 9, but we will be using 'Auth0' for integration instead. mobaXterm will also be used for convenience.

   <img src="https://i.imgur.com/7fpn0yk.png" height="40%" width="40%" alt="SIEM"/>
   <img src="https://i.imgur.com/5x9xcWo.png" height="40%" width="40%" alt="SIEM"/>
   <img src="https://i.imgur.com/IrwcihT.png" height="40%" width="80%" alt="SIEM"/>
   <img src="https://i.imgur.com/ItgVQgn.png" height="40%" width="80%" alt="SIEM"/>
   <img src="https://i.imgur.com/F3j3VJA.png" height="40%" width="80%" alt="SIEM"/>
   <img src="https://i.imgur.com/CoREJxc.png" height="40%" width="40%" alt="SIEM"/>
   <img src="https://i.imgur.com/ZMPF3GO.png" height="40%" width="80%" alt="SIEM"/>
   <img src="https://i.imgur.com/rj5aFsf.png" height="40%" width="80%" alt="SIEM"/>
   <img src="https://i.imgur.com/zkYv0aB.png" height="40%" width="80%" alt="SIEM"/>

12. I will also configure pfsense to ensure the firewall logs are sent to ELK as well.

   <img src="https://i.imgur.com/lTJKsCd.png" height="40%" width="80%" alt="SIEM"/>
   <img src="https://i.imgur.com/tOiJcNd.png" height="40%" width="40%" alt="SIEM"/>
   <img src="https://i.imgur.com/U7tgzsh.png" height="40%" width="80%" alt="SIEM"/>

13. Lastly, to ensure that all machines' time are synchronized. (linux web server, ELK, DC, pfsense)

   <img src="https://i.imgur.com/Ah2UGG9.png" height="40%" width="40%" alt="SIEM"/>
   <img src="https://i.imgur.com/IW9sDTN.png" height="40%" width="40%" alt="SIEM"/>
   <img src="https://i.imgur.com/sICZv9W.png" height="40%" width="40%" alt="SIEM"/>
   <img src="https://i.imgur.com/8M3krnk.png" height="40%" width="40%" alt="SIEM"/>

