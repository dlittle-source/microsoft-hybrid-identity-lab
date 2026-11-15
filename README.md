# Microsoft Hybrid Identity Implementation Lab

### Windows Server 2025 | Active Directory Domain Services | Microsoft Entra Connect Sync

## Project Overview

This project demonstrates the implementation of a Microsoft Hybrid Identity environment integrating on-premises Active Directory Domain Services (AD DS) with Microsoft Entra ID using Microsoft Entra Connect Sync.

The environment was built using Windows Server 2025 virtual machines and a Microsoft Entra ID cloud tenant.

The implementation includes:

- Active Directory domain infrastructure and identity management
- Microsoft Entra Connect Sync installation and configuration
- User Principal Name (UPN) suffix configuration
- Organizational Unit (OU) synchronization filtering
- Password Hash Synchronization (PHS)
- Cloud identity synchronization and authentication validation
- Microsoft Entra ID security group membership management

**Project Goal:** Demonstrate practical hybrid identity engineering skills by synchronizing an on-premises Active Directory user to Microsoft Entra ID, validating cloud authentication, and managing cloud security group membership.

## Lab Architecture

The hybrid identity environment was deployed using Oracle VirtualBox and Windows Server 2025, integrating an existing on-premises Active Directory domain with Microsoft Entra ID.

### Infrastructure Components

| Component | Configuration | Purpose |
|---|---|---|
| WIN-DC01 | Windows Server 2025 / 192.168.100.10 | Active Directory Domain Controller and DNS |
| WIN-DC02 | Windows Server 2025 / 192.168.100.11 | Additional Domain Controller and DNS |
| WIN-SYNC01 | Windows Server 2025 | Domain-joined Microsoft Entra Connect Sync server |
| Active Directory Domain | dsolutions.local | On-premises identity directory |
| Microsoft Entra ID | DemarkoCloudLab | Cloud identity directory |
| Synchronization Method | Microsoft Entra Connect Sync | Synchronizes selected AD identities to Entra ID |
| Authentication Method | Password Hash Synchronization | Enables cloud authentication using synchronized password hash data |

### Identity Synchronization Flow

1. An Active Directory user account was created and maintained within the Finance organizational unit.
2. Microsoft Entra Connect Sync was configured on WIN-SYNC01.
3. OU filtering was configured to synchronize identities from the Finance OU.
4. An alternative UPN suffix matching the Microsoft Entra ID tenant domain was configured.
5. Password Hash Synchronization was enabled.
6. John Doe's identity was successfully synchronized to Microsoft Entra ID.
7. Cloud authentication was validated using the synchronized account and its on-premises password.
8. The synchronized user was added to a cloud-managed Microsoft Entra ID security group.

### Design Considerations

- **Dedicated synchronization server:** Separates the synchronization service from domain controller workloads.
- **Scoped synchronization:** Limits synchronized identities to the intended organizational unit.
- **Password Hash Synchronization:** Enables Microsoft Entra ID to authenticate users without contacting an on-premises domain controller for each cloud sign-in.
- **Cloud-managed security groups:** Demonstrates cloud identity membership administration while retaining Active Directory as the source for the synchronized user identity.
