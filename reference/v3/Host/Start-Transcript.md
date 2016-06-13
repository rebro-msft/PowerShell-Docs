---
external help file: PSITPro3_Host.xml
schema: 2.0.0
---

# Start-Transcript
## SYNOPSIS
Creates a record of all or part of a Windows PowerShell session in a text file.

## SYNTAX

### UNNAMED_PARAMETER_SET_1
```
Start-Transcript [[-Path] <String>] [-Append] [-Force] [-NoClobber] [-Confirm] [-WhatIf]
```

### UNNAMED_PARAMETER_SET_2
```
Start-Transcript [[-LiteralPath] <String>] [-Append] [-Force] [-NoClobber] [-Confirm] [-WhatIf]
```

## DESCRIPTION
The Start-Transcript cmdlet creates a record of all or part of a Windows PowerShell session in a text file.
The transcript includes all command that the user types and all output that appears on the console.

## EXAMPLES

### -------------------------- EXAMPLE 1 --------------------------
```
PS C:\>start-transcript
```

This command starts a transcript in the default file location.

### -------------------------- EXAMPLE 2 --------------------------
```
PS C:\>start-transcript -path c:\transcripts\transcript0.txt -noclobber
```

This command starts a transcript in the Transcript0.txt file in C:\transcripts.
The NoClobber parameter prevents any existing files from being overwritten.
If the Transcript0.txt file already exists, the command fails.

## PARAMETERS

### -Append
Adds the new transcript to the end of an existing file.
Use the Path parameter to specify the file.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: 
Accept pipeline input: false
Accept wildcard characters: False
```

### -Force
Allows the cmdlet to append the transcript to an existing read-only file.
When used on a read-only file, the cmdlet changes the file permission to read-write.
Even using the Force parameter, the cmdlet cannot override security restrictions.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: 
Accept pipeline input: false
Accept wildcard characters: False
```

### -NoClobber
Will not overwrite \(replace the contents\) of an existing file.
By default, if a transcript file exists in the specified path, Start-Transcript overwrites the file without warning.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: 
Accept pipeline input: false
Accept wildcard characters: False
```

### -Path
Specifies a location for the transcript file.
Enter a path to a .txt file.
Wildcards are not permitted.

If you do not specify a path, Start-Transcript uses the path in the value of the $Transcript global variable.
If you have not created this variable, Start-Transcript stores the transcripts in the $Home\My Documents directory as \PowerShell_transcript.\<time-stamp\>.txt files.

If any of the directories in the path do not exist, the command fails.

```yaml
Type: String
Parameter Sets: UNNAMED_PARAMETER_SET_1
Aliases: 

Required: False
Position: 1
Default value: 
Accept pipeline input: false
Accept wildcard characters: False
```

### -LiteralPath
Specifies a location for the transcript file.
Unlike Path, the value of the LiteralPath parameter is used exactly as it is typed.
No characters are interpreted as wildcards.
If the path includes escape characters, enclose it in single quotation marks.
Single quotation marks tell Windows PowerShell not to interpret any characters as escape sequences.

```yaml
Type: String
Parameter Sets: UNNAMED_PARAMETER_SET_2
Aliases: 

Required: False
Position: 1
Default value: 
Accept pipeline input: false
Accept wildcard characters: False
```

### -Confirm
Prompts you for confirmation before running the cmdlet.Prompts you for confirmation before running the cmdlet.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: false
Accept pipeline input: false
Accept wildcard characters: False
```

### -WhatIf
Shows what would happen if the cmdlet runs.
The cmdlet is not run.Shows what would happen if the cmdlet runs.
The cmdlet is not run.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: false
Accept pipeline input: false
Accept wildcard characters: False
```

## INPUTS

### None
You cannot pipe objects to this cmdlet.

## OUTPUTS

### System.String
Start-Transcript returns a string that contains a confirmation message and the path to the output file.

## NOTES
To stop a transcript, use the Stop-Transcript cmdlet.

To record an entire session, add the Start-Transcript command to your profile.
For more information, see about_Profiles.

## RELATED LINKS

[Online Version:](http://go.microsoft.com/fwlink/?LinkID=113408)

[Stop-Transcript](71bf7425-d76b-407b-a0c8-5f0e0934abe3)

