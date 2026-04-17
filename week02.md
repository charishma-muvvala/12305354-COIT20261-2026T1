# Week 2 Encapsulation and Decapsulation.

## Project Overview
This project demonstrates how to configure IP addresses on multiple hosts in GNS3 and test connectivity using ping commands. It focuses on basic networking concepts such as IP addressing and troubleshooting.

## Network Topology
<img width="1096" height="661" alt="Setting-IP-12305354-network" src="https://github.com/user-attachments/assets/fd77c43e-31c5-42c5-bd6e-41a0f3e93c24" />
<img width="727" height="532" alt="Setting-IP-12305354-host2" src="https://github.com/user-attachments/assets/6de4b86c-cbb2-470a-a7e0-b315a487f760" />

The network includes:
- 1 Switch
- 4 Hosts (Host1, Host2, Host3, Host4)

All hosts are connected to a central switch.

## IP Address Configuration
<img width="649" height="503" alt="Setting-IP-12305354-host3" src="https://github.com/user-attachments/assets/f92cf600-e1bd-4bb2-8b03-07e85dce1637" />
<img width="926" height="340" alt="Setting-IP-12305354-host4" src="https://github.com/user-attachments/assets/aef66706-256c-44da-9a41-3507c78ff734" />
Each host is configured with a static IP address in the same subnet:
- Host1 - 10.1.1.1 /24  
- Host2 - 10.1.1.2 /24  
- Host3 - 10.1.1.3 /24  
- Host4 - 10.1.1.4 /24  

### Command used to verify:

ip address show

## Connectivity Testing
<img width="742" height="450" alt="Ping-Basics-12305354-simple" src="https://github.com/user-attachments/assets/e560f9a9-e78b-4789-98b4-dd295e8ed68d" />
<img width="742" height="450" alt="Ping-Basics-12305354-simple" src="https://github.com/user-attachments/assets/e560f9a9-e78b-4789-98b4-dd295e8ed68d" />
<img width="489" height="187" alt="Ping-Basics-12305354-options" src="https://github.com/user-attachments/assets/c8904f25-4c26-4a21-8a16-df0711d99682" />
<img width="698" height="244" alt="Ping-Basics-1205354-error" src="https://github.com/user-attachments/assets/3db3c1e1-d846-4730-b643-5bef0983057b" />

### 1. Simple Ping
ping 10.1.1.2
Result:
- Successful communication
- 0% packet loss

## 2. Ping to Wrong IP

ping 10.1.1.10
Result:
- Destination Host Unreachable
- 100% packet loss

# Ping with Options

ping -c 5 -s 2 -i 2 10.1.1.2

Explanation:
- -c 5 - send 5 packets
- -s 2 - packet size
- -i 2 - interval between packets

Result:
- Controlled ping execution
- Successful communication

##  Reflection

In this assignment, I learned how to configure IP addresses manually on different hosts in GNS3. Initially, it was difficult to understand how devices communicate through a switch, but after assigning IP addresses in the same subnet, the concept became clear.

The `ip address show` command helped me verify configurations. The ping command was useful for testing connectivity. A successful ping confirmed communication, while a wrong IP resulted in "Destination Host Unreachable," helping me understand errors.

Using ping with options improved my understanding of advanced testing. Overall, this assignment enhanced my practical networking skills and knowledge of troubleshooting.



