﻿
# New-Provmastervmimage
Prepare a new master image for a provisioning scheme.
## Syntax

```
New-ProvMasterVMImage [-ProvisioningSchemeName] <String> -MasterImageVM <String> [-VhdTemplateSource <String>] [-VhdResultDestination <String>] [-AppScanResultsFile <String>] [-FunctionalLevel <String>] [-RunAsynchronously] [-PurgeJobOnSuccess] [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]  
  
New-ProvMasterVMImage -ProvisioningSchemeUid <Guid> -MasterImageVM <String> [-VhdTemplateSource <String>] [-VhdResultDestination <String>] [-AppScanResultsFile <String>] [-FunctionalLevel <String>] [-RunAsynchronously] [-PurgeJobOnSuccess] [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
Provides the ability to prepare an update for the hard disk image used to provision virtual machines.

A snapshot is used rather than a VM, so that the content of the hard disk for the provisioning scheme can be easily determined.

As the snapshot is specified using a path into the Citrix Host Service Powershell Provider, the Citrix Host Service Powershell snap-in must also be loaded for this cmdlet to be used.

The prepared hard disk image path is stored into the history (see Get-ProvSchemeMasterVMImageHistory).  The data stored in the history allows for a fast update to be undertaken, to switch to using the newly prepared hard disk image at a time chosen by the system administrator.


## Related Commands

* [Publish-ProvMasterVMImage](../Publish-ProvMasterVMImage/)
* [Get-ProvSchemeMasterVMImageHistory](../Get-ProvSchemeMasterVMImageHistory/)
* [Get-ProvScheme](../Get-ProvScheme/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ProvisioningSchemeName | The provisioning scheme to which the hard disk image should be updated. | true | true (ByPropertyName) |  |
| MasterImageVM | The path in the hosting unit provider to the virtual machine snapshot that will be used.  This identifies the hard disk to be used and the default values for the memory and processors.  This must be a path to a Snapshot item in the same hosting unit that the hosting unit name or hosting unit Uid refers to.  
Valid paths are of the format; XDHyp:\\HostingUnits\\&lt;HostingUnitName&gt;\\&lt;path&gt;\\&lt;VMName&gt;.vm\\&lt;SnapshotName&gt;.snapshot | true | true (ByPropertyName) |  |
| ProvisioningSchemeUid | The provisioning scheme identifier to which the hard disk image should be updated. | true | false |  |
| VhdTemplateSource | File path to a source VHD template to be used when performing application scanning during image preparation. The presence of this parameter in conjunction with VhdResultDestination implies that application scanning is to be performed | false | false |  |
| VhdResultDestination | File path (including file name) where the VHD disk file containing the results of application scanning should be written. | false | false |  |
| AppScanResultsFile | File name to which the results of application scanning should be written. | false | false |  |
| FunctionalLevel | The FunctionalLevel of the VDA installed on the given MasterImageVM. | false | false |  |
| RunAsynchronously | Indicates whether or not the cmdlet should return before it is complete.  If specified, the command returns an identifier for the task that was created.  You can monitor this task using the Get-ProvTask cmdlet. | false | false | false |
| PurgeJobOnSuccess | Indicates that the task history will be removed from the database when the task has finished.  This cannot be specified for tasks that are run asynchronously. | false | false | false |
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
When "RunAsynchronously" is specified, this identifier is returned to provide the task identifier.  
          System.Management.Automation.PSCustomObject  
          This object provides details of the task run and contains the following information:  
          TaskId &lt;Guid&gt;  
          The identifier for the task that was performed.  
          Active &lt;Boolean&gt;  
          Indicates whether the task is still processing or is complete.  
          Host &lt;string&gt;  
          The name of the host on which the task is running or was run.  
          DateStarted &lt;DateTime&gt;  
          The date and time that the task was initiated.  
          Type &lt;Citrix.XDInterServiceTypes.JobType&gt;  
          The type of the task. For new provisioning scheme tasks this is always "NewProvisioningScheme".  
          Metadata &lt;Citrix.MachineCreation.Sdk.Metadata\[\]&gt;  
          The list of metadata stored against the task. For new tasks this will be empty until metadata is added.  
          WorkflowStatus &lt;System.Workflow.Runtime.WorkflowStatus&gt;  
          Indicates the status of the workflow that is being used to process the task.  
          ProvisioningSchemeName &lt;string&gt;  
          The name of the provisioning scheme that the task was for.  
          ProvisioningSchemeUid &lt;Guid&gt;  
          The unique identifier of the provisioning scheme that the task was for.  
          MasterImage &lt;string&gt;  
          The path (in the hosting unit provider) of the virtual machine snapshot that was used as the master image for the task.  
          IdentityPoolName &lt;string&gt;  
          The name of the identity pool (from the ADIdentity PowerShell snap-in) that the new provisioning scheme will use.  
          IdentityPoolUid &lt;guid&gt;  
          The unique identifier name of the identity pool (from the ADIdentity PowerShell snap-in) that the new provisioning scheme will use.  
          HostingUnitName &lt;string&gt;  
          The name of the hosting unit (from the Hosting Unit PowerShell snap-in) that the new provisioning scheme will use.  
          HostingUnitUid  
          The unique identifier of the hosting unit (from the Hosting Unit PowerShell snap-in) that the new provisioning scheme will use.  
          TaskState &lt;Citrix.DesktopUpdateManager.SDK.NewProvisioningSchemeState&gt;  
          The state of the task.  This can be any of the following:  
          Processing  
          Indicates that the task has just begun and has not done anything yet.  
          LocatingResources,  
          Indicates that the workflow is locating resources from other services.  
          HostingUnitNotFound  
          Indicates that the task failed because the required hosting unit could not be located.  
          VirtualMachineSnapshotNotFound  
          Indicates that the task failed because the required snapshot could not be located.  
          ConsolidatingMasterImage  
          Indicates that the task is consolidating the master image.  
          ReplicatingConsolidatedImageToAllStorage  
          Indicates that the task is replicating the consolidated master image.  
          StoringProvisioningScheme  
          Indicates that the task is storing the provisioning scheme data to the database.  
          Finished  
          Indicates that the task has completed with no errors.  
          ProvisioningSchemeAlreadyExists  
          Indicates that the task failed because a provisioning scheme with the same name already exists.  
          IdentityPoolNotFound  
          Indicates that the task failed because the identity pool specified could not be found.  
          MasterVMImageIsNotPartOfProvisioningSchemeHostingUnit,  
          Indicates that the hosting unit that the master image originated from is not the hosting unit that the provisioning scheme is defined to use.  
          MasterVmImageIsNotASnapshot  
          Indicates that the task failed because the master VM Image path does not refer to a Snapshot item.  
          ProvisioningSchemeNotFound  
          Could not find a provisioning scheme with the specified name.  
          TaskAlreadyRunningForProvisioningScheme  
          A task for a provisioning scheme with the same name is already running.  
          InvalidMasterVMConfiguration  
          The VM snapshot specified as the master had an invalid configuration.  
          InvalidMasterVMState  
          The VM snapshot specified as the master is currently in an invalid state.  
          InsufficientResources  
          Indicates that the task failed because the hypervisor did not have enough resources to complete the task.  
          StorageNotFound  
          Indicates that no associated storage was found in the hosting unit.  
          Canceled  
          Indicates that the task was stopped by user intervention (using Stop-ProvTask)  
          TaskStateInformation &lt;string&gt;  
          Holds string data providing more details about the current task state.  
          TaskProgress  
          The progress of the task 0-100%.
## Notes
Only one long-running task per provisioning scheme can be processed at any one time.  
    In the case of failure, the following errors can result.  
    Error Codes  
    -----------  
    JobCreationFailed  
    The requested task could not be started.  
    DatabaseError  
    An error occurred in the service while attempting a database operation.  
    DatabaseNotConfigured  
    The operation could not be completed because the database for the service is not configured.  
    ServiceStatusInvalidDb  
    An error occurred in the service while attempting a database operation - communication with the database failed for  
    for various reasons.  
    WorkflowHostUnavailable  
    The task could not be started because the database connection is inactive.  
    CommunicationError  
    An error occurred while communicating with the service.  
    PermissionDenied  
    The user does not have administrative rights to perform this operation.  
    ConfigurationLoggingError  
    The operation could not be performed because of a configuration logging error.  
    ExceptionThrown  
    An unexpected error occurred. To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.  
    UnsupportedByServer  
    The requested operation is not supported by this version of the service.  
    The cmdlet is associated with a task of type PublishImage, and while active will move through the following operations (CurrentOperation field)  
    ValidatingInputs  
    ConsolidatingMasterImage  
    PreparingMasterImage  
    ReplicatingMasterImage
## Examples

### Example 1

```
c:\PS>New-ProvMasterVMImage -ProvisioningSchemeName MyScheme -MasterImageVM XDHyp:\H  
  
          stingUnits\HostUnit1\RhoneCC_baseXP.vm\base.snapshot  
  
          TaskId                 : 248f102f-073f-45fe-aea9-1819a6d6dd1f  
  
          Active                 : False  
  
          Host                   : MyHost  
  
          DateStarted            : 17/05/2010 17:37:57  
  
          Type                   : PublishImage  
  
          Metadata               : {}  
  
          WorkflowStatus         : Completed  
  
          ProvisioningSchemeUid  : 7585f0de-192e-4847-a6d8-22713c3a2f42  
  
          ProvisioningSchemeName : MyScheme  
  
          MasterImage            : /RhoneCC_baseXP.vm/base.snapshot  
  
          HostingUnitName        : HostUnit1  
  
          HostingUnitUid         : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501  
  
          ADIdentityPoolName     :  
  
          ADIdentityPoolUid      : 03743136-e43b-4a87-af74-ab71686b3c16  
  
          CurrentOperation       :  
  
          TaskState              : Finished  
  
          TaskStateInformation   :  
  
          DeferRollout           : True  
  
          MasterImageVMId        : 9a23ab7d-a4e6-3788-53b9-ae5edef9c612
```

#### Description
Prepares a new master hard disk image for the provisioning Scheme "MyScheme" using the "base.snapshot" hard disk image.
