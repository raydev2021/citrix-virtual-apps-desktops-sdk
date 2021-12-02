﻿
# Remove-Brokerautotagrulemetadata
Deletes AutoTagRule Metadata from the AutoTagRule objects
## Syntax

```
Remove-BrokerAutoTagRuleMetadata [-InputObject] <AutoTagRule[]> -Name <String> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```

## Detailed Description
The Remove-BrokerAutoTagRuleMetadata cmdlet deletes Metadata from the AutoTagRule objects.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the AutoTagRule object's instance whose Metadata is to be deleted. | true | true (ByValue) |  |
| Name | Specifies the name of the Metadata to be deleted | true | false |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Brokerautotagrule
You can pipe the AutoTagRule to delete the metadata.
## Return Values

### None

## Examples

### Example 1

```
C:\PS> Remove-BrokerAutoTagRuleMetadata -InputObject $obj-Uid -Name "MyMetadataName"
```

#### Description
This command deletes the Metadata "MyMetadataName" key-value pair for the AutoTagRule whose instance is pointed by \$obj-Uid
### Example 2

```
C:\PS> Get-BrokerAutoTagRule | Remove-BrokerAutoTagRuleMetadata -Name "MyMetadataName"
```

#### Description
This command deletes the Metadata "MyMetadataName" key-value pair for all the AutoTagRule in the site