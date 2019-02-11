---
title: Step 1: Requirements
taxonomy:
    category: docs
---

# Step 1: Requirements

## System Requirements
The GitPrime application runs many different processes in the background that are fairly resource intensive.  Because of this, we recommend the following system requirements for a bare-metal server or virtual machine:

- A minimum of 4 CPU cores, recommended 8 CPU cores or more
- A minimum of 8 GB of RAM, with a recommended amount of 16GB or more
- A minimum of 30 GB of disk space for the main system
- A directory (or mounted volume) on the host for repository data.  See Calculating Required Storage below.

We recommend running GitPrime Enterprise on Ubuntu Linux 16.04.x.  However, the on-premises version of GitPrime Enterprise can be run on other compatible operating systems that meet these criteria:

- Must be Linux-based
- Must be 64-bit
- Must have a kernel version of 3.10 or higher
- Must support Docker Enterprise 1.13.1-34 (and above) or Docker Community Edition 17.03.1-ce and above.

For more information about OS requirements, please see Replicated's list of requirements at https://www.replicated.com/docs/distributing-an-application/supported-operating-systems/.

## Calculating Required Storage

A minimum of 64 GB of storage is recommended for the repository work directory.  However, this is just a guess based on the average size of customer data.  To truly calculate how much storage you require, you should perform the following tasks:

- For each repository you intend to analyze with GitPrime, locate its current size
- Sum them all together
- Add 25% for growth

We strongly recommend that the directory used be something that can be easily exchanged or grown.  However, it does not need to be "permanent" storage.  It can be ephemeral.

## Database Requirements
GitPrime Enterprise requires a PostgreSQL database that meets the following specifications:

- Version 9.5.1 or higher but not version 10
- A minimum of 2 CPU cores, recommended 4 CPU cores or more
- A minimum of 8 GB of RAM

## Network Requirements
GitPrime Enterprise can be installed, and can function, without access to the Internet.  However, it is recommended that it be able to connect to port HTTPS/443 on external addresses for access to installer files during the install and later for updates.  This, obviously, could be scheduled to coincide with your maintenance schedules.  If you require the system to have no external Internet access, an airgapped installation can be achieved and maintained.

For data analysis, your GitPrime Enterprise system must have access to your Git repositories and your ticket system.  The following ports should be allowed to those instances:

- HTTP/80 and HTTPS/443: This should be the standard ports where your Git repository and ticket system server data for both Git data and API information.
- SSH:  Most Git vendors also allow for SSH download of the repositories they serve.  This is sometimes port 22 and sometimes port 7999 or a custom port.

For access to the system itself by your users, it also requires the following ports be open to internal users:

- HTTP/80: This must be open for internal health-check pings.
- HTTPS/443: This must be open for users to use the interface.
- HTTPS/8800: This port is used to reach the administration interface with a web browser.  It does not have to be open to general users, but must be available to system administrators.
- SSH/22: System administrators will need access to SSH on the server instance running GitPrime enterprise for occasional updates and maintenance.

##E-mail Server Requirements
To offer a full experience to users, GitPrime Enterprise requires that an SMTP server be provided.  This e-mail server and information is required for the system to function.  You must choose an e-mail server that meets the following criteria:

- It must be able to send e-mail from the e-mail you choose to use as the "From" address in system e-mails.
- It must be able to send e-mail to any users you intend to invite into the system.
- It must be able to be reached on the given hostname and port from your chosen server.
- It must not be a one-off installation of SendMail or Postfix on the local host server running the application.