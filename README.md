# About me:

Hi everyone, My name is Sayed Hossain Ansari. I'm From Kolkata. Ambitious B.Tech/BE student at Jalpaiguri Government Engineering College (JGEC), West Bengal, specializing in Computer Science, Cyber Security. Eager to leverage technical skills and creativity to contribute to innovative projects and make a positive impact in the field of technology✨

```"I am happy to share that I have learned how to configure a cisco switch." ```

# #Networking [Switch Configuation---Part-1]

### **Topics :-**

**- Working of VLAN**

**1. Create VLAN**

**2. Assign Ports to VLAN**

**3. View VLAN Database(command)**

### Working of VLAN : 
     A VLAN (Virtual Local Area Network) in a Cisco switch allows network segmentation by creating multiple logical networks within
     
     a single physical network. Each VLAN is identified by a unique ID and operates as a separate broadcast domain, isolating
      
     traffic to improve performance and security. VLANs are configured using commands to create, assign IDs, and add ports to
       
     specific VLANs. This setup enables efficient traffic management and enhanced network security.

### 1. Create VLAN : 
         SW(config)# vlan <number>     (ex:- 10)

 ### Name VLAN : 

         SW(config-vlan)# name ____________  (ex:- SALES) 

### 2. Assign Ports to VLAN:

       SW(config)# interface <interface name>  (ex:-fastEthernet 0/1) 

       SW(config-if)# switchport mode access

       SW(config-if)# switchport access vlan 10

### 3. View Vlan Data Base(command)

    SW# show vlan

### - Here is the sample picture of VLAN Configuration : (Drawing no. 1)

<img align="" width="800" height="800" src="./part 1.jpg">


---------------------------
------------------------
-----------------------

# #Networking [Switch Configuation---Part-2]

### Topics : -

**- Working of VTP (VLAN Trunking Protocol)**

**1. Configuration**.

**2. VTP Prunning**.

**3. Native Vlan**.

### Working of VLAN:
    ***First of all VTP is not a Trunking Protocol***

    VTP (VLAN Trunking Protocol) is a Cisco-proprietary protocol used to manage VLANs across a network of switches. It simplifies
    
    VLAN configuration by propagating VLAN definitions from a central switch to all other switches in the VTP domain. VTP operates 
     
    in three modes: Server, Client, and Transparent. In Server mode, switches can create, modify, and delete VLANs, and these 
     
    changes are advertised to other switches. Client mode switches receive and apply VLAN information from servers
     
    but cannot make changes. Transparent mode switches forward VTP advertisements but do not apply the
      
    changes themselves.

### 1. Configuration: 

    SW(config)# vtp version 1/2

    SW(config)# vtp mode (server/client/transparent)

            here, In Server mode, switches can create, modify, and delete VLANs, and these changes are advertised to other switches.

            In Client mode switches receive and apply VLAN information from servers but cannot make changes. 

            In Transparent mode switches forward VTP advertisements but do not apply the changes themselves.


    SW(config)# vtp domain _____________ (any domain name ex:- sayed.org)

    SW(config)# vtp password <word>  (ex:- word = cisco)

### 2. VTP Prunning:

    VTP pruning is a feature of the VLAN Trunking Protocol (VTP) that enhances network efficiency by reducing unnecessary traffic 
    
    on trunk links. When enabled, VTP pruning prevents broadcast, multicast, and unknown unicast traffic from being sent across 
    
    trunk links to switches that do not have ports in the destination VLAN. This helps in conserving bandwidth and optimizing 
    
    network performance by ensuring that VLAN traffic is only forwarded to trunk links that require it.


Configuration : 
    
    SW(config)# vtp prunning

    SW(config)# interface <#>  (ex:- fastEthernet 0/1)

    SW(config-if)# switchport mode trunk

    SW(config-if)# switchport trunk allowed vlan <all/none/add/remove/#>


### 3. Native VLAN:

    SW(config)# switchport trunk native vlan <#>

             ----In VTP, the native VLAN is used to handle untagged traffic on a trunk port. It allows devices that do not support 
             
                  VLAN tagging to communicate with the network and ensures compatibility with older devices and protocols.


### Here is the Sample Picture of VTP SETUP : (Drawing no. 2)

<img align="" width="1000" height="500" src="./PART 2.jpg">


------------
--------------------
--------------------

# #Networking [Switch Configuation---Part-3]

### Topics :-

**1. Slow connections**


**2. Switch Port Security**

###    ***1.  Slow connection :*** {
    Reason for slow connection : -
           
                1. DUPLEX :- {  1. Half Duplex      2. Full Duplex }
                2. SPEED
   
    ~ Half Duplex :-  Means device can only transmit or recieve.

    ~ Full Duplex :- Means device can do both(transmit and recieve) at the same time.
}

#### SET DUPLEX :
    SW(config)# interface fastEthernet 0/1  (# whatever interfaces you want)

    SW(config-if)# duplex ______________   (full/half)

#### SET SPEED (Internet speed of Switch)
    SW(config)# interface fastEthernet 0/1   (# whatever you want)

    SW(config)# speed ______________   (ex :- 50, 100 ----> in MBPS)

### ***2. Switch Port Security :***

  ##### CONFIGUARTION :-

    SW(config)# interface fastEthernet 0/1       (whatever interfaces you want)

    SW(config)# switchport mode access

    SW(config)# switchport access vlan 1

    SW(config)# switchport port-security ?
                ---> mac address = secure mac address
                ---> maximum = max secure address
                ---> violation = security violation mode.

    lets use the [mac address] option

    SW(config)# switchport port-security mac address __________________  (put any mac address, whatever you want)


    **NOTE : - If you manually provide a MAC address, only the device with that MAC address will be supported on that interface, 
               and other devices will not be supported.

#### ANOTHER WAY TO ASSIGN MAC ADDRESS  *(USING STICKY KEY)* : -

    SW(config-if)# switchport port-security mac-address sticky

    **NOTE :- This command means that as soon as a system communicates through this port, its MAC address will be automatically 
    allocated to that interface, and only that device will be able to communicate with the switch.

#### Or we can also use **maximum** and **violation** port-security mode
