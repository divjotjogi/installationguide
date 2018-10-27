# Guide for making platform ready to Learn Docker
## Open or controlled Internet access to below sites.
- https://www.virtualbox.org/wiki/Downloads
- http://isoredirect.centos.org/centos/7/isos/x86_64/CentOS-7-x86_64-Minimal-1804.iso
- https://download.docker.com
- https://hub.docker.com/
- https://docker.io
- http://mirror.centos.org/centos/
- http://mirror3.ubuntulinux* 
## Hardware Minimum : 1 Host (Laptop/system) with 4 GB Ram and 2 CPUs.
1. Download and Install hypervisor to run multiple operating systems on your Laptop. Virtual box virtulisation comes for    flavour windows, Linux and Mac-OS.


# Download and Install Virual Box For virtualization  
https://www.virtualbox.org/wiki/Downloads

2. Download operating system ISO to deploy VMs.Ubuntu is preferred, Though Centos 7 is a good alternative.

# Ubuntu ISO download 
https://www.ubuntu.com/download/server

# Centos Minimal ISO download
http://isoredirect.centos.org/centos/7/isos/x86_64/CentOS-7-x86_64-Minimal-1804.iso

3. Docker Installation Guide

## INSTALL on Ubuntu Latest

### NEW Installation


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



## Below are the plain shell scripts for both ubuntu and centos OSes in case you would like to automate the installation piece. Basic knowledge of shell scripting is required though. 
## UB 


#!/bin/bash <br />
apt-get update -y <br />
apt-get install -y linux-image-extra-$(uname -r) linux-image-extra-virtual <br />
apt-get install -y apt-transport-https ca-certificates curl software-properties-common <br />
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add - <br />
add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" <br />
apt-get update -y <br /> 
apt-get install -y docker-ce <br />
echo "done Installation completed" <br />

## Centos

#!/bin/bash <br />
echo "starting installation , This installation requires internet connectivity" <br />
yum install -y yum-utils device-mapper-persistent-data lvm2 <br />
yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo <br />
yum-config-manager --enable docker-ce-stable <br />
yum -y install docker-ce <br />
systemctl start docker <br />
systemctl enable docker <br />
docker --version <br />
echo "Installation completed" <br />








