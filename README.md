# hyperledger-setup
Step by step guide to setup hyperledger fabric first-network in ubuntu 16.04

# Scope
Install & configure pre-requisites, softwares and deploy the sample fabric-network/first-network in the environment and test the setup using the cli.

# Important point before starting the installation

1. Docker installation and configuration is not covered.
2. User permissions and user accounts are not covered.
3. Folder and file permissions are not covered.
4. Ubuntu installation is not covered.

#Starting with pre-requisites.


1  sudo ls -la /root
2  exit
3  pwd
4  ls

List docker services installed and running
netstat -an | grep docker

Stop the docker service
sudo service docker stop

Make sure the docker service is stopped
netstat -an | grep docker

The followings commands will remove/uninstall docker from ubuntu
sudo apt-get purge -y docker-engine
sudo apt-get autoremove -y --purge docker-engine
sudo apt-get autoclean
sudo apt-get purge -y docker-engine docker docker.io docker-ce
sudo apt-get autoremove -y --purge docker-engine docker docker.io docker-ce
sudo rm -rf /var/lib/docker

Now we have successfully uninstalled docker.

Install docker using the following steps.

First setup docker repository

1. Update the apt package index:

sudo apt-get update

2. Install packages to allow apt to use a repository over HTTPS:

sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common

3. Add Docker’s official GPG key:

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

4. Use the following command to set up the stable repository

#amd64
  sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"

Install Docker Now
1. Update the apt package index.

sudo apt-get update

2. Install the latest version of Docker CE

sudo apt-get install docker-ce

3. Verify that Docker CE is installed correctly by running the hello-world image

sudo docker run hello-world
