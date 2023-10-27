---
layout: post
title: build-ubuntu-vsphere-image-with-packer
---
I wanted to get into K8s and needed a better way to deploy Ubuntu Servers. William Lam to the rescue. I learn so much from him it's crazy. I ended up switching gears and using Proxmox but this was still a valuable nugget.

[Building a custom Ubuntu image using Packer Examples for VMware vSphere project](https://williamlam.com/2023/04/building-a-custom-ubuntu-image-using-packer-examples-for-vmware-vsphere-project.html)

Pretty much followed it exactly, but here are some changes I made to make it work for me.
- DHCP; I needed the machines to pick up an address and it worked just fine (DHCP is configured from my Palo Alto) but during the cloud init process it reboots causing a new IP to be leased - I briefly attempted reservations and modifying lease times but to no avail - I ended up using a segment in NSX-T that had DHCP and that worked as intended.

- Using a different version of Ubuntu that on the blog post 22.04.3 so you'll need to update accordingly (iso name/location)

