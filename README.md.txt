# AWS VPC Peering Project

## Project Overview

This project demonstrates the implementation of **AWS VPC Peering** to enable secure communication between two Virtual Private Clouds (VPCs) using private IP addresses. The project includes VPC creation, subnet configuration, Internet Gateway, route tables, security groups, EC2 instances, VPC peering, and connectivity testing.

---

## Architecture

```
                    Internet
                        |
                 Internet Gateway
                        |
                  ewb-bastion
                 (10.10.1.10)
                        |
          +-------------+-------------+
          |                           |
      VPC-A                       VPC-B
    10.10.0.0/16               10.20.0.0/16
          |                           |
     ewb-app-a                   ewb-app-b
     10.10.2.10                 10.20.1.10

        ======= VPC Peering =======
```

---

## AWS Services Used

- Amazon VPC
- VPC Peering
- Amazon EC2
- Security Groups
- Route Tables
- Internet Gateway
- Amazon Linux 2023
- SSH

---

## Network Configuration

### VPC-A
- CIDR: `10.10.0.0/16`

Subnets:
- Public: `10.10.1.0/24`
- Private: `10.10.2.0/24`

---

### VPC-B
- CIDR: `10.20.0.0/16`

Subnet:
- Private: `10.20.1.0/24`

---

## EC2 Instances

| Instance | Private IP | Purpose |
|----------|------------|---------|
| ewb-bastion | 10.10.1.10 | Bastion Host |
| ewb-app-a | 10.10.2.10 | Application Server A |
| ewb-app-b | 10.20.1.10 | Application Server B |

---

## Security Groups

### Bastion
- SSH from My Public IP

### App-A
- SSH from Bastion
- ICMP from App-B

### App-B
- SSH from Bastion
- ICMP from App-A

---

## VPC Peering

Peering Connection established between:

- VPC-A
- VPC-B

Status:

**Active**

---

## Route Tables

Configured routes for:

- Internet access through Internet Gateway
- VPC Peering communication
- Forward route
- Return route

---

## Connectivity Tests

### Before Peering

- Ping failed

### After Peering

- App-A → App-B Ping ✅
- App-B → App-A Ping ✅
- Bastion → App-B SSH ✅

### ICMP Testing

- ICMP Blocked ❌
- ICMP Restored ✅

---

## Screenshots

The `screenshots` folder contains:

- VPC Creation
- Subnets
- Route Tables
- Security Groups
- EC2 Instances
- VPC Peering
- Route Updates
- Ping Tests
- SSH Proof
- ICMP Failure
- ICMP Recovery

---

## Learning Outcomes

Through this project I learned:

- Creating multiple VPCs
- Configuring public and private subnets
- Working with Internet Gateway
- Creating VPC Peering
- Configuring Route Tables
- Managing Security Groups
- Private communication using EC2
- Troubleshooting routing and security issues

---

## Cleanup

After completing the project:

- EC2 Instances terminated
- VPC Peering deleted
- Route Tables removed
- Security Groups removed
- Internet Gateway detached
- VPCs deleted

---

## Author

Dinesh Sai

AWS Networking Project – VPC Peering