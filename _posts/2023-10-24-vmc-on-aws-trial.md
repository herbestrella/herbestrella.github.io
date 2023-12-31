---
layout: post
title: vmc-on-aws-trial
date: 2023-10-24 12:00:00 -500
categories: [homelab,vmc-on-aws]
tags: [vmc,aws,vmware,vmc-on-aws] # TAG names should always be lowercase, separated by commas
---

# VMC-on-AWS-Trial

## Goals
- Successfully sign up for VMC on AWS Trial
- Create (VMC) SDDC

## Pre-requisites
- VMware Customer Connect Account 
    - [VMware Customer Connect](https://customerconnect.vmware.com/home)
- AWS Account
    - [AWS Free Tier](https://aws.amazon.com/free/?trk=fce796e8-4ceb-48e0-9767-89f7873fac3d&sc_channel=ps&ef_id=CjwKCAjwysipBhBXEiwApJOcu3i2DNJ0GD1-VOYKmPYjSW09SKIUfNGo7eccOgxgDD952ar4f-1n4RoC1AEQAvD_BwE:G:s&s_kwcid=AL!4422!3!592542020599!e!!g!!aws!1644045032!68366401852&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free%20Tier%20Types=*all&awsf.Free%20Tier%20Categories=*all)

## Trial Period (30 Days)

Sign up for the free trial, my assumption is that you will need a justifiable use-case. For me I have a registered company name with a matching domain name. When VMware reached out I gave them my justification and it was accepted! 30 Days of VMC on AWS!

You can signup for the trial period here: [VMC on AWS Trial Signup](https://www.vmware.com/products/vmc-on-aws/free-trial.html?src=ps_39szbtx12scfm&cid=7012H000000sxcfQAA&gclid=CjwKCAjwp8OpBhAFEiwAG7NaEqMhZTF94TyH7LWbsnJhaKYg30NIKXjPENGrWWMo7aRUP-5kpaEcxRoCv50QAvD_BwE&gclsrc=aw.ds)

Vendor Documentation regarding the trial: [VMC on AWS Trial Official Documentation](https://docs.vmware.com/en/VMware-Cloud-on-AWS/services/com.vmware.vmc-aws.getting-started/GUID-2844809E-3C4A-49D9-9068-191E6985CE5C.html)

Reference Architecture: [Getting Started with VMC on AWS Reference Architecture](https://www.vmware.com/content/dam/digitalmarketing/vmware/en/pdf/docs/vmw-getting-started-with-vmc-on-aws-reference-architecture.pdf)

Super helpful YouTube "Quick Start Series" [VMWare Cloud on AWS Quick Start](https://youtube.com/playlist?list=PLNOz1mVhDkG5JH3JqN1yPSfenGdizXqwh&si=sUJ7oUPVq6URgx_z)

If you have never used VMC on AWS and would like a primer, I highly suggest trying out the [VMware Cloud on AWS - Fundamentals - Hands-on Lab](https://customerconnect.vmware.com/en/evalcenter?p=vmc-aws-hol-gen-23)

![VMC on AWS Trial Email Response](/assets/images/vmc-trial.png)

## Networking

### On-prem Networks

| Name | Subnet | VLAN ID | Usable Addresses |
| ----- | ----- | ----- | ----- |
| Management | 10.120.0.0/16 | 10 | 10.120.0.1 - 10.120.255.254 |
| user-vlan-11 | 192.168.250.0/24 | 11 | 192.168.250.1 - 192.168.250.254 |

### VMC on AWS (example)

| Component | Value | Usable Addresses |
| ---- | ---- | ---- |
| AWS Region | us-east-1 | n/a |
| VPC Name | VMC-VPC | n/a |
| VPC CIDR Block | 10.100.0.0/21 | 10.100.0.1 - 10.100.7.254 |
| SDDC Name | SDDC-1-DAF1 | n/a |
| SDDC Management CIDR Block (default) | 10.2.0.0/16 | 10.2.0.1 - 10.2.255.254 |

### Create VPC Subnets as needed (example)

| Subnet Purpose | Availability Zone A | Availability Zone B |
| ---- | ---- | ---- |
| Private Subnet | 10.100.**0**.0/23 | 10.100.**2**.0/23 |
| Connected SDDC | 10.100.**4**.0/24 | 10.100.**5**.0/24 |
| Public Subnet | 10.100.**6**.0/24 | 10.100.**7**.0/24 |

## Create VPC

Login to your AWS account navigate to your VPC section; from here you'll want to click on "Create VPC"

Once completed you will have a VPC created that can be used with VMC on AWS; i.e. "VMC-VPC" **10.100.0.0/21**

![Create VPC](/assets/images/create-vpc.png)

### Create Subnets inside of the newly created VPC (VPC-VMC)

For my example since the trial only allows for a single AZ, the subnets I create are for the **Private Subnet** and **Public Subnet** show in the [VPC Subnets Table](https://github.com/herbestrella/learn-vmc-on-aws-things/blob/main/journal/VMC-on-AWS-Trial.md#create-vpc-subnets-as-needed-example)

![Create Subnets](/assets/images/create-subnets.png)

Once completed you will have created something similar to the below in your desired region.

![AWS Logical Network Diagram](/assets/images/aws-cloud-network-logical.png)

## Create SDDC

Now that you have your networking completed on AWS you will have everything you need to get started with your SDDC Build.

You can pre yourself further by going through the "View Journey Map" this will go through the quick start series YouTube videos and has clear instructions on how to get your SDDC installed and operational. Essentially it will guide you through creating a VPC and sort out the logistics (payment, etc).

![View Journey Map](/assets/images/SDDC-build-1.png)

When you're ready to build your SDDC you can click "Get Started"

From here you will need a enter some information:
- SDDC Name: **SDDC-1-DAF1**
    - I opted to go with something basic, my on-prem uses all lower case and so I thought this would be good opportunity to switch it up and go with CAPS to differentiate between the two.
- AWS Region: **US East (N. Virginia)
    - I'm in the east region so it's the logical choice for me.
- Deployment: **Single Host**
    - Trial allows for a single host only
- Host Type: I3 (Local SSD)
    - Trial allows for I3, I believe I could have selected I4 but went with the lowest option
-Number of Hosts: 1
    - Single Host option is all that is allowed for the Trial

The rest are pretty much defaults and no advanced configuration - click **Next**

![Getting Started](/assets/images/SDDC-build-2.png)

Assuming you're already signed into your AWS Console you click on **Open AWS Console with Cloudformation Template** if not you should have the opportunity to add credentials.

![Create SDDC](/assets/images/SDDC-build-3.png)

This is just a acknowledge before creating the stack, if you're good to go, check the box and click **Create Stack**

![Create SDDC](/assets/images/SDDC-build-4.png)

From here you will see an overview and stack should be created.

![Create SDDC](/assets/images/SDDC-build-5.png)

You should now be able to select the VPC and subnet you created earlier.

![Create SDDC](/assets/images/SDDC-build-6.png)

Management CIDR block, I left blank as it will take the default **10.2.0.0/16**

![Create SDDC](/assets/images/SDDC-build-7.png)

If everything is entered to your liking, you can now **Deploy SDDC**

![Create SDDC](/assets/images/SDDC-build-8.png)

The page will change to show you status of your SDDC Build

![Create SDDC](/assets/images/SDDC-build-9.png)

It's takes a couple of hours, this might have been close or over the 2hr mark

![Create SDDC](/assets/images/SDDC-build-10.png)

Once completed you will now be able to explore and start using your SDDC!

![Create SDDC](/assets/images/SDDC-build-final.png)

## Things To Do Next

- Add your on-prem public IP address to the NSX Firewall Rules for remote access to the vCenter
[Allow Access to SDDC vCenter over Public Internet](https://youtu.be/g9WdbCWVbYQ?si=FOqXU_YLThLj2WjJ)
- VPN Connectivity from your On-Prem Datacenter to your SDDC.
[Overview of Network Connectivity Options](https://youtu.be/y-Likfr6mxM?si=8bvBGtts6ArUsDRL)