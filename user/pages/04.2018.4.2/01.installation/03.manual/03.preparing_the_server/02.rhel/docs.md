---
title: RedHat Enterprise Linux
taxonomy:
    category: docs
---

GitPrime Enterprise only supports RedHat Enterprise Linux 7 and above.  We require this to insure that customers have the latest OS compatibility and security updates. 

To prepare RHEL 7 for installation of Docker, Replicated, and GitPrime Enterprise, it is recommended that you follow the steps outlined in this document.

## Install All Updates
It is recommended that you bring RHEL up to the latest set of updates before beginning.  This can be done with the command:

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

## Enable Extras Repository
For things to work smoothly, it is expected that you will also enable the "extras" repository for RHEL.  This can be done by executing the following command:

`
sudo yum-config-manager --enable rhel-7-server-extras-rpms
`

If you are in AWS, you will also need to execute:

`
sudo yum-config-manager --enable rhui-REGION-rhel-server-extras
`

Once you have enabled these repositories, you will need to update the yum cache appropriately:

`
sudo yum makecache fast
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