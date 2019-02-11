---
title: Step 2: Before You Begin
taxonomy:
    category: docs
---

## Choose a Hostname
This will be the fully qualified domain name (FQDN) used to access the server where GitPrime Enterprise is installed.  This should be something that can be pointed to the server directly or to a load-balancer, if you choose to use one.

For example, if you choose gitprime.mycompany.com, the system will be available to users at https://gitprime.mycompany.com.

For information on registering a domain name in AWS Route53 see: https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/registrar.html

>>>>> Trial Tip: GitPrime Enterprise can be installed even if you have not setup a hostname, however, GitPrime Enterprise cannot be fully configured without a valid hostname (FQDN).

## Purchase or Generate TLS/SSL Certificates
GitPrime Enterprise requires that you have TLS/SSL certificates to function.  This is for security purposes and is configured through the administration console.

It is recommended that you purchase certificates for this specific purpose.  For example, if you chose gitprime.mycompany.com for your hostname, you should purchase an TLS/SSL certificate for that hostname.  However, you are also welcome to do self-signed certificates.  This is especially useful if you are a large organization with your own certificate authority. It is also acceptable to utilize wildcard certificates.  For example, a wildcard certificate for *.mycompany.com would work fine for gitprime.mycompany.com.

>>> At this time wildcards are not supported in the Subject Alternative Name (SAN) section of the certificate. 

For more information on obtaining certificates, please see "Obtaining Certificates".

Regardless of how you obtain them, you will need to do some preparation on the certificates prior to uploading them to the server.  Replicated's console, and GitPrime, both used a "combined" certificate format for handling intermediate certificates.  To prepare, you will need the following:

- The private key, with no password, used to generate the certificate in PEM format
- The certificate itself in PEM format
- Any intermediate certificates, in PEM format.
- The root trusted authority certificate, if using an internally signed certificate, in PEM format. 

>>>>> Tip: Certificates should always be in base64 (plain text) format and never DER format.

Once you have gathered the certificates, you must assemble them into a file. This file is called a certificate bundle. Add the certificate contents to the file in this order:

- The certificate
- Any intermediate certificates
- The root trusted authority certificate

The resulting file (certificate bundle) will look something like this if you have intermediate certificates:

`
-----BEGIN CERTIFICATE----- 
(Your Primary SSL certificate: server.crt) 
-----END CERTIFICATE----- 
-----BEGIN CERTIFICATE----- 
(Your Intermediate certificate: DigiCertCA.crt) 
-----END CERTIFICATE----- 
-----BEGIN CERTIFICATE----- 
(Your Root certificate: TrustedRoot.crt) 
-----END CERTIFICATE-----
`

If you do not have intermediate certificates, you will simply need a certificate file that contains your certificate.  That file will look like:

`
-----BEGIN CERTIFICATE----- 
(Your Primary SSL certificate: server.crt) 
-----END CERTIFICATE----- 
`

## Find Your E-mail Server
GitPrime Enterprise requires an e-mail server so that it can send e-mails to your users.  Before you do the installation, you should gather the following data:

- The hostname, port, username, and password for an SMTP server that can send e-mail to your users.
- Choose an e-mail address that you want system e-mails to come from and provision it with your main provider.  For example, if you choose gitprime@mycompany.com, users will see that e-mail address on all e-mails from the system.

**PLEASE NOTE:**  This e-mail server and information is required for the system to function.  You must choose an e-mail server that meets the following criteria:

- It must be able to send e-mail from the e-mail you choose to use as the "From" address in system e-mails.
- It must be able to send e-mail to any users you intend to invite into the system.
- It must be able to be reached on the given hostname and port from your chosen server.
- It must not be a one-off installation of SendMail or Postfix on the local host server running the application.