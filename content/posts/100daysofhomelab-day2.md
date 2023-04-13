---
title: "#100daysofhomelab - Day 2 - DroneCI and Ubuntu Cloud Templates"
date: 2023-04-12T14:15:16+09:30
draft: false
---

## Day 2

Today I wanted to get two things done:

- Automatic website updates
- Easier VM deployments

I figured the best way to do this would be to setup DroneCI to handle the website updates (and other future CI tasks), and to help make new VM setups quicker in the future, I decided I'd deploy a Ubuntu cloud image template on my Proxmox server in Colo.

## Ubuntu Cloud Template

Last night I watched Techno Tim's [video](https://www.youtube.com/watch?v=shiIi38cJe4) on this topic, and then this morning decided to follow along, downloading the Ubuntu Cloud image for 22.04/Focal, creating a VM, adding the hardware needed command by command, and then eventually converting it to a template. Once this was done, I resized the hard disk image to 8GB as a starting point that I can easily expand when the VM is cloned.

## DroneCI

After that, I used that template to set up a new VM, dedicated to DroneCI. Once the server was deployed (in record time for the homelab), I installed Docker, creeated an OAuth app in my Gitea instance, and then went about starting up DroneCI's Docker image using their excellent [documentation](https://docs.drone.io/). Once this was done, I spun up two Docker based runners in their own containers on the same server. Once this was done, I also installed [lazydocker](https://github.com/jesseduffield/lazydocker) which gives me a nice terminal based view of everything running in Docker on that host.

Once DroneCI was up and running, I went about setting up my .drone.yml file to automatically build and deploy this website to my web server, thankfully Thomas Leister has a pretty decent [guide](https://thomas-leister.de/en/drone-ci-with-codeberg) that covers this. After spending time trying to figure out why DroneCI wasn't able to connect to my web server (I forgot to add the SSH key after generating it on the web server), I was able to get it to successfully complete a CI build, and now, this post should automatically be available shortly after my pull request from the staging branch to main.

### Update

After pushing this, I found a few more issues. For some reason, the theme submodule wasn't being cloned by DroneCI (turns out this is default behaviour), but I thought something was wrong with the image. So now I've learned how to build a Docker image from a Dockerfile, since the image I was using before was several years old. When that still didn't work, I discovered the submodule issue, changed my .drone.yml file to include a step that clones the submodule in, and now I've got a website that automatically updates!

I also created a staging site for this now, so I can see changes as they are pushed to my staging branch, with the main site being updated when a pull request is made into the main branch.

## Tomorrow

Tomorrow I reckon I'll start looking at some Infrastructure as Code basics, starting with managing one or two of my domains in Cloudflare with Terraform, with the goal to expand that further for easier management.