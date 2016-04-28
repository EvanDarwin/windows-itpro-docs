---
title: Add workstations to domain (Windows 10)
description: Describes the best practices, location, values, policy management and security considerations for the Add workstations to domain security policy setting.
ms.assetid: b0c21af4-c928-4344-b1f1-58ef162ad0b3
ms.prod: W10
ms.mktglfcycl: deploy
ms.sitesec: library
author: brianlic-msft
---

# Add workstations to domain


**Applies to**

-   Windows 10

Describes the best practices, location, values, policy management and security considerations for the **Add workstations to domain** security policy setting.

## Reference


This policy setting determines which users can add a device to a specific domain. For it to take effect, it must be assigned so that it applies to at least one domain controller. A user who is assigned this user right can add up to ten workstations to the domain.

Adding a machine account to the domain allows the device to participate in Active Directory-based networking.

Constant: SeMachineAccountPrivilege

### Possible values

-   User-defined list of accounts

-   Not Defined

### Best practices

-   Configure this setting so that only authorized members of the IT team are allowed to add devices to the domain.

### Location

Computer Configuration\\Windows Settings\\Security Settings\\User Rights Assignment\\

### Default values

By default, this setting allows access for Authenticated Users on domain controllers, and it is not defined on stand-alone servers.

The following table lists the actual and effective default policy values for the most recent supported versions of Windows. Default values are also listed on the policy’s property page.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Server type or GPO</th>
<th align="left">Default value</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Default Domain Policy</p></td>
<td align="left"><p>Not Defined</p></td>
</tr>
<tr class="even">
<td align="left"><p>Default Domain Controller Policy</p></td>
<td align="left"><p>Not Defined</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Stand-Alone Server Default Settings</p></td>
<td align="left"><p>Not Defined</p></td>
</tr>
<tr class="even">
<td align="left"><p>Domain Controller Effective Default Settings</p></td>
<td align="left"><p>Authenticated Users</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Member Server Effective Default Settings</p></td>
<td align="left"><p>Not Defined</p></td>
</tr>
<tr class="even">
<td align="left"><p>Client Computer Effective Default Settings</p></td>
<td align="left"><p>Not Defined</p></td>
</tr>
</tbody>
</table>

 

## Policy management


Users can also join a computer to a domain if they have the Create Computer Objects permission for an organizational unit (OU) or for the Computers container in the directory. Users who are assigned this permission can add an unlimited number of devices to the domain regardless of whether they have the **Add workstations to domain** user right.

Furthermore, machine accounts that are created by means of the **Add workstations to domain** user right have Domain Administrators as the owner of the machine account. Machine accounts that are created by means of permissions on the computer’s container use the creator as the owner of the machine account. If a user has permissions on the container and also has the **Add workstation to domain** user right, the device is added based on the computer container permissions rather than the user right.

A restart of the device is not required for this policy setting to be effective.

Any change to the user rights assignment for an account becomes effective the next time the owner of the account logs on.

### Group Policy

Settings are applied in the following order through a Group Policy Object (GPO), which will overwrite settings on the local computer at the next Group Policy update:

1.  Local policy settings

2.  Site policy settings

3.  Domain policy settings

4.  OU policy settings

When a local setting is greyed out, it indicates that a GPO currently controls that setting.

## Security considerations


This policy has the following security considerations:

### Vulnerability

The **Add workstations to domain** user right presents a moderate vulnerability. Users with this right could add a device to the domain that is configured in a way that violates organizational security policies. For example, if your organization does not want its users to have administrative privileges on their devices, users could install Windows on their computers and then add the computers to the domain. The user would know the password for the local administrator account, could log on with that account, and then add a personal domain account to the local Administrators group.

### Countermeasure

Configure this setting so that only authorized members of the IT team are allowed to add computers to the domain.

### Potential impact

For organizations that have never allowed users to set up their own computers and add them to the domain, this countermeasure has no impact. For those that have allowed some or all users to configure their own devices, this countermeasure forces the organization to establish a formal process for these procedures going forward. It does not affect existing computers unless they are removed from and then added to the domain.

## Related topics


[User Rights Assignment](user-rights-assignment.md)

 

 




