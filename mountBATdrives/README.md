# mountBATdrive
Script to connect Networkdrives with old net use commands. 
Use the same user for everyone 
Use AllUserStartup-Folder 

## Steps to reproduce
### mountDrive.bat
Script to connect the Network Drive
```
@echo off
net use T: \\192.168.1.1\share /user:username password
exit
```

### mountDrive.bat
Script to move bat-File to Global AllUserStartUp
```
Copy-Item -Path "$psscriptroot\mountDrive.bat" -Destination "C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup\mountTaststar.bat"

Return 0
```

### Transform to intunewin-File 
Generate Intune-File using [Intune-Win32-AppPackaging-Tool](https://github.com/microsoft/Intune-Win32-App-Packaging-Tool)
```
PS C:\Users\Nico\Desktop\Microsoft-Win32-Content-Prep-Tool> .\IntuneWinAppUtil.exe
Please specify the source folder: C:\Users\Nico\Desktop\input
Please specify the setup file: copyToStartup.ps1
Please specify the output folder: C:\Users\Nico\Desktop\output
Do you want to specify catalog folder (Y/N)?n

...

[=================================================]   100%  
INFO   Done!!!
```

### Upload File to Intune App using Win32