## Proxmox
Proxmox VE is an open source bare-metal hypervisor for virtual machines and containers, similar to ESXi, that runs on Linux.  

I tested and had was able to run Proxmox VE 4.4 inside VirtualBox 5.1 and VMWare Workstation 12.

## Setting up the host VM machine

I had major issues with networking, machine could not get an IP so no internet access. This is required if you want to download templates for machines. I found that this was related to the OS I chose when initially creating the machine i.e. even before getting to the part of installing the actual OS. 

VirtualBox: Other/Unknown(64-bit)  
VMWare Workstation: esxi 5  

Network adapter was set to Bridged (non replicating) on both, so Proxmox machine would get its own IP.
I gave it 4GB of RAM and 30GB (pre-allocated) HDD.

## Installing Proxmox

Grabbed Proxmox VE 4.4 ISO Installer from here: https://www.proxmox.com/en/downloads  
Mount the ISO and start the machine  
Follow the instructions. When asked for a hostname, it is necessary to provide a fully qualified domain name so I put "proxmox.local".

## Testing the install

Ensure you can login as Root  
Ensure PuTTY can connect  
Test internet by pinging google `ping www.google.com -c 3`  
Update the software `apt-get update`

## Creating Containers

First you have to have some templates installed. Go to Datacenter>proxmox>local hard drive. Select Content > Templates. Download a template OS.  

Create the container.

Setting up networking: set IPv4 to static and provide an appropriate IP and gateway, set IPv6 to DHCP.
