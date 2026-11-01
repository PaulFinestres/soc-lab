# Lab 5.1 – Network Architecture & Infrastructure

**Status:** Completed  
**Estimated duration:** 10–12 hours

## Objective

Build the network foundation for the SOC lab. This includes the virtual infrastructure, network segmentation, routing, firewall policy and basic service validation.

## Environment

- **Hypervisor:** Proxmox VE
- **Firewall/router:** OPNsense
- **Directory and DNS:** Windows Server / Active Directory
- **SOC server:** Ubuntu Server 26.04.1 LTS
- **Administration:** Windows workstation with SSH access through WindTerm

## Network architecture

![SOC network architecture](architecture.png)

The lab is divided into separate VLANs for clients, attack simulation, DMZ, servers, SOC services, administration and infrastructure management.

## VLAN addressing

| VLAN | Name | Network | Gateway |
|---:|---|---|---|
| 10 | CLIENTS | `192.168.10.0/24` | `192.168.10.254` |
| 20 | ATTACKER | `172.20.20.0/24` | `172.20.20.254` |
| 40 | DMZ | `10.0.40.0/27` | `10.0.40.30` |
| 50 | SERVERS | `10.0.50.0/28` | `10.0.50.14` |
| 80 | SOC / MONITORING | `172.20.80.0/28` | `172.20.80.14` |
| 90 | ADMIN | `192.168.90.0/28` | `192.168.90.14` |
| 99 | INFRA-MGMT | `192.168.99.96/28` | `192.168.99.110` |

## Virtual machines

The Proxmox resource pool contains the following lab VMs:

| VM ID | Name | Role |
|---:|---|---|
| 600 | `soc-fw-01` | OPNsense firewall |
| 601 | `soc-adm-01` | Administration workstation |
| 602 | `soc-attack-01` | Attack simulation workstation |
| 604 | `soc-dmz-01` | DMZ host |
| 605 | `soc-ad-01` | Active Directory and DNS |
| 607 | `soc-siem-01` | SOC / SIEM server |
| 608 | `soc-cli-01` | Client workstation |

## Configuration and validation

### OPNsense

- Configured the WAN connection and upstream gateway.
- Created the VLAN interfaces and their gateway addresses.
- Applied interface firewall rules for the services currently required by the lab.
- Configured manual outbound source NAT for the lab networks, translating traffic to the OPNsense WAN address (`192.168.1.200`).
- Confirmed outbound connectivity from the relevant internal networks.

### DNS

The Active Directory DNS server is `10.0.50.10`, with the internal DNS domain `paul.lan`.

Validation included:
- Forward lookup of `soc-ad1.paul.lan`.
- Reverse lookup of `172.20.80.10`, resolving to `soc-wazuh1.paul.lan`.
- Confirmation that the SOC server uses `10.0.50.10` as its DNS resolver.

### SSH administration

Remote access from the administration workstation to the SOC server was validated using WindTerm.

SSH is configured with:
- Public-key authentication enabled.
- Password authentication disabled.
- Root login disabled.
- SSH listening on TCP port `3333`.

## Evidence

Screenshots supporting the configuration and validation are stored in [`evidence/`](evidence/).

| File | Evidence |
|---|---|
| `01-proxmox-vm-inventory.png` | SOC virtual machines in the Proxmox resource pool |
| `02-opnsense-dashboard.png` | OPNsense system, gateway and interface status |
| `03-opnsense-source-nat.png` | Manual outbound source NAT rules |
| `04-ssh-hardening.png` | Effective SSH daemon security settings |
| `05-dns-reverse-lookup.png` | Reverse DNS lookup for the SOC server |
| `06-dns-forward-lookup.png` | Forward DNS lookup for the AD server |
| `07-ssh-connection.png` | Successful SSH administration session |

## Result

The virtual network is deployed and basic connectivity has been validated. OPNsense provides routing, firewalling and outbound NAT between the lab networks. DNS resolution and secured SSH administration to the SOC server are working.

## Next step

**Lab 5.2 – Suricata IDS on OPNsense:** deploy and configure network intrusion detection, then validate alert generation using controlled test traffic.
