## 📆 Days 1–5: Lab Setup, ELK Stack, and Network Hardening

## 🛠️ SOC Environment Overview

The first phase focused on designing and deploying the foundational infrastructure for the SOC lab. Using Vultr’s cloud environment, I spun up multiple virtual machines and created a secure Virtual Private Cloud (VPC) to isolate and segment the lab components.

I also built a high-level network diagram using draw.io to visualize the environment:

![SOC Environment Diagram](../images/soc_environment_diagram.png) <!-- [screenshot] -->

### 🔧 Core Components

- **SOC Analyst Workstation**: Access point for interacting with the environment
- **Elastic Stack (Elasticsearch + Kibana)**: For log collection, storage, and visualization
- **Windows Server 2022 (RDP Enabled)**: Simulated attack target
- **Ubuntu Server (SSH Enabled)**: Hosts Elastic and provides telemetry
- **Fleet Server**: Manages Elastic Agents on endpoints
- **OS Ticket Server**: Handles alerting and ticket-based workflows
- **Mythic C2 Server**: Reserved for red team emulation in later phases
- **VPC**: Secure private network for traffic segmentation

---

## 🔍 ELK Stack Setup

I deployed Elasticsearch and Kibana on the Ubuntu server. This setup is the foundation for log management and data visualization:

- **Elasticsearch** was installed to serve as the backend for storing and indexing security logs.
- **Kibana** was configured to interface with Elasticsearch, providing dashboarding and visualization capabilities.

I explored Kibana's core features:
- **Discover Tab** for raw log inspection
- **Visualizations** for bar charts, line graphs, and pie charts
- **Dashboards** for centralized threat monitoring

> 💡 *Tip:* While downloading Elasticsearch, make sure to choose `deb x86_64` (for Ubuntu). I initially downloaded `linux x86_64`, which caused compatibility issues.

---

## 🖥️ Windows Server + Isolation Strategy

On Day 5, I set up a **Windows Server 2022 VM** with RDP exposed to the internet. This simulates a vulnerable asset often targeted by attackers in real-world environments.

To harden the architecture, I made an important change:

### 🔐 Updated Network Segmentation

I isolated the Windows and Ubuntu servers **from the main VPC** to reduce lateral movement risk. This limits potential attacker access to the critical components (Elastic, Fleet, OS Ticket) in case the exposed server is compromised.

![Updated SOC Architecture](../images/soc_environment_diagram_updated.png) <!-- [screenshot] -->

Benefits of the updated architecture:
- Limits blast radius of a compromised host
- Mimics real-world segmentation strategies
- Simulates DMZ vs internal network separation

---

## 🧪 RDP Access Troubleshooting

RDP did not work immediately after setup. I verified credentials and firewall rules — everything seemed correct. Eventually, after waiting ~10 minutes, I was able to connect.  
> 🧠 If this happens, don’t troubleshoot too early. The VM may need a few minutes for the RDP service to become fully accessible.

---

## ✅ Summary

By the end of Day 5:

- The lab environment is fully deployed in the cloud
- ELK Stack is operational for logging and visualization
- Windows and Ubuntu servers are in place for monitoring and testing
- VPC segmentation is implemented to mimic secure architecture

Next: We’ll begin deploying agents and collecting real log data across endpoints.

