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