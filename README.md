# smtpdocker-wsl2
using Docker engine to be integrated with Windows Subsystem Linux (WSL) version 2, deploying a basic local Postfix/SMTP server

requirements

1. windows version higher than 1903 build 18362 


from windows documentation `https://docs.microsoft.com/en-us/windows/wsl/install-win10`

firstly to enable windows feature on WSL

click on windows icon, search for `turn windows feature on or off`, and tick on `Windows Subsystem for Linux`

or using powershell, run this command `dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart`

now to set default WSL version on your windows.

using poweshell, type `wsl --set-default-version 2`










