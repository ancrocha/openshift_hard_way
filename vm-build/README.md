# Building VMs

This section is dedicated for the build of the virtual machines required for the openshift environment.

We are going to build the following VMs:


| Hostname                 | Function               | CPU | Memory | Storage | Image        | Network        | IP address               |
|--------------------------|------------------------|-----|--------|---------|--------------|----------------|--------------------------|
| ocp-bastion.ocp.lan      | Offline Registry/Proxy | 4   | 8192   | 500     | Ubuntu 24.04 | ocp + external | 192.168.1.10, 10.0.0.36  |
| ocp-tools.ocp.lan        | DHCP+NTP               | 1   | 4096   | 32      | Ubuntu 24.04 | ocp            | 192.168.1.5              |
| ocp-dns.ocp.lan          | DNS                    | 1   | 4096   | 32      | Ubuntu 24.04 | ocp            | 192.168.1.6              |
| ocp-lbexternal.ocp.lan   | External LB            | 1   | 2048   | 32      | Ubuntu 24.04 | ocp + external | 192.168.1.6, 10.0.0.35   |
| ocp-bootstrap.lab.ocp.lan| bootstrap              | 4   | 16384  | 50      | Rhcos-4.18.1 | ocp            | 192.168.1.200            |
| ocp-cp-1.lab.ocp.lan     | Control plane          | 8   | 16384  | 50      | Rhcos-4.18.1 | ocp            | 192.168.1.201            |
| ocp-cp-2.lab.ocp.lan     | Control plane          | 8   | 16384  | 50      | Rhcos-4.18.1 | ocp            | 192.168.1.202            |
| ocp-cp-3.lab.ocp.lan     | Control plane          | 8   | 16384  | 50      | Rhcos-4.18.1 | ocp            | 192.168.1.203            |
| ocp-w-1.lab.ocp.lan      | Worker Node            | 4   | 8192   | 50      | Rhcos-4.18.1 | ocp            | 192.168.1.204            |
| ocp-w-2.lab.ocp.lan      | Worker Node            | 4   | 8192   | 50      | Rhcos-4.18.1 | ocp            | 192.168.1.205            |
| ocp-w-3.lab.ocp.lan      | Worker Node            | 4   | 8192   | 50      | Rhcos-4.18.1 | ocp            | 192.168.1.206            |


## Downloading the ISO images
Bellow the necessary images for our openshift build: 

[Ubuntu 24.04](https://ubuntu.com/download/server)  - I selected Ubuntu due to the easy of use and the number of available tutorials.

[Rhcos-4.18.1-x86_64-live.x86_64.iso](https://mirror.openshift.com/pub/openshift-v4/dependencies/rhcos/4.18/4.18.1/rhcos-4.18.1-x86_64-live.x86_64.iso) - This is an immutable OS ideal for container load and recommended for openshift installation.


## Loading the image into proxmox
* On the proxmox server, select the disk where the image will be stored.
* Select ISO Images.
* Click on Upload.

![Upload Image](images/upload_image_1.jpg)


* Select the location of the file and upload it to proxmox server.

![Upload Image](images/upload_image_2.jpg)
