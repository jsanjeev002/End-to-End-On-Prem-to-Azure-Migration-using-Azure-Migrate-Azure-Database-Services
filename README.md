# Azure On-Premises to Cloud Migration Lab (Enterprise Simulation)

## Overview

This project simulates a real-world **enterprise on-premises data center migration to Microsoft Azure** using nested virtualization.  
The goal is to demonstrate **cloud migration planning, assessment, execution, and validation**, not just VM creation.

The lab covers:
- On-prem infrastructure simulation
- Azure Migrate assessment & dependency analysis
- Lift-and-shift (IaaS) migration
- Database re-platforming to PaaS
- Azure networking configuration
- Post-migration validation

This project reflects tasks performed by **Cloud Support Engineers / Cloud Engineers** in real migration engagements.

---

## Problem Statement

Most enterprises cannot directly move workloads to the cloud without:
- Understanding application dependencies
- Assessing compatibility and cost
- Choosing the right migration strategy (IaaS vs PaaS)

This lab solves that by simulating a full migration lifecycle.

---

## Architecture Summary

### On-Premises (Simulated)
- Azure VM used as Hyper-V host (nested virtualization)
- 4 on-prem virtual machines:
  - Windows Server 2012 (Legacy Application Server)
  - Windows Server 2016 (Application Server)
  - Linux Server (Web/API workload)
  - Dedicated Database Server

### Azure (Target)
- Azure Virtual Network with segmented subnets
- Network Security Groups for traffic control
- Azure Virtual Machines for migrated workloads
- Azure Database service (PaaS) for database re-platforming

---

## Tech Stack

- Microsoft Azure
- Azure Virtual Machines
- Azure Migrate
- Hyper-V (Nested Virtualization)
- Windows Server 2012 & 2016
- Linux
- Azure Database (PaaS)
- Azure Data Studio
- Azure Virtual Network (VNet)
- Network Security Groups (NSG)
- PowerShell

---

## Environment Setup

### Step 1: Azure Host VM Creation

A high-capacity Azure VM was provisioned to support nested virtualization.

Recommended size:


Nested virtualization enabled to allow Hyper-V inside Azure.

---

### Step 2: Hyper-V Installation

Hyper-V role installed on the Azure VM to simulate an on-premises data center.

Result:
- Azure VM acts as physical on-prem host
- Internal virtual switch used for VM communication

---

### Step 3: On-Prem VM Provisioning

| VM Name | OS | Purpose |
|------|----|--------|
| WS2012 | Windows Server 2012 | Legacy app server |
| WS2016 | Windows Server 2016 | Application server |
| LinuxVM | Linux | Web/API server |
| DBServer | Windows/Linux | Database server |

Each VM was configured with:
- Static IP
- Application/database workload
- Inter-VM communication

---

## Assessment Phase (Azure Migrate)

Azure Migrate was used to evaluate cloud readiness.

### Activities Performed
- Installed Azure Migrate appliance
- Discovered on-prem VMs
- Collected performance metrics
- Performed dependency analysis
- Generated readiness and sizing reports

### Outcomes
- Identified VM dependencies
- Determined migration suitability
- Estimated Azure cost
- Selected migration strategy:
  - IaaS for application servers
  - PaaS for database

---

## Migration Strategy

### Lift-and-Shift (IaaS)

Migrated to Azure Virtual Machines:
- Windows Server 2012
- Windows Server 2016
- Linux Server

Reason:
- Preserve OS and application configuration
- Minimal refactoring
- Faster migration

Migration steps:
1. Enable replication
2. Test migration
3. Perform final cutover
4. Validate workloads

---

### Re-Platforming (PaaS)

Database server migrated to **Azure Database service**.

Reason:
- Reduce infrastructure management
- Built-in backups and high availability
- Improved scalability
- Lower operational overhead

---

## Database Migration

### Tool Used
Azure Data Studio

### Migration Steps
1. Schema export from on-prem DB
2. Data migration to Azure Database
3. Integrity validation
4. Application connectivity testing

### Validation
- Record count verification
- Application read/write testing
- Query performance check

---

## Azure Networking Configuration

### Components
- Virtual Network (VNet)
- Subnets:
  - Application Subnet
  - Database Subnet
- Network Security Groups (NSG)

### Security Controls
- RDP/SSH restricted to admin IP
- Application ports allowed
- Database access restricted to app subnet only

Networking was validated before and after migration to ensure zero connectivity issues.

---

## Post-Migration Validation

### Validation Checklist
- Application availability
- Database connectivity
- Service startup verification
- CPU and memory utilization
- Network traffic flow
- Log verification

Result:
All migrated workloads functioned as expected in Azure.

---

## Results & Benefits

| Area | Before Migration | After Migration |
|----|----|----|
| Infrastructure Management | Manual | Reduced |
| Database Maintenance | High | Minimal |
| Scalability | Limited | Elastic |
| Availability | Single Host | Azure Managed |
| Recovery | Manual | Built-in Azure |

---

## Challenges & Solutions

| Challenge | Resolution |
|--------|-----------|
| Nested virtualization performance | Increased VM size |
| Replication lag | Bandwidth tuning |
| Database connectivity issues | NSG and firewall fixes |
| Dependency conflicts | Azure Migrate dependency mapping |

---

## Cost Considerations

- Azure Migrate used for right-sizing
- PaaS database reduced operational cost
- IaaS retained only where required

Estimated cost varies based on region and VM sizing.

---

## Key Learnings

- Azure Migrate dependency analysis is critical
- Lift-and-shift is fast but not always optimal
- Re-platforming significantly reduces ops effort
- Networking misconfiguration is the most common failure point
- Test migration before final cutover is mandatory

---

## Skills Demonstrated

- Enterprise cloud migration planning
- Azure Migrate assessment
- Lift-and-shift migration (IaaS)
- Database re-platforming (PaaS)
- Azure networking design
- Hyper-V & nested virtualization
- PowerShell-based automation
- Troubleshooting production-like issues

---

## How to Reproduce This Lab

1. Create Azure host VM
2. Enable nested virtualization
3. Install Hyper-V
4. Create on-prem VMs
5. Deploy Azure Migrate appliance
6. Run assessment & dependency analysis
7. Perform test migration
8. Execute final migration
9. Re-platform database
10. Validate applications and networking

---

This is **not a tutorial project**.  
This is a **migration simulation that mirrors real enterprise cloud workloads**.

---
