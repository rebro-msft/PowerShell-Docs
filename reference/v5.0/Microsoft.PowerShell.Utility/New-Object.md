---
external help file: PSITPro5_Utility.xml
online version: http://go.microsoft.com/fwlink/p/?linkid=293993
schema: 2.0.0
---

# New-Object
## SYNOPSIS
Creates an instance of a Microsoft .NET Framework or COM object.

## SYNTAX

### UNNAMED_PARAMETER_SET_1
```
New-Object [-TypeName] <String> [[-ArgumentList] <Object[]>] [-Property <IDictionary>]
```

### UNNAMED_PARAMETER_SET_2
```
New-Object [-ComObject] <String> [-Property <IDictionary>] [-Strict]
```

## DESCRIPTION
The New-Object cmdlet creates an instance of a .NET Framework or COM object.

You can specify either the type of a .NET Framework class or a ProgID of a COM object.
By default, you type the fully qualified name of a .NET Framework class and the cmdlet returns a reference to an instance of that class.
To create an instance of a COM object, use the ComObject parameter and specify the ProgID of the object as its value.

## EXAMPLES

### Example 1: Create a System.Version object
```
PS C:\>New-Object -TypeName System.Version -ArgumentList "1.2.3.4"
Major  Minor  Build  Revision

-----  -----  -----  --------

1      2      3      4
```

This command creates a System.Version object.
It uses a 1.2.3.4 string as the constructor.

### Example 2: Create an Internet Explorer COM object
```
PS C:\>$IE = New-Object -COMObject InternetExplorer.Application -Property @{Navigate2="www.microsoft.com"; Visible = $True}
```

This command creates an instance of the COM object that represents the Internet Explorer application.
The value of the Property parameter is a hash table that calls the Navigate2 method and sets the Visible property of the object to $True to make the application visible.

This command is the equivalent of the following:

$ie = New-Object -COMObject InternetExplorer.Application

$ie.Navigate2("www.microsoft.com")

$ie.Visible = $True

### Example 3: Use the Strict parameter to generate a non-terminating error
```
PS C:\>$A = New-Object -COMObject Word.Application -Strict -Property @{Visible = $True}
New-Object : The object written to the pipeline is an instance of the type
"Microsoft.Office.Interop.Word.ApplicationClass" from the component's primary
interop assembly. If this type exposes different members than the IDispatch
members, scripts written to work with this object might not work if the
primary interop assembly is not installed.

At line:1 char:14
+ $a=New-Object  <<<< -COM Word.Application -Strict; $a.visible=$true
```

This example demonstrates that adding the Strict parameter causes the New-Object cmdlet to generate a non-terminating error when the COM object uses an interop assembly.

### Example 4: Create a COM object to manage Windows desktop
```
The first command uses the ComObject parameter of the New-Object cmdlet to create a COM object with the Shell.Application ProgID. It stores the resulting object in the $objShell variable.
PS C:\>$objshell = New-Object -COMObject "Shell.Application"

The second command pipes the $objShell variable to the Get-Member cmdlet, which displays the properties and methods of the COM object. Among the methods is the ToggleDesktop method.
PS C:\>$objshell | Get-Member
   TypeName: System.__ComObject#{866738b9-6cf2-4de8-8767-f794ebe74f4e}


Name                 MemberType Definition

----                 ---------- ----------

AddToRecent          Method     void AddToRecent (Variant, string)

BrowseForFolder      Method     Folder BrowseForFolder (int, string, int, Variant)

CanStartStopService  Method     Variant CanStartStopService (string)

CascadeWindows       Method     void CascadeWindows ()

ControlPanelItem     Method     void ControlPanelItem (string)

EjectPC              Method     void EjectPC ()

Explore              Method     void Explore (Variant)

ExplorerPolicy       Method     Variant ExplorerPolicy (string)

FileRun              Method     void FileRun ()

FindComputer         Method     void FindComputer ()

FindFiles            Method     void FindFiles ()

FindPrinter          Method     void FindPrinter (string, string, string)

GetSetting           Method     bool GetSetting (int)

GetSystemInformation Method     Variant GetSystemInformation (string)

Help                 Method     void Help ()

IsRestricted         Method     int IsRestricted (string, string)

IsServiceRunning     Method     Variant IsServiceRunning (string)

MinimizeAll          Method     void MinimizeAll ()

NameSpace            Method     Folder NameSpace (Variant)

Open                 Method     void Open (Variant)

RefreshMenu          Method     void RefreshMenu ()

ServiceStart         Method     Variant ServiceStart (string, Variant)

ServiceStop          Method     Variant ServiceStop (string, Variant)

SetTime              Method     void SetTime ()

ShellExecute         Method     void ShellExecute (string, Variant, Variant, Variant, Variant)

ShowBrowserBar       Method     Variant ShowBrowserBar (string, Variant)

ShutdownWindows      Method     void ShutdownWindows ()

Suspend              Method     void Suspend ()

TileHorizontally     Method     void TileHorizontally ()

TileVertically       Method     void TileVertically ()
ToggleDesktop        Method     void ToggleDesktop ()

TrayProperties       Method     void TrayProperties ()

UndoMinimizeALL      Method     void UndoMinimizeALL ()

Windows              Method     IDispatch Windows ()

WindowsSecurity      Method     void WindowsSecurity ()

WindowSwitcher       Method     void WindowSwitcher ()

Application          Property   IDispatch Application () {get}

Parent               Property   IDispatch Parent () {get}

The third command calls the ToggleDesktop method of the object to minimize the open windows on your desktop.
PS C:\>$objshell.ToggleDesktop()
```

This example shows how to create and use a COM object to manage your Windows desktop.

## PARAMETERS

### -ArgumentList
Specifies a list of arguments to pass to the constructor of the .NET Framework class.
Separate elements in the list by using commas (,).
The alias for ArgumentList is Args.

```yaml
Type: Object[]
Parameter Sets: UNNAMED_PARAMETER_SET_1
Aliases: Args

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComObject
Specifies the programmatic identifier (ProgID) of the COM object.

```yaml
Type: String
Parameter Sets: UNNAMED_PARAMETER_SET_2
Aliases: 

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Property
Sets property values and invokes methods of the new object.

Enter a hash table in which the keys are the names of properties or methods and the values are property values or method arguments.
New-Object creates the object and sets each property value and invokes each method in the order that they appear in the hash table.

If the new object is derived from the PSObject class, and you specify a property that does not exist on the object, New-Object adds the specified property to the object as a NoteProperty.
If the object is not a PSObject, the command generates a non-terminating error.

```yaml
Type: IDictionary
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Strict
Generates a non-terminating error when a COM object that you attempt to create uses an interop assembly.
This feature distinguishes actual COM objects from .NET Framework objects with COM-callable wrappers.

```yaml
Type: SwitchParameter
Parameter Sets: UNNAMED_PARAMETER_SET_2
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeName
Specifies the fully qualified name of the .NET Framework class.
You cannot specify both the TypeName parameter and the ComObject parameter.

```yaml
Type: String
Parameter Sets: UNNAMED_PARAMETER_SET_1
Aliases: 

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

## INPUTS

### None
You cannot pipe input to this cmdlet.

## OUTPUTS

### Object
New-Object returns the object that is created.

## NOTES
* New-Object provides the most commonly-used functionality of the VBScript CreateObject function. A statement like Set objShell = CreateObject("Shell.Application") in VBScript can be translated to $objShell = New-Object -COMObject "Shell.Application" in Windows PowerShell.
* New-Object expands upon the functionality available in the Windows Script Host environment by making it easy to work with .NET Framework objects from the command line and within scripts.

*

## RELATED LINKS

[Compare-Object](bdc20eac-bff6-44bc-b130-1a986c79fb78)

[ForEach-Object](bea187c1-37b5-4fc7-9422-d29820643a4d)

[Group-Object](494af40a-1315-420f-8bd6-932006576dac)

[Measure-Object](f40a7de5-95a8-47a8-bb7c-8b2a4cdd2daf)

[Select-Object](2f182056-7955-4b77-9c58-64ab4a680074)

[Sort-Object](52c4a447-238d-43b4-8d3f-6aee5864b905)

[Tee-Object](ae5c403c-6a21-430e-a94a-74a1edee149a)

[Where-Object](6a70160b-cf62-48df-ae5b-0a9b173013b4)
