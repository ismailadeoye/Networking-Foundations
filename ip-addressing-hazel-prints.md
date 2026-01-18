# IP Addressing Lab
This lab is divided into two sections.

Section ALPHA - Packet Tracer

Section BETA - Virtual Machines

Focus:
This lab focuses on understanding IPv4 addressing, subnet masks, and default gateways
using Packet Tracer and virtual machines.

Key concepts tested:
- Local vs remote traffic
- ARP resolution
- Default gateway behaviour

SECTION ALPHA
Mr Hazel approaches a Junior Network Engineer about his new company named Hazel Printing Press 
who would like to use a router, swicth and three PCs, each for ADMIN, SECRETARY, and GUESTS respectively
using IP address 192.168.10.0/24 network address. Configure and tests all connectivity from each hosts and 
to the router named Hazel_Prints.

DOCUMENTATION FOR THE NETWORK TOPOLOGY
- THE NETWORK TOPOLOGY FOR HAZEL PRINTING COMPANY
<img width="1358" height="716" alt="image" src="https://github.com/user-attachments/assets/c25b1177-3152-471b-b33d-6ecaa0aa8f38" />

ROUTER CONFIGURATION ( Hazel_Prints )
								
<img width="640" height="309" alt="image" src="https://github.com/user-attachments/assets/6b2cf4f5-0026-4958-a0ec-468d685d85a1" />

PCs CONFIGURATION

SECRETARY

<img width="388" height="237" alt="image" src="https://github.com/user-attachments/assets/6b680bba-629b-4b2f-bbea-84beab1a3799" />

ADMIN

					
<img width="389" height="227" alt="image" src="https://github.com/user-attachments/assets/22ceb6a1-e02b-4a12-83b1-6b310ddf7ba7" />


GUEST

<img width="404" height="239" alt="image" src="https://github.com/user-attachments/assets/70991d5e-0e1c-48b1-aaa3-39c599477bf7" />


TEST CONNECTIVITY
ADMIN pings SECRETARY

					
<img width="432" height="330" alt="image" src="https://github.com/user-attachments/assets/7d6f625e-b3a1-4a0b-977f-e89b47ad0ecc" />


ADMIN pings GUEST

<img width="416" height="199" alt="image" src="https://github.com/user-attachments/assets/782b4722-afaf-4c1c-bdae-5f86f8268ccd" />


SECRETARY pings GUEST

<img width="425" height="346" alt="image" src="https://github.com/user-attachments/assets/12504ce9-d1be-48ce-92ac-52e894402ab4" />


GUEST pings ADMIN

<img width="433" height="335" alt="image" src="https://github.com/user-attachments/assets/eccaa25a-6929-490f-a4c6-77ce4d0609f6" />


GUEST pings Hazel_Prints (Gateway)

<img width="444" height="535" alt="image" src="https://github.com/user-attachments/assets/251097d1-1b90-4089-960e-f7e8152fd6c9" />

BREAK IT FOR TROUBLESHOOTING

Confirm SECRETARY pings Hazel_Prints (GATEWAY)

<img width="405" height="191" alt="image" src="https://github.com/user-attachments/assets/c2b70c3f-3995-43e4-b3f4-c173170706a9" />

Change SECRETARY's GATEWAY

<img width="388" height="302" alt="image" src="https://github.com/user-attachments/assets/1e78e5bc-93ab-44b2-8f96-a9331723647e" />

SECRETARY pings GATEWAY after Changing it


<img width="469" height="491" alt="image" src="https://github.com/user-attachments/assets/8b3d4d63-27a5-4486-9810-42bd037f6dbf" />


# Default Gateway Misconfiguration Test

After changing the default gateway on PC -SECRETARY, local connectivity to 192.168.10.1
remained functional. This is because hosts communicate directly within the same
subnet using ARP, that it, it finds the MAC address of 192.168.10.1 and sends packets directly 
using Address Resolution Protocol.

However, traffic to 192.168.20.1 failed because the default gateway was not
reachable, demonstrating that the gateway is only required for off-subnet traffic.
# Fix It

<img width="357" height="297" alt="image" src="https://github.com/user-attachments/assets/e414c568-f752-4bb3-bf44-be8bebfc7b66" />
<img width="413" height="198" alt="image" src="https://github.com/user-attachments/assets/3f8bcd39-0714-40d8-9ab1-821bf7393768" />

Connectivity is restored.

**Why did the ping fail?**
According to the rule, a traffic sent within same subnet would deliver successful using ARP, while traffic sent outside of the subnet, 
would require a default gateway to route traffic. The ping fails because the default gateway for Hazel_Prints router is 192.168.10.1, 
and become unreachable because the IP was wrongly configured on the Secretary's PC to 192.168.20.1. 
Although, despite the changes observed, the ping to 192.168.10.1 was successful because is the same local subnet of the host (SECRETARY's PC).
The default gateway is ONLY used when traffic is destined for a DIFFERENT NETWORK.  

**What role did the default gateway play?** 
It serves as the path to forward traffic from local to remote, or from the host (PCs ) subnet to a different subnet.
