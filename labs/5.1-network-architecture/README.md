# Lab 5.1 – Network Architecture & Infrastructure

**Status:** Completed  
**Estimated duration:** 10–12 hours

## Objective

Build the network foundation for the SOC lab: virtual infrastructure, network segmentation, routing, firewall policy and basic service validation.

## Architecture

The lab runs on Proxmox VE. OPNsense provides routing, firewall policy and outbound NAT between the virtual networks.

![SOC network architecture](architecture.png)

## Environment

| Component | Role |
|---|---|
| Proxmox VE | Hypervisor |
| OPNsense (`soc-fw-01`) | Firewall and router |
| Windows Server (`soc-ad-01`) | Active Directory and DNS |
| Ubuntu Server 26.04.1 (`soc-siem-01`) | SOC / SIEM server |
| `soc-adm-01` | Administration workstation |
| `soc-attack-01` | Attack simulation workstation |
| `soc-dmz-01` | DMZ host |
| `soc-cli-01` | Client workstation |

### Virtual machines

The following VMs are deployed in Proxmox:

![Proxmox SOC VM inventory](evidence/01-proxmox-vm-inventory.png)

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

## Firewall and outbound NAT

OPNsense handles inter-VLAN routing and applies firewall rules according to the services currently required by the lab.

Outbound source NAT is configured manually. Internal network traffic is translated to the OPNsense WAN address (`192.168.1.200`) when leaving through `WAN_HOME`.

![OPNsense dashboard](evidence/02-opnsense-dashboard.png)

**Manual outbound source NAT rules:**

![OPNsense outbound NAT rules](evidence/03-opnsense-source-nat.png)

## Administration access

Remote administration from the ADMIN workstation to the SOC server was validated using WindTerm.

SSH listens on TCP port `3333` and is configured to use public-key authentication. Password authentication and root login are disabled.

**Effective SSH daemon settings:**

![Effective SSH configuration](evidence/04-ssh-hardening.png)

**Successful remote SSH session:**

![SSH connection to SOC server](evidence/07-ssh-connection.png)

## DNS validation

The Active Directory DNS server is `10.0.50.10`, using the internal DNS domain `paul.lan`.

Forward lookup of the AD server:

![DNS forward lookup](evidence/06-dns-forward-lookup.png)

Reverse lookup of the SOC server address (`172.20.80.10`):

![DNS reverse lookup](evidence/05-dns-reverse-lookup.png)

The SOC server uses `10.0.50.10` as its DNS resolver.

## Result

The virtual network is deployed and basic connectivity has been validated. OPNsense provides routing, firewalling and outbound NAT. DNS resolution and secured SSH administration to the SOC server are working.

## Next step

**Lab 5.2 – Suricata IDS on OPNsense:** deploy and configure network intrusion detection, then validate alert generation using controlled test traffic.
