# DHCP-Relay-and-ACL-Lab
Cisco router lab simulating DHCP Relay configuration with optional ACL filtering for real-world enterprise scenarios.

 [PC] --- [SW] --- R1 (Cisco 1921) --- R2 (Cisco 4331)
                      |                    |
              192.168.10.0/24       192.168.100.0/24
                      |_______10.0.0.0/30________|
## 📦 Device Roles
## R1 (Cisco 1921): Acts as a DHCP Relay Agent

## R2 (Cisco 4331): Configured as the DHCP Server

## 🔧 Configuration Summary
## R1 – DHCP Relay (Cisco 1921)

## hostname R1
## interface GigabitEthernet0/0
 ip address 192.168.10.1 255.255.255.0
 no shutdown

## interface GigabitEthernet0/1
 ip address 10.0.0.1 255.255.255.252
 no shutdown

## ip helper-address 10.0.0.2

## ip route 192.168.100.0 255.255.255.0 10.0.0.2
## R2 – DHCP Server (Cisco 4331)
## hostname R2
interface GigabitEthernet0/0
 ip address 192.168.100.1 255.255.255.0
 no shutdown

## interface GigabitEthernet0/1
 ip address 10.0.0.2 255.255.255.252
 no shutdown

## ip dhcp excluded-address 192.168.10.1 192.168.10.10

## ip dhcp pool VLAN10
 network 192.168.10.0 255.255.255.0
 default-router 192.168.10.1
 dns-server 8.8.8.8

## ip route 192.168.10.0 255.255.255.0 10.0.0.1

## ✅ Results
## PCs connected to R1’s LAN (192.168.10.0/24) receive IP addresses via DHCP

## Routing works between subnets via static routes

## Relay function successfully tested

## 💡 Notes
## Make sure the switch is forwarding traffic properly.

## Disable Wi-Fi on the PC and ensure it's connected via Ethernet.

## Optional: ACLs can be added on R1 to restrict traffic based on source IPs.
## Contact 
https://github.com/IlkinNureddinov
