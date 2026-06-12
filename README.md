# Myles' Homelab: Small Business IT Environment Simulations

A grouping of my homelab experience thus far.

**Purpose:** Concurrent with my studies, I have created this homelab to simulate a real world small-to-medium business IT environment to the best of my abilities. Configurations, breakages, and fixes are all documented here with the aim to develop hands-on skills for a Level 1 Help Desk / IT Suppoer role. 

**Status:**`[Active]`
**Last Update:**`[12-06-2026]`

---

## Lab Overview








---
# Glossary List 


| Term	| Definition |
| --- | --- |
| Forest |	Security boundary, top-level container |
| Domain	| Namespace and administrative boundary |
| Domain Controller (DC) | A server that hosts Active Directory Domain Services and authenticates users/computers in a domain | 
| DNS (Domain Name System) | Resolves domain names (e.g., DC01.homelab.local) to IP addresses so clients can locate domain controllers |
| Static IP | A manually assigned IP address that does not change, required for domain controllers |
| DHCP (Dynamic Host Configuration Protocol | Automatically assigns IP addresses to client devices; DC should NOT use DHCP |
| Tree	| A set of domains with contiguous DNS names |
| OU | Container for users/computers within a domain |
| Global Catalog | Searchable index of all objects in the forest |
| Global Group | A group scope that contains users from the same domain and can be nested into other groups |
| Security Group | A collection of user accounts used to assign permissions collectively instead of individually | 
