## Ex. No: 5  VLAN Configuration Using a Managed Switch
# Date: 29-10-2026
________________________________________
# Objective
To configure Virtual Local Area Networks (VLANs) on a managed switch and verify that hosts within the same VLAN can communicate while others cannot.
________________________________________
# Apparatus/Tools Required
•	Cisco Packet Tracer<br>
•	1 Managed Switch (e.g., 2960)<br>
•	4 PCs<br>
•	Straight-through Ethernet cables<br>
________________________________________
# Network Topology Diagram
Description:<br>
•	PC0 and PC1 are assigned to VLAN 10.<br>
•	PC2 and PC3 are assigned to VLAN 20.<br>
•	All PCs are connected to different ports on the same switch.<br>
(Insert screenshot of your Packet Tracer setup here)<br>
<img width="1920" height="1200" alt="Screenshot 2026-10-29 161916" src="https://github.com/user-attachments/assets/3b66b994-eda0-40cd-bed4-009e1ebf4801" />

________________________________________
# IP Addressing Table
Device	VLAN	IP Address	Subnet Mask	Port<br>
PC0	10	192.168.10.1	255.255.255.0	FastEthernet0/1<br>
PC1	10	192.168.10.2	255.255.255.0	FastEthernet0/2<br>
PC2	20	192.168.20.1	255.255.255.0	FastEthernet0/3<br>
PC3	20	192.168.20.2	255.255.255.0	FastEthernet0/4<br>
________________________________________
# Procedure
1.	Open Cisco Packet Tracer and add 4 PCs and 1 Switch.<br>
2.	Connect PC0–PC3 to switch ports FastEthernet0/1 to FastEthernet0/4 respectively.<br>
3.	Assign static IP addresses to each PC as per the IP table.<br>
4.	Enter the Switch CLI and create two VLANs:<br>
o	VLAN 10 for PC0 and PC1<br>
o	VLAN 20 for PC2 and PC3<br> 
5.	Assign the respective switch ports to their VLANs.<br>
6.	Use the ping command from PC0 to PC1 (should succeed).<br>
7.	Try pinging from PC0 to PC2 (should fail — different VLANs).<br>
________________________________________
# Commands Used (Switch CLI)
bash<br>
CopyEdit<br>
Switch> enable<br>
Switch# configure terminal<br>

Switch(config)# vlan 10<br>
Switch(config-vlan)# name STAFF<br>
Switch(config-vlan)# exit<br>

Switch(config)# vlan 20<br>
Switch(config-vlan)# name STUDENTS<br>
Switch(config-vlan)# exit<br>

Switch(config)# interface range fastethernet0/1 - 2<br>
Switch(config-if-range)# switchport mode access<br>
Switch(config-if-range)# switchport access vlan 10<br>
Switch(config-if-range)# exit<br>

Switch(config)# interface range fastethernet0/3 - 4<br>
Switch(config-if-range)# switchport mode access<br>
Switch(config-if-range)# switchport access vlan 20<br>
Switch(config-if-range)# exit<br>
________________________________________
# Output (Screenshots)
•	VLAN configuration on switch<br>
•	PC IP settings<br>
•	Successful ping between PCs in the same VLAN<br>
•	Failed ping between PCs in different VLANs<br>
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/a1fcf51a-6de8-4081-9296-c602ed885025" />
<img width="1920" height="1200" alt="Screenshot 2026-10-29 162247" src="https://github.com/user-attachments/assets/7a02a071-5bee-418d-80e6-fe3eed858606" />
<img width="1920" height="1200" alt="Screenshot 2026-10-29 162314" src="https://github.com/user-attachments/assets/74977ec2-d5db-4e95-9067-57a34c968f2a" />
<img width="1920" height="1200" alt="Screenshot 2026-10-29 162402" src="https://github.com/user-attachments/assets/eaa79a10-13e0-425e-9e68-4c2ac3c24621" />
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/2709731b-2bed-44ee-afda-4944e8ebcb8a" />

________________________________________
# Result
Successfully created and configured VLANs on a managed switch. Verified that only PCs within the same VLAN could communicate with each other.

