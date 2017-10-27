# Hyperledger Setup on Mulit Node/Host
Step by step guide to setup hyperledger fabric with multi-node/multi-host  in Ubuntu 16.04

# Scope
Install & configure pre-requisites, software and deploy the sample fabric-network/first-network in the environment and test the setup using the CLI.

### Important points before starting the installation

1. Docker installation and configuration can be skipped if you have docker installed.
2. Do not use ** root ** user!
3. Do not change folder and file permissions unless otherwise specified
4. Ubuntu installation is not covered.

## Starting with pre-requisites.

### List docker services installed and running
```
netstat -an | grep docker
```
### Stop the docker service
```
sudo service docker stop
```
### Make sure the docker service is stopped
```
netstat -an | grep docker
```

### The followings commands will remove/uninstall docker from ubuntu
```
sudo apt-get purge -y docker-engine
sudo apt-get autoremove -y --purge docker-engine
sudo apt-get autoclean
sudo apt-get purge -y docker-engine docker docker.io docker-ce
sudo apt-get autoremove -y --purge docker-engine docker docker.io docker-ce
sudo rm -rf /var/lib/docker
```
Now we have successfully uninstalled docker.

## Install docker using the following steps

### First setup docker repository

1. Update the apt package index:
```
sudo apt-get update
```

2. Install packages to allow apt to use a repository over HTTPS:
```
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common
```

3. Add Docker’s official GPG key:
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

4. Use the following command to set up the stable repository

### amd64
```
  sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
```
### Install Docker Now
1. Update the apt package index.
```
sudo apt-get update
```

2. Install the latest version of Docker CE
```
sudo apt-get install docker-ce
```

3. Verify that Docker CE is installed correctly by running the hello-world image
```
sudo docker run hello-world
```
### Post install Steps for docker

1. Create the docker group.
```
sudo groupadd docker
```

2. Add your user to the docker group.
```
sudo usermod -aG docker $USER
```

3. Verify that you can run docker commands without sudo
```
docker run hello-world
```

## Create the following folder structure
```
mkdir -p go/src/github.com/hyperledger
mkdir -p go/src/github.com/<< github id >> //Substitute your github id here
mkdir -p go/bin
mkdir -p go/pkg
```

## Install Fabric sample
```
git clone https://github.com/hyperledger/fabric-samples.git

cd farbric-samples

sudo curl -sSL https://goo.gl/Q3YRTi | bash

cd first-network
```

### Export Path
```
export  PATH=./:../bin:$PATH
```
### Running the byfn.sh (Building Your First Network script)
```
cd go/src/github.com/hyperledger/fabric-samples/first-network
./byfn.sh -m up
```
### Once you see the my-network deployed and the chain code run successfully, issue the following command
```
./byfn.sh -m down

```

# Configuring the Multi-host setup

In progress...


# Conclusion
