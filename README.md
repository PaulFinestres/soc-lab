# SOC Lab – Network Security & Monitoring

A personal virtual lab focused on network administration, defensive security and security monitoring.

The environment runs on **Proxmox VE**, with **OPNsense** providing routing and firewalling. The project is divided into smaller labs that can be built, tested and documented independently.

## Network architecture

![SOC lab network architecture](labs/5.1-network-architecture/architecture.png)

## Labs

| Lab | Subject | Status |
|---|---|---|
| [5.1 – Network Architecture & Infrastructure](labs/5.1-network-architecture/README.md) | Virtual infrastructure, VLANs, routing and basic service validation | Completed |
| 5.2 – Suricata IDS on OPNsense | Network intrusion detection and alert validation | Next |

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
        └── evidence/
```

Each lab contains its own documentation and supporting evidence.
