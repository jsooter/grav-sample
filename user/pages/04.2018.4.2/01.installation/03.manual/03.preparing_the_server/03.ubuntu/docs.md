---
title: Ubuntu
taxonomy:
    category: docs
---

GitPrime Enterprise only supports Ubuntu version 16.04 and above.  This release is a Long Term Support (LTS) release.  We require this to insure that customers have the latest OS compatibility and security updates. 

To prepare Ubuntu for installation of Docker, Replicated, and GitPrime Enterprise, it is recommended that you follow the steps outlined in this document.

## Install All Updates
It is recommended that you bring Ubuntu up to the latest set of updates before beginning.  This can be done with the command:

`
sudo apt-get update
sudo apt-get dist-upgrade -y
After installing updates, it is recommended that you reboot the system, as there may have been kernel-level updates installed.
`

## Install Dependencies
For the installation script to go smoothly, it is recommended that you install the following packages:

- apt-transport-https
- ca-certificates
- curl
- software-properties-common

This can be done by running this command:

`
sudo apt-get install -y \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common
`

## Remove Unneeded Packages
After updates have completed and you have rebooted, you should also remove any unneeded packages.  This can be accomplished by running the command:

`
sudo apt-get autoremove -y
`

## Remove Older Docker Installations
If you have previously installed docker on the server, it is recommended that you remove it.  This can be done by running the commands:

`
sudo apt-get remove -y docker docker-engine docker.io
`