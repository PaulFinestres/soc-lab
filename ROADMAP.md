# Roadmap

Current scope: the network foundation and centralised security monitoring.

## Lab 5.1 – Network Architecture & Infrastructure

**Status:** Completed

Build the virtual network, configure Proxmox networking and OPNsense, define VLANs and IP addressing, and validate connectivity, DNS and administrative access.

## Lab 5.2 – Suricata IDS/IPS on OPNsense

**Status:** Completed

Install and configure Suricata in IPS mode, select suitable rule sets, create custom detection rules, validate intrusion detection and traffic blocking, review alerts and configure logging.

## Lab 5.3 – Wazuh SIEM

**Status:** Completed

Deploy Wazuh to collect and analyse security events from selected lab systems, integrate Suricata events from OPNsense, and provide centralised investigation and visualisation through dashboards.

## Lab 5.4 – Attack Simulation & Detection Validation

**Status:** Planned

Use Kali Linux to generate controlled test traffic and attack scenarios, then evaluate how Suricata detects the activity and how the resulting events are forwarded to and investigated in Wazuh. The objective is to validate the detection pipeline as a whole and identify gaps in visibility or detection coverage.
