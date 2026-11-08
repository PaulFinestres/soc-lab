# SOC Lab – Network Security & Monitoring

![Proxmox VE](https://custom-icon-badges.demolab.com/badge/Proxmox_VE-E57000?logo=proxmox&logoColor=white)
![OPNsense](https://custom-icon-badges.demolab.com/badge/OPNsense-EF7B4D?logo=opnsense&logoColor=white)
![Suricata](https://custom-icon-badges.demolab.com/badge/Suricata-EF3B2D?logo=suricata&logoColor=white)
![Wazuh](https://custom-icon-badges.demolab.com/badge/Wazuh-4A90E2?logo=wazuh&logoColor=white)
![Kali Linux](https://custom-icon-badges.demolab.com/badge/Kali_Linux-557C94?logo=kalilinux&logoColor=white)

A virtual lab focused on network administration, defensive security and security monitoring.

Hosted on **Proxmox VE**, the environment uses **OPNsense** for routing, firewalling and network segmentation. The project aims to integrate **Suricata** for intrusion detection and prevention (IDS/IPS), alongside **Wazuh** for security monitoring, log collection and analysis.

**Kali Linux** is used as a supporting tool to simulate attacks and generate network traffic, allowing the defensive capabilities of the infrastructure to be tested and evaluated.

The project is organised into independent labs, each covering a specific aspect of the infrastructure and its security capabilities.

## Overall Network Architecture

![SOC lab network architecture](labs/5.1-network-architecture/architecture.png)
- *Diagram created with Excalidraw. It provides a simplified overview of the lab's network architecture.*

## Labs

| Lab | Subject | Status |
|---|---|---|
| [5.1 – Network Architecture & Infrastructure](labs/5.1-network-architecture/README.md) | Virtual infrastructure, VLANs, routing and basic service validation | Completed |
| 5.2 – Suricata IDS/IPS on OPNsense | Network intrusion detection, prevention and alert validation | Next |

See [ROADMAP.md](ROADMAP.md) for the current scope.

## Repository structure

```text
.
├── README.md
├── ROADMAP.md
├── .gitignore
└── labs/
    └── 5.1-network-architecture/
        ├── README.md
        ├── architecture.png
        ├── configs/
        │   ├── netplan/
        │   └── ssh/
        └── evidence/
```
