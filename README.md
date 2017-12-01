# Installation Guide

## INSTALL on Ubuntu 16 Latest
 
### Remove older version of Docker (Optional)
$ apt-get remove docker docker-engine 

### Update 
$ apt-get update

### Install the image extra *packages, which allows Docker to use the AUFS storage drivers
$ apt-get install -y linux-image-extra-$(uname -r) linux-image-extra-virtual

### Setup the repository 
#### The procedure for setting up the repository is different for Docker CE and Docker EE
#### Install packages to allow apt to use repository over HTTPS:

$ apt-get install -y apt-transport-https ca-certificates curl software-properties-common

### Add Docker's official GPG key
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

### Verify that the key fingerprint is 9DC8 5822 9FC7 DD38 854A E2D8 8D81 803C 0EBF CD88.
$ apt-key fingerprint 0EBFCD88

### Use the following command to set up the stable repository. You always need the stable repository, even if you want to install edge builds as well.

$add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

### INSTALL DOCKER 
### 1. Update the apt package index by using the below command:
$ apt-get update -y 

### 2. Install the latest version of Docker, or go to the next step to install a specific version. Any existing installation of Docker is replaced. Use this command to install the latest version of Docker:
$ apt-get install -y docker-ce


### Verify Installation

$ docker run hello-world 
Unable to find image 'hello-world:latest' locally Pulling repository 
hello-world 91c95931e552:
Download complete a8219747be10: 
Download complete Status: 
Downloaded newer image for hello-world:latest Hello from Docker. 
This message shows that your installation appears to be working correctly.

## Docker on Centos 7 
### Uninstall Old versions (Optional)
$yum remove docker docker-common docker-selinux docker-engine

### Setup Repository 
$ yum install -y yum-utils device-mapper-persistent-data lvm2

### Configure Stable repository 
$ yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
$ yum-config-manager --enable docker-ce-stable

### INSTALL DOCKER CE
$ sudo yum install docker-ce
$ systemctl start docker
$ docker run hello-world  


## UB 


#!/bin/bash
apt-get update -y
apt-get install -y linux-image-extra-$(uname -r) linux-image-extra-virtual
apt-get install -y apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
apt-key fingerprint 0EBFCD88
add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
apt-get update -y 
apt-get install -y docker-ce
echo "done"

## Centos

#!/bin/bash
echo "starting installation , This installation requires internet connectivity"
yum install -y yum-utils device-mapper-persistent-data lvm2
yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
yum-config-manager --enable docker-ce-stable
yum -y install docker-ce
systemctl start docker
systemctl enable docker
docker --version
echo "Installation completed"







