---
title: "How to install ACME client protocol"
thumbnail: "/images/acme-ssl-cert.png"
date: 2022-07-24
toc: true
draft: false
categories: ["acme"]
tags: ["automation", "ssl"]
description: "ACME is a protocol to automate the issuance and renewal of certificates ."
slug: "/notes/how-to-install-acme-client-protocol/"
---
## 1. How to install Acme using Git

Please provide a valid email address.

```bash
git clone https://github.com/acmesh-official/acme.sh.git
cd acme.sh
./acme.sh --install --accountemail "security@example.com"
source ~/.bashrc
cd
```


## 2. Issue SAN Certs using Standalone validation with acme.sh 

```bash
acme.sh --issue --standalone -d example.com -d www.example.com --ocsp-must-staple --keylength 2048
```
## 3. Issue SAN Certs using Webroot validation with acme.sh 
```bash
acme.sh --issue -d example.com -d www.example.com --webroot /var/www/_letsencrypt --reloadcmd "sudo systemctl reload nginx.service" --ocsp-must-staple --keylength 2048
```
## 4. Issue Wildcard Certs using DNS API validation with acme.sh 

```bash
acme.sh --issue --dns dns_cf -d example.com -d '*.example.com' --ocsp-must-staple --keylength 2048
```

## 5. Display all the certs.

```bash
acme.sh --list
```
## 5. Create folder for the certs.
```bash
mkdir -p /etc/acmeprovider/example.com
```
## 6. Copy the certificates to the proper location
Make sure to change out example.com for your domain
```bash
acme.sh --install-cert
    --domain example.com
    --cert-file /etc/acmeprovider/example.com/cert.pem
    --key-file /etc/acmeprovider/example.com/key.pem
    --fullchain-file /etc/acmeprovider/example.com/fullchain.pem
```
You’ll then need to install them in the proper location for your web server