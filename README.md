# Getting started with Docker

# install docker in ubuntu

```bash
sudo apt-get update

sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release

sudo mkdir -p /etc/apt/keyrings

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

echo \
"deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
$(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt-get update

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin

sudo docker run hello-world
```

# install docker-compose in ubuntu

```bash
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

sudo chmod +x /usr/local/bin/docker-compose

docker-compose --version
```

# Remove sudo from Docker

```bash
sudo groupadd docker

sudo usermod -aG docker $USER

newgrp docker

docker run hello-world
```

> **_'You successfully Installed the Docker!'_**

## Build the Docker

##### run the Command in the folder from cmd :

```bash
$ docker-compose build
```

expected output:

```
Successfully built xxxxxxxxxxxx
Successfully tagged docker_php:latest
```

#### run the Docker

```bash
$ docker-compose up
```

# Do below steps to run the project

1---> Create app folder in docker directory

2---> Provide 777 permission to app folder

3---> Create your project files in app folder

# phpmyadmin should run in localhost:8081

# project should run in localhost:8080
