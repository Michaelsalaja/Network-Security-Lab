# Configuring a Standard ACL

## Introduction

This lab project is meant to help understand how to configure a standard Access Control List (ACL). ACLs are, to my understanding, the unsung heroes of or security and network management. ACLs are ordered sets of rules that control the traffic that is permitted or denied the use of a path through a router. These rules can operate at Layer 3, making these decisions on the basis of IP addresses, or at Layer 4, when only certain types of traffic are allowed based on a Transmission Control Protocol (TCP) or User Datagram Protocol (UDP) port number. When this is done, the ACL will typically reference a port number of the service or application that is allowed or denied.

## Note

* Standard ACLs can only be applied to IP traffic. Only Extended ACLs can be used to filter other types of traffics.
* Misconfiguring ACLs rule could lead to some real head-scratching moments when you are troubleshooting network issues. You might think you have blocked a host or IP, but something is still sneaking through because the ACLs is applied wrongly and unintendedly.

## Instructions

### Step 1

PuTTY is installed and opened from Desktop

### Step 2

In the PuTTY Configuration window, I typed Host Name (or IP address) as <mark>192.168.116.128</mark> and Port as <mark>5011</mark>

### Step 3

* Under Connection type, “Other” radio button is selected and clicked
* A command line prompt in the terminal window will pop up
* Press “Enter”

![image alt](https://github.com/Michaelsalaja/Network-Security-Lab/blob/fdc3a1b2896f12114537b1117cfcb65a2de1b491/Figure%201_PuTTy%20Terminal%20Window.png)
*Figure 1.1 PuTTy Terminal Window*

# Step 4

* In the PC3 terminal window, the following command was executed to ping the 192.168.1.100 host:

  `ping 192.168.1.100`

* It is observed that PC3 is able to ping the 192.168.1.100 host

![image alt](https://github.com/Michaelsalaja/Network-Security-Lab/blob/fdc3a1b2896f12114537b1117cfcb65a2de1b491/Figure%202_PC3%20Terminal%20Window.png)
*Figure 1.2. PC3 Terminal Window*

# Step 5

* The PC3 terminal window is minimized

* On the left side bar, PuTTy is right clicked to open a new Window

![image alt](https://github.com/Michaelsalaja/Network-Security-Lab/blob/fdc3a1b2896f12114537b1117cfcb65a2de1b491/Figure%203_PuTTy%20Sidebar.png)
*Figure 1.3. PuTTY Sidebar*

A new window emerges

![image alt](https://github.com/Michaelsalaja/Network-Security-Lab/blob/fdc3a1b2896f12114537b1117cfcb65a2de1b491/Figure%204_PuTTy%20Configuration%20Window.png)
*Figure 1.4. PuTTy Configuration Window*

# Step 6

In the PuTTY Configuration window, in the right pane, I typed Host Name (or IP address) as <mark>192.168.116.128</mark> and Port as <mark>5033</mark>.

![image alt](https://github.com/Michaelsalaja/Network-Security-Lab/blob/fdc3a1b2896f12114537b1117cfcb65a2de1b491/Figure%205_Overview%20of%20Putty%20Configuration%20Info.png)
*Figure 1.5. Overview of Putty Configuration Info*

* Under Connection type, “Other” radio button is selected and clicked

* A command line prompt in the terminal window will pop up

* Press “Enter”

* R8 Terminal will emerge

![image alt](https://github.com/Michaelsalaja/Network-Security-Lab/blob/fdc3a1b2896f12114537b1117cfcb65a2de1b491/Figure%206_Display%20of%20R8%20Terminal%20Window.png)
*Figure 1.6. Display of R8 Terminal Window*

# Step 7

In the R8 terminal window, I proceeded as follows:

* The following command was executed to enter into configuration mode

<span style="color: purple">Conf t</span>

![image alt](https://github.com/Michaelsalaja/Network-Security-Lab/blob/fdc3a1b2896f12114537b1117cfcb65a2de1b491/Figure%207_Output%20of%20conf%20t%20command.png)
*Figure 2.1. Output of conf t command*

# Step 8

* The following commands were executed in configuration mode to create the standard numbered access-list and deny the host (Note: each command was executed at a time.):

* blockaccess-list 10 deny host 192.168.2.101
* access-list 10 permit any
* interface e0/1
* IP access-group 10 out
* end

# Terminal Window
*R8#

*R8#

*R8#conf t

*Enter configuration commands, one per line. End with CNTL/Z.

*R8(config)#access-list 10 deny host 192.168.2.101

*R8(config)#access-list 10 permit any

*R8(config)#interface e0/1

*R8(config-if)#IP access-group 10 out

*R8(config-if)#end

*R8#

*Mar 1 03:59:38.487: %SYS-5-CONFIG_I: Configured from console by console

*R8#](page_9_image_1_v2.jpg)

![image alt](https://github.com/Michaelsalaja/Network-Security-Lab/blob/fdc3a1b2896f12114537b1117cfcb65a2de1b491/Figure%208_Output%20of%205%20Command%20Executions%20in%20Configuration%20Mode.png)
*Figure 2.2 Output of 5 Command Executions in Configuration Mode*

* The following command was executed in enable mode to save router settings:

`copy running-config startup-config`

* When asked for Destination filename [startup-config]?, I pressed Enter.

* Configurations will then be built and “{OK}” will emerge in the terminal

![image alt](https://github.com/Michaelsalaja/Network-Security-Lab/blob/fdc3a1b2896f12114537b1117cfcb65a2de1b491/Figure%209-Display%20of%20Destination%20File%20Name%20Request.png)
*Figure 2.3. Display of Destination File Name Request*

![image alt](https://github.com/Michaelsalaja/Network-Security-Lab/blob/fdc3a1b2896f12114537b1117cfcb65a2de1b491/Figure%2010_Output%20of%20Destination%20File%20Name%20Response.png)
*Figure 2.4. Output of Destination File Name Response*

# Step 9

* The following command was executed in enable mode to view the access list:

<p style="text-align: center; color: purple">Show access-lists</p>

* Access list will be displayed

![image alt](https://github.com/Michaelsalaja/Network-Security-Lab/blob/fdc3a1b2896f12114537b1117cfcb65a2de1b491/Figure%2011_Overview%20of%20Access%20List%2010%20%20%20%20%20.png)
*Figure 2.5. Overview of Access Lists 10*

# Step 11

Minimized the R8 terminal window

# Step 12

On the left sidebar, I clicked the PuTTY icon and clicked on the 192.168.116.128 terminal to restore the PC3 terminal window.

![image alt](https://github.com/Michaelsalaja/Network-Security-Lab/blob/fdc3a1b2896f12114537b1117cfcb65a2de1b491/Figure%2012_PuTTy%20Configuration%20Windows%20PC3%20and%20R8.png)
*Figure 2.6. PuTTY Configuration Windows PC3 and R8*

# Step 11

* In the PC3 terminal window, the following command was executed to ping the 192.168.1.100 host:

`ping 192.168.1.100`

* It was clearly observed that PC3 was not able to ping the 192.168.1.100 host, and communication is prohibited.

![image alt](https://github.com/Michaelsalaja/Network-Security-Lab/blob/fdc3a1b2896f12114537b1117cfcb65a2de1b491/Figure%2013_Output%20of%20Ping%20command.png)
*Figure 3.1. Output of Ping command*

# Step 12

I closed the PC3 and R8 terminal windows.

At the PuTTY Exit Confirmation prompts, I clicked Yes.

![image alt](https://github.com/Michaelsalaja/Network-Security-Lab/blob/fdc3a1b2896f12114537b1117cfcb65a2de1b491/Figure%2014_Display%20of%20PuTTy%20Exit%20Confirmation.png)
*Figure 3.2. Display of PuTTy Exit Confirmation*

# Conclusion

This lab project focused on demonstrating how to configure a Standard ACL. ACLs are like traffic cops of the internet that help us prevent unauthorized access to our network. They control which data is allowed to pass and which one should be blocked. They are used for managing network traffic and prioritizing some certain types of data and even optimizing network performance. They are all about network security or a set of rules that we can configure on our routers to filter different traffics based on criteria. They filter traffic based on source IP address, destination IP address, protocol, and even port number on a router interface, which lets network administrators have granular control over inbound and outbound connection of their network. ACL can also be used to allow certain web traffic from a certain subnet.

We also have the Wild Card mask, which is a pattern matching system.

**Wild Card Mask:** It can be a little tricky at first, but what it does is to help us have a better control about how specific or general we want our matching to be. It is like a filter for your IP address. You can choose which part you want to match exactly and which part you want to be more flexible about. The logic of Wild card Mask is based on binary operations because IP addresses are just strings of 1s and 0s. Each bit in a Wild Card Mask corresponds to a bit in the IP address we are trying to match. It is about controlling which bit the router should pay attention to.

As I get deeper into networking, I could see just how versatile and essential ACLs are for security and network management. In my next project, I am going to concentrate on configuring an Extended ACL. Extended ACL configuration is more complex than Standard ACL configuration.
