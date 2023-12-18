---
layout: post
title: hcx-deployment
---

Link to vmware cloud gateway
HCX 

Make sure you have a valid key or the plugin won't download
DNS Settings
- resolve hosts
- resolve vCenter
- resolve dns/ad
- Public IP addresses (enough of them)

service mesh
- do not have your uplink network advertised via BGP
- vmotion needs internet access otherwise ovf uploads may fail to deploy appliances
- nothing special with management
- ensure all hosts resolve properly - I inadvertently put a incorrect dns entry for a host causing it fail


[Requirements for Network Extension](https://docs.vmware.com/en/VMware-HCX/4.7/hcx-user-guide/GUID-0C746416-850E-46F7-85DD-4D4326A23785.html)

[Create an Identity Source for SDDC](https://docs.vmware.com/en/VMware-Cloud-on-AWS/services/com.vmware.vsphere.vmc-aws-manage-data-center-vms.doc/GUID-D3547C4A-64CF-4DFE-844E-400622EAF1E5.html)

[Link VMware Cloud Gateway to SDDC](https://docs.vmware.com/en/VMware-Cloud-on-AWS/services/com.vmware.vsphere.vmc-aws-manage-data-center-vms.doc/GUID-57D1E4C1-926F-4F01-A223-5EF174D8F1AF.html)

[Add Identity Source to On-Prem](https://docs.vmware.com/en/VMware-vSphere/8.0/vsphere-authentication/GUID-B23B1360-8838-4FF2-B074-71643C4CB040.html)

[Route Redistribution PA](https://www.reddit.com/r/paloaltonetworks/comments/w7y3sb/local_rib/)

[HCX Ports](https://ports.esp.vmware.com/home/VMware-HCX)

[Troubleshooting HCX](https://www.m80arm.co.uk/2020/10/troubleshooting-hcx-connectivity-and.html)

[More Troubleshooting HCX](https://www.provirtualzone.com/hcx-ix-appliance-tunnel-down-service-mesh-service-pipeline-status-is-down/)

[Slow Migrations or Tunnel DOWN!!](https://kb.vmware.com/s/article/83178)

[VMware Cloud Services Status](https://status.vmware-services.io/)

[DNS ZONES](http://www.patrickkremer.com/vmc-on-aws-vpn-dns-zones-ttls/)

[HCX Service Mesh Deployment Fails - no IPs](https://kb.vmware.com/s/article/83106)

[migrate vm with hcx](https://docs.vmware.com/en/VMware-HCX/4.7/hcx-user-guide/GUID-14D48C15-3D75-485B-850F-C5FCB96B5637.html)