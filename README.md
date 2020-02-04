# Scenario Tests for WSL2

This document goes over some basic scenarios that can test some of the different functionalities in WSL2. 

## Installing WSL2 and migrating distros

First you'll need to get WSL2 installed on your machine.

### Install WSL2

Follow the instructions [at this link](https://aka.ms/wsl2-install) to install WSL2.

It's recommended to install 'Ubuntu' from the store. And when you need to uninstall it, simply run `wsl --unregister Ubuntu`, and once you need to reinstall just open up the start menu and run the Ubuntu app. This will save you a lot time since you won't have to redownload the distro each time.

### Migrate a WSL1 distro to WSL2

- In Powershell run: 
   `wsl --set-default-version 1` 

- Uninstall your distro with `wsl --unregister Ubuntu` and then reinstall it by opening the Ubuntu app.

- Initialize the Ubuntu distro with a name and password and then quit out of the Window

- In Powershell run:
   `wsl --set-version Ubuntu 2`

- Once conversion is complete run the Ubuntu distro with `wsl -d Ubuntu` and make sure everything works.

### Install straight to a WSL2 distro

- In Powershell run: 
   `wsl --set-default-version 2`

- Uninstall your distro with `wsl --unregister Ubuntu` and then reinstall it by opening the Ubuntu app.

- Initialize the Ubuntu distro with a name and password

- Ensure your Ubuntu distro works properly and was converted successfully.
   - You check the version of your distro by running `wsl -l -v` in Powershell.

## Interop and accessing Linux files

Interop is one of the coolest features in WSL, so let's make sure it works.

### Run a Windows command

Run `powershell.exe` in your bash prompt. You should get access to a Powershell prompt without any errors. To go back to your bash shell in WSL simply type `exit`.

### Use interop to access Linux files in \\wsl$\

Type in these commands to open up a File Explorer Window in your home directory.

```
cd
explorer.exe .
```

Please check that the Window opened correctly and that you can view the Linux files in your home directory.

## Networking with Docker-Compose!

Next we're going to test networking using `localhost` on Windows. 

### Install Docker and Docker-Compose

First make sure you have docker, and docker-compose installed.

The easiest way to install them is to make sure you are using Ubuntu 18.04 and then using the script provided in this repo by running: 

`sudo ./installDockerUbuntu.sh`

Or if you want to install it manually you can use [this link](https://docs.docker.com/install/linux/docker-ce/ubuntu/) to install Docker, and [this link](https://docs.docker.com/compose/install/) to install Docker-Compose.

### Run the app

Move into the dockerComposeTest folder and run the app:

```
cd dockerComposeTest
sudo docker-compose up --build
```

Once you see a green message saying 'done' you'll know it's ready.

### Connect to the sample sites

Open up Microsoft Edge and connect to http://localhost:7000 you'll see a message there that will prompt you to click on it to connect to another site: http://localhost:8000 . Please verify that both of these work and you're done!
