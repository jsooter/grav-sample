---
title: Step 3: Preparing the Server
taxonomy:
    category: docs
---

We highly recommend that you create or provision a brand new server or virtual machine for GitPrime Enterprise.  The analysis of repositories can, sometimes, be very resource intensive and it becomes much harder to debug issues.  We have also noticed that many people who try and run other processes and applications on the same instance run into large issues with port and network conflicts.

Once you have created the server or virtual machine for hosting GitPrime Enterprise, you need to perform a few basic steps.

## Perform Updates
It is important to make sure that your operating system has the latest updates.  Having the latest kernel, system packages, and drivers will help insure that Replicated and GitPrime Enterprise function at their best.  You should perform these updates according to your organization's update and approved package standards.

## Install Security Patches
Security is important to us and to our users.  We highly recommend that you also install any system security patches and updates that your OS maintainer recommends for your OS version.  This, also, should be done according to your organizations standards for updating and approved packages.

## Provision the IP Address and DNS Name
GitPrime Enterprise requires that it utilize a DNS name pointed at the IP address of the machine.  You should prepare a DNS hostname that you will be using.  For example, gitprime.mycompany.com.  Make note of the IP address of the server and point the DNS name you prepared to this IP address.

If your servers use dynamic addressing, you will need to associate the DNS with the serve according to your IT organization's standard practices.

## Allow Access to the Proper Ports
GitPrime Enterprise requires three ports open to web browsers to function correctly:

- HTTP/80:  The regular non-TLS web request port.
- HTTPS/443:  The TLS/SSL enabled web request port.
- HTTPS/8800: This port is for the HTTPS traffic for the replicated administration console.

Additionally, it is wise to open the following, at least during installation and troubleshooting:

- SSH/22:  You must also open a port for SSH access for your system administrators.  This may not be port 22, but you should make sure this is done according to standard company IT policies.

>>> We have had several users try and forward port 80 to 8800 because their regular ACLs don't allow port 8800 for traffic. You **MUST NOT** do this.  Forwarding port 80 using iptables or other means will cause problems.

## Preparing the Storage Directory
GitPrime does not permanently store your repository data.  In the cloud version, we do not keep it even in memory for any longer than we require.  However, in the Enterprise product, we are secure behind your firewall and infrastructure security.  In this case, we allow for a cache directory to keep repositories around for up to 48 hours.  This helps take significant weight off your source control server and GitPrime Enterprise's use of server resources.

During the installation, you will be asked to provide the path to the directory you wish to use for this purpose.  As stated in the "Requirements" section, this should be enough space to properly contain your repositories.  During the preparation phase, we recommend:

- Create and attach the appropriate storage.
- Format it as ext3 or ext4.
- Mount it at the path you wish to use.
- Make sure that the permissions mode is 0755 or rwxr-xr-x
- Write down this path for later use in the installation.

## Operating System Specific Steps
For some operating systems, there are also some steps that must be performed outside the regular preparation steps.  Please see the following guides for more information:

- Ubuntu 16.04 and above
- RedHat Enterprise Linux 7 (and above)
- CentOS 7 (and above)