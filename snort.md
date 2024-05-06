<h1>Snort</h1>

<h2>
  Objectives: <br>
  - Download and install snort <br>
  - Configure it to act as an Intrusion Detection System (IDS) <br>
  - Create snort rules to send alerts <br>
</h2>

This is a network map of what the network looks like at the end of installation and configuration: <br>
   <img src="https://i.imgur.com/CCRkO8X.png" height="80%" width="80%" alt="IDS"/> <br>  


1. I chose snort as the IDS solutions as it can be easily installed using pfsense's package manager.

   <img src="https://i.imgur.com/kPYqbMG.png" height="40%" width="80%" alt="IDS"/>
   <img src="https://i.imgur.com/EpHec8f.png" height="40%" width="80%" alt="IDS"/>

2. Configuration of the snort interfaces after installation.

    <img src="https://i.imgur.com/ZiqrNW0.png" height="80%" width="80%" alt="IDS"/>
   
3. Going to snort interfaces to create rules under custom.rules for LAN, and testing whether it works.

   <img src="https://i.imgur.com/NCdkwlO.png" height="40%" width="80%" alt="IDS"/>
   <img src="https://i.imgur.com/gW9ZOSn.png" height="40%" width="80%" alt="IDS"/>

4. Creating snort rules for DMZ interface.

   <img src="https://i.imgur.com/FCLkTNr.png" height="40%" width="80%" alt="IDS"/>
