
## Project Overview
This project demonstrates the configuration of VLANs and inter-VLAN communication using a router in GNS3. The network consists of multiple hosts connected to a switch, which is further connected to a router for routing between VLANs.

##  Network Design
<img width="769" height="585" alt="Vlan-Basics-12305354-network" src="https://github.com/user-attachments/assets/08ae2ab9-6cab-4e3a-a0e6-cbaa0d0f7a85" />
- 1 Switch
- 1 Router
- 4 Hosts
- VLAN segmentation implemented
- Inter-VLAN routing configured
## Configuration Summary
### VLAN Configuration
- VLAN 34 - Host1 & Host2
- VLAN 55 - Host3 & Host4
### Switch Configuration
- Ports assigned to VLANs
- Trunk port configured between switch and router

### Router Configuration
- Subinterfaces created
- IP addresses assigned for each VLAN
- Routing enabled between VLANs
  <img width="704" height="458" alt="Vlan-Basics-12305354-ports" src="https://github.com/user-attachments/assets/35691ad1-842f-4be9-9c8f-59a8e412f72b" />
<img width="836" height="366" alt="Vlan-Router-12305354-ports" src="https://github.com/user-attachments/assets/0c734ad8-0293-43ac-8a39-a6ca6018198f" />
<img width="540" height="258" alt="Vlan-Router-12305354-ports2" src="https://github.com/user-attachments/assets/56692435-5837-4135-88d3-e3770d4c01e1" />
<img width="836" height="366" alt="Vlan-Router-12305354-ports" src="https://github.com/user-attachments/assets/d77c544f-db95-4d44-b710-293aa3c34771" />

## Reflection
In this assignment, I learned how to configure VLANs and implement inter-VLAN routing using GNS3. Initially, I found it challenging to understand how devices in different VLAs communicate with each other. However, after configuring the switch ports and setting up router subinterfaces, I was able to clearly understand the concept.
One of the key learnings from this task was the importance of VLAN segmentation in improving network security and performance. Assigning different VLANs to different hosts helped in isolating traffic effectively. Additionally, configuring trunk ports between the switch and router was an important step in enabling communication between VLANs.
During testing, I observed that devices within the same VLAN could communicate easily, but communication between VLANs required proper router configuration. This helped me understand the practical implementation of routing in networks.
Overall, this assignment improved my practical networking skills and gave me hands-on experience with VLAN configuration, troubleshooting, and network design using GNS3.


