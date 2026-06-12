# Progress Notes

**Purpose:** Session-to-session documentation of what I have done, learnt, broke, or fixed for the purpose of education and training. The practice of record keeping is vital for learning from mistakes and as a point of reference for future tickets.

---

### Set up the environment using Virtual Box
## 04/06/2026

### Goals

- Create a Windows Server 2022 VM using VirtualBox
  - Network configured (static IP)
  - Computer renamed to reflect Domain Controller role

### Notes

Using VirtualBox, I deployed a Windows Server 2022 VM, configuring it with 4GB RAM, 64GB storage, and dedicated 2 CPU processors for the purpose of acting as a Domain Controller.

Prior to running, I also changed the Adapter 1 Network Settings from **Attached To: NAT** to **Attached To: Internal Network**. This is because I do not want the DC to talk directly to my home router just yet. I will enable that later when I add NAT for internet access.

Upon booting for the first time, using Server Manager in Windows Server, I firstly renamed the PC to `DC01` and configured the static IP address.

<img width="991" height="362" alt="image" src="https://github.com/user-attachments/assets/af0e54e3-8f4c-4027-911f-e1c8251739b4" />

<br />

<div align="center">
<img width="412" height="575" alt="image" src="https://github.com/user-attachments/assets/e53a2148-fae2-41d5-9f69-2e295cabea1c" />
</div>

### Why a static IP?

Assigned a static IP address (192.168.10.10) instead of DHCP. Domain Controllers require a static IP for two reasons:

1. Client computers store the DC's IP address in their DNS cache and network configuration. A changing IP would break name resolution and domain trust.

2. The DC runs the DNS Server role, which must be bound to a fixed address. DHCP lease expiration or renewal would cause DNS failures across the entire domain.

If the IP ever changed, client computers would not be able to locate the DC to authenticate and log in.

- `192.168.X.X` is a private IP range and safe for internal network use
- `.10` is a common subnet for small businesses
- `.10` as the host address is easy to remember (either `.10` or `.1` are typical)
  
<div align="center">
<img width="469" height="527" alt="image" src="https://github.com/user-attachments/assets/b85e8917-d732-4815-9ff9-210a50ddb867" />
</div>


### Why DNS set to itself (127.0.0.1)?

At this moment, DNS is not installed yet. Setting it to `127.0.0.1` (itself) prepares the server to run DNS after I add the role. A Domain Controller must be its own DNS server to resolve domain name queries from client computers such as "Where is DC01?".

### Why no default gateway?

The default gateway has been left blank intentionally because the VM is in **Internal Network** mode. Later, I will either add a second network adapter or change network modes to give the DC internet access.

---
### Set up Domain Controller and domain
## 06/06/2026

### Goals

- Install Active Directory Domain Services (AD DS) role
  - Promote `DC01` to a Domain Controller
  - Create a domain: `homelab.local`
  - Create the first domain user account


Created homelab.local as a new forest to establish a completely independent Active Directory environment. 
In my small deployment lab, the forest and the domain share the same name (`homelab.local`). A larger company deployment may have a forest named `companyExample.com` with domains like `us.company.Example.com` or `au.company.com` etc.


### Notes

- **Domain name:** `homelab.local`
- **Login after reboot:** `HOMELAB\Administrator`

<img width="1241" height="462" alt="image" src="https://github.com/user-attachments/assets/ba228c88-e65c-4493-bb74-f312a0c29267" />

### Organisational Units, users, groups
## 06/06/2026

### Goals

- Create Organisational Units (Sales, HR, IT)
- Create users within said OUs
- Create groups for permission management and add users to groups

<img width="1080" height="456" alt="image" src="https://github.com/user-attachments/assets/2c7a74f9-8231-434b-b487-9c386c015b5f" />

---

### Group Policy
## 07/06/2026

### Goals

- 


