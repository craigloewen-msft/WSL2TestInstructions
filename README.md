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

## Networking with Docker-Compose!

Next we're going to test networking using `localhost` on Windows. 

### Install Docker and Docker-Compose

First make sure you have docker, and docker-compose installed.

If you're running Ubuntu-18.04 you can use the script included in this repo by running:

`sudo ./installDockerUbuntu.sh`

### Run the app

Move into the dockerComposeTest folder and run the app:

```
cd dockerComposeTest
sudo docker-compose up --build
```

Once you see a green message saying 'done' you'll know it's ready.

### Connect to the sample sites

Open up Microsoft Edge and connect to https://localhost:7000 you'll see a message there that will prompt you to click on it to connect to another site: https://localhost:8000 . Please verify that both of these work and you're done!