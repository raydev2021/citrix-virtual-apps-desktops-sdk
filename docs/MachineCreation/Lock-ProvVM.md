﻿
# Lock-Provvm
Locks a VM.
## Syntax

```
Lock-ProvVM [-VMID] <String[]> -ProvisioningSchemeName <String> [-Tag <String>] [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]  
  
Lock-ProvVM [-VMID] <String[]> -ProvisioningSchemeUid <Guid> [-Tag <String>] [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
Provides the ability to 'lock' a virtual machine with a tag string.  This stops other commands from being able to remove the virtual machine without unlocking the VM first.  This is to enable consumers of the virtual machines to indicate that the VM is being used.


## Related Commands

* [UnLock-ProvVM](../UnLock-ProvVM/)
* [Get-ProvVM](../Get-ProvVM/)
* [Remove-ProvVM](../Remove-ProvVM/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| VMID | The virtual machine Id (hypervisor context). | true | true (ByPropertyName) |  |
| ProvisioningSchemeName | The name of the provisioning scheme. | true | true (ByPropertyName) |  |
| ProvisioningSchemeUid | The unique identifier of the provisioning scheme. | true | false |  |
| Tag | The string to be held against the VM being locked. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### Citrix.Machinecreation.Sdk.Provisionedvirtualmachine  
    You Can Pipe An Object Containing A Parameter Called 'Vmid' And 'Provisioningschemename' To Lock-Provvm

## Return Values

### 

## Notes
In the case of failure, the following errors can result.  
    Error Codes  
    -----------  
    VMDoesNotExist  
    The specified VM cannot be located.  
    VMAlreadyLocked  
    The VM is already unlocked.  
    VMDoesNotExistForProvisioningScheme  
    The specified VM does exist in the hypervisor, but is not part of the specified provisioning scheme.  
    PermissionDenied  
    The user is not authorized to perform this operation  
    ConfigurationLoggingError  
    The operation could not be performed because of a configuration logging error  
    DatabaseError  
    An error occurred in the service while attempting a database operation.  
    DatabaseNotConfigured  
    The operation could not be completed because the database for the service is not configured.  
    ServiceStatusInvalidDb  
    An error occurred in the service while attempting a database operation - communication with the database failed for  
    for various reasons.  
    CommunicationError  
    An error occurred while communicating with the service.  
    PermissionDenied  
    The user does not have administrative rights to perform this operation.  
    ExceptionThrown  
    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1

```
C:\PS>Lock-ProvVM -provisioningSchemeName MyScheme -VMId  bc79802c-ba6e-8de8-99e9-4c35d7ad24b4 -Tag LockedString
```

#### Description
Locks the VM with the Id 'bc79802c-ba6e-8de8-99e9-4c35d7ad24b4' in the provisioning scheme 'MyScheme' with the tag 'LockedString'.
### Example 2

```
C:\PS>Get-ProvVM -provisioningSchemeName MyScheme | Lock-ProvVM -Tag LockedString
```

#### Description
Locks all the VMs in the provisioning scheme 'MyScheme' with the tag 'LockedString'.
