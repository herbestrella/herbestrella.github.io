---
layout: post
title: install-vmware-cloud-gateway-for-hybrid-cloud-management
date: 2023-11-27 12:00:00 -500
categories: [homelab,vmc-on-aws,vmware-cloud-gateway]
---

## Goals

Setup the **VMware Cloud Gateway** to view On-Prem and VMC on AWS vCenters at the same time.

## Prerequisites

Make sure you have Active Directory
- I setup a new Domain and DNS server
- Make sure your internal DNS is setup properly
- I had to setup a DNS proxy on my Palo Alto to resolve my local domains addresses 
- Add DNS to your VMC on AWS NSX
- Add the FQDN Zone to your DNS Gateways in (VMC on AWS) NSX
- Verify connectivity in troubleshooting section of VMC on AWS Console
    - Resolve all and ensure they are green, in my setup one of hosts had an issue with port 902 and I only had a single DNS server, but it still worked. 

## Setup

Download the ISO from [VMware Customer Connect](https://customerconnect.vmware.com/home)

Run the UI-Installer
- Add the ISO (to my Ubuntu VM in Fusion)
- ```sh
    cd /media/<name>/'VMware VCGW'/ui-installer/lin64 #path to install

    ./installer #command to run installer
    ```
- Add the values for your on-prem environment, vCenter, SSO Admin, SSO Password, etc.
- Once completed you can now browse to your VMware Cloud Gateway VM using a modern browser
    - note: I had some issues with the browser I was using for this appliance and had to try different flavors/versions as the page didn't load all the way.
    - Use root credentials ![Login Page](/assets/images/vcgw-hlm-01.png) 
    - Select Enable Hybrid Management ![HLM enable](/assets/images/vcgw-hlm-02.png)
    - Enter your information ![variables](/assets/images/vcgw-hlm-04.png)
    - Cloud vCenter can be retrieved from settings of your SDDC
    - On-premises SSO (this takes some time) ![on-prem](/assets/images/vcgw-hlm-05.png)
    - Skipped Active Directory as it was optional and Access to Cloud vCenter I left alone as well, then clicked configure.
        - **This method did not work** as I had to have consistency with from an auth standpoint from VMC to On-Prem - in addition I wasn't able to get the VMC on AWS vCenter to show up in the Cloud Gateway, I ended up setting up the following:
            - On-Prem domain controller
            - Dns zone in NSX on the VMC on AWS
            - Adding AD Auth to the On-Prem vCenter and then the VMC on AWS vCenter, dns, dns-proxy on the PA, ensuring all the fw ports were open accordingly 
    - When successful you login it your VMware Cloud Gateway via a modern brower and both On-Prem and VMC on AWS vCenters will be displayed ![vcloud gw](/assets/images/cloud-gateway-1.png)

Helpful Links
[Quick Start Series Video on HLM](https://www.youtube.com/watch?v=P5uHzqa4n44
)