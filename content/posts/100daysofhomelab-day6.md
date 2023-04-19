---
title: "#100daysofhomelab - Day 6 - Cloudflare Tunnels"
date: 2023-04-16T11:30:43+09:30
draft: false
tags: ["100daysofhomelab", "homelab"]
---

## Tunnels to the Cloud

After my mistake with geolocking my website, I decided that it was time to set up Cloudflare Tunnels and move my website to be behind there. Since I set up my Cloudflare DNS to be managed by Terraform, I thought I'd do the same here. This took a bit of documentation reading, but once I had my head around how the Cloudflare provider for Terraform works and how it handles tunnels, I started writing out the two tunnels, one for home and one for colo.

After forgetting the default rule for my colo tunnel, I eventually got the configuration pushed up to Cloudflare. This let me log into Cloudflare and grab the token needed to install cloudflared on a new Ubuntu server. However, as usual, I came across a slight issue, but not on my end for once.

It turns out there's a slight issue with the Cloudflare provider where a couple of bits of configuration need to be applied twice for some reason, but because of how Terraform works, that means I need to make some kind of change. A workaround for now is to just edit the relevant section in Cloudflare's dashboard and just hit save, reapplying what is already there. After doing this, my website is now behind Cloudflare Tunnels, and I could re-apply the geoblock on my Colo firewall.

## Staging Website

I also found one issue with my staging website, since Hugo builds all links using the base URL entered in it's config.

Getting around this was easy, the *alpine* container includes *sed*, so I just added a step that replaces andrewwelch.net with staging.andrewwelch.net in my config.toml file, fixing this issue. The staging website isn't used heavily right now, but will be good in future when making larger changes.