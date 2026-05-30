# 🛡️ Operation Fortress – Defense in Depth Security Architecture

## Project Overview

**Operation Fortress** is a cybersecurity defense-in-depth lab focused on implementing multiple independent security controls designed to detect and block adversary activity across network, perimeter, and endpoint layers.

The scenario simulates an active threat actor leveraging:

* Command and Control (C2) infrastructure hosted on **198.51.100.0/24**
* Web shell exploitation using **cmd=whoami**
* Post-exploitation payload delivery through **curl http://198.51.100.5**

This project demonstrates layered defensive security engineering using firewall controls, intrusion detection systems, and endpoint monitoring.

---

## Mission Objectives

Implement and document three independent defensive layers:

### Layer 1 — Perimeter Firewall (iptables)

Block outbound communication to adversary infrastructure.

**Security Control:**

* Egress filtering
* Network segmentation
* C2 disruption

**Rule Implemented:**

```bash
iptables -A OUTPUT -d 198.51.100.0/24 -j DROP
```

---

### Layer 2 — Network IDS (Suricata)

Detect web shell activity targeting HTTP services.

**Security Control:**

* Signature-based intrusion detection
* Web exploit monitoring
* Network visibility

**Signature Implemented:**

```bash
alert tcp any any -> any 80 (msg:"Web Shell cmd=whoami Attempt Detected"; content:"cmd=whoami"; sid:1000001; rev:1;)
```

---

### Layer 3 — Endpoint Detection (Sysmon for Linux)

Detect post-exploitation payload execution on the endpoint.

**Security Control:**

* Process monitoring
* Command-line inspection
* Endpoint telemetry

**Sysmon Rule Implemented:**

```xml
<CommandLine condition="contains">curl http://198.51.100.5</CommandLine>
```

---

## Technical Stack

| Component           | Technology           |
| ------------------- | -------------------- |
| Operating System    | Ubuntu Linux         |
| Firewall            | iptables             |
| IDS                 | Suricata             |
| Endpoint Monitoring | Sysmon for Linux     |
| Version Control     | Git / GitHub         |
| Environment         | VirtualBox + VS Code |

---

## Project Files

```text
Operation_Fortress_Report.md
firewall_task.sh
suricata_task.rules
sysmon_task.xml
README.md
```

---

## Skills Demonstrated

* Defense in Depth Architecture
* Network Security Engineering
* Intrusion Detection Development
* Endpoint Detection and Monitoring
* Linux Security Administration
* Threat Detection Engineering
* Security Documentation
* Git & GitHub Workflow

---

## Portfolio Value

This project demonstrates the practical implementation of layered cybersecurity defenses where multiple independent controls operate together to reduce attacker success and improve detection visibility.

Defense in Depth ensures that when one control fails, another continues protecting the environment.
