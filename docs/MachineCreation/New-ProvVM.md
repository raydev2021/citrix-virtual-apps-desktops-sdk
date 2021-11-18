﻿
# New-Provvm
Creates a new virtual machine.
## Syntax

```
New-ProvVM -ProvisioningSchemeName <String> -ADAccountName <String[]> [-FastBuild] [-NetworkMapping <Hashtable>] [-AutoAssignVLAN] [-SecurityGroup <String[]>] [-MachinesPerAssistant <Int32>] [-MaxAssistants <Int32>] [-RunAsynchronously] [-PurgeJobOnSuccess] [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]  
  
New-ProvVM -ProvisioningSchemeUid <Guid> -ADAccountName <String[]> [-FastBuild] [-NetworkMapping <Hashtable>] [-AutoAssignVLAN] [-SecurityGroup <String[]>] [-MachinesPerAssistant <Int32>] [-MaxAssistants <Int32>] [-RunAsynchronously] [-PurgeJobOnSuccess] [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
Lets you create new virtual machines with the configuration specified by a provisioning scheme.

The virtual machines are created using all of the storage specified in the provisioning scheme. The storage is used in a round robin mechanism. For the duration of this task, the AD accounts are locked (by the AD Identity Service), which stops the same accounts being used by other virtual machine creation tasks.


## Related Commands

* [Get-ProvVM](../Get-ProvVM/)
* [Remove-ProvVM](../Remove-ProvVM/)
* [Lock-ProvVM](../Lock-ProvVM/)
* [Unlock-ProvVM](../Unlock-ProvVM/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ProvisioningSchemeName | The name of the provisioning scheme in which the virtual machines are created. | true | false |  |
| ProvisioningSchemeUid | The unique identifier for the provisioning scheme in which the virtual machines are created. | true | false |  |
| ADAccountName | A list of the Active Directory account names that are used for the virtual machines. The accounts must be provided in a domain-qualified format. This parameter accepts Identity objects as returned by the New-AcctADAccount cmdlet, or any PSObject with string properties "Domain" and "ADAccountName". | true | false |  |
| FastBuild | Indicates whether or not the command can improve speed by using optimizations in the creation process. This may mean that machines you create cannot be booted until ResetVM operations have been performed by the Broker and Machine Identity Services. | false | false |  |
| NetworkMapping | Specifies how the attached NICs are mapped to networks. If this parameter is omitted, provisioned VMs are created with network settings as inherited from the provisioning scheme. If this parameter is supplied, machines are created with the number of NICs specified in the map, and each NIC is attached to the specified network. | false | false |  |
| AutoAssignVLAN | Indicates whether or not the VLAN of the network should be automatically assigned to the new VM or if the VLAN from the master image should be used | false | false | false |
| SecurityGroup | The security groups to apply to machines created in Cloud Hypervisors | false | false |  |
| MachinesPerAssistant | The number of concurrent volume operations that may be performed by each volume worker helper machine | false | false |  |
| MaxAssistants | The maximum number of volume worker help machines that may be created for this operation. | false | false |  |
| RunAsynchronously | Indicates whether or not the command returns before it is complete. If specified, the command returns an identifier for the task that was created. This task can be monitored using the get-ProvTask command. | false | false | false |
| PurgeJobOnSuccess | Indicates that the task history is removed from the database when the task has finished. This cannot be specified for tasks that are run asynchronously. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller to which the PowerShell snap-in connects. You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

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
            The type of task. For newly provisioned VM tasks, this is always "NewVirtualMachine".  
        Metadata &lt;Citrix.MachineCreation.Sdk.Metadata\[\]&gt;  
            The list of metadata stored against the task. For new tasks this is empty until metadata is added.  
        WorkflowStatus &lt;System.Workflow.Runtime.WorkflowStatus&gt;  
            Indicates the status of the workflow that is used to process the task.  
        ProvisioningSchemeName &lt;string&gt;  
            The name of the provisioning scheme that the task was for.  
        ProvisioningSchemeUid &lt;Guid&gt;  
            The unique identifier of the provisioning scheme that the task was for.  
        MasterImage &lt;string&gt;  
            The path (in the hosting unit provider) of the virtual machine snapshot that was used as the master image for the task.  
        IdentityPoolName &lt;string&gt;  
            The name of the identity pool (from the ADIdentity PowerShell snap-in) that the new provisioning scheme uses.  
        IdentityPoolUid &lt;guid&gt;  
            The unique identifier name of the identity pool (from the ADIdentity PowerShell snap-in) that the new provisioning scheme uses.  
        HostingUnitName &lt;string&gt;  
            The name of the hosting unit (from the Hosting Unit PowerShell snap-in) that the new provisioning scheme uses.  
        HostingUnitUid  
            The unique identifier of the hosting unit (from the Hosting Unit PowerShell snap-in) that the new provisioning scheme uses.  
        TaskState &lt;Citrix.DesktopUpdateManager.SDK.ProvisionVMState&gt;  
            The state of the task.  This can be any of the following:  
            Processing  
                Indicates that the task is in its initial state.  
            LocatingResources,  
                Indicates that the task is locating information from other services.  
            HostingUnitNotFound  
                Indicates that the required hosting unit could not be located.  
            ProvisioningSchemeNotFound  
                Indicates that the required provisioning scheme could not be located.  
            Provisioning  
                Indicates that the task is at the provisioning stage.  
            IdentityPoolNotFound  
                Indicates that the required identity pool could not be located.  
            TaskAlreadyRunningForProvisioningScheme  
                Indicates that the provisioning scheme already has another task running.  
            HypervisorInMaintenanceMode  
                Indicates that the hypervisor is not available for normal use.  
            NoAvailableStorage  
                Indicates that no storage is available for the hypervisor.  
            NoAvailableNetwork  
                Indicates that no network is available for the hypervisor.  
            Finalizing  
                Indicates that the task is finalizing.  
            Finished  
                Indicates that the task is complete.  
            FinishedWithErrors  
                Indicates that the task is complete but there were errors. Specific details of errors are included with each failed virtual machine.  
            Removing  
                Indicates that the task is removing virtual machines from the hypervisor.  
            Failed  
                The job failed for reasons specified in TaskStateInformation.  
            Canceled  
                Indicates that the task was stopped by user intervention (using Stop-ProvTask).  
        TaskStateInformation  
            Provides more detailed information about the current task state.  
        VirtualMachinesToCreateCount &lt;int&gt;  
            The total number of virtual machines that the task is trying to create.  
        VirtualMachinesCreatedCount &lt;int&gt;  
            The number of virtual machines that the task has created so far. Details of the machines that were created are in the CreatedVirtualMachines parameter.  
        VirtualMachinesCreationFailedCount &lt;int&gt;  
            The number of virtual machines that the task has failed to create. Details of the machines that were not created are in the FailedVirtualMachines parameter.  
        FailedVirtualMachines &lt;Citrix.DesktopUpdateManager.SDK.VirtualMachineCreation\[\]&gt;  
            ADAccountName &lt;string&gt;  
                The domain qualified AD Account name of the machine.  
            ADAccountSid &lt;string&gt;  
                The AD account SID of the machine account.  
            DiagnosticInformation &lt;Citrix.MachineCreation.Sdk.ExceptionSurrogate\[\]&gt;  
                A collection of handled error states which caused the provisioning to fail.  
                    ExceptionType &lt;string&gt;  
                      The type of exception this object represents  
                    Message  &lt;string&gt;  
                      The exception message  
                    Details  &lt;string&gt;  
                      The full exception content including stack trace  
                    InnerException &lt;Citrix.MachineCreation.Sdk.ExceptionSurrogate&gt;  
                      Information relating to any contributing error state  
            Status &lt;string&gt;  
            StatusAdditionalInformation &lt;string&gt;  
            VMId &lt;string&gt;  
                The virtual machine identifier within the hypervisor in which the VM resides.  
            VMName &lt;string&gt;  
                The display name of the virtual machine within the hypervisor in which the VM resides.  
        CreatedVirtualMachines &lt;Citrix.DesktopUpdateManager.SDK.VirtualMachineCreation\[\]&gt;  
            See FailedVirtualMachines for details of the object parameters.
## Notes
Only one long-running task in each provisioning scheme can be processed at a time.  
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
    An error occurred in the service while attempting a database operation. Communication with the database failed  
    for various reasons.  
    WorkflowHostUnavailable  
    The task could not be started because the database connection is inactive.  
    PermissionDenied  
    The user does not have administrative rights to perform this operation.  
    ConfigurationLoggingError  
    The operation could not be performed because of a configuration logging error  
    CommunicationError  
    An error occurred while communicating with the service.  
    InvalidParameterCombination  
    Both PurgeJobOnSuccess and RunAsynchronously were specified.  
    When running asynchronously, the cmdlet terminates before the job does,  
    so it cannot clean up the completed job.  
    PermissionDenied  
    The user does not have administrative rights to perform this operation.  
    ExceptionThrown  
    An unexpected error occurred. To locate more details, see the Windows event logs  
    on the controller being used, or examine the XenDesktop logs.  
    The cmdlet is associated with a task of type NewVirtualMachine, and while active will move through the following operations (CurrentOperation field)  
    ValidatingInputs  
    CreatingVirtualMachines  
    ReleasingAccountLocks
## Examples

### Example 1

```
C:\PS>New-provVM -ProvisioningSchemeName MyScheme -ADAccountName "domain\Account"  
  
TaskId                             : 4b49f13a-277c-4cb0-bc40-f088430cfe8a  
  
Active                             : False  
  
Host                               : DUMTESTDDC  
  
DateStarted                        : 18/05/2010 10:54:32  
  
Type                               : NewVirtualMachine  
  
Metadata                           : {}  
  
WorkflowStatus                     : Completed  
  
MasterImage                        : /Base.vm/Base.snapshot  
  
ProvisioningSchemeName             : MyScheme  
  
ProvisioningSchemeUid              : 7585f0de-192e-4847-a6d8-22713c3a2f42  
  
CurrentOperation                   :  
  
TaskState                          : Finished  
  
TaskStateInformation               :  
  
HostingUnitUid                     : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501  
  
HostingUnitName                    : XenHU  
  
IdentityPoolUid                    : 03743136-e43b-4a87-af74-ab71686b3c16  
  
IdentityPoolName                   : idPool1  
  
VirtualMachinesToCreateCount       : 1  
  
VirtualMachinesCreatedCount        : 1  
  
VirtualMachinesCreationFailedCount : 0  
  
CreatedVirtualMachines             : {DOMAIN\Account$}  
  
FailedVirtualMachines              : {}  
  
ProvisioningJob                    : 6fa5dc7c-6d49-4616-8682-aeb1580866b3  
  
ProvisioningStatus                 : Completed
```

#### Description
Creates a new virtual machine using the AD account "domain\\account" in the provisioning scheme "MyScheme".
### Example 2

```
C:\PS>New-provVM -ProvisioningSchemeName MyScheme -ADAccountName "domain\Account" -RunAsynchronously  
  
Guid  
  
----  
  
6dd85fec-96cf-46b1-9cd4-d8ba7d06e85b
```

#### Description
Creates a new virtual machine using the AD account "domain\\account" in the provisioning scheme "MyScheme" asynchronously. To get the task details, use Get-ProvTask -TaskID &lt;task id&gt;  
i.e.  
C:\\PS&gt;Get-ProvTask -TaskID 6dd85fec-96cf-46b1-9cd4-d8ba7d06e85b  
TaskId                             : 4b49f13a-277c-4cb0-bc40-f088430cfe8a  
Active                             : False  
Host                               : MyHost  
DateStarted                        : 18/05/2010 10:54:32  
Type                               : NewVirtualMachine  
Metadata                           : {}  
WorkflowStatus                     : Completed  
MasterImage                        : /Base.vm/Base.snapshot  
ProvisioningSchemeName             : MyScheme  
ProvisioningSchemeUid              : 7585f0de-192e-4847-a6d8-22713c3a2f42  
TaskState                          : Finished  
TaskStateInformation               :  
HostingUnitUid                     : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501  
HostingUnitName                    : XenHU  
IdentityPoolUid                    : 03743136-e43b-4a87-af74-ab71686b3c16  
IdentityPoolName                   : idPool1  
VirtualMachinesToCreateCount       : 1  
VirtualMachinesCreatedCount        : 1  
VirtualMachinesCreationFailedCount : 0  
CreatedVirtualMachines             : {DOMAIN\\Account\$}  
FailedVirtualMachines              : {}  
ProvisioningJob                    : 6fa5dc7c-6d49-4616-8682-aeb1580866b3  
ProvisioningStatus                 : Completed
### Example 3

```
C:\PS>$accounts = Get-AcctAdAccount -IdentityPool MyPool -State Available  
  
C:\PS>New-provVM -ProvisioningSchemeName MyScheme -ADAccountName $t -RunAsyncronously
```

#### Description
Creates a new virtual machine using all of the available AD accounts from the identity pool "MyPool" in the provisioning scheme "MyScheme" asynchronously. To get the task details, use Get-ProvTask -TaskID &lt;task id&gt;  
For example:  
C:\\PS&gt;Get-ProvTask -TaskID 6dd85fec-96cf-46b1-9cd4-d8ba7d06e85b  
TaskId                             : 4b49f13a-277c-4cb0-bc40-f088430cfe8a  
Active                             : False  
Host                               : MyHost  
DateStarted                        : 18/05/2010 10:54:32  
Type                               : NewVirtualMachine  
Metadata                           : {}  
WorkflowStatus                     : Completed  
MasterImage                        : /Base.vm/Base.snapshot  
ProvisioningSchemeName             : MyScheme  
ProvisioningSchemeUid              : 7585f0de-192e-4847-a6d8-22713c3a2f42  
TaskState                          : Finished  
TaskStateInformation               :  
HostingUnitUid                     : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501  
HostingUnitName                    : XenHU  
IdentityPoolUid                    : 03743136-e43b-4a87-af74-ab71686b3c16  
IdentityPoolName                   : idPool1  
VirtualMachinesToCreateCount       : 1  
VirtualMachinesCreatedCount        : 1  
VirtualMachinesCreationFailedCount : 0  
CreatedVirtualMachines             : {DOMAIN\\Account\$}  
FailedVirtualMachines              : {}  
ProvisioningJob                    : 6fa5dc7c-6d49-4616-8682-aeb1580866b3  
ProvisioningStatus                 : Completed
