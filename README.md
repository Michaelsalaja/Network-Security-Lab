# Configuring a Standard ACL

## Introduction

This lab project is meant to help understand how to configure a standard Access Control List (ACL). ACLs are, to my understanding, the unsung heroes of or security and network management. ACLs are ordered sets of rules that control the traffic that is permitted or denied the use of a path through a router. These rules can operate at Layer 3, making these decisions on the basis of IP addresses, or at Layer 4, when only certain types of traffic are allowed based on a Transmission Control Protocol (TCP) or User Datagram Protocol (UDP) port number. When this is done, the ACL will typically reference a port number of the service or application that is allowed or denied.

## Note

* ![bullet point](image) Standard ACLs can only be applied to IP traffic. Only Extended ACLs can be used to filter other types of traffic
* ![bullet point](image) Misconfiguring ACLs rule could lead to some real head-scratching moments when you are troubleshooting network issues. You might think you have blocked a host or IP, but something is still sneaking through because the ACLs is applied wrongly and unintendedly.

## Instructions

### Step 1

PuTTY is installed and opened from Desktop

### Step 2

In the PuTTY Configuration window, I typed Host Name (or IP address) as <mark>192.168.116.128</mark> and Port as <mark>5011</mark>

### Step 3

* ![bullet point](image) Under Connection type, “Other” radio button is selected and clicked
* ![bullet point](image) A command line prompt in the terminal window will pop up
* ![bullet point](image) Press “Enter”

![PuTTY Configuration window showing basic options for a session, including Host Name 192.168.116.128 and Port 5011.](page_2_image_1_v2.jpg)

*PuTTy Terminal Window*

# Step 4

* In the PC3 terminal window, the following command was executed to ping the 192.168.1.100 host:

  `ping 192.168.1.100`

* It is observed that PC3 is able to ping the 192.168.1.100 host

![A screenshot of a Linux desktop environment showing a PuTTY terminal window with ping results. The terminal title is "192.168.116.128 - PuTTY". Inside the terminal, it shows:
ping 192.168.1.100
192.168.1.100 icmp_seq=1 timeout
64 bytes from 192.168.1.100 icmp_seq=2 ttl=62 time=41.937 ms
64 bytes from 192.168.1.100 icmp_seq=3 ttl=62 time=38.606 ms
64 bytes from 192.168.1.100 icmp_seq=4 ttl=62 time=26.141 ms
64 bytes from 192.168.1.100 icmp_seq=5 ttl=62 time=38.622 ms
PC3>](page_3_image_1_v2.jpg)

*PC3 Terminal Window*

# Step 5

* The PC3 terminal window is minimized

* On the left side bar, PuTTy is right clicked to open a new Window

![A screenshot of a Linux desktop environment (Ubuntu) showing the top bar with "Activities" and the date "Apr 2 03:59", a sidebar with application icons, and a context menu for the PuTTY application with options: All Windows, New Window, Remove from Favorites, and Quit. The background is a purple jellyfish wallpaper.](page_4_image_1_v2.jpg)

*PuTTY Sidebar*

A new window emerges

![PuTTY Configuration Window showing the session settings on a Linux desktop.](page_5_image_1_v2.jpg)

*PuTTy Configuration Window*

# Step 6

In the PuTTY Configuration window, in the right pane, I typed Host Name (or IP address) as <mark>192.168.116.128</mark> and Port as <mark>5033</mark>.

![Overview of Putty Configuration Info](page_6_image_1_v2.jpg)

*Overview of Putty Configuration Info*

* Under Connection type, “Other” radio button is selected and clicked

* A command line prompt in the terminal window will pop up

* Press “Enter”

* R8 Terminal will emerge

![Display of R8 Terminal Window](page_7_image_1_v2.jpg)

*Display of R8 Terminal Window*

# Step 7

In the R8 terminal window, I proceeded as follows:

* The following command was executed to enter into configuration mode

<span style="color: purple">Conf t</span>

![Screenshot of a PuTTY SSH Client terminal showing the output of the 'conf t' command on router R8.](page_8_image_1_v2.jpg)

*Output of conf t command*

# Step 8

* The following commands were executed in configuration mode to create the standard numbered access-list and deny the host (Note: each command was executed at a time.):

* blockaccess-list 10 deny host 192.168.2.101
* access-list 10 permit any
* interface e0/1
* IP access-group 10 out
* end

![Screenshot of a PuTTY SSH Client terminal window showing Cisco IOS configuration commands. The terminal text shows:
R8 con0 is now available
Press RETURN to get started.
R8#
R8#
R8#conf t
Enter configuration commands, one per line. End with CNTL/Z.
R8(config)#access-list 10 deny host 192.168.2.101
R8(config)#access-list 10 permit any
R8(config)#interface e0/1
R8(config-if)#IP access-group 10 out
R8(config-if)#end
R8#
*Mar 1 03:59:38.487: %SYS-5-CONFIG_I: Configured from console by console
R8#](page_9_image_1_v2.jpg)

*Output of 5 Command Executions in Configuration Mode*

* The following command was executed in enable mode to save router settings:

`copy running-config startup-config`

* When asked for Destination filename [startup-config]?, I pressed Enter.

* Configurations will then be built and “{OK}” will emerge in the terminal

![Screenshot of a PuTTY SSH Client terminal window showing Cisco IOS configuration commands. The terminal displays the configuration of an access list and an interface, followed by a copy running-config startup-config command. A red box highlights the final command and the prompt "Destination filename [startup-config]?".](page_10_image_1_v2.jpg)

*Display of Destination File Name Request*

![Screenshot of a PuTTY SSH Client terminal showing Cisco IOS configuration commands for an access list and saving the running configuration to startup configuration.](page_11_image_1_v2.jpg)

*Output of Destination File Name Response*

# Step 9

* The following command was executed in enable mode to view the access list:

<p style="text-align: center; color: purple">Show access-lists</p>

* Access list will be displayed

![Screenshot of a PuTTY SSH Client terminal window showing Cisco IOS configuration commands for an access list on router R8.](page_12_image_1_v2.jpg)

Overview of Access Lists 10

# Step 11

Minimized the R8 terminal window

# Step 12

On the left sidebar, I clicked the PuTTY icon and clicked on the 192.168.116.128 terminal to restore the PC3 terminal window.

![Screenshot of a PuTTY SSH Client session on a Linux desktop showing terminal commands on router R8. The terminal shows a failed copy command due to typos, a successful `copy running-config startup-config`, and the output of `show access-lists` displaying Standard IP access list 10 with '10 deny 192.168.2.101' and '20 permit any'.](page_13_image_1_v2.jpg)

*PuTTY Configuration Windows PC3 and R8*

# Step 11

* In the PC3 terminal window, the following command was executed to ping the 192.168.1.100 host:

`ping 192.168.1.100`

* It was clearly observed that PC3 was not able to ping the 192.168.1.100 host, and communication is prohibited.

![Output of Ping command showing successful pings followed by "Communication administratively prohibited" messages from 192.168.3.1.](page_14_image_1_v2.jpg)

*Output of Ping command*

# Step 12

I closed the PC3 and R8 terminal windows.

At the PuTTY Exit Confirmation prompts, I clicked Yes.

![Display of PuTTY SSH Client showing ping results and an exit confirmation dialog box. The terminal shows ICMP packets being "Communication administratively prohibited" by 192.168.3.1.](page_15_image_1_v2.jpg)

*Display of PuTTy Exit Confirmation*

# Conclusion

This lab project focused on demonstrating how to configure a Standard ACL. ACLS are like traffic cops of the internet that helps us prevent unauthorized access to our network. They control which data is allowed to pass and which one should be blocked. They are used for managing network traffic and prioritize some certain type of data and even optimize network performance. They are all about network security or a set of rules that we can configure on router to filter different traffics based on criteria. They filter traffic based on source IP address, destination IP address, protocol, and even port number on a router interface, which lets network administrators have granular control over inbound and outbound connection of their network. ACL can also be used to allow certain web traffic from a certain subnet.

We also have the Wild Card mask, which us a pattern matching system.

**Wild Card Mask:** It can be a little tricky at first, but what it does is to help us have a better control about how specific or general we want our matching to be. It is like a filter for your IP address. You can choose which part you want to match exactly and which part you want to be more flexible about. The logic of Wild card Mask is based on binary operations because IP addresses are just strings of 1s and 0s. Each bit in a Wild Card Mask corresponds to a bit in the IP address we are trying to match. It is about controlling which bit the router should pay attention to.

As I get deeper into networking, I could see just how versatile and essential ACLs are for security and network management. In my next project, I am going to concentrate on configuring Extended ACL. Extended ACL configuration is more complex than Standard ACL configuration.
