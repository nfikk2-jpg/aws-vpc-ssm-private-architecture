# AWS Private VPC & Zero-Trust SSM Architecture Lab

## Overview
This project demonstrates a secure, multi-tier AWS cloud network architecture built around zero-trust administrative access. The design eliminates inbound SSH (Port 22) exposure and public IP addresses by leveraging **AWS Systems Manager (SSM) Session Manager** routed through **VPC Endpoints**.

---

## Architecture Highlights
* **VPC Setup:** Configured custom VPC (`lab-vpc`) spanning multiple Availability Zones with dedicated public and private subnets.
* **Zero-Trust Compute Tier:** Deployed application instance (`Lab2-App-Server`) strictly within an isolated private subnet with no assigned public IPv4 address.
* **Keyless Management:** Configured EC2 instances without SSH key pairs, restricting administrative command-line access entirely to IAM-authenticated AWS SSM Session Manager.
* **Network Isolation:** Custom Security Groups enforcing least-privilege egress/ingress controls across application and database tiers.
* **IAM Least-Privilege:** Provisioned IAM Instance Profiles attached with `AmazonSSMManagedInstanceCore` to authorize Systems Manager agent communication over AWS private network infrastructure.

---

## Security Controls & Verification

| Control | Implementation Details | Verification |
| :--- | :--- | :--- |
| **Inbound SSH Removal** | Port 22 completely blocked in Security Groups | Zero SSH attack surface exposed to the public internet |
| **Private Shell Access** | Session Manager over SSM Endpoints / Fleet Manager | Browser-based encrypted shell authenticated via IAM |
| **Tier Isolation** | Ingress rules restricted to security group references | Application instances can only reach database resources on designated application ports |

---

## Technical Skills Demonstrated
* **AWS Cloud Networking:** VPC design, Subnetting, Security Groups, Route Tables.
* **Identity & Access Management (IAM):** Instance Profiles, Role-based policy attachment.
* **Systems & Operations Security:** AWS Systems Manager (SSM), Session Manager, Fleet Manager, Zero-Trust Access Control.
* **Version Control:** Git GUI workflows, repository management, documentation.