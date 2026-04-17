

# Task 1 – ARP (Address Resolution Protocol)

## Network Topology
<img width="1049" height="724" alt="Setting-IP-12305354" src="https://github.com/user-attachments/assets/e5131ad1-b791-4cb5-a29f-1fd065dba4c9" />

* Four hosts: A, B, C, D
* Connected via a Layer 2 switch
* Same subnet: 192.168.0.0/24


---

## Commands Used


ip addr show
ip neigh show
ping -c 3 <destination_ip>


---

## ARP Table Observations (Host A)
<img width="960" height="830" alt="ARP-Basics-12305354-HostA" src="https://github.com/user-attachments/assets/fa3d57d1-adf4-4479-b323-d80fbfe6f9ca" />

### Initial State

* **Command:** ip neigh show

* **Result:**

  * No ARP entries present

* **Explanation:**

  * Host A has not communicated with any devices yet
  * No IP-to-MAC mappings exist in the ARP cache

---

### After Pinging 192.168.0.3 (Host C)
<img width="1051" height="616" alt="ARP-Basics-12305354-HostC" src="https://github.com/user-attachments/assets/e2d52fd8-db0a-43d9-b676-6ab5b0ae6ccc" />


ping -c 3 192.168.0.3


* **Result:**

  * 3 packets transmitted, 3 received (0% packet loss)
  * Low latency (~0.02–0.04 ms)

* **ARP Change:**

  * Entry added for 192.168.0.3
  * MAC address learned and stored
  * State: REACHABLE

* **Explanation:**

  * Host A sends an ARP request (broadcast)
  * Host C replies with its MAC address
  * Mapping is stored in Host A’s ARP table

---

### After Pinging 192.168.0.1


ping -c 3 192.168.0.1

* **Result:**

  * 3 packets transmitted, 3 received (0% packet loss)
  * Latency ~0.12–0.44 ms

* **ARP Change:**

  * Entry added for 192.168.0.1
  * Multiple ARP entries now exist
  * States: REACHABLE

* **Explanation:**

  * Another ARP request/reply cycle occurs
  * Host A learns additional IP-to-MAC mappings

---

### After Communication from Host C to Host A

* **ARP Change:**

  * Existing entry for Host C is refreshed
  * State remains `REACHABLE` or may transition to `STALE` over time

* **Explanation:**

  * Incoming traffic updates ARP cache timers
  * Frequently used entries remain active

---

## Summary of ARP Behavior

* ARP table starts empty
* Entries are added dynamically after communication
* Each entry maps:

  * IP address → MAC (hardware) address
* ARP uses broadcast requests and unicast replies
* Entries may change state over time:

  * `REACHABLE`, `STALE`, etc.

---
## Key Networking Insights
- All hosts are in the same subnet → direct communication
- No router is required
- Switch forwards ARP broadcast to all devices
- Communication occurs using MAC addresses after ARP resolution
##  Reflection
This lab helped me understand how ARP works in a practical environment rather than just theory. Initially, I assumed devices could communicate directly using IP addresses, but this exercise showed that MAC address resolution is a necessary step in local networks.

One important observation was that the ARP table is empty before any communication. This highlights that ARP is a dynamic protocol that only stores information when needed. After performing ping operations, I could see how entries were created automatically, which made the process much clearer.

Another key takeaway is the role of broadcasts in ARP. When Host A needed to find another device, it sent a broadcast request to all devices in the network. This demonstrated how switches handle broadcast traffic and how only the correct host responds.

I also noticed that once an ARP entry is created, subsequent communication becomes more efficient because the MAC address is already known. This reduces network overhead and improves performance.

## task -2
<img width="1838" height="772" alt="Default-Gateway-12305354-network" src="https://github.com/user-attachments/assets/02ad2d24-a9e6-4adb-901a-5b8a55550af6" />


### Left LAN (192.168.0.0/24)

#### HOST 1

<img width="834" height="813" alt="host1" src="https://github.com/user-attachments/assets/85ba67a1-3be4-4316-8a60-7143a1dccee3" />

##### HOST 2

<img width="955" height="331" alt="host2" src="https://github.com/user-attachments/assets/3c2675bd-452d-4da8-b5aa-17ae724e9d75" />

| Device  | IP Address   | Default Gateway |
|---------|--------------|-----------------|
| Host1   | 192.168.0.2  | 192.168.0.1     |
| Host2   | 192.168.0.3  | 192.168.0.1     |
| Router1 | 192.168.0.1  | -               |

### Right LAN (192.168.1.0/24)
#### HOST 3

<img width="934" height="570" alt="host3" src="https://github.com/user-attachments/assets/e67f8883-b58d-4fc9-b693-366de631e571" />

#### HOST 4

<img width="954" height="388" alt="host4" src="https://github.com/user-attachments/assets/afe038b9-f251-419c-af10-bdb36f316345" />

| Device  | IP Address   | Default Gateway |
|---------|--------------|-----------------|
| Host3   | 192.168.1.2  | 192.168.1.1   |
| Host4   | 192.168.1.3  | 192.168.1.1   |
| Router2 | 192.168.1.1  | -               |



### Router1

<img width="612" height="275" alt="router1" src="https://github.com/user-attachments/assets/2f3b0e69-4f90-45d0-b71c-cffee0d52e5d" />


ip addr add 192.168.0.1/24 dev eth0
ip route add 192.168.1.0/24 via <Router2-Link-IP>

###  Router2
ip addr add 192.168.1.1/24 dev eth0
ip route add 192.168.0.0/24 via <Router1-Link-IP>

### Test Ping

<img width="1102" height="852" alt="Communication ping" src="https://github.com/user-attachments/assets/e267ab20-b919-4a44-abe5-abc3f9738ffb" />


ping 192.168.1.2

### Expected Result
- Successful communication between subnets
- 0% packet loss

## Key Concept
- Devices in different subnets **cannot communicate directly**
- Traffic must go through a router (default gateway)
- Each subnet has its own gateway:
  - Left LAN - 192.168.0.1
  - Right LAN - 192.168.1.1

## Reflection

During this lab, I initially configured the same default gateway (192.168.0.1) for all hosts, but this caused communication issues for devices in the 192.168.1.0 network. This helped me realize that a default gateway must always belong to the same subnet as the host.

After correcting the gateway for Host3 and Host4 to 192.168.1.1, the network started working correctly. This demonstrated the importance of proper IP addressing and gateway configuration.

I also learned that routers act as intermediaries between networks, and without correct routing and gateway settings, devices cannot communicate across subnets.

![Network](images/12279834-defult gateway.gns3project)


