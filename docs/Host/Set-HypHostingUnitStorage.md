﻿
# Set-Hyphostingunitstorage
Sets options for a storage location on a hosting unit.
## Syntax

```
Set-HypHostingUnitStorage [-LiteralPath] <String> [-StoragePath] <String> [-StorageType <StorageType>] [-Superseded <Boolean>] [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
Use this command to set options for storage locations that are defined for a hosting unit. Do not use this command if the connection for the hosting unit is in maintenance mode.


## Related Commands

* [New-Item](../New-Item/)
* [Add-HypMetadata](../Add-HypMetadata/)
* [Remove-HypHostingUnitStorage](../Remove-HypHostingUnitStorage/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| LiteralPath | Specifies the path to the hosting unit which defines the storage. The path must be in one of the following formats: &lt;drive&gt;:\\HostingUnits\\&lt;HostingUnitName&gt; or  &lt;drive&gt;:\\HostingUnits\\{&lt;HostingUnit Uid&gt;} | true | false |  |
| StoragePath | Specifies the path to the storage that will be modified. The path must be in one of the following formats: &lt;drive&gt;:\\Connections\\&lt;ConnectionName&gt;\\MyStorage.storage or  &lt;drive&gt;:\\Connections\\{&lt;Connection Uid&gt;}\\MyStorage.storage or  &lt;drive&gt;:\\HostingUnits\\&lt;HostingUnitName&gt;\\MyStorage.storage or  &lt;drive&gt;:\\HostingUnits\\{&lt;hostingUnit Uid&gt;}\\MyStorage.storage | true | true (ByValue) |  |
| StorageType | Specifies the type of storage in StoragePath. Supported storage types are: OSStorage PersonalvDiskStorage TemporaryStorage | false | false | OSStorage |
| Superseded | Specifies that this storage has been superseded and must not be used for future provisioning operations. Existing virtual machines using this storage will continue to function. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects. This can be a host name or an IP address. | false | false | LocalHost. When a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### System.String  
    You Can Pipe A String That Contains A Path To Add-Hyphostingunitstorage (Storagepath Parameter).

## Return Values

### Citrix.Xdpowershell.Hostingunit
Set-HypHostingUnitStorage returns an object containing the new definition of the hosting unit.  
    HostingUnitUid &lt;Guid&gt;  
        Specifies the unique identifier for the hosting unit.  
    HostingUnitName &lt;string&gt;  
        Specifies the name of the hosting unit.  
    HypervisorConnection &lt;Citrix.XDPowerShell.HypervisorConnection&gt;  
        Specifies the connection that the hosting unit uses to access a hypervisor.  
    RootId &lt;string&gt;  
        Identifies, to the hypervisor, the root of the hosting unit.  
    RootPath &lt;string&gt;  
        The hosting unit provider path that represents the root of the hosting unit.  
    Storage &lt;Citrix.XDPowerShell.Storage\[\]&gt;  
        The list of storage items that the hosting unit can use.  
    PersonalvDiskStorage &lt;Citrix.XDPowerShell.Storage\[\]&gt;  
        The list of storage items that the hosting unit can use for storing personal data.  
    VMTaggingEnabled &lt;Boolean&gt;  
        Specifies whether or not the metadata in the hypervisor can be used to store information about the XenDesktop Machine Creation Service.  
    NetworkId &lt;string&gt;  
        The hypervisor's internal identifier that represents the network specified for the hosting unit.  
    NetworkPath &lt;string&gt;  
        The hosting unit provider path to the network specified for the hosting unit.  
    AdditionalStorage  
        The list of additional storage items that the hosting unit can use.  
    Metadata &lt;Citrix.XDPowerShell.Metadata\[\]&gt;  
        A list of key value pairs that can store additional information about the hosting unit.
## Notes
The storage path must be valid for the hosting unit. The rules that are applied are as follows: XenServer (HypervisorConnection Type = XenServer)  
    NA  
    VMWare vSphere/ESX (HypervisorConnection Type = vCenter)  
    The storage path must be directly contained in the root path item of the hosting unit.  
    Microsoft SCVMM/Hyper-v (HypervisorConnection Type = SCVMM)  
    Only one storage entry for these connection types is valid, and it must reference an SMB share. Additionally, if a Hyper-V failover cluster is used the SMB share must be the top-level mount point of the cluster shared volume on one of the servers in the cluster (i.e. C:\\ClusterStorage).  
    In the case of failure, the following errors can be produced.  
    Error Codes  
    -----------  
    HostingUnitsPathInvalid  
    The path provided is not to an item in a subdirectory of a hosting unit item.  
    HostingUnitStoragePathInvalid  
    The specified path is invalid.  
    HostingUnitStoragePathInvalid  
    The storage path cannot be found or is invalid. See notes above about validity.  
    HostingUnitStorageDuplicateObjectExists  
    The specified storage path is already part of the hosting unit.  
    HypervisorInMaintenanceMode  
    The hypervisor for the connection is in maintenance mode.  
    DatabaseError  
    An error occurred in the service while attempting a database operation.  
    DatabaseNotConfigured  
    The operation could not be completed because the database for the service is not configured.  
    DataStoreException  
    An error occurred in the service while attempting a database operation. Communication with the database failed for  
    for various reasons.  
    CommunicationError  
    An error occurred while communicating with the service.  
    PermissionDenied  
    The user does not have administrative rights to perform this operation.  
    ExceptionThrown  
    An unexpected error occurred. To locate more details, see the Windows event logs on the controller being used, or examine the XenDesktop logs.
## Examples

### Example 1

```
c:\PS>Set-HypHostingUnitStorage -LiteralPath XDHyp:\HostingUnits\MyHostingUnit -StoragePath 'XDHyp:\HostingUnits\MyHostingUnits\newStorage.storage' -Superseded $true  
  
          HostingUnitUid       : bcd3d649-86d1-4aa8-8ec2-d322b6a2c457  
  
          HostingUnitName      : MyHostingUnit  
  
          HypervisorConnection : MyConnection  
  
          RootPath             : /  
  
          RootId               :  
  
          NetworkPath          : /Network 0.network  
  
          NetworkId            : ab47080b-ca15-771a-c8dc-6ad9650158f1  
  
          Storage              : {/Local storage.storage, /newStorage.storage}  
  
          PersonalvDiskStorage : {/newStorage.storage}  
  
          VMTaggingEnabled     : True  
  
          AdditionalStorage    : {TemporaryStorage}  
  
          Metadata             : {}
```

#### Description
The command updates a storage location called "newStorage.storage" associated with the hosting unit called "MyHostingUnit".
