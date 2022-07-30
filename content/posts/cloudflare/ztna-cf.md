+++
author = "talzcloning"
title = "How to Implement Zero Trust Network Access (ZTNA) using Cloudflare"
date = "2022-07-24"
description = "A brief description of Hugo Shortcodes"
toc = "true"
tags = [
    "cloudflare",
    "zero trust",
    "ztna",
]
thumbnail = "images/ztna/ztna-cf.png"
+++

# Introduction

Zero Trust Network Access (ZTNA) technologies have been hailed as the future of security. ZTNA creates a perimeter around an application and blocks all unauthorised traffic. 
This guide will show you how to implement a clientless VPN for your web apps.


# Prerequisites

1. Cloudflared running in Debian.
2. IIS Webserver
3. Cloudflare access account

## Zero Trust Architecture

![](/images/ztna/ztna-cf.png)

# How to Implement Zero Trust using Cloudflare


### 1. Navigate to [Cloudflare](https://dash.cloudflare.com/login).

### 2. Enter you Email and Password.

![](/images/ztna/login-to-cloudflare.png)

### 3. Type "your@email.com"

### 4. Click "Zero Trust"

![](/images/ztna/cf-zero-trust.png)

### 5. Click "Access"

![](/images/ztna/cfzt-access.png)

### 6. Click "Create a tunnel"

![](/images/ztna/cfzt-tunnel.png)

### 7. Click the "Tunnel name(Required)" field.
#### Type "CF-Tunnel" as Tunnel name

#### Click "Save tunnel"

![](/images/ztna/cfzt-createtunnel.png)

###  8. Click Debian as the operating system.

![](/images/ztna/cfzt-debiancf-tunnel.png)

### 9. Click Copy icon to install in Cloudflare connector.

![](/images/ztna/cfzt-cloudconnector.png)

###  10. Click "Next"


###  11. Click domain.
#### Click "zerotrustmodel.org"
#### Click the "Subdomain" field.
#### In subdomain type iis and domain. Click "Select..."
#### Select "HTTP"
#### Click the "Public hostname(Required)" field.
#### Type "192.168.133.11" for Web Apps server
#### Click "Save CF-Tunnel tunnel"

![](/images/ztna/cf-public-hostname.webp)


### 12. Navigate back to access then tunnel.

###  13. Click "Configure"

![](/images/ztna/cfzt-configure.png)

###  14. Click "Private Network"

![](/images/ztna/cfzt-privatenet.png)

### 15. Click "Add a private network"

![](/images/ztna/cfzt-addprivatenet.png)

### 16. Click the "CIDR(Required)" field.
#### Type IIS server IP and Click "Save private network"

![](/images/ztna/cfzt-cidr.png)

### 17. Click "Add a private network" again.

![](/images/ztna/cfzt-addagain.png)

### 18. Type cloudflared server IP and Click "Save private network"

![](/images/ztna/cfzt-saveprivate.png)

### 19. Click "Overview"

![](/images/ztna/cfzt-overview.png)

### 19. Try access https://iis.zerotrustmodel.org/ will redirect to zero trust.