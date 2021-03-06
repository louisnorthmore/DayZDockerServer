# Description
Running DayZ Server on Docker.

# Requirements
- Your Steam account
- Docker Desktop
- Windows 10 version 1809 or above

# Usage
## Preparation
Copy X3DAudio1_7.dll and XAPOFX1_5.dll to the Dockerfile's directory from your PC. They are located in the C:\Windows\System32.
## Build image
To start setting up DayZ Server container image, in this directory, please run this command.
```ps1
docker-compose build --build-arg steamlogin=STEAM_USERNAME --build-arg steampasswd=STEAM_PASSWORD --build-arg steamguard=STEAM_GUARD
```
- This command is including several arguments (STEAM_USERNAME, STEAM_PASSWD, STEAM_GUARD) to login and download, so please replace it to your steam account.
- This might cause error because the steam guard can be expired while this install process.
- By default, this install process will use Windows Server Core 1809 to use process isolation. If your environment is not this, it can be customized by using 'tag' build argument. (See the Full Tag Listing section: https://hub.docker.com/_/microsoft-windows-servercore )

## Run server
To start the DayZ Server in the docker container, please run these commands.
```ps1
docker-compose up -d
```
After running this command, you can connect to local server by using 172.16.238.99:2302.
In addition, Using Dayz Launcher is easier to use because it can specify the server IP address.

## Stop server
To stop the running DayZ Server in the docker container, please run these commands.
```ps1
docker-compose down
```

# Notification
Please do not make the server's image public like in DockerHub because it contains licensed files of DayZ Server.

# Current issues
X3DAudio1_7.dll and XAPOFX1_5.dll cannot be copied from build image, because of the installation of DirectX failure.

# TODO
- Creating a volume to customize configuration.

# Links
- https://community.bistudio.com/wiki/DayZ:Server_Configuration
- https://developer.valvesoftware.com/wiki/Command_Line_Options#SteamCMD
- https://write.corbpie.com/installing-and-setting-up-a-dayz-standalone-server-on-windows-server-2016-guide/
