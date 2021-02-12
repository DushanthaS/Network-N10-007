# 4.0 Network Security

- [4.0 Network Security](#40-network-security)
  - [4.1 Summarize the purposes of physical security devices](#41-summarize-the-purposes-of-physical-security-devices)
    - [Detection](#detection)
    - [Prevention](#prevention)
  - [4.2 Explain authentication and access controls](#42-explain-authentication-and-access-controls)
    - [Authorization, authentication and accounting](#authorization-authentication-and-accounting)
    - [Multifactor authentication](#multifactor-authentication)
    - [Access control](#access-control)
  - [4.3 Given a scenario, secure a basic wireless network](#43-given-a-scenario-secure-a-basic-wireless-network)
    - [Wireless encryption](#wireless-encryption)
    - [WPA (Wi-Fi Protected Access)](#wpa-wi-fi-protected-access)
    - [TKIP-RC4 (Temporal Key Integrity Protocol)](#tkip-rc4-temporal-key-integrity-protocol)
    - [WPA2](#wpa2)
    - [CCMP-AES](#ccmp-aes)
    - [Authentication and authorization](#authentication-and-authorization)
    - [Geofencing](#geofencing)
  - [4.4 Summarize common networking attacks](#44-summarize-common-networking-attacks)
    - [DoS (Denial of Service)](#dos-denial-of-service)
    - [Social engineering](#social-engineering)
    - [Insider threat](#insider-threat)
    - [Logic bomb](#logic-bomb)
    - [Rogue access point](#rogue-access-point)
    - [Evil twin](#evil-twin)
    - [War-driving](#war-driving)
    - [Phishing](#phishing)
    - [Ransomware](#ransomware)
    - [DNS poisoning](#dns-poisoning)
    - [ARP poisoning](#arp-poisoning)
    - [Spoofing](#spoofing)
    - [Deauthentication](#deauthentication)
    - [Brute force](#brute-force)
    - [VLAN hopping](#vlan-hopping)
    - [On-path attack (previously known as man-in-the-middle attack)](#on-path-attack-previously-known-as-man-in-the-middle-attack)
    - [Exploits vs. vulnerabilities](#exploits-vs-vulnerabilities)
  - [4.5 Given a scenario, implement network device hardening](#45-given-a-scenario-implement-network-device-hardening)
    - [Changing default credentials](#changing-default-credentials)
    - [Avoiding common passwords](#avoiding-common-passwords)
    - [Upgrading firmware](#upgrading-firmware)
    - [Patching and updates](#patching-and-updates)
    - [File hashing](#file-hashing)
    - [Disabling unnecessary services](#disabling-unnecessary-services)
    - [Using secure protocols](#using-secure-protocols)
    - [Generating new keys](#generating-new-keys)
    - [Disabling unused ports](#disabling-unused-ports)
  - [4.6 Explain common mitigation techniques and their purposes](#46-explain-common-mitigation-techniques-and-their-purposes)
    - [Signature management](#signature-management)
    - [Device hardening](#device-hardening)
    - [Change from the default VLAN](#change-from-the-default-vlan)
    - [Switch port protection](#switch-port-protection)
    - [Network segmentation](#network-segmentation)
    - [Privileged user account](#privileged-user-account)
    - [File integrity monitoring](#file-integrity-monitoring)
    - [Role separation](#role-separation)
    - [Restricting access via ACLs](#restricting-access-via-acls)
    - [Honeypot/honeynet](#honeypothoneynet)
    - [Penetration testing](#penetration-testing)

## 4.1 Summarize the purposes of physical security devices
[Professor Messer](https://youtu.be/jMlbasNbgiY)

### Detection

- Video surveillance
  - CCTV (Closed circuit television)
    -  Can replace physical guards
  -  Camera properties are important
     -  Focal length - Shorter is wider angle
     -  Depth of field - How much is in focus
     -  Illumination requirements - See in the dark
  -  Often many different cameras
     -  Networked together and recorded over time
  -  Motion detection
      -  Can provide notification of activity
- Asset tracking tags
  -  A record of every asset
     -  Routers, switches, cables, fiber modules,
  CSU/DSUs, etc.
  -  Financial records, audits, depreciation
     -  Make/model, configuration, purchase date,
  location, etc.
  -  Tag the asset
     -  Barcode, RFID, visible tracking number

- Tamper detection

  -  You can’t watch all of your equipment all of the time
     -  Have your systems monitor themselves
  -  Hardware tampering
     -  Case sensors, identify case removal
     -  Alarm sent from BIOS
     -  Firewalls, routers, etc.
  -  Foil asset tags
     -  Identify the tampering

### Prevention
- Badges
 -  ID badge
    -  Picture, name, other details
    -  Must be worn at all times
 -  May be integrated with door access or a smart card
    -  It’s more than just a visual identification
 -  Standardized format
    -  Train all employees to look for ID and
ask questions if they don’t see one
- Biometrics
   - Biometric authentication
     - Fingerprint, iris, voiceprint
   - Usually stores a mathematical representation
  of your biometrics
     - Your actual fingerprint isn’t usually saved
   - Difficult to change
     - You can change your password
     - You can’t change your fingerprint
   - Used in very specific situations
     - Not foolproof
- Smart cards
  - Smart card
    - Integrates with devices
    - May require a PIN
  - USB token
    - Certificate is on the USB device
  - Hardware or software tokens / key fobs
    - Generates pseudo-random authentication codes
  - Your phone
    - SMS a code to your phone

- Locks

  - Conventional
    - Lock and key
  - Deadbolt
    - Physical bolt
  - Electronic
    - Keyless
  - Token-based
    - Magnetic swipe card or proximity reader
  - Multi-factor
    - Smart card and PIN

## 4.2 Explain authentication and access controls
[Professor Messer](https://youtu.be/i0l6UCiybRI)

### Authorization, authentication and accounting

- AAA framework
  - Identification - This is who you claim to be
    - Usually your username
  - Authentication
    - Prove you are who you say you are
    - Password and other authentication factors
  - Authorization
    - Based on your identification and authentication,
what access do you have?
  - Accounting
    - Resources used: Login time,
data sent and received, logout time

- RADIUS (Remote Authentication Dial-In User Service)

  - One of the more common AAA protocols
    - Supported on a wide variety of platforms and devices
    - Not just for dial-in
  - Centralize authentication for users
    - same credential to log on to Routers, switches, firewalls
    - Server authentication
    - Remote VPN access
    - 802.1X network access
  - RADIUS services available on almost any server
operating system

- TACACS+ (Terminal Access Controller Access-Control System)
  - TACACS+
    - Remote authentication protocol alternative to RADIUS
    - Created to control access to dial-up lines to ARPANET
  - XTACACS (Extended TACACS)
    - A Cisco-created (proprietary) version of TACACS
    - Additional support for accounting and auditing
  - TACACS+
    - The latest version of TACACS, not backwards compatible
    - More authentication requests and response codes
    - Released as an open standard in 1993
- Kerberos
  - Network authentication protocol
    - Authenticate once, trusted by the system (unlike TACACS and RADIUS)
    - No need to re-authenticate to everything
    - Mutual authentication - the client and the server
      - Protect against man-in-the-middle or replay attacks
  - Standard since the 1980s
    - Developed by the Massachusetts Institute of Technology
(MIT)
    - RFC 4120
  - Microsoft starting using Kerberos in Windows 2000
    - Based on Kerberos 5.0 open standard
    - Compatible with other operating systems and devices

- Single sign-on with kerberos

  - Authenticate one time
    - Lots of backend ticketing, uses cryptographic tickets
  - No constant username and password input! - Save time
  - Only works with Kerberos
    - Not everything is Kerberos-friendly
- Local authentication

  - Credentials are stored on the local device
    - Does not use a centralized database
  - Most devices include an initial local account
    - Good devices will force a password change
  - Difficult to scale local accounts
    - No centralized administration
    - Must be added or changed on all devices
  - Sometimes useful as a backup
    - The AAA server might not be available
  
- LDAP (Lightweight Directory Access Protocol)
  - Protocol for reading and writing directories over an IP network
    - An organized set of records, like a phone directory
  - X.500 specification was written by the International
Telecommunications Union (ITU)
    - They know directories!
  - DAP ran on the OSI protocol stack
    - LDAP is lightweight, and uses TCP/IP (tcp/389 and udp/389)
  - LDAP is the protocol used to query and update an X.500 directory
    - used in windows AD / Apple OpenDirectory and OpenLDAP 
    - use attribute and value pairs (OU=Marketing/ L=London)
    - Hierarchical structure - builds a tree
    - Container objects - country / organization / OU
    - Leaf objects - users , computers , printers and files 

- Certificates
  - Smart card 
    - Private key is on the card
  - PIV (Personal Identity Verification) card
    - US Federal Government smart card
    - Picture and identification information
  - CAC (Common Access Card)
    - US Department of Defense smart card
    - Picture and identification
  - IEEE 802.1X
    - Gain access to the network using a certificate
    - On device storage or separate physical device

- Auditing and logging
  - Log all access details
    - Automate the log parsing
    - OS logins, VPN, device access
  - Usage auditing
    - How are your resources used?
    - Are your systems and applications secure?
  - Time-of-day restrictions
    - Nobody needs to access the lab at 3 AM


### Multifactor authentication
[Professor Messer](https://youtu.be/HKrJyfxi6xw)
- More than one factor 
  - Something you know - PW/PIN/pattern
  - Something you have - smart card/certificate on usb key/ HW,software token
  - Something you are - fingerprint / iris scan
  - Somewhere you are - IPv4 address/gps
  - Something you do -signature/ typing style
- Can be expensive
  - separate hardware tokens
  - Specialized scanning equipment

### Access control
[Professor Messer](https://youtu.be/HKrJyfxi6xw)
-  Network access control (NAC)
  - IEEE 802.1x - port based
  - You dont get access until you authenticate 
  - These are physical ports (not TCP/UDP ports)
  - Make extensive use of EAP and RADIUS - Extendable authentication protocol (EAP)
  - Administrative enable / disable - disable unused ports 
  - Duplicate MAC address checking - prevent spoofers
- IEEE 802.1x Authentication process
  - 
- Port security
  - Prevent unauthorized users from connecting to a switch interface - alert or disable the port
  - Configure a max number of source MAC addresses on an interface
  - The switch monitors the number of unique Mac addresses and maintain a list
- MAC filtering
  - Media Access Control - the hardware address 
  - Limit access through the physical hardware address 
  - Easy to spoofed
- Captive portal
  - Common on wireless networks
  - Access table recognizes a lack of authentication - redirect your web access to a captive portal page
  - Once proper auth is provided the web session continues  
- Access control lists
  - Used to allow / deny traffic 
  - Defined on the ingress or egress of an interface 
  - ACL evaluate on certain criteria (source IP/ Destination IP/ TCP/UDP port numbers)
  - Deny or permit

## 4.3 Given a scenario, secure a basic wireless network
[Professor Messer](https://youtu.be/UUQ4mhDAt1w)
### Wireless encryption 
  - All wireless computers are radio transmitters
and receivers - anyone can listen in
  - Solution: Encrypt the data
    - Everyone gets the shared password
    - Or their own password
  - Only people with the password can transmit and listen
    - WPA and WPA2
### WPA (Wi-Fi Protected Access)
  - 2002: WPA was the replacement for serious
cryptographic weaknesses in
WEP (Wired Equivalent Privacy)
    - Don’t use WEP
  - Needed a short-term bridge between WEP and
whatever would be the successor
    - Run on existing hardware
  - WPA: RC4 with TKIP (Temporal Key Integrity Protocol)
    - Initialization Vector (IV) is larger and use an encrypted hash along with IV
    - Every packet gets a unique 128-bit encryption key

Message Authentication Code Protocol) replaced TKIP
### TKIP-RC4 (Temporal Key Integrity Protocol)
  - Mixed the keys
    - Information send will change constantly because it Combines the secret root key with the IV
  - Adds sequence counter - prevents replay attacks
  - Implements a 64-bit Message Integrity Check
    - Protects against tampering
  - TKIP has it’s own set of vulnerabilities
    - Deprecated in the 802.11-2012 standard
### WPA2
  - WPA2 certification began in 2004
    - AES (Advanced Encryption Standard) replaced RC4
  - CCMP (Counter Mode with Cipher Block Chaining Message Authentication Code Protocol) replaced TKIP

### CCMP-AES
  - CCMP's block cipher mode uses AES for data confidentiality
  - 128-bit key and a 128-bit block size
  - Requires additional computing resources
  - CCMP security services (features)
    - Data confidentiality (AES), authentication,
and access control

### Authentication and authorization
- Along with Encryption methods like WPA we need Authentication methods to access the networks
- EAP (Extensible Authentication Protocol)
  - An authentication framework
  - Many different ways to authenticate based on RFC standards
  - WPA and WPA2 use five EAP types as authentication mechanisms
  - Two different Authentication methods, Tunneling based and Certificate based 
  - Tunneling based EAP
    - EAP PEAP, EAP-TTLS, EAP FAST
  - Certificate based EAP
    - EAP TLS
- EAP-FAST (EAP Flexible Authentication via Secure Tunneling)
  - Cisco’s proposal to replace LEAP (Lightweight EAP - previously used with WEP)
  - Lightweight and secure 


- PEAP (Protected Extensible Authentication Protocol)
  - Protected EAP , most widely used method
  - Created by Cisco, Microsoft, and RSA Security
  - Encapsulates EAP in a TLS tunnel, one certificate on the server
    - Combined a secure channel and EAP
  - Commonly implemented as PEAPv0/EAP-MSCHAPv2
    - Authenticates to Microsoft’s MS-CHAPv2 databases


- EAP-TTLS (EAP Tunneled Transport Layer Security)
  - Additional options to EAP-TLS, a widely used method
  - Allow us to tunnel other types of Authentication through the existing encrypted EAP communication
  - Support other authentication protocols in a TLS tunnel
  - Use any authentication you can support, while maintain security with TLS

- EAP-TLS (EAP Transport Layer Security)
  - Strong security, wide adoption (same security used for web servers)
  - Support from most of the industry
- 
- Wireless security modes
  - Configure the authentication on your wireless access point / wireless router based on need
  - Open System - No authentication password is required
  - WPA-Personal / WPA-PSK - home office or homes
    - WPA2 with a pre-shared key
    - Everyone uses the same 256-bit pre shared key
  - WPA-Enterprise / WPA-802.1X
    - Uses 802.1X to provide network access control 
    - Authenticates users individually with an authentication server (i.e., RADIUS)


- MAC filtering
  - Media Access Control - The “hardware” address
  - Limit access through the physical hardware address
    - Keeps the neighbors out
    - Additional administration with visitors
  - Easy to find working MAC addresses through wireless LAN analysis
    - MAC addresses can be spoofed
    - Security through obscurity (not actual security)
### Geofencing
  - Some MDMs allow for geofencing
  - Restrict or allow features when the device is in a particular area
  - Cameras
    - The camera might only work when outside the office
  - Authentication
    - Only allow logins when the device is located in a particular area
## 4.4 Summarize common networking attacks

### DoS (Denial of Service)
  - Force a service to fail
    - Overload the service
  - Take advantage of a design failure or vulnerability
    - Keep your systems patched!
  - Cause a system to be unavailable
    - Competitive advantage
  - Create a smokescreen for some other exploit
    - Precursor to a DNS spoofing attack
  - Doesn’t have to be complicated - simply Turn off the power

- Reflective
  - A reflective DoS is not a direct attack; it requires a third party that will inadvertently execute the DoS. 
  - The attacker will send a request to a third-party server and forge the source address of the packet with the victim’s IP address.
  - When the third party responds, it responds to the victim. 
  - There are two victims in this type of DoS attack; the first is the victim the attack is aimed at, and the second is the third-party server used to carry out |the attack.
- Amplified

  - An amplified DoS is a variant of a reflective DoS attack. 
  - Turn your small attack into a big attack
    - Often reflected off another device or service
  - An increasingly common DDoS technique
    - Turn Internet services against the victim
  - Uses protocols with little (if any) authentication or checks
    - NTP, DNS, ICMP
    - A common example of protocol abuse
  
- Distributed

  - Launch an army of computers to bring down a service
    - Use all the bandwidth or resources - traffic spike
  - This is why the bad guys have botnets
    - Thousands or millions of computers at your command
    - At its peak, Zeus botnet infected over 3.6 million PCs
    - Coordinated attack
  - Asymmetric threat
    - The attacker may have fewer resources than the victim
### Social engineering
  - Social engineering is the art of extracting vital information from an organization’s employee without raising suspicion. 
  - Social engineering works because employees often do not know what is sensitive and what is not. 
  - When an employee is put into a dilemma, like trying to help a fellow employee, they can disclose sensitive information. T
  - he tactics of a social engineering hacker is the “gift of gab.”


### Insider threat
  - We give people tons of access
    - Least privilege, anyone?
  - You have more access than others just by
entering the building
    - Lock away your documents
    - Some organizations have very specific procedures
  - Significant security issues
    - Harms reputation
    - Critical system disruption
    - Loss of confidential or proprietary information
  - Innocent employees - Phishing scams, hacking scams
  - Careless employees - Using a laptop for personal use
  - Disgruntled employees - Someone is out to get you
  - Defense in depth - Cover all possible scenarios
### Logic bomb
  - Waits for a predefined event
    - Often left by someone with grudge
  - Time bomb
    - Time or date
  - User event
    - Logic bomb
  - Difficult to identify
    - Difficult to recover if it goes off
### Rogue access point
  - A significant potential backdoor
    - Huge security concerns
  - Very easy to plug in a wireless AP
    - Or enable wireless sharing in your OS
  - Schedule a periodic survey
    - Walk around your building/campus
    - Use third-party tools / WiFi Pineapple
  - Consider using 802.1X (Network Access Control)
    - You must authenticate, regardless of connection type
    - Enable port security, limit MAC addresses per port
### Evil twin
  - An evil twin attack is a wireless phishing attack in which the attacker sets up a wireless access point to mimic the organization’s wireless access points. 
  - When a user connects to the evil twin, it allows the attacker to listen in on the user’s traffic. 
  - Evil twin access points often report a stronger signal to entice the user to connect to the specific access point.
### War-driving
  - War-driving was popular when wireless was first introduced to the market back in 2000.
  - It was used to find open access points for the use of free Internet. 
  - It is now used as an attack method for finding misconfigured access points for illegal entry into an organization’s network. 
  - It is performed with a laptop, GPS sensor, wireless card, and wireless mapping software (Kismet, inSSIDer)
### Phishing
  - Social engineering with a touch of spoofing
  - Phishing is normally performed via email by an attacker in an effort to gain usernames, passwords, and other personally identifiable information (PII).
  - An attacker will craft an email that looks like an organization’s system. 
  - The email will generally contain a URL to a compromised web server where the user will be prompted for their information.
### Ransomware
  - Ransomware is malicious software that encrypts files and requests a ransom for decryption of the files.
### DNS poisoning
 - DNS poisoning is an attack that targets an organization’s DNS server.
 -  An attacker will attempt to replace valid DNS entries with a compromised server’s IP address.
 -  The replacement of valid DNS entries is often performed via a DNS exploit or poisoning of DNS cache.
### ARP poisoning
 - ARP poisoning is an attack in which an attacker sends a forged ARP reply to a client to redirect traffic to the attacker’s host.
 - The forged ARP reply will contain the MAC address of the attacker’s host. 
 - The attacker can then use their host as a relay and eavesdrop on the conversation.
### Spoofing
  - Pretend to be something you aren’t
    - Fake web server, fake DNS server, etc.
  - Email address spoofing
    - The sending address of an email isn’t really the sender
  - Caller ID spoofing
    - The incoming call information is completely fake
  - Man-in-the-middle attacks
    - The person in the middle of the conversation pretends to be both endpoints
- MAC spoofing
  - Circumvent MAC-based ACLs
  - Fake-out a wireless address filter
  - Very difficult to detect
- IP address spoofing
  - Take someone else’s IP address
  - Used for ARP poisoning / DNS amplification / DDoS
  - Apply rules to prevent invalid traffic,enable switch security
### Deauthentication
 - The 802.11 wireless protocol contains a method for deauthentication of clients via a deauthentication frame. 
 - An attacker can send a deauthentication frame on behalf of the user, which disconnects them from the access point. 
 - Attackers will use this method in conjunction with an evil twin attack or in an effort to generate association traffic for purposes of cracking a passphrase.
 - 802.11w will prevent this, Some of the important management frames are encrypted
### Brute force
  - Brute force attacks - Online
    - Keep trying the login process
    - Very slow
    - Most accounts will lockout after a number of failed attempts
  - Brute force the hash - Offline
    - Obtain the list of users and hashes
    - Calculate a password hash, compare it to a stored
### VLAN hopping
- VLAN hopping is an attack method in which an attacker switches the VLAN that they are currently assigned to gain access to a system on another VLAN.
- VLAN hopping allows the attacker to bypass access controls to the protected resource.
- Two primary methods
  - Switch spoofing and double tagging
- Switch spoofing
  - Some switches support automatic configuration
    - Is the switch port for a device, or is it a trunk?
  - There’s no authentication required
    - Pretend to be a switch
    - Send trunk negotiation
  - Now you’ve got a trunk link to a switch
    - Send and receive from any configured VLAN
  - Switch administrators should disable trunk negotiation
   - Administratively configure trunk interfaces and device/access interfaces
- Double tagging
  - Craft a packet that includes two VLAN tags
    - Takes advantage of the “native” VLAN configuration
  - The first native VLAN tag is removed by the first switch
    - The second “fake” tag is now visible to the second switch
    - Packet is forwarded to the target
  - This is a one-way trip
    - Responses don’t have a way back to the source host
  - Don’t put any devices on the native VLAN
    - Change the native VLAN ID
    - Force tagging of the native VLAN
### On-path attack (previously known as man-in-the-middle attack)
  - Conventional MitM attacks allow the attacker to impersonate both parties involved in a network conversation. 
  - This allows the attacker to eavesdrop and manipulate the conversation without either party knowing. 
  - Can be used in conjunction with ARP poisoning, evil twin attack

### Exploits vs. vulnerabilities
  - Vulnerability
    - A weakness in a system
    - Allows the bad guys to gain access or cause a security breach
    - Some vulnerabilities are never discovered
    - Or discovered after years of use
    
  - Exploit
    - An exploit is script, code, or a technique to take advantage of a vulnerability.
    - Gain control of a system
    - Modify data
    - Disable a service
    - Zero-day exploits are exploits in which a system is targeted and no known patch exists to remediate the vulnerability.
## 4.5 Given a scenario, implement network device hardening

### Changing default credentials
  - Most devices have default usernames
and passwords
  , Change yours!
  , The right credentials provide full control
  , Administrator access
  , Very easy to find the
### Avoiding common passwords
  - People use common words as passwords
  , You can find them in the dictionary
  , Brute force attackers start with the easy ones
  , password, ninja, football
  , Many common wordlists are available
  , Some are customized by language
or line of work
### Upgrading firmware
  - Many network devices do not use
a traditional operating system
  , All updates are made to firmware
  , The potential exists for security vulnerabilities
  , Upgrade the firmware to
a non-vulnerable version
  , Plan for the unexpected
  , Always have a rollback plan
  , Save those firmware binaries
### Patching and updates
### File hashing
  - Hashing represents data as a short string of text
  , A message digest
  , Unique value
  , A hash is unique to a particular data structure
  , The hash will be different if the data changes
  , Verify a downloaded file (integrity)
  , Hashes may be provided on the download site
  , Compare the downloaded file hash with the posted hash value
### Disabling unnecessary services
  - Every service has the potential for trouble
  , The worst vulnerabilities are 0-day
  , “Unnecessary” isn’t always obvious
  , Windows 7 includes over 130 services by default
  , Windows 10 has over 240
  , This may require a lot of research
  , Many different sources
  , Don’t rely on the manufacturer
  , Trial and error may be necessary
  , Testing and monitoring
### Using secure protocols
  - SSH - Secure Shell
  , Terminal sessions; use instead of Telnet
  , SFTP - Secure (SSH) File Transfer Protocol
  , File transfer using SSH instead of FTP
  , SNMPv3 - Simple Network Management Protocol
  , Version 3 added encrypted communication
instead of SNMPv1 and v2
  , TLS/SSL - Transport Layer Security / Secure Sockets Layer
  , HTTP inside of TLS is HTTPS
  , IPsec - Internet Protocol Security
  , Encrypt at the IP packet level
### Generating new keys
  - We communicate to network devices
over encrypted channels
  , HTTPS, SSH
  , Encryption keys are usually managed on the device
  , SSL/TLS keys for HTTPS, SSH keys
  , Anyone with the key can potentially decrypt
administrative sessions
  , Or gain access to the device
  , Update or change the keys during the installation
  , Have a formal policy to outline processes
and procedures
### Disabling unused ports
- IP ports
  - Control traffic based on data within the content
  , Data in the packets
  , Use a firewall to allow or restrict port numbers
  , TCP and UDP filtering
  , Firewall location
  , Personal/Software firewall
  , Network-based firewall
- Device ports (physical and virtual)
  -    , Enabled physical ports
  , Conference rooms
  , Break rooms
  , Administratively disable unused ports
  , More to maintain, but more secure
  , Network Access Control (NAC)
  , 802.1X controls
  , You can’t communicate unless
you are authenticated

## 4.6 Explain common mitigation techniques and their purposes
[Professor Messer](https://youtu.be/AHg0eDLygHs)
### Signature management
- IPS signature management
    - You determine what happens when unwanted traffic
  appears
      - Block, allow, send an alert, etc.
      - Thousands of rules - Or more
    - Rules can be customized by group
      - Or as individual rules
  - This can take time to find the right balance
      - Security / alert “noise” / false positives
      - Old systems slow down with more rules, next gen IPS integrated with firewalls / hardware based systems 
### Device hardening
  - No system is secure with the default configurations
    - You need some guidelines to keep everything safe
  - Hardening guides are specific to the software or platform
    - Get feedback from the manufacturer or Internet
interest group
  - Other general-purpose guides are available online
### Change from the default VLAN
  - This is different than the “default VLAN” (which is the VLAN PCs connect by default if you dont specify - this is not it)

  - There is another type of VLAN called Native VLAN
  - When data is transmitted on a trunk link that is not tagged with a VLAN ID, the data will default to the native VLAN. 
  - The native VLAN is also the VLAN used for switch management.
  - The default native VLAN is VLAN 1 on all unconfigured switches from the factory; it is also the default membership for all ports on an unconfigured switch. 
  - This creates a potential security issue; if a new switch is plugged into the network and the default VLAN is not changed on the switch ports, a user will have direct access to the management network.

  - Native VLAN defaults to VLAN 1
  - But some Cisco management protocols use VLAN 1
  - Change the native VLAN number (e.g., VLAN 999)
  - Management protocols will continue to use VLAN 1
(even if it’s not formally configured on the trunk)
  - Non-trunked traffic will use the native VLAN number (VLAN 999)
### Switch port protection
[Professor Messer](https://youtu.be/2ufRXD3Jm2U)
- Spanning tree protocol 
  - Spanning tree can create large outages if not properly configured.
  - To find the root bridge, the Spanning Tree Protocol (STP) recalculates the entire switching topology every time a switch or any device is connected to a switch port. 
  - During this time, frames are not allowed to pass on the switch port transitioning to an up status. 
  - Rapid Spanning Tree Protocol (RSTP) takes a more proactive approach to calculation of the switching topology, so the switch port is turned up quicker.

- Flood guard

  - Configure a maximum number of source MAC addresses on an interface
    - You decide how many is too many
    - You can also configure specific MAC addresses
  - The switch monitors the number of unique MAC addresses
    - Maintains a list of every source MAC address
  - Once you exceed the maximum, port security activates
    - Interface is usually disabled by default

- BPDU guard Bridge Protocol Data Unit
  - Spanning tree takes time to determine if a switch port should forward frames
    - Bypass the listening and learning states
    - Cisco calls this PortFast
  - BPDU (Bridge Protocol Data Unit)
    - The spanning tree control protocol
  - If a BPDU frame is seen on a PortFast configured interface (i.e., a workstation), shut down the interface
  - This shouldn’t happen - Workstations don’t send BPDUs

- Root guard

  - The feature is similar to BPDU Guard because it is configured in conjunction with STP and RSTP on user-facing access ports. 
  - It should never be configured on trunk ports between switches, similar to BPDU Guard.
  - Spanning tree determines the root bridge
    - You can set the root bridge priority to 0, but that doesn’t always guarantee the root
  - Root guard allows you to pick the root
    - Cisco feature
    - Prevents a rogue root bridge
  - If your root bridge receives a superior STP BPDU on a root guard port, root guard changes the interface status to “root-inconsistent” (listening)
    - This effectively disables the interface to the rogue root

- DHCP snooping
  - DHCP snooping is a feature on Cisco switches as well as other vendor switches. 
  - It prevents a rouge DHCP server, also called a spurious DHCP server, from sending DHCP messages to clients. 
  - When DHCP snooping is configured on switches, all switch ports are considered untrusted ports. 
  - Only a trusted port can forward DHCP messages; all untrusted ports are filtered for DHCP messages.
  - IP tracking on a layer 2 device (switch)
    - The switch is a DHCP firewall
    - Trusted: Routers, switches, DHCP servers
    - Untrusted: Other computers, unofficial DHCP servers
  - Switch watches for DHCP conversations
    - Adds a list of untrusted devices to a table
  - Filters invalid IP and DHCP information
  - Static IP addresses
    - Devices acting as DHCP servers
    - Other invalid traffic patterns
### Network segmentation
- When a network is flat with no segmentation, it is impossible to secure because an intruder has potential access to all hosts and devices. Network segmentation allows for smaller broadcast domains that increases usable bandwidth. We can also implement access control lists (ACLs) between the segments. This directly increases security as well as usable bandwidth.
- Screened subnet (previously
known as DMZ)
  - Demilitarized zone
    - An additional layer of security
between the Internet and you
    - Public access to public resources

  - Physical, logical, or virtual segmentation
    - Devices, VLANs, virtual networks
  - Performance - High-bandwidth applications
  - Security
    - Users should not talk directly to database servers
    - The only applications in the core are SQL and SSH
  - Compliance
    - Mandated segmentation (PCI compliance)
    - Makes change control much easier
Physical segmentation
  - Devices are physically separate
    - Switch A and Switch B
  - Must be connected to provide communication
    - Direct connect, or another switch or router
    - Web servers in one rack
    - Database servers on another
  - Customer A on one switch, customer B on another
    - No opportunity for mixing data
  - Separate devices
    - Multiple units, separate infrastructure

Logical segmentation with VLANs
  - Virtual Local Area Networks (VLANs)
    - Separated logically instead of physically - Cannot communicate between VLANs without a Layer 3 device / router
### Privileged user account

  - Elevated access to one or more systems
    - Administrator, Root
  - Complete access to the system
    - Often used to manage hardware, drivers, and software installation
  - Needs to be highly secured
    - Strong passwords, 2FA
    - Scheduled password changes
  - User accounts should have limited control
    - Role separation with different access rights
    - More difficult for a single limited account
### File integrity monitoring
  - Some files change all the time
    - Some files should NEVER change
  - Monitor important operating system & application files
    - Identify when changes occur
  - Windows - SFC (System File Checker)
  - Linux - Tripwire
  - Many host-based IPS options
### Role separation
### Restricting access via ACLs
  - Use device ACLs to limit access to important
infrastructure devices
    - Only admins should be able to login (only allow traffic from  network management subnet)
  - Drop all other traffic
    - Define the subnets for the technology teams
  - This is a bit different than setting an application ACL
    - You’re dropping traffic for non-authorized users
    - Used mostly for access to management interfaces with whitelisted IPs
Honeypots
  - Attract the bad guys - and trap them there
  - The bad guys are probably a machine
  - Makes for interesting recon
  - Honeypots / Honeynet - a network of honeypots
  - Many different options
  - http://www.projecthoneypot.org/, honeyd
  - Constant battle to discern the real from the fake

### Honeypot/honeynet
  - Attract the bad guys - and trap them there
  - The bad guys are probably a machine
    - Makes for interesting recon
  - Honeypots / Honeynet - a network of honeypots
  - Many different options
    - projecthoneypot.org, honeyd
- Constant battle to discern the real from the fake
### Penetration testing
  - Pentest
    - Simulate an attack
  - Similar to vulnerability scanning
    - Except we actually try to exploit the vulnerabilities
  - Often a compliance mandate
    - Regular penetration testing by a 3rd-party
  - National Institute of Standards and Technology , echnical Guide to Information Security Testing and Assessment