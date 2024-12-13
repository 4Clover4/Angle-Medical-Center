### **Security Measures Overview**

### **Network Security Hardening Measures - A Football Analogy**

Hello everyone! Today, we’re going to talk about network security hardening. But instead of diving into dry technical details, I’ll use a fun football analogy to explain the security measures we implement in our network. This should make the concepts a lot easier to grasp, and I’ll also share some real-world commands and strategies we use in our network.### **Security Measures Breakdown**

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


