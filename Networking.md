# About me:

Hi everyone, My name is Sayed Hossain Ansari. I'm From Kolkata. Ambitious B.Tech/BE student at Jalpaiguri Government Engineering College (JGEC), West Bengal, specializing in Computer Science, Cyber Security. Eager to leverage technical skills and creativity to contribute to innovative projects and make a positive impact in the field of technology✨

```"I am happy to share that I have learned how to configure a cisco switch." ```

# #Networking [Switch Configuation---Part-1].

### **Topics :-**

- Working of VLAN
1. Create VLAN
2. Assign Ports to VLAN
3. View VLAN Database(command)

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

### - Here is sample picture : -


<img align="middle" width="" height="" src="./part 1.jpg">
