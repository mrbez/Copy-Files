# Copy-Files
Copies specified files and directories to each specified destination using Robocopy.

## Description
* Specified sources, destinations, and robocopy options will be used to make copy operations.
* Both files and directories can be used as sources.
* Sources and destinations paths can either be local (e.g. `'C:\Folder'`), network (e.g. `'\\ServerName\Folder'`), or relative from the working directory (e.g. `'Folder\Subfolder'`).

## Usage
Copy-Files can either be used as a standalone script, or as a module together with separate configuration scripts. The Standalone script allows for greater portability and isolation, while the module allows for greater accessibility, scalability and upgradability.

### Standalone Script
* Specify the sources, destinations, and robocopy options within the `Copy-Files.ps1` script.
* Give the script a unique name.
* Run the script to copy the files and directories.

### Module
* Install the `Copy-Files.psm1` module. Refer to Microsoft's documentation on installing PowerShell modules.
* Specify the sources, destinations, and robocopy options within the `Copy-Files-Config.ps1` script.
* Give the script a unique name.
* Run the script to copy the files and directories.

## Copying

### via File Explorer
* Right-click the script, and choose 'Run with PowerShell'.

### via Command line
* Run the script via a command line.

```
Powershell "C:\scripts\Copy-Files\Copy-Files-Project1.ps1"
```

### Batches
* Make as many copies of the standalone or configuration script as desired.
* Give each script a unique name.
* Specify the sources, destinations, and robocopy options within each script.
* Run each script to copy the respective files and directories.

An example of scripts representing separate batches of files and directories to be copied:

```
Copy-Files-Project1.ps1
Copy-Files-Project2.ps1
Copy-Files-Data1.ps1
Copy-Files-Data2.ps1
Copy-Files-Backup.ps1
```

## Scheduling
* Set up the script to be run.
* Create a task in *Task Scheduler*, giving the task a name, configuring the user account to run the script on, and defining a schedule for the script.
* Add an *Action* with the following settings:
  * Action: `Start a program`
  * Program/script: `Powershell`
  * Add arguments (optional): `C:\path\to\script.ps1`
* Repeat the steps for each script that is to be scheduled.
* If unsure, refer to official documentation or guides on using *Task Scheduler*.

## Parameters

```
Copy-Files [-Config] <Hashtable[]> [<CommonParameters>]

PARAMETERS
    -Config <Hashtable[]>
        The configuration hashtable containing sources, destinations, and robocopy options to be used by Copy-Files.

    <CommonParameters>
        This cmdlet supports the common parameters: Verbose, Debug,
        ErrorAction, ErrorVariable, WarningAction, WarningVariable,
        OutBuffer, PipelineVariable, and OutVariable. For more information, see
        about_CommonParameters (https:/go.microsoft.com/fwlink/?LinkID=113216).
```

## Examples

#### Example 1
Runs the script within the working directory named `Copy-Files-Project1.ps1` in the current instance of PowerShell.

```
.\Copy-Files-Project1.ps1
```

#### Example 2
Runs script named `Copy-Files-Project1.ps1` in a separate instance of Powershell.

```
Powershell "C:\scripts\Copy-Files\Copy-Files-Project1.ps1"
```

#### Example 3
Runs the Copy-Files module with the configuration hashtable named `$myconfig`.

```
Copy-Files -Config $myconfig
```

## Security
Unverified scripts are restricted from running on Windows by default. To run Copy-Files, you will need to allow the execution of unverified scripts. To do so, open PowerShell as an *Administrator*. Then run the command:

```
Set-ExecutionPolicy Unrestricted -Force
```

To revert the policy, simply run the command:

```
Set-ExecutionPolicy Undefined -Force
```

## Notes
* Copy-Files serves as a wrapper around Robocopy as a convenient and automatable file and directory copying solution.
* Robocopy, otherwise known as Robust File Copy, is a command-line directory and/or file replication command in Windows.
* It is recommended you have some knowledge about and experience with Robocopy before using Copy-Files.
* For more information on Robocopy, refer to Microsoft's documentation on the command, or run `'robocopy /?'`.

### Tips
* To quickly get the full path of a file or directory in File Explorer, simply *Shift + Right-Click* on the item and select 'Copy as path'.

## Requirements
* Windows with <a href="https://github.com/PowerShell/PowerShell#get-powershell" target="_blank" title="PowerShell">PowerShell v3</a> or higher.