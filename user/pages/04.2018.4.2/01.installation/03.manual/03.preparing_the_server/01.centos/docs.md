---
title: Centos
taxonomy:
    category: docs
---

GitPrime Enterprise only supports CentOS 7 and above.  We require this to insure that customers have the latest OS compatibility and security updates. 

To prepare CentOS 7 for installation of Docker, Replicated, and GitPrime Enterprise, it is recommended that you follow the steps outlined in this document.

## Install All Updates
It is recommended that you bring CentOS up to the latest set of updates before beginning.  This can be done with the command:

`
sudo yum update -y
`

After installing updates, it is recommended that you reboot the system, as there may have been kernel-level updates installed.

## Install Dependencies
For the installation script to go smoothly, it is recommended that you install the following packages:

- yum-utils
- device-mapper-persistent-data
- lvm2

This can be done by running this command:

`
sudo yum install -y \
   yum-utils \
   device-mapper-persistent-data \
   lvm2
`

## Remove Older Docker Installations
If you have previously installed docker on the server, it is recommended that you remove it.  This can be done by running the commands:

`
sudo yum remove \
   docker \
   docker-common \
   docker-selinux \
   docker-engine-selinux \
   docker-engine
`