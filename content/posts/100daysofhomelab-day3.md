---
title: "#100daysofhomelab - Day 3 - Terraform and Cloudflare DNS"
date: 2023-04-13T20:07:29+09:30
draft: false
---

## Day 3

Today I started with a plan to use Infrastructure as Code and Continuous Integration to manage my Cloudflare DNS records. I got halfway there, but unfortuantely ran into issues between DroneCI and Terraform Cloud, and unfortunately will have to pick that part up later. However, I now can manage it with IaC, just without the automated process to commit any changes to Cloudflare.

## Terraform and Cloudflare

I got started once again with a Techno Tim [video](https://youtube.com/watch?v=FmYvrxYvBP0), and followed along for the majority of the video, skipping the Github Actions section since I use Gitea and Drone instead.
After going through the steps to install Terraform, get the basic .tf file created, I then used [cf-terraforming](https://github.com/cloudflare/cf-terraforming) to bring my current Cloudflare DNS records into ny .tf file and into Terraform's local state, before moving that to Terraform Cloud. Once I had this working, it was time to try and automate this with Drone.

## Drone, and the issues I faced

There were two big problems I faced during this. The first was an outdated Docker image, that I ended up just cloning the repository and building an updated image. The second, was the inability for me to pass my Terraform Cloud API Token into the container Drone was using to run the Terraform actions. This one was one I haven't yet overcome, but I do have an idea or two.

I probably spent an hour just looking through various options and trying them out, with no luck. I decided that I would just push my current state up to Gitea, and look into what other options I have.

I've come up with two possible solutions: Change my state backend to use Hashicorp Consul, or change how the Drone pipeline runs to not use a container.
If I change the state backend to Consul, I'll need to spin up a server for this and learn Consul. While this could be a good learning opportunity, I don't have any other purpose for this so I don't see much value here, and just running Consul purely for this seems like overkill.
If I change how the Drone pipeline runs, I'd be looking at using SSH to run this directly on a server. This could just be done on my Drone server, by installing Terraform and logging in with a user that already has Terraform Cloud set up. While I'd rather not have to run Terraform directly on the Drone server, the only other option would be to custom build a Docker container that somehow has the ability to bring the Terraform Cloud token into a usable place, which isn't how I want to actually learn how to create my own Docker images.

At this stage, I'm probably going to go with SSHing back to the Drone server and running Terraform on there, but that won't be for a little while. I might see if I can eventually build the Docker container to just use Terraform Cloud inside the existing Docker image I rebuilt, so that I can keep everything related to Drone into containers for better isolation.

## Next few days

The next few days I'll be at my partners house. I'll still be doing #100daysofhomelab, but it's more likely to be maintenance and catching up on documentation from the last few days.