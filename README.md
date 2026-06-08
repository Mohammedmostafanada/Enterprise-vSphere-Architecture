# Enterprise vSphere Resilience Architecture

## 📌 Project Overview
This project focuses on the design and deployment of a robust, enterprise-grade virtual infrastructure capable of providing continuous service availability. The core objective was to engineer a "Self-Healing" system that mitigates hardware failures and eliminates single points of failure, while optimizing resource utilization through intelligent automation.

## 🏗️ Infrastructure Topology

![Infrastructure Topology](images/topology.png)

The architecture is built upon a multi-layered approach to ensure maximum scalability, manageability, and resilience:

* **Management Layer:** Centralized administration is seamlessly handled by the **vCenter Server Appliance (VCSA)**, providing a "single pane of glass" for comprehensive cluster management and monitoring.
* **Compute Layer:** The backbone of the system consists of three bare-metal **ESXi Hosts (192.168.1.53, .55, and .56)**, aggregated into a unified, high-performance computing environment named the **"Snagim Cluster"**.
* **Storage Layer:** A highly available **Shared Storage system** was implemented utilizing the **NFS protocol**. This centralized datastore is pivotal, enabling critical enterprise features such as vMotion and High Availability (HA) by allowing all hosts simultaneous access to the virtual disk files.
* **Network Layer:** A meticulously designed networking schema was deployed. It utilizes dedicated **VMkernel adapters** to isolate and manage specific traffic types, including Management, vMotion (for seamless live migrations), and FT Logging (for continuous, real-time state synchronization).

## 🚀 Key Implementation Highlights & Advanced Features

To achieve the project's high-availability and automation goals, the following advanced VMware vSphere features were successfully configured, integrated, and validated:

* **Distributed Resource Scheduler (DRS):** Implemented in **Fully Automated mode** to dynamically balance CPU and Memory workloads across the cluster, ensuring optimal hardware utilization without manual intervention.
* **vSphere High Availability (HA):** Configured to provide rapid disaster recovery. In the event of a physical server failure, affected virtual machines are automatically and swiftly restarted on surviving, healthy hosts.
* **Fault Tolerance (FT):** Applied strictly to mission-critical workloads to guarantee **Zero Downtime**. This was achieved by establishing a live, real-time "Shadow VM" on a secondary host, ensuring instantaneous failover without data loss or connection interruption.
* **Enterprise Directory Services Integration:** The entire vSphere infrastructure was securely integrated with a corporate **Windows Active Directory Domain (`iti.local`)** via LDAP. This enabled centralized Identity Management and enforced strict **Role-Based Access Control (RBAC)** for administrators.

## 🛠️ Core Tech Stack
* **Hypervisor:** VMware ESXi 6.7
* **Centralized Management:** vCenter Server Appliance (VCSA) 6.7
* **Storage Protocol:** Network File System (NFS)
* **Identity Management:** Microsoft Active Directory (LDAP/RBAC)
* **Guest OS:** Red Hat Fedora Workstation

---
*Architected and deployed by Assem Ragab, Emad Elsayed Singab, and Mohamed Mostafa Nada under the supervision of Eng. Ekram Abdelwahab, as part of the Information Technology Institute (ITI) program.*
