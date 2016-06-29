---
external help file: PSITPro5_Management.xml
online version: http://go.microsoft.com/fwlink/p/?linkid=293916
schema: 2.0.0
---

# Show-EventLog
## SYNOPSIS
Displays the event logs of the local or a remote computer in Event Viewer.

## SYNTAX

```
Show-EventLog [[-ComputerName] <String>]
```

## DESCRIPTION
The Show-EventLog cmdlet opens Event Viewer on the local computer and displays in it all of the classic event logs on the local computer or a remote computer.

To open Event Viewer on Windows Vista and later versions of the Windows operating system, the current user must be a member of the Administrators group on the local computer.

The cmdlets that contain the EventLog noun (the EventLog cmdlets) work only on classic event logs.
To get events from logs that use the Windows Event Log technology in Windows Vista and later versions of the Windows operating system, use the Get-WinEvent cmdlet.

## EXAMPLES

### Example 1: Display event logs for the local computer
```
PS C:\>Show-EventLog
```

This command opens Event Viewer and displays in it the classic event logs on the local computer.

### Example 2: Display event logs for a remote computer
```
PS C:\>Show-EventLog -ComputerName "Server01"
```

This command opens Event Viewer and displays in it the classic event logs on the Server01 computer.

## PARAMETERS

### -ComputerName
Specifies a remote computer.
Show-EventLog displays the event logs from the specified computer in Event Viewer on the local computer.
The default is the local computer.

Type the NetBIOS name, an IP address, or a fully qualified domain name of a remote computer.

This parameter does not rely on Windows PowerShell remoting.
You can use the ComputerName parameter even if your computer is not configured to run remote commands.

```yaml
Type: String
Parameter Sets: (All)
Aliases: CN

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

## INPUTS

### None
You cannot pipe input to this cmdlet.

## OUTPUTS

### None
This cmdlet does not generate any output.

## NOTES
* The Windows PowerShell command prompt returns as soon as Event Viewer opens. You can work in the current session while Event Viewer is open.

  Because this cmdlet requires a user interface, it does not work on Server Core installations of Windows Server.

*

## RELATED LINKS

[Clear-EventLog](525ef611-6484-4088-887c-e084f3f5763b)

[Get-EventLog](b4985b11-82bf-487d-928d-becd96fc0419)

[Limit-EventLog](c3c3797c-e5d2-494b-b9c8-170999440385)

[New-EventLog](21e8f496-8f5b-4b79-9393-f16c86287e67)

[Remove-EventLog](487325e7-2a78-49fe-9126-c56222a8fa58)

[Write-EventLog](c93c4cd3-028f-4343-bfe6-b70f8f249290)
