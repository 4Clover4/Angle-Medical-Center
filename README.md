

### **Switch Hardening Security Measures**

| **Security Action**                       | **Description**                                                                 | **Example Command**                                                                                                                                      |
|-------------------------------------------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Set Strong Passwords**                  | Set strong passwords for management access to prevent unauthorized access.      | `enable secret <strong-password>`                                                                                                                      |
| **Enable SSH for Remote Management**      | Disable Telnet and use SSH for encrypted remote access.                         | `ip ssh version 2`                                                                                                                                      |
| **Disable Unused Ports**                  | Disable unused ports to prevent unauthorized devices from accessing the network. | `interface range f 0/12 - 20` <br> `shutdown`                                                                                         |
| **Port Security (MAC Address Limiting)**  | Limit the number of allowed MAC addresses per port to prevent MAC address spoofing. | `switchport port-security` <br> `switchport port-security maximum 2`                                                                                   |
| **Port Security (Violation Action)**      | Define what happens when a security violation occurs, like an unknown MAC address. | `switchport port-security violation **restrict**`                                                                                                          |
| **Port Security (Sticky MAC Addresses)**  | Allow the switch to dynamically learn and bind MAC addresses to a port.         | `switchport port-security mac-address **sticky**`                                                                                                          |
| **Enable BPDU Guard**                     | Protect against malicious STP attacks by disabling BPDU on vulnerable ports.     | `spanning-tree **bpduguard** enable`                                                                                                                       |
| **Disable CDP (Cisco Discovery Protocol)**| Prevent revealing network topology by disabling CDP.                            | `no cdp run`                                                                                                                                           |
| **Trunk Port Security**                   | Restrict allowed VLANs on trunk ports to avoid unauthorized VLAN traffic.        | `switchport trunk allowed vlan 10,20,30,40,50,60,70,80,90,100` |

####  
Switch hardening ensures that only authorized devices can access the network by limiting port access, protecting management access with strong encryption, and preventing network topology exposure.

The **switchport port-security violation restrict** command specifies that if a security violation occurs (such as when an unauthorized MAC address is detected), the port will restrict the connection rather than shutting it down. The port will continue to function, but any traffic from unauthorized MAC addresses will be dropped, and a log entry will be created. This option is useful to avoid disrupting network connectivity while still enforcing security.
The **restrict** option is chosen over `shutdown` or `protect` because it prevents unauthorized devices from accessing the network without disabling the entire port, allowing for continued operation but with more controlled access.

The **switchport port-security mac-address sticky** command enables the switch to dynamically learn and save the MAC addresses of devices connected to the port. These learned MAC addresses are then stored in the running configuration, allowing the switch to automatically permit these addresses in future connections.

The **spanning-tree bpduguard enable** command protects the network by disabling a port if it receives a Bridge Protocol Data Unit (BPDU), preventing potential spanning tree loops caused by unauthorized devices.

The command **no cdp run** disables the Cisco Discovery Protocol (CDP) on a device, preventing it from sending or receiving CDP information, which is used for discovering neighboring Cisco devices and their details.

### **Router Hardening Security Measures**

| **Security Action**                       | **Description**                                                                  | **Example Command**                                                                                                                                          |
|-------------------------------------------|----------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Set Strong Passwords**                  | Use strong, encrypted passwords for protecting router management access.          | `enable secret <strong-password>`                                                                                                                          |
| **Enable Encrypted Password Storage**     | Store passwords securely by encrypting them.                                     | `service password-encryption`                                                                                                                             |
| **Disable Unused Services**               | Disable unnecessary services to reduce the attack surface.                        | `no ip http server` <br> `no ip http secure-server`                                                                                                       |
| **Disable CDP**                           | Disable CDP to prevent revealing sensitive network information.                  | `no cdp run`                                                                                                                                               |
| **Enable SSH for Remote Management**      | Disable Telnet and enable SSH for encrypted remote management.                   | `ip ssh version 2` <br> `line vty 0 4` <br> `transport input ssh`                                                                                        |
| **Enable NAT (Network Address Translation)**| Protect internal networks by translating private IP addresses to public ones.    | `ip nat inside source list 1 interface gigabitEthernet 0/0 *overload*` <br> `access-list 1 permit 192.168.0.0 0.0.255.255`                                 |
| **OSPF Hardening**                        | Use authentication to secure OSPF communications between routers.                | `router **ospf** 66` <br> `area 0 `                                                                                              |
| **Access Control Lists (ACLs)**           | Control traffic flow to prevent unauthorized access between networks.           | `access-list 130 deny ip 192.168.40.0 0.0.0.255 192.168.10.0 0.0.0.255`                                                                                  |

####  
Router hardening focuses on securing management access, reducing unnecessary attack surfaces, and protecting the internal network by utilizing NAT, ACLs, and secure routing protocols like OSPF.

The **overload** keyword in the command `ip nat inside source list 1 interface gigabitEthernet 0/0 overload` enables Port Address Translation (PAT), allowing multiple internal devices to share a single public IP address. Each device’s connection is distinguished by a unique port number, saving public IP addresses.

**OSPF** (Open Shortest Path First) is a link-state routing protocol used to find the best path for data exchange in an IP network, by calculating the shortest path first based on the network's topology.
                                                                                          |

####  
Securing protocols ensures that sensitive information like passwords and routing updates are transmitted securely. Encryption and authentication mechanisms prevent unauthorized interception.

---

### **End Device Hardening**

| **Security Action**                       | **Description**                                                                  | **Example Command**                                                                                                            |
|-------------------------------------------|----------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------|
| **Device Hardening**                      | Regular patching, antivirus, and limiting access privileges to secure devices.    | Patching is done manually or through software management tools. Enable antivirus protection and configure user privileges.     |
| **VLAN Segmentation**                     | Place devices into separate VLANs to control access between different groups.    | `interface Vlan10` for Medical VLAN, `interface Vlan20` for guest VLAN                                                              |
| **Access Control on End Devices**         | Limit device access based on role or department to restrict network access.      | ACLs should be configured on the switch ports or routers to enforce role-based access.                                        |

####  
End device hardening focuses on securing the actual devices connected to the network by controlling their access and ensuring they are regularly maintained, reducing the chance of compromise.



### **Monitoring and Scanning**

| **Security Action**                       | **Description**                                                                  | **Example Command**                                                                                                                                 |
|-------------------------------------------|----------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| **Syslog and SNMP Configuration**         | Configure centralized logging and monitoring of network devices.                 | `logging host 192.168.100.194`                                                                                                                  |
| **Network Scanning**                      | Regularly scan the network for vulnerabilities or unauthorized devices.         | Use automated scanning tools (e.g.,Nmap， Wireshark) and ensure all security settings are intact.                                           |
| **Monitor VLAN Traffic**                  | Regularly check traffic to ensure that only authorized communication happens.    | VLAN monitoring tools (such as SNMP(Simple Network Management Protocol) or syslog integration) should be used to track unusual or unauthorized traffic.                         |

####  
Continuous monitoring and scanning of the network allow for early detection of security issues, ensuring that potential threats are dealt with before they cause significant damage.

The table expressing the security measures :

| **Device**             | **Security Measures**                                         | **Explanation**                                                                                       |
|------------------------|---------------------------------------------------------------|-------------------------------------------------------------------------------------------------------|
| **Multilayer 3 Switch (VLAN20 for Guest)** | **VLAN Isolation**                                             | Ensures that the guest VLAN (VLAN20) is isolated from the internal network VLAN (e.g., VLAN10), preventing external devices from accessing internal resources.  |
|                        | **ACL (Access Control List)**                                 | Configure ACLs to allow VLAN20 only internet access while blocking access to internal network segments, improving security. |
|                        | **Port Security**                                             | Limits the number of MAC addresses allowed per port and enables sticky MAC address learning, preventing unauthorized devices from connecting. |
|                        | **DHCP Snooping**                                             | Enables DHCP snooping to prevent DHCP spoofing attacks, allowing only trusted DHCP servers to assign IP addresses to VLAN20. |
|                        | **ARP Protection**                                            | Enables ARP inspection to prevent ARP spoofing, ensuring that devices in VLAN20 communicate only with legitimate ARP entries. |
| **Wireless AP (Guest Network)** | **SSID Hiding**                                               | Hides the SSID to prevent potential attackers from discovering the network, reducing the chance of unauthorized connections. |
|                        | **WPA3 Encryption**                                           | Uses WPA3 encryption standard, providing stronger encryption algorithms to prevent wireless traffic from being cracked. |
|                        | **Frequent Wireless Password Changes**                        | Regularly changes wireless passwords to minimize the risk of password leaks. |
|                        | **Network Access Control**                                    | Configures network access control to limit the type of access allowed (e.g., only web browsing), preventing malicious behavior. |
| **Wireless Router (Internal Network)** | **SSID Hiding**                                               | Hides the SSID to prevent external individuals from detecting the network, reducing the risk of unauthorized access. |
|                        | **Wireless Access Control**                                   | Limits connections to only authorized devices using MAC address filtering or WPA3 authentication to ensure trustworthiness. |
|                        | **Network Segmentation**                                      | Ensures that internal and guest networks are segregated, preventing unauthorized access to internal data. |
|                        | **Strong Passwords and Encryption**                           | Uses strong passwords to secure the wireless network and ensures encryption for communication protection. |

### Additional Explanation:
- **VLAN Isolation**: By separating guest networks from internal networks, you reduce the risk of external threats accessing internal data.
- **ACL**: Access Control Lists ensure that only authorized traffic (such as internet access) can enter and exit the guest network, blocking unwanted access.
- **DHCP Snooping**: Protects the network by preventing rogue DHCP servers from assigning invalid IP addresses to guest network devices.
- **WPA3 Encryption**: Adopting the latest encryption technology ensures the wireless network cannot be cracked or eavesdropped on.
- **SSID Hiding**: Hiding the SSID reduces the chances of the network being discovered and accessed by unauthorized users.
  
