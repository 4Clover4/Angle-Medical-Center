### **Security Measures Overview**

### **Network Security Hardening Measures - A Football Analogy**

Hello everyone! Today, we’re going to talk about network security hardening. But instead of diving into dry technical details, I’ll use a fun football analogy to explain the security measures we implement in our network. This should make the concepts a lot easier to grasp, and I’ll also share some real-world commands and strategies we use in our network.

### **The Team: The Football Pitch**

Imagine your entire network as a football team, with the goal of preventing the opposing team (the hackers) from scoring against us. Our job is to make sure they never get a chance to break through. By using proper security measures, we can make sure that the "goalposts" are safe and our data is secure. 

The following are key categories of network hardening techniques covered in this document:

1. **Switch Hardening Security Measures**  
2. **Router Hardening Security Measures**  
3. **End Device Hardening**  
4. **Monitoring and Scanning Security Measures**

Each category addresses different aspects of network security, such as authentication, encryption, access control, and traffic monitoring.

###  The Switch – The Midfielders

In a football team, the midfielders are key players who control the flow of the game. They pass the ball to the forwards and help transition the defense to attack. In the network world, switches act like midfielders – they control data flow and connect devices across different parts of the network.
 
Think of the switch like Barcelona's Xavi. Xavi was always the one distributing precise passes, making sure each player got the ball at the right time. If the switch isn't secured, unauthorized devices can easily connect to the network, just like an opponent breaking through the midfield. This could lead to network breaches or even data theft.

**How We Secure the Switch:**  
We can "lock down" the midfield by implementing **port security**, such as the command `switchport port-security maximum 2`, which restricts the number of MAC addresses per port. This is like Xavi only passing the ball to trusted teammates—if an unauthorized device tries to connect, the port will shut down or restrict access. This prevents unwanted devices from "breaking through" into the network.

The **switchport port-security violation restrict** command specifies that if a security violation occurs (such as when an unauthorized MAC address is detected), the port will restrict the connection rather than shutting it down. The port will continue to function, but any traffic from unauthorized MAC addresses will be dropped, and a log entry will be created. This option is useful to avoid disrupting network connectivity while still enforcing security.
The **restrict** option is chosen over `shutdown` or `protect` because it prevents unauthorized devices from accessing the network without disabling the entire port, allowing for continued operation but with more controlled access.

The command **no cdp run** disables the Cisco Discovery Protocol (CDP) on a device, preventing it from sending or receiving CDP information, which is used for discovering neighboring Cisco devices and their details.


###  The Router – The Goalkeeper

The goalkeeper is arguably the most important player in a football team. They stand at the goal and prevent the opposing team from scoring. In the same way, the router acts as the "goalkeeper" for your network, controlling the flow of traffic in and out of your internal network. If the router isn’t properly secured, hackers can easily bypass it and score by gaining access to the internal network.

Think of the router as Chelsea's Edouard Mendy, always standing strong to block the opposition’s shots. If the router isn’t properly secured, it’s like having a goalkeeper who's not paying attention, allowing hackers to sneak past.

**How We Secure the Router:**  
We ensure that the router only allows authorized traffic by implementing **Access Control Lists (ACLs)** like the command `access-list 130 deny ip 192.168.40.0 0.0.0.255 192.168.10.0 0.0.0.255`, blocking certain IP addresses or traffic. Just like Edouard won’t let any balls get past him, we ensure that only valid data packets can pass through the router.

We also make use of **SSH for remote management** (via `ip ssh version 2`), which encrypts our management traffic to prevent unauthorized users from controlling our router remotely. This is like Edouard wearing a high-tech kit to ensure his performance is secure and untraceable by the opponents.

####  
Router hardening focuses on protecting the internal network by utilizing NAT, ACLs, and secure routing protocols like OSPF.

The **overload** keyword in the command `ip nat inside source list 1 interface gigabitEthernet 0/0 overload` enables Port Address Translation (PAT), allowing multiple internal devices to share a single public IP address. Each device’s connection is distinguished by a unique port number, saving public IP addresses.

**OSPF** (Open Shortest Path First) is a link-state routing protocol used to find the best path for data exchange in an IP network, by calculating the shortest path first based on the network's topology.

####  
End device hardening focuses on securing the actual devices connected to the network by controlling their access and ensuring they are regularly maintained, reducing the chance of compromise.

###  The Network Monitoring System – The Coach

Just as a football coach is responsible for observing the game and making tactical adjustments, our **network monitoring system** watches over the network and ensures everything is functioning correctly. It looks for vulnerabilities, scans for unauthorized devices, and helps us detect potential threats early on.
  
Imagine the network monitoring system as a coach like José Mourinho—always alert, watching the game unfold, and ready to make the right call at the right moment. Without monitoring, it's like having a coach who’s not paying attention, missing vital changes in the game and allowing an easy goal.


**How We Monitor the Network:**  
We use **Syslog**  for centralized logging, making sure we receive real-time updates about any security incidents. Tools like **Wireshark** or **Nmap** allow us to monitor traffic and detect threats, just like a coach using video analysis to spot the opposition’s weaknesses.

### The Wireless Access Point (AP) – The Wing Players

In football, the wing players are responsible for delivering precise crosses into the box, providing opportunities for scoring. In the network, the wireless access point (AP) serves a similar function, allowing wireless devices (like laptops and phones) to connect to the network, just like a winger providing a ball for a goal opportunity.

Imagine the wireless access point as Kylian Mbappé, darting down the wing and delivering crosses to his teammates. However, if our AP isn't properly secured, it’s like Kylian running without support—easily intercepted by the opposing team, allowing attackers into our network.

**How We Secure the AP:**  
We can hide the SSID of our wireless network (similar to keeping our attacking strategy under wraps), so unauthorized users can’t see or connect to it. Additionally, we enforce **WPA3 encryption**, which strengthens wireless security and prevents attackers from cracking the encryption, just like Kylian is protected from being tackled by an opponent.


### The Whole Team: Perfect Coordination

In a football team, the entire squad needs to work together—each player has their role. The midfielders pass, the defenders protect, the forwards attack, and the goalkeeper blocks. Similarly, in network security, every component of the network must work together to protect our data. A single weak link—whether it’s an unsecured switch, router, or AP—could allow attackers to infiltrate.


### A Winning Team

By implementing these security measures, we ensure that our network is like a well-coordinated football team, with each player (device) doing its part. The **switch** (midfielders) controls the flow of traffic, the **router** (goalkeeper) defends the network perimeter, the **AP** (winger) allows wireless access but is protected, and the **monitoring system** (coach) ensures the game runs smoothly.

Just like in football, where team coordination leads to victory, the security of our network depends on how well each device and measure is configured and maintained. Together, we can ensure that our network remains secure, and like a champion football team, we can prevent any hackers from scoring.

Thank you for listening! Let’s keep our network security strong and continue to “win” this cybersecurity match together!
