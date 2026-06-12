# Progress Notes


**Purpose:** Session-to-session documentation of what I have done, learnt, broke or fixed for the purpose of education and training. The practice of record keeping being vital for learning from mistakes and a point of reference for future tickets.



**04/06/2026**
**Goals:** >Create a Windows Server 2022 VM using VirtualBox
                  >> Network configured (static IP)
                  >>> Computer rename to reflect Domain Controller
                  >>>>


Using VirtualBox, I deployed a Windows Server 2022 VM, configuring it with 4GB RAM, 64 GB storage and dedicated 2 CPU processors for the purpose of acting as a Domain Controller. 

Prior to running, I had also changed the Adapter 1 Network Settings from ATTACHED TO > **NAT**  to ATTACHED TO > **INTERNAL NETWORK**.
This is because I dont want the DC to talk directly to my home router just yet. I will do that later on when I add NAT for internet access.

Upon booting for the first time, using the Server Manager in Windows Server, I firstly renamed the PC to "DC01" and configured the static IP address.



<img width="991" height="362" alt="image" src="https://github.com/user-attachments/assets/af0e54e3-8f4c-4027-911f-e1c8251739b4" />





<img width="412" height="575" alt="image" src="https://github.com/user-attachments/assets/e53a2148-fae2-41d5-9f69-2e295cabea1c" />

Assigning a static IP address instead of using automatic assignment (DHCP) as Domain Controllers must have a static IP address, lest the client computers would not be able to find the DC to log in.
192.168.X.X being a private IP range and safe for internal network use.
.10 being a common subnet for small businesses.
.10 as the host address is easy to remember. (Either .10 or .1)

<img width="469" height="527" alt="image" src="https://github.com/user-attachments/assets/b85e8917-d732-4815-9ff9-210a50ddb867" />

At this moment, DNS is not installed yet. But setting it to 127.0.0.1 (itself) prepares the server to run DNS after I add the role. 
It is set to itself to be able to answer queries from client computers such as "Where is DC01?". A DC must be its own DNS server to resolve domain names queries,

Default gateway has been left blank intentionally, as we are in "Internal Network" mode. Further on I will either add a second network adapter or change network modes to give the DC internet access.


**06/06/2026**
**Goals:** > Install Active Directory Domain Services role
                  >> Promote DC01 to a Domain Controller
                  >>> Create my first domain (homelab.local)
                  >>>> Create my first domain user account

