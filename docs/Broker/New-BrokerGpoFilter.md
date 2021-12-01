﻿
# New-Brokergpofilter
Creates a new GPO filter.
## Syntax

```
New-BrokerGpoFilter -FilterData <String> -FilterName <String> -FilterType <String> -PolicyGuid <Guid> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```

## Detailed Description
Creates a GPO filter for a policy to specify how the policy should be applied.


## Related Commands

* [Get-BrokerGpoFilter](../Get-BrokerGpoFilter/)
* [Set-BrokerGpoFilter](../Set-BrokerGpoFilter/)
* [Remove-BrokerGpoFilter](../Remove-BrokerGpoFilter/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| FilterData | The filter data. | true | true (ByPropertyName) |  |
| FilterName | The filter name. | true | true (ByPropertyName) |  |
| FilterType | The filter type. | true | true (ByPropertyName) |  |
| PolicyGuid | The ID of the policy for which the filter is defined | true | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None
Input cannot be piped to this cmdlet.
## Return Values

### Citrix.Broker.Admin.Sdk.Gpofilter
Outputs the GPO filter object.
## Examples

### Example 1

```
C:\PS> New-BrokerGpoFilter -PolicyGuid {123...} -FilterType ClientName -FilterName 'CNFilter0' -FilterData 'Client1'
```

#### Description
Creates a new client name filter for a policy.
