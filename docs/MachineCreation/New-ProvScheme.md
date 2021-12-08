﻿
# New-Provscheme
Creates a new provisioning scheme.
## Syntax

```
New-ProvScheme [-ProvisioningSchemeName] <String> -HostingUnitName <String> -IdentityPoolName <String> -MasterImageVM <String> [-VMCpuCount <Int32>] [-VMMemoryMB <Int32>] [-CleanOnBoot] [-UsePersonalVDiskStorage] [-UseWriteBackCache] [-Scope <String[]>] [-NoImagePreparation] [-NetworkMapping <Hashtable>] [-Metadata <Hashtable>] [-ServiceOffering <String>] [-SecurityGroup <String[]>] [-DedicatedTenancy] [-TenancyType <String>] [-AzureAdJoinType <String>] [-VhdTemplateSource <String>] [-VhdResultDestination <String>] [-AppScanResultsFile <String>] [-MachineProfile <String>] [-CustomProperties <String>] [-ResetAdministratorPasswords] [-FunctionalLevel <String>] [-UseFullDiskCloneProvisioning] [-MasterImageNote <String>] [-RunAsynchronously] [-PurgeJobOnSuccess] [-InitialBatchSizeHint <Int32>] [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]  
  
New-ProvScheme [-ProvisioningSchemeName] <String> -HostingUnitUid <Guid> -IdentityPoolUid <Guid> -MasterImageVM <String> [-VMCpuCount <Int32>] [-VMMemoryMB <Int32>] [-CleanOnBoot] [-UsePersonalVDiskStorage] [-UseWriteBackCache] [-Scope <String[]>] [-NoImagePreparation] [-NetworkMapping <Hashtable>] [-Metadata <Hashtable>] [-ServiceOffering <String>] [-SecurityGroup <String[]>] [-DedicatedTenancy] [-TenancyType <String>] [-AzureAdJoinType <String>] [-VhdTemplateSource <String>] [-VhdResultDestination <String>] [-AppScanResultsFile <String>] [-MachineProfile <String>] [-CustomProperties <String>] [-ResetAdministratorPasswords] [-FunctionalLevel <String>] [-UseFullDiskCloneProvisioning] [-MasterImageNote <String>] [-RunAsynchronously] [-PurgeJobOnSuccess] [-InitialBatchSizeHint <Int32>] [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
Lets you create a new provisioning scheme. The creation process makes a copy of the hard disk attached to a virtual machine snapshot or VM template and stores it in every storage location that the hosting unit referenced by the provisioning scheme defines. This is a long-running task and typically takes several minutes to complete (depending on the size of the hard disk that is being copied and the number of snapshots that the hard disk consists of).

A snapshot or VM template must be used rather than a VM, so that the content of the hard disk for the provisioning scheme can be easily determined.

Because the snapshot or VM template are specified using a path into the Citrix Host Service PowerShell Provider, the Citrix Host Service PowerShell snap-in must also be loaded for this cmdlet to be used.

This cmdlet requires information to be provided that is retrieved using other snap-ins that form part of the Citrix Machine Creation Services: Hosting Unit Service Snapin The snap-in that provides information about the hypervisors. AD Identity Service Snapin The snap-in that provides information about the identity pools.

The provisioning scheme is a collection of all of the data that is required to form a template against which virtual machines can be created.  It therefore requires the following: Hosting Unit A reference to an item defined in the Host Service that defines the hypervisor, the network, and the storage to be used. Identity Pool A reference to the collection of Active Directory accounts that is used for virtual machines created from the provisioning scheme.


## Related Commands

* [Get-ProvTask](../Get-ProvTask/)
* [Get-ProvScheme](../Get-ProvScheme/)
* [Test-ProvSchemeNameAvailable](../Test-ProvSchemeNameAvailable/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ProvisioningSchemeName | The name of the provisioning scheme to be created.  This must be a name that is not being used by an existing provisioning scheme, and it must not contain any of the following characters \\/;:#.\*?=&lt;&gt;|\[\]()""' | true | false |  |
| HostingUnitName | The name of the hosting unit used for the provisioning scheme. | true | false |  |
| IdentityPoolName | The name for the identity pool used for the provisioning scheme. | true | false |  |
| MasterImageVM | The path in the hosting unit provider to the virtual machine, snapshot or VM template that is used as the master image and the default values for the memory and processors. This must be a path to a VM, Snapshot or Template item in the same hosting unit that the hosting unit name or hosting unit UID refers to.  
Valid paths are of the format: XDHyp:\\HostingUnits\\&lt;HostingUnitName&gt;\\&lt;path&gt;\\&lt;VMName&gt;.vm\\&lt;SnapshotName&gt;.snapshot XDHyp:\\HostingUnits\\&lt;HostingUnitName&gt;\\&lt;path&gt;\\&lt;TemplateName&gt;.template | true | true (ByPropertyName) |  |
| HostingUnitUid | The identifier for the hosting unit used for the provisioning scheme. | true | false |  |
| IdentityPoolUid | The identifier of the identity pool used for the provisioning scheme. | true | false |  |
| VMCpuCount | The number of processors used by virtual machines created from the provisioning scheme. | false | false | The number of CPUs assigned to the base image VM snapshot or VM template. |
| VMMemoryMB | The maximum amount of memory used by virtual machines created from the provisioning scheme. | false | false | The amount of memory assigned to the base image VM snapshot or VM template. |
| CleanOnBoot | Indicates whether or not the virtual machines created from this provisioning scheme are reset to their initial condition each time they are started. | false | false | false |
| UsePersonalVDiskStorage | Indicates whether or not personal vDisks are used for the VMs in this provisioning scheme. | false | false |  |
| UseWriteBackCache | Indicates whether or not write back cache is enabled for the VMs in this provisioning scheme. Use additional parameters to configure the write back cache. WriteBackCacheDiskSize: The size in GB of any temporary storage disk used by the write back cache. Should be used in conjunction with WriteBackCacheMemorySize. WriteBackCacheMemorySize: The size in MB of any write back cache if required. Should be used in conjunction with WriteBackCacheDiskSize. Setting RAM Cache to 0 but specifying Disk Cache effectively disables the RAM Cache. However, there will be some memory still used to allow the I/O Optimization to operate. | false | false |  |
| Scope | The administration scopes to be applied to the new provisioning scheme. | false | false |  |
| NoImagePreparation | Indicates that image preparation should not be performed on this provisioning scheme. | false | false |  |
| NetworkMapping | Specifies how the attached NICs are mapped to networks. If this parameter is omitted, provisioned VMs are created with a single NIC, which is mapped to the default network in the HostingUnit. If this parameter is supplied, machines are created with the number of NICs specified in the map, and each NIC is attached to the specified network. | false | false |  |
| Metadata | Specifies any metadata to be attached to the scheme when it is created. | false | false |  |
| ServiceOffering | The Service Offering to use when creating machines in Cloud Hypervisors. | false | false |  |
| SecurityGroup | The security groups to apply to machines created in Cloud Hypervisors. | false | false |  |
| DedicatedTenancy | Indicates whether to use dedicated tenancy when creating machines in Cloud Hypervisors. | false | false | false |
| TenancyType | Indicates whether to use tenancy type Shared, Instance or Host when creating machines in Cloud Hypervisors. | false | false | Shared |
| AzureAdJoinType | Specifies the Azure Active Directory join type. | false | false | None |
| VhdTemplateSource | A file path to a source VHD template to be used when performing application scanning during image preparation. The presence of this parameter in conjunction with VhdResultDestination implies that application scanning is to be performed. | false | false |  |
| VhdResultDestination | A file path (including file name) where the VHD disk file containing the results of application scanning should be written. | false | false |  |
| AppScanResultsFile | File name to which the results of application scanning should be written. | false | false |  |
| MachineProfile | The inventory path to the source that is used as a template. This profile identifies the values for the VMs created by the catalog. This must be a path to an item in the same hosting unit that the hosting unit name or hosting unit UID refers to.  
Valid paths are of the format: XDHyp:\\HostingUnits\\&lt;HostingUnitName&gt;\\&lt;path&gt;\\&lt;VMName&gt;.vm | false | false |  |
| CustomProperties | The properties of the provisioning scheme that are specific to the target hosting infrastructure. See about\_Prov\_CustomProperties for more information. | false | false |  |
| ResetAdministratorPasswords | Indicates whether to reset the password for the administrator accounts on provisioned machines. | false | false |  |
| FunctionalLevel | The FunctionalLevel of the VDA installed on the given MasterImageVM. | false | false |  |
| UseFullDiskCloneProvisioning | Indicates that the virtual machines created from the provisioning scheme should be created using the dedicated full disk clone feature. | false | false |  |
| MasterImageNote | A note for the master image. | false | false |  |
| RunAsynchronously | Indicates whether or not the command returns before it is complete. If specified, the command returns an identifier for the task that was created. This task can be monitored using the get-ProvTask command. | false | false | false |
| PurgeJobOnSuccess | Indicates that the task history is removed from the database when the task has finished. This can only be specified for tasks that are not run asynchronously. | false | false |  |
| InitialBatchSizeHint | Provides a predictive hint for the number of initial VMs that will be added to the MCS catalog when the scheme is succesfully created. Callers should supply this parameter in situations where the completion of New-ProvScheme will be closely followed by a New-ProvVM call to create an initial batch of VMs in the catalog. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### System.Guid
When the RunAsynchronously identifier is specified, this GUID is returned and provides the task identifier.  
System.Management.Automation.PSCustomObject  
    This object provides details of the task that was run and contains the following information:  
        TaskId &lt;Guid&gt;  
            The identifier for the task that was performed.  
        Active &lt;Boolean&gt;  
            Indicates whether the task is still processing or is complete.  
        Host &lt;string&gt;  
            The name of the host on which the task is running or was run.  
        DateStarted &lt;DateTime&gt;  
            The date and time that the task was initiated.  
        Type &lt;Citrix.XDInterServiceTypes.JobType&gt;  
            The type of task. For new provisioning scheme tasks, this is always NewProvisioningScheme.  
        Metadata &lt;Citrix.MachineCreation.Sdk.Metadata\[\]&gt;  
            The list of metadata stored against the task. For new tasks, this is empty until metadata is added.  
        WorkflowStatus &lt;System.Workflow.Runtime.WorkflowStatus&gt;  
            Indicates the status of the workflow that is used to process the task.  
        ProvisioningSchemeName &lt;string&gt;  
            The name of the provisioning scheme that the task was for.  
        ProvisioningSchemeUid &lt;Guid&gt;  
            The unique identifier of the provisioning scheme that the task was for.  
        MasterImage &lt;string&gt;  
            The path (in the hosting unit provider) of the virtual machine snapshot or VM template that was used as the master VM image for the task.  
        IdentityPoolName &lt;string&gt;  
            The name of the identity pool (from the ADIdentity PowerShell snap-in) that the new provisioning scheme uses.  
        IdentityPoolUid &lt;guid&gt;  
            The unique identifier name of the identity pool (from the ADIdentity PowerShell snap-in) that the new provisioning scheme uses.  
        HostingUnitName &lt;string&gt;  
            The name of the hosting unit (from the Hosting Unit PowerShell snap-in) that the new provisioning scheme uses.  
        HostingUnitUid  
            The unique identifier of the hosting unit (from the Hosting Unit PowerShell snap-in) that the new provisioning scheme uses.  
        PersonalVDiskDriveLetter  
            The drive letter on which a personal vDisk is mounted (blank if the personal vDisk feature was not selected).  
        PersonalVDiskDriveSize  
            The size of any personal vDisk (zero if the personal vDisk feature was not selected).  
        WriteBackCacheDiskSize  
            The size of any write back cache disk (zero if the write back cache feature was not selected).  
        WriteBackCacheMemorySize  
            The size of the write back cache (zero if the write back cache feature was not selected).  
        Scopes &lt;Citrix.Fma.Sdk.ServiceCoreScopeReference\[\]&gt;  
            The delegated administration scopes to which the scheme will belong.  
        NetworkMap &lt;Citrix.MachineCreation.Sdk.NetworkMap&gt;  
            The list of NIC to network associations, if specified.  
        UseFullDiskCloneProvisioning &lt;Boolean&gt;  
            Indicates whether the machines are provisioned using the dedicated full disk clone feature.  
        ProvisioningSchemeMetadata &lt;Dictionary&lt;string, string&gt;&gt;  
            The metadata to apply to the provisioning scheme, if specified.  
        TaskState &lt;Citrix.MachineCreation.Sdk.NewProvisioningSchemeState&gt;  
            The state of the task. This can be any of the following:  
                Processing  
                    The task has begun but has not done anything yet.  
                LocatingResources,  
                    The workflow is locating resources from other services.  
                HostingUnitNotFound  
                    The task failed because the required hosting unit could not be located.  
                VirtualMachineSnapshotNotFound  
                    The task failed because the required VM snapshot or VM template could not be located.  
                ConsolidatingMasterImage  
                    The task is consolidating the master image.  
                ReplicatingConsolidatedImageToAllStorage  
                    The task is replicating the consolidated master image.  
                StoringProvisioningScheme  
                    The task is storing the provisioning scheme data in the database.  
                Finished  
                    The task completed with no errors.  
                ProvisioningSchemeAlreadyExists  
                    The task failed because a provisioning scheme with the same name already exists.  
                IdentityPoolNotFound  
                    The task failed because the specified identity pool could not be found.  
                MasterVMImageIsNotPartOfProvisioningSchemeHostingUnit,  
                    The task failed because the hosting unit from which the master image originated is not the same hosting unit that the provisioning scheme is using.  
                MasterVmImageIsNotASnapshot  
                    The task failed because the master VM path does not refer to a snapshot or VM template item.  
                ProvisioningSchemeNotFound  
                    The task failed because it could not find a provisioning scheme with the specified name.  
                TaskAlreadyRunningForProvisioningScheme  
                    The task failed because a task for a provisioning scheme with the same name is already running.  
                InvalidMasterVMConfiguration  
                    The task failed because the VM snapshot or VM template specified as the master has an invalid configuration.  
                InvalidMasterVMState  
                    The task failed because the VM snapshot or VM template specified as the master is currently in an invalid state.  
                InsufficientResources  
                    The task failed because the hypervisor did not have enough resources to complete the task.  
                DiskConsolidationFailed  
                    The disk consolidation task failed. Details are in the task state information string.  
                StorageNotFound  
                    The task failed because no associated storage was found in the hosting unit.  
                ConfigurationError  
                    The task failed because the service is unable to contact one of the other services. This is because not all appropriate Configuration Service registrations have been performed.  
                RequestedFeatureNotEnabled  
                    The task failed because a requested feature is not enabled.  
                MachineProfileNotSupported  
                    The task failed because machine profile is not supported.  
                Canceled  
                    The task was stopped by user intervention (using Stop-ProvTask).  
        TaskStateInformation  
            Additional information about the current task state.  
        TaskProgress  
            The progress of the task 0-100%.  
        DiskSize  
            The size of the master image in GB  
        DedicatedTenancy  
            Whether to use dedicated tenancy when creating machines in Cloud Hypervisors.  
        TenancyType  
            Type of tenancy Shared, Instance or Host when creating machines in Cloud Hypervisors.  
        AzureAdJoinType  
            Specifies the Azure Active Directory join type.  
        MachineProfile  
            The inventory path to the source that the scheme uses as a template.  
        MasterImageNote  
            The note of the master image.
## Notes
Only one long-running task for each provisioning scheme can be processed at a time.  
    In case of failure, the following errors can result.  
    Error Codes  
    -----------  
    JobCreationFailed  
    The requested task could not be started.  
    DatabaseError  
    An error occurred in the service while attempting a database operation.  
    DatabaseNotConfigured  
    The operation could not be completed because the database for the service is not configured.  
    ServiceStatusInvalidDb  
    An error occurred in the service while attempting a database operation. Communication with the database failed for  
    for various reasons.  
    MachineCreationServiceDoesNotSupportPersonalDisk  
    The service instance being used has not been upgraded to support the personal vDisk feature.  
    DatabaseMissingCapabilites  
    The database supporting the service instance being used has not been upgraded to support the personal vDisk feature.  
    CommunicationError  
    An error occurred while communicating with the service.  
    InvalidParameterCombination  
    Both PurgeJobOnSuccess and RunAsynchronously were specified. When running asynchronously, the cmdlet terminates before the job does, so it cannot clean up the completed job.  
    PermissionDenied  
    The user does not have administrative rights to perform this operation.  
    ConfigurationLoggingError  
    The operation could not be performed because of a configuration logging error.  
    ScopeNotFound  
    One or more of the scopes nominated for the new provisioning scheme do not exist.  
    WorkflowHostUnavailable  
    The task could not be started because the database connection is inactive.  
    ExceptionThrown  
    An unexpected error occurred. To locate more details, see the Windows event logs on the controller being used, or examine the XenDesktop logs. VhdParametersMustBeSupplied  
    When parameter VhdTemplateSource or VhdResultDestination is supplied, both parameters are required to be supplied. ServiceDoesNotSupportFullDiskClone  
    The full disk clone parameter is being used when the service does not support the full disk clone feature. Upgrade the service or remove the parameter. FullDiskCloneDoesNotSupportCleanOnBootVMs  
    The full disk clone functionality is applicable to dedicated provisioned machines only. FullDiskCloneDoesNotSupportPvdVMs  
    The full disk clone functionality is only applicable to dedicated provisioned machines that do not use Personal VDisks.  
    The cmdlet is associated with a task of type NewProvisioningScheme, and while active will move through the following operations (CurrentOperation field)  
    ValidatingInputs  
    ConsolidatingMasterImage  
    PreparingMasterImage  
    ReplicatingMasterImage  
    CommittingScheme
## Examples

### Example 1

```
C:\PS> New-ProvScheme -ProvisioningSchemeName XenPS -HostingUnitName XenHu -IdentityPoolName idPool1 -CleanOnBoot -MasterImageVM XDHyp:\HostingUnits\XenHU\Base.vm\Base.snapshot  
  
TaskId                              : 90e93b9d-a225-4701-ad50-fa1546af35ac  
  
Active                              : False  
  
Host                                : MyHost  
  
DateStarted                         : 17/05/2010 08:22:22  
  
Type                                : NewProvisioningScheme  
  
Metadata                            : {}  
  
WorkflowStatus                      : Completed  
  
ProvisioningSchemeName              : XenPS  
  
MasterImage                         : /Base.vm/Base.snapshot  
  
IdentityPoolName                    : idPool1  
  
IdentityPoolUid                     : 03743136-e43b-4a87-af74-ab71686b3c16  
  
HostingUnitName                     : XenHU  
  
HostingUnitUid                      : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501  
  
PersonalVDiskDriveLetter            :  
  
PersonalVDiskDriveSize              : 0  
  
ProvisioningSchemeUid               : 7585f0de-192e-4847-a6d8-22713c3a2f42  
  
CurrentOperation                    :  
  
TaskState                           : Finished  
  
TaskStateInformation                :  
  
TaskProgress                        : 100  
  
DiskSize                            : 24
```

#### Description
Creates a new provisioning scheme with the name "XenPS" using the hosting unit "XenHu" and the identity pool "idPool1" from the master VM snapshot called "Base.snapshot".
### Example 2

```
C:\PS> New-ProvScheme -ProvisioningSchemeName XenPS -HostingUnitName XenHu -IdentityPoolName idPool1 -CleanOnBoot -MasterImageVM XDHyp:\HostingUnits\XenHU\Base.vm\Base.snapshot -RunAsynchronously  
  
Guid  
  
----  
  
6dd85fec-96cf-46b1-9cd4-d8ba7d06e85b
```

#### Description
Creates a new provisioning scheme with the name "XenPS" using the hosting unit "XenHu" and the identity pool "idPool1" from the master VM snapshot called "Base.snapshot" asynchronously. To get the task details, use Get-ProvTask -TaskID &lt;task id&gt;  
i.e.  
C:\\PS&gt;Get-ProvTask -TaskID 6dd85fec-96cf-46b1-9cd4-d8ba7d06e85b  
TaskId                              : 6dd85fec-96cf-46b1-9cd4-d8ba7d06e85b  
Active                              : False  
Host                                : MyHost  
DateStarted                         : 17/05/2010 08:22:22  
Type                                : NewProvisioningScheme  
Metadata                            : {}  
WorkflowStatus                      : Completed  
ProvisioningSchemeName              : XenPS  
MasterImage                         : XDHyp:\\HostingUnits\\XenHU\\Base.vm\\Base.snapshot  
IdentityPoolName                    : idPool1  
IdentityPoolUid                     : 03743136-e43b-4a87-af74-ab71686b3c16  
HostingUnitName                     : XenHU  
HostingUnitUid                      : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501  
PersonalVDiskDriveLetter            :  
PersonalVDiskDriveSize              : 0  
ProvisioningSchemeUid               : 7585f0de-192e-4847-a6d8-22713c3a2f42  
TaskState                           : Finished  
TaskStateInformation                :  
TaskProgress                        : 100  
DiskSize                            : 24
### Example 3

```
C:\PS>$provScheme = New-ProvScheme -ProvisioningSchemeName XenPS2 -HostingUnitName XenHu -IdentityPoolName idPool1 -CleanOnBoot -MasterImageVM XDHyp:\HostingUnits\XenHU\Base.vm\Base.snapshot -UsePersonalVDiskStorage -PersonalVDiskDriveSize 17 -PersonalVDiskDriveLetter x
```

#### Description
Creates a new provisioning scheme with the name "XenPS2" using the hosting unit "XenHu" and the identity pool "idPool1" from the master VM snapshot called "Base.snapshot"; apply a 17GB personal vDisk. The personal vDisk is mapped as drive X. The operation runs synchronously, and the return value contains the task details  
For example:  
C:\\PS&gt;\$provScheme  
TaskId                              : d726222a-04b5-4098-b9ac-db85ed9d351b  
Active                              : False  
Host                                : MyHost  
DateStarted                         : 12/09/2011 09:30:04  
Type                                : NewProvisioningScheme  
Metadata                            : {}  
ProvisioningSchemeName              : XenPS2  
IdentityPoolName                    : idPool1  
IdentityPoolUid                     : 03743136-e43b-4a87-af74-ab71686b3c16  
HostingUnitName                     : XenHU  
HostingUnitUid                      : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501  
PersonalVDiskDriveLetter            : X  
PersonalVDiskDriveSize              : 17  
WorkflowStatus                      : Completed  
MasterImage                         : XDHyp:\\HostingUnits\\XenHU\\Base.vm\\Base.snapshot  
ProvisioningSchemeUid               : 7585f0de-192e-4847-a6d8-22713c3a2f42  
TaskState                           : Finished  
TaskStateInformation                :  
TaskProgress                        : 100  
DiskSize                            : 24
