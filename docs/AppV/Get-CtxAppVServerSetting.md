﻿
# Get-Ctxappvserversetting
Returns settings for the specified App-V Publishing Server.
## Syntax

```
Get-CtxAppVServerSetting -AppVPublishingServer <string> [<CommonParameters>]
```

## Detailed Description
Returns settings for the specified App-V Publishing Server. For more information about these settings, see the App-V documentation on the Microsoft website at http://technet.microsoft.com/en-us/library/jj687745.aspx


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AppVPublishingServer | The full URL (including port number) of the Publishing Server for which settings are to be returned. | true | true (ByValue, ByPropertyName) |  |

## Input Type

### 

## Return Values

### Publishing Server Settings. These Settings Are:
GlobalRefreshEnabled  
GlobalRefreshOnLogon  
GlobalRefreshInterval  
GlobalRefreshIntervalUnit  
UserRefreshEnabled  
UserRefreshOnLogon  
UserRefreshInterval  
UserRefreshIntervalUnit
## Examples

### Example 1

```
Get-CtxAppVServerSetting -AppVPublishingServer http://appv-pubsrv.mydomain.com:8082
```

#### Description
This example returns settings associated with http://appv-pubsrv.mydomain.com:8082 in the following format:  
GlobalRefreshEnabled: false  
GlobalRefreshOnLogon: false  
GlobalRefreshInterval: 0  
GlobalRefreshIntervalUnit: Day  
UserRefreshEnabled: true  
UserRefreshOnLogon: false  
UserRefreshInterval: 0  
UserRefreshIntervalUnit: Hour
