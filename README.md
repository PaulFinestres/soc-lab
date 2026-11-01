# SOC Lab

A personal virtual lab for learning network administration, defensive security and security monitoring.

The environment is hosted on **Proxmox VE** and uses **OPNsense** for routing and firewalling. The work is divided into small labs so that each part can be built, tested and documented separately.

## Labs

| Lab | Subject | Status |
|---|---|---|
| [5.1 – Network Architecture & Infrastructure](labs/5.1-network-architecture/README.md) | Proxmox, OPNsense, VLANs, addressing and connectivity | Completed |
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

Each lab has its own README and keeps its supporting screenshots nearby. The structure is intentionally small; add folders only when a lab needs them.

## Notes

- IP addresses shown in the documentation belong to the private lab network.
- Screenshots are included as implementation and validation evidence.
- Do not commit passwords, private keys, API tokens, or other credentials.
