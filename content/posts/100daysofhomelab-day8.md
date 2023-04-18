---
title: "#100daysofhomelab - Day 8 - Mastodon Part 2 and Matrix"
date: 2023-04-18T17:57:59+09:30
draft: false
---

## Mastodon Part 2

So after yesterday's struggles, I gave Mastodon another go, using Ubuntu 20.04 this time. Followed the guide provided by Mastodon... and it worked. Couldn't find a real reason why Mastodon doesn't work on 22.04, but at least it's working now! If you do want to follow me, I'm on [@fortera@andrewwelch.net](https://social.andrewwelch.net/@fortera) and [@fortera@aus.social](https://aus.social/@fortera).

## Matrix

After this, I thought I'd give a Matrix server a go. Read the documentation, figured out how to handle federation using my root domain but have the server at a subdomain, and eventually got it going. The guide provided by Matrix is pretty good, the only issue I'm having now is performance. The only issue I had was that I wanted it behind a Cloudflare Tunnel, but that was interfering with Matrix somehow, moving it away from the tunnel sorted it out. I'll see how things go, but at the moment it's taking a long time to load the history of rooms. I might just need to bump up the resources for the VM, but if it doesn't give me much value, I might just find another server to use for it. I did spin up Element as my web interface for it, and even if I get rid of my own Matrix server, I'll likely keep the Element server sice it's pretty lightweight and runs in a Docker container.

## Tomorrow

Tomorrow, I'm going to try and find some kind of homepage/dashboard to use, to give me easy access to my various systems. I'll also look at moving a few more things to be behind Cloudflare Tunnels that already exist, and I might even move one or two web apps behind it with either Google Workspace or Authelia (if this is even possible) authentication in front of it.