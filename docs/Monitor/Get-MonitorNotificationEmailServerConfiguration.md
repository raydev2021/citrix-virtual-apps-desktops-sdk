﻿
# Get-Monitornotificationemailserverconfiguration
Gets email server configuration
## Syntax

```
Get-MonitorNotificationEmailServerConfiguration [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
Retrurns the existing email server configurations required to send email alerts.


## Related Commands

* [Set-MonitorNotificationEmailServerConfiguration](../Set-MonitorNotificationEmailServerConfiguration/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a Citrix Virtual Apps and Desktops 7 controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Icollection&lt;Monitornotificationemailserverconfiguration&gt; System.String
Email server configuration
## Examples

### Example 1

```
GetMonitorNotificationEmailServerConfigurationCommand
```

#### Description
Returns the email configuration
