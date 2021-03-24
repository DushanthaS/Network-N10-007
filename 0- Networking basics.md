# Networking Basics

## Ethernet 
[Professor Messer](https://youtu.be/iXfBbs9SSFQ)
- Ethernet is defined by Data Link layer and Physical Layer protocol.
- Ethernet Frame structure  [image](Images/ethernet-ii-hdr-n-fields.jpg)
  - Preamble - Alternating 1 and 0s , receiving workstation know that rest of the info about to arrive is part of ethernet frame
  - SFD - very specific set of 1 and 0s, rest of the info about to arrive is part of ethernet commutation
  - Type - whats inside this particular frame (IPv4/IPv6)
  - Payload - actual data thats Layer 3 and higher (IP info ect)
  - FCS - CRC checksum of the frame so ethernet card will drop the frame if this doesn't match. it will also increment a count of dropped frames (CRC counter)

## MAC Address
 -  Ethernet Media Access Control address
    -  The “physical” address of a network adapter
    -  Unique to a device
    -  48 bits / 6 bytes long
    -  Displayed in hexadecimal
- Duplicate prevention  
  - To prevent the possibility of duplicate MAC addresses, IEEE decided to assign each manufacturer an ID and then let the manufacturer further allocate IDs. 
  - The result is that in a MAC address, the first 3 bytes define the manufacturer (organizational unique identifier -OUI) , and the last 3 are assigned by the manufacturer, (universal LAN MAC address) They make this interface unique.

## Duplex
 -  Half-duplex
    -  A device cannot send and receive simultaneously
    -  All LAN hubs are half-duplex devices (old)
    -  Switch interfaces can be configured as half-duplex, but usually only when connecting to another half-duplex device
 -  Full-duplex
    -  Data can be sent (to switch) and received at the same time
    -  A properly configured switch interface will be set to full-duplex

## Collision

- In half duplex hub configuration theres a possibility of 2 devices communicate simultaneously, thats called collision
- Everyone on the network will notice this and they will wait random amount of time to communicate back  
## IPv4 addressing

- To communicate on a network using TCP/IP, each system must be assigned a unique address. 
- The address defines both the number of the network to which the device is attached and the number of the node on that network. In other words, the IP address provides two pieces of information. 
- It’s a bit like a street name and house number in a person’s home address.
 
 - network address / node addresses
   - “Each device on a logical network segment must have the `same network address` as all the other devices on the segment. All the devices on that network segment must then have `different node addresses`.”
- Written in dotted decimal notation, each IPv4 address is divided in to 4 separate numbers and divided by dots
- Each of these divisions are call octets due to having 8 bits assigned
- “An IPv4 address is composed of four sets of 8 binary bits, which are called octets. The result is that IP addresses contain 32 bits. Each bit in each octet is assigned a decimal value. 
- The far-left bit has a value of 128, followed by 64, 32, 16, 8, 4, 2, and 1, left to right.
- Each bit in the octet can be either a 1 or a 0. If the value is 1, it is counted as its decimal value, and if it is 0, it is ignored. If all the bits are 0, the value of the octet is 0. 
- If all the bits in the octet are 1, the value is 255, which is 128 + 64 + 32 + 16 + 8 + 4 + 2 + 1.
- By using the set of 8 bits and manipulating the 1s and 0s, you can obtain any value between 0 and 255 for each octet.”
- 11011111 is 128 + 64 + 16 + 8 + 4 + 2 + 1 = 223

## Subnet Mask
  - In IP addressing, another set of numbers, called a subnet mask, defines which portion of the IP address refers to the network address and which refers to the node (host) address.
  - Subnet mask defines the network portion
    -  Network portion if a binary 1
    -  Host portion if binary 0
  -  Like an IP address, a subnet mask is most commonly expressed in 32-bit dotted-decimal format. 
  -  Unlike an IP address, though, a subnet mask performs just one function—it defines which parts of the IP address refers to the network address and which refers to the node (host) address. 
  -  Each class of the IP address used for address assignment has a default subnet mask associated with it. 

## IP Address Classes
  - IP addresses are grouped into logical divisions called classes. 
  - The IPv4 address space has five address classes (A through E); however, only three (A, B, and C) assign addresses to clients. 
  - Class D is reserved for multicast addressing, and Class E is reserved for future development.
  - Of the three classes available for address assignments, each uses a fixed-length subnet mask to define the separation between the network and the node (host) address. 
  - A Class A address uses only the first octet to represent the network portion; a Class B address uses two octets; and a Class C address uses the first three octets. 
  - The upshot of this system is that Class A has a small number of network addresses, but each Class A address has a large number of possible host addresses. ”


##  Subnetting
   -  “Subnetting is a process by which the node (host) portions of an IP address create more networks than you would have if you used the default subnet mask.”
   -  “With subnetting, you use bits from the node portion of the address to create more network addresses. This reduces the number of nodes per network, but you probably will still have more than enough.”
   -  “two main reasons for subnetting:
      -  “It enables you to more effectively use IP address ranges.
    - It makes IP networking more secure and manageable by providing a mechanism to create multiple networks rather than having just one.”

## Classless Interdomain Routing
  - Classless interdomain routing (CIDR) is an IPv4 method of assigning addresses outside the standard Class A, B, and C structure. 
  - Specifying the number of bits in the subnet mask offers more flexibility than the three standard class definitions.”
  - “Using CIDR, addresses are assigned using a value known as the slash. 
  - The actual value of the slash depends on how many bits of the subnet mask are used to express the network portion of the address. 
  - For example, a subnet mask that uses all 8 bits from the first octet and 4 from the second would be described as /12, or “slash 12.” 
  - A subnet mask that uses all the bits from the first three octets would be called /24. Why the slash? In addressing terms, the CIDR value is expressed after the address, using a slash. So, the address 192.168.2.1/24 means that the node’s IP address is 192.168.2.1, and the subnet mask is 255.255.255.0.”

## Default Gateways
  - Default gateways are the means by which a device can access hosts on other networks for which it does not have a specifically configured route. 
  - Most workstation configurations default to using default gateways rather than having any static routes configured. 
  - This enables workstations to communicate with other network segments or with other networks, such as the Internet.”
  - “When a system wants to communicate with another device, it first determines whether the host is on the local network or a remote network. 
  - If the host is on a remote network, the system looks in the routing table to determine whether it has an entry for the network on which the remote host resides. If it does, it uses that route. 
  - If it does not, the data is sent to the default gateway.”
  - “On the network, a default gateway could be a router or a computer with network interfaces (mutihomed) for all segments to which it is connected. 
  - These interfaces have local IP addresses for the respective segments. If a system is not configured with any static routes or a default gateway, it is limited to operating on its own network segment.”

## IPv4 Address Types
- IPv4 has three primary address types: unicast, broadcast, and multicast.
  - Unicast Address
    - With a unicast address, a single address is specified. Data sent with unicast addressing is delivered to a specific node identified by the address. It is a point-to-point address link.
  - Broadcast Address
    - A broadcast address is at the opposite end of the spectrum from a unicast address. A broadcast address is an IP address that you can use to target all systems on a subnet or network instead of single hosts. In other words, a broadcast message goes to everyone on the network.
  - Multicast
    - Multicasting is a mechanism by which groups of network devices can send and receive data between the members of the group at one time, instead of separately sending messages to each device in the group. The multicast grouping is established by configuring each device with the same multicast IP address.”

 
## Network Switching Overview

[Professor Messer](https://youtu.be/jR3VoKZWJyc)
  - The Switch
     -  Forward or drop frames
     -  Based on the destination MAC address
     -  Gather a constantly updating list of MAC addresses
     -  Builds the list based on the source
    MAC address of incoming traffic
     -  Maintain a loop-free environment
     -  Using Spanning Tree Protocol (STP)

  -  Learning the MACs
      -  Switches examine incoming traffic
      -  Makes a note of the source MAC address
      -  Adds unknown MAC addresses to the MAC address table
      -  Sets the output interface to the received interface
  - Flooding for unknown Macs
     -  The switch doesn’t always have a MAC address in the table
     -  When in doubt, send the frame to everyone
  - Address Resolution Protocol
     -  Determine a MAC address based on an IP address
     -  You need the hardware address to communicate
     -  `arp -a`
     -  View local ARP table

## Switch operation
   -  Forwarding decisions made by MAC address
   -  Keeps a big table of MAC address that have been seen
   -  All forwarding decisions are filtered through this list
   -  If the destination MAC is unknown, the frame is flooded
   -  Sent to every switch port in the local subnet/VLAN
   -  Hopefully the destination station will respond
   -  Flooding is hopefully a temporary process
   -  Directed traffic resumes when the MAC is seen


## Switch Interface Properties
[Professor Messer](https://youtu.be/dqQny4UXiX0)
- Basic Interface Configuration
   -  Speed and duplex
   -  Speed: 10 / 100 /1,000
   -  Duplex: Half/Full
   -  Automatic and manual
   -  Needs to match on both sides
   -  IP address management
   -  Layer 3 interfaces
   -  VLAN interfaces
   -  Management interfaces
   -  IP address, subnet mask/CIDR block,
  default gateway, DNS (optional)

- VLANs
   -  VLAN assignment
   -  Each device port should be assigned a VLAN
   -  Trunking
   -  Connecting switches together - Multiple VLANs in a single link
   -  Tagged and untagged VLANs
   -  A non-tagged frame is on the default VLAN
   -  Also called the native VLAN
   -  Trunk ports will tag the outgoing frames
   -  And remove the tag on incoming frames


- Routing
  -  Different topologies use different data link protocols
  -  Ethernet, HDLC, etc.
  -  Each router rewrites the frame to add its own data-link header
  -  The IP packet remains intact

- IGP and EGP

[Professor Messer](https://youtu.be/14s-M01m1fQ)
  - AS (Autonomous System)
    -  Autonomous
    -  Existing as an independent entity
    -  Group of IP routes under common control
    -  RFC 1930, Section 3: Definitions
       -  “An AS is a connected group of one or more IP prefixes run by one or more network operators which has a SINGLE and CLEARLY DEFINED routing policy.”
  -  Important point of reference for discussing Interior Gateway Protocols and Exterior Gateway Protocols

  - IGP (Interior Gateway Protocol)
    -  Used within a single autonomous system (AS)
       -  Not intended to route between AS
          -  That’s why there’s Exterior Gateway Protocols (EGPs)

    -  IPv4 dynamic routing
       -  OSPFv2 (Open Shortest Path First)
       -  RIPv2 (Routing Information Protocol version 2)
       -  EIGRP (Enhanced Interior Gateway Routing Protocol)
    -  IPv6 dynamic routing
       -  OSPFv3
       -  EIGRP for IPv6
       -  RIPng (RIP next generation)
  - EGP (Exterior Gateway Protocol)
    -  Used to route between autonomous systems
       -  Leverages the IGP at the AS to handle local routing
    -  BGP (Border Gateway Protocol)
       -  Many organizations use BGP as their EGP


## IPv4 and IPv6 Addressing

[Professor Messer](https://youtu.be/U2IxdEYgoEg)
- The IP address of a device
  -  IP Address, e.g., 192.168.1.165
     -  Every device needs a unique IP address
  -  Subnet mask, e.g., 255.255.255.0
     -  Used by the local workstation to determine what subnet it’s on
     -  The subnet mask isn’t (usually) transmitted across the network
     -  You’ll ask for the subnet mask all the time
     -  What’s the subnet mask of this network?
- The secret behind the IP address
  -  The IP address isn’t really a single address.
  -  An IP address is a combination of a network ID and a host ID
     -  The subnet mask determines what part of the IP address is the network and which part is the host
     -  The subnet mask is just as important as your IP address!
     -  The best way to see this work is in binary
     -  This is the (very easy) math part

- IPv4 addresses - Internet Protocol version 4
  -  OSI Layer 3 address
  -  Since one byte is 8 bits, the maximum decimal value for each byte is 255
- IPv6 addresses
  -  Internet Protocol v6 - 128-bit address
  -  340,282,366,920,938,463,463,374,607,431,768,211,456 addresses (340 undecillion)
  -  6.8 billion people could have 5,000,000,000,000,000,000,000,000,000 addresses each
- IPv6 address compression
  -  Your DNS will become very important!
  -  Groups of zeros can be abbreviated with a double colon ::
     -  Only one of these abbreviations allowed per address
  -  Leading zeros are optional