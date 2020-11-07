# Run Unreal Tournament 99 windows files on linux
Quite totally taken from https://github.com/zedr/docker-unreal-tournament-99 \
Just reshaped to be used with docker-compose \
Thanks a lot, I've been stuck a moment on the server configuration

## Install docker and docker compose for ubuntu

Install curl

```sudo apt update && sudo apt upgrade```

```sudo apt install curl```

Install docker 

```sudo apt-get remove docker docker-engine docker.io containerd runc```

```
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
```

```curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add - ```

``` 
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable" 
```

Install the docker engine

``` sudo apt-get update ```

``` sudo apt-get install docker-ce docker-ce-cli containerd.io ```

Install docker compose

```sudo curl -L "https://github.com/docker/compose/releases/download/1.26.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose ```

``` sudo chmod +x /usr/local/bin/docker-compose```

## Commands to launch the program

Before, give access to graphical interface

``` xhost +"local:docker@" ``` 

Then, change the docker-compose.yml file to set the path of your UT folder. Change the volume line in the ut99 service.
Mine is "/media/millet/Backup Windows/2017_09_17 Archives/Jeux/Jeux reseaux (7Go)/UnrealTournament", which is the same folder on an usb key than the one used on windows. it worls tolally and is useful to keep saved progression.

Run game, launch servers and containers

``` docker-compose up -d``` 

Terminate containers

``` docker-compose down``` 

Set brightness back

``` /usr/bin/xgamma -gamma 0.9 ``` 

Sound problem - not solved yet


## File architecture


```
IBM
|-- readme.md
|-- docker-compose.yml
|-- dockerfiles
|-- |-- wine_ut99_dockerfile
|-- |-- wine_ut99_server_dockerfile
|-- docker-volumes
|-- |-- ut99
|-- |-- |-- UnrealTournament.ini

Somewhere else
UnrealTournament
```
