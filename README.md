# PSCustomDrives

This PowerShell provides no functions to be used. It will provides a easy way to
have persistent PSDrives mapped.

## Configuration

To use this module, you need to create a `psdrives.txt` file at your home folder
(`$Env:USERPROFILE\psdrives.txt`).  Each line represents a drive to be mapped:
each one will be splitted at first non-black character, using first term as
PSDrive name, and second one as paths

Example:

    win    C:\Windows
    progf  C:\Program Files

It will map:

* `win:` to `C:\Windows`
* `progf` to `C:\Program Files`

PSCustomDrives will also always creating a mapping named `Modules` to the
directory in which modules are being installed.

### Quick command

It's also possible to execute a quick command, use the mapped folder as working
directory, without actually changing the current one. You just need to provide
the command line as an argument.

Example: `prof: Get-ChildItem`

If you need more complexes command, that would require special char (such as
`|`), you can use a ScriptBlock.

Example: `prof: { Get-ChildItem | Out-File contents.txt }`


## Installing

Windows 10 users:

    Install-Module PSCustomDrives -Scope CurrentUser

Otherwise, if you have [PsGet](http://psget.net/) installed:


    Install-Module PSCustomDrives
  
Or you can install it manually coping `PSCustomDrives.psm1` to your modules
folder (e.g. `
$Env:USERPROFILE\Documents\WindowsPowerShell\Modules\PSCustomDrives\`)

After installed, you will need to explicit load this module to have PSDrives
mapped:

    Import-Module PSCustomDrives

It's recommended to put this command to your profile file (`$PROFILE`).
