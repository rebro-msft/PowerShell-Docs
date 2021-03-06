---
description:  
manager:  carmonm
ms.topic:  reference
author:  jpjofre
ms.prod:  powershell
keywords:  powershell,cmdlet
ms.date:  2016-12-12
title:  Get OperationValidation
ms.technology:  powershell
external help file:   Microsoft.PowerShell.Operation.Validation-help.xml
schema:   2.0.0
online version:   http://go.microsoft.com/fwlink/?LinkId=834963
---


# Get-OperationValidation

## SYNOPSIS
Gets Operation Validation Framework tests.

## SYNTAX

```
Get-OperationValidation [[-ModuleName] <String[]>] [-TestType <String[]>] [<CommonParameters>]
```

## DESCRIPTION
The **Get-OperationValidation** cmdlet gets Operation Validation Framework tests for installed modules.

Modules that include a Diagnostics folder are inspected for Pester tests in the Simple or Comprehensive subfolder, or both.

## EXAMPLES

### Example 1: Get Operation Validation tests
```
PS C:\>Get-OperationValidation -ModuleName "C:\temp\modules\AddNumbers"
    Type:     Simple
    File:     addnum.tests.ps1
    FilePath: C:\temp\modules\AddNumbers\Diagnostics\Simple\addnum.tests.ps1
    Name:
        Add-Em
        Subtract em
        Add-Numbers
    Type:     Comprehensive
    File:     Comp.Adding.Tests.ps1
    FilePath: C:\temp\modules\AddNumbers\Diagnostics\Comprehensive\Comp.Adding.Tests.ps1
    Name:
        Comprehensive Adding Tests
        Comprehensive Subtracting Tests
        Comprehensive Examples
```

This command gets validation tests from the module named AddNumbers in the C:\temp\modules folder.

## PARAMETERS

### -ModuleName
Specifies an array of names of modules.

```yaml
Type: String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TestType
Specifies an array of test types.
Valid values are Simple, Comprehensive, or both.
The default is "Simple,Comprehensive".

```yaml
Type: String[]
Parameter Sets: (All)
Aliases:
Accepted values: Simple, Comprehensive

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](../microsoft.powershell.core/about/about_commonparameters.md).

## INPUTS

### None
You cannot pipe any input to this cmdlet.

## OUTPUTS

### PSCustomObject
The **PSCustomObject** describes the validation.

## NOTES

## RELATED LINKS

[Invoke-OperationValidation](Invoke-OperationValidation.md)

