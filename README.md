# All things Docker

## Installation

On Debian

Source: [https://docs.docker.com/engine/install/debian/](https://docs.docker.com/engine/install/debian/)

[https://www.youtube.com/watch?v=eGz9DS-aIeY](https://www.youtube.com/watch?v=eGz9DS-aIeY)

Remove old versions

```jsx
sudo apt-get remove docker docker-engine docker.io containerd runc
```

Install

```bash
sudo apt update && sudo apt upgrade
sudo apt-get install     apt-transport-https     ca-certificates     curl     gnupg     lsb-release -y
```

```bash
sudo echo \
  "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/debian \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

Install Docker container

```bash
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
```

Verify installation by running hello-world image

```bash
sudo docker run hello-world
```

### Other Docker commands

Check status of running containers

```bash
sudo docker stats
```

List containers

```bash
sudo docker container ls
```

Stop container (SIGSTOP)

```bash
sudo docker container stop arne
```

Kill container (SIGKILL)

```bash
sudo docker container kill arne
```

Run Command

```bash
sudo docker -i -t exec arne bash
```

Print the last 100 entries of a containers logs

```bash
sudo docker container logs --tail 100 arne
```

### Create new CentOs image

```bash
sudo docker pull centos
sudo docker run -d -t --name arne centos
```

### Create networkchuck web container

```bash
sudo docker pull thenetworkchuck/nccoffee:frenchpress
```

### Installing Docker Compose

Following [https://docs.docker.com/compose/install/](https://docs.docker.com/compose/install/)

```bash
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

sudo chmod +x /usr/local/bin/docker-compose
```

### OnlyOffice image for Nextcloud integration

Following: [https://github.com/ONLYOFFICE/docker-onlyoffice-nextcloud](https://github.com/ONLYOFFICE/docker-onlyoffice-nextcloud)

```bash
git clone https://github.com/ONLYOFFICE/docker-onlyoffice-nextcloud

cd docker-onlyoffice-nextcloud

docker-compose up -d

bash set_configuration.sh
```

Run it

```bash
sudo docker run -t -d -p 80:80 --name nccoffee thenetworkchuck/nccoffee:frenchpress
```

## Docker Guide

Thanks to Chris Titus

https://christitus.com/docker-guide/

https://www.youtube.com/watch?v=94VQvRpjfO8

Install and Getting Started
---------------------------

-   Official Docker: <https://docs.docker.com/get-docker/>
-   Official Portainer: <https://docs.portainer.io/start/install/server/docker>

Quick Commands
--------------

### Run a new container

-   New Image - `docker run IMAGE`
-   Name Container and Launch Image - `docker run --name CONTAINER IMAGE`
-   Map Container Ports and Launch Image -`docker run -p HOSTPORT:CONTAINERPORT IMAGE`
-   Map ALL Ports and Launch Image - `docker run -P IMAGE`
-   Launch Image as Background Service - `docker run -d IMAGE`
-   Map Local Directory and Launch - `docker run -v HOSTDIR:TARGETDIR IMAGE`

### Manage Containers

-   List RUNNING Containers - `docker ps`
-   List ALL containers - `docker ps -a`
-   Delete container - `docker rm CONTAINER`
-   Delete a Running Container - `docker rm -f CONTAINER`
-   Stop Container - `docker stop CONTAINER`
-   Start Container - `docker start CONTAINER`
-   Copy File FROM container - `docker cp CONTAINER:SOURCE TARGET`
-   Copy File TO container - `docker cp TARGET CONTAINER:SOURCE`
-   Start Shell inside container - `docker exec -it CONTAINER bash`
-   Rename container - `docker rename OLD NEW`
-   Create new Image from Container - `docker commit CONTAINER`

### Manage Images

-   Download Image - `docker pull IMAGE[:TAG]`
-   Upload Image to repository - `docker push IMAGE`
-   Delete Image - `docker rmi IMAGE`
-   List Images - `docker images`
-   Build Image from Docker file - `docker build DIRECTORY`
-   Tag Image IMAGE - `docker tag IMAGE NEWIMAGE:TAG`

### Troubleshooting and Information

-   Show logs - `docker logs CONTAINER`
-   Show stats - `docker stats`
-   Show processes - `docker top CONTAINER`
-   Show modified files - `docker diff CONTAINER`
-   Show mapped ports - `docker port CONTAINER`

---

## Commands used by others / random stuff
```bash
podman run -it --hostname twitch.tv --name ws ws-image
```
