# smtpdocker-wsl2
using Docker engine to be integrated with Windows Subsystem Linux (WSL) version 2, deploying a basic local Postfix/SMTP server

requirements

1. windows version higher than 1903 build 18362 

## Setup WSL2 on Windows

from windows documentation `https://docs.microsoft.com/en-us/windows/wsl/install-win10`

firstly to enable windows feature on WSL

click on windows icon, search for `turn windows feature on or off`, and tick on `Windows Subsystem for Linux`

or using powershell, run this command `dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart`

now to set default WSL version on your windows.

using poweshell, type `wsl --set-default-version 2`


open microsoft store and select your linuxdistribution and install.


after finish installing, theck the WSL version using command `wsl --list --verbose` 

and then to set specifically which WSL to be converted into version 2 `wsl --set-version (distribution name) (versionNumber)`

or you want default version set to 2, which when future WSL installation becomes version 2 by default

`wsl --set-default-version 2`

after finish installation and setup. You can access to the folder by using simple command `.\explorer.exe`


## Setup Docker

in your WSL,

first to install Docker

```
sudo apt-get update -y


sudo apt-get install -y \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common
    
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

sudo apt-key fingerprint 0EBFCD88

sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
   
sudo apt-get update -y && sudo apt-get install -y docker-ce

sudo usermod -aG docker $USER

```

now to install Docker-Compose

```
sudo apt-get install -y docker-compose
```

now to configure WSL to connect to Docker for Windows

`echo "export DOCKER_HOST=tcp://localhost:2375" >> ~/.bashrc && source ~/.bashrc `


now you only have to install Docker on your Win 10

do not forget to Expose daemon on tcp://localhost:2375 without TLS on your Docker general setting.

on your WSL, test the docker using command `docker info`

and when you try to run something frowm WSL, your Docker Windows is actually pulling the container.
























