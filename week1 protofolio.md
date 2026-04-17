# Week 1 Introduction to Internetworking

## Task Overview

This task involved creating a basic project in GNS3 to understand:

* Project creation
* Adding and configuring a Linux host
* Assigning a static IP address
* Using the console to verify configuration


## Steps Performed

1. Created a new project named:
   **GNS3-Intro-<studentid>**

2. Added a Linux host node

3. Configured static IP address by editing:
   /etc/network/interfaces

4. Started the node

5. Opened console and ran command:

ip address show



## Output Screenshots

### Network Topology

<img width="1249" height="610" alt="GNS-Intro-12305354-network" src="https://github.com/user-attachments/assets/7f7047f7-2424-4c14-bb45-e02619acd7bd" />

### IP Address Output

<img width="902" height="276" alt="GNS-Intro-12305354-ipaddress" src="https://github.com/user-attachments/assets/5e973158-d6c5-4447-856b-f1a4c4b5bb96" />

### GNS3 file 

## Learnings

* Learned how to create and manage GNS3 projects
* Understood how to configure static IP addresses in Linux
* Learned basic Linux networking commands
* Understood the importance of disabling IP forwarding for hosts



## Challenges Faced

* Initial confusion while editing `/etc/network/interfaces`
* Ensuring correct syntax and formatting of IP configuration
* Verifying whether the IP was correctly applied



## Reflection

This task provided a practical introduction to network simulation using GNS3. I developed a better understanding of how networking concepts such as IP addressing are applied in a real environment. Configuring the IP address manually helped me understand the structure of network configuration files in Linux.

One key learning was the importance of accuracy when editing configuration files, as even small mistakes can lead to incorrect setups. I also learned how to verify configurations using command-line tools, which is an essential skill in networking and cybersecurity.

In future tasks, I will aim to improve my confidence in using Linux commands and explore more advanced GNS3 features such as connecting multiple devices and testing network communication between them.



## Conclusion

This task helped build foundational skills in GNS3 and Linux networking, which are essential for future networking and cybersecurity tasks.




