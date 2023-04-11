---
title: "#100daysofhomelab - Day 1 - Maintenance and Website"
date: 2023-04-11T18:38:06+09:30
draft: false
---

## Introduction

So, after being inspired by [TechnoTim](https://twitter.com/TechnoTimLive) and [SysAdminAfterDark](https://twitter.com/sysadafterdark) and some inspiration to learn more, both about new things and expanding on old knowledge, I decided I'd give [100 Days of Homelab](https://100daysofhomelab.com) a go. I've already got a homelab running, but it's a bit of a mess and needs some TLC, and this has also motivated me to get this website working properly, so it's time to get started.


## My Existing Homelab

I haven't got a diagram yet (lets add that to the list now) so I'll just describe my homelab.
I currently have two locations, my home and my colocation.

Home consists of a FortiGate as a firewall/router, some fanless Cisco Catalyst switches to connect everything together, UniFi UAP Lites for wireless, and an old PC repurposed as a Proxmox server for VMs that need to be local to my house. There's also a NetGear and Synology NAS for backups and other storage. Eventually I'll look at some PCs like the Lenovo Tiny/HP Mini/Dell Micro range for some extra home Proxmox nodes in a cluster, to give me some more local lab capacity.

Colocation consists of a FortiGate as a firewall/router (with IPsec back to home), as well as a Dell R720 as a Proxmox server, Dell R210 II for Proxmox Backup Server, and a Dell R515 with TrueNAS for media storage. Most of the heavy lifting is done out of here currently, but this setup is a bit of a mess and I'd love to get some better segmentation and a more logical setup of VMs between here and home.

I also partake in [DN42](https://dn42.eu), with a VyOS router and a couple of servers on the Proxmox server in colo, as well as routers in Vultr London and Los Angeles, and soon Tokyo.

## Day 1

Today mostly consisted of a bit of a tidy up of the Proxmox host in colo, moving storage around to free up some space on the SSD storage for servers that need the extra speed, and moving anything less important over to HDD storage where I've got plenty of space currently.

I also spent some time getting this site up and running on my web server VM in colo.

If you're following along, follow me on [Twitter](https://twitter.com/andrewtwelch) as I go through the adventure that is 100 Days of Homelab.