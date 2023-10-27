---
layout: post
title: deploy-app-to-TKC-using-embedded-harbor-registry
---

# Goals

The main reason to perform this type of scenario is to use the embedded harbor registry as my main source for container images. I can already natively leverage the harbor registry with vSphere Pods and now I want to extend it to my TKC (Tanzu Kubernetes Clusters). The desired end result will be accessing the widely used “yelb” application deployed to the TKC via the Laptop.

If you have made it this far we are going to assume the following:
- vSphere with Tanzu (Workload Management) is enabled and operational
- Networking within the environment specific to “Workload Management” is fully functional via NSX-T
- A namespace is created with the minimum
    - Permissions (example: user@vsphere.local has edit permissions on the namespace)
    - Storage - Storage Policy is assigned
    - VM Service - has the appropriate VM Classes
        - best-effort-small
        - best-effort-xsmall
    - A TKC Cluster is deployed
- Pod Security Policy is applied
- Ubuntu VM (a.k.a. Developer Workstation)
    - Ability to obtain the necessary container images and download locally (internet access)
    - Ability to create Yaml files created associated with deploying the application (IDE)
    - Kubectl
    - docker credential helper