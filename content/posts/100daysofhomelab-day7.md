---
title: "#100daysofhomelab - Day 7 - Mastodon: Part 1"
date: 2023-04-17T21:47:32+09:30
draft: false
tags: ["100daysofhomelab", "homelab"]
---

## Mastodon, and not getting there

Currently I have a Mastodon account on [aus.social](https://aus.social), but I decided I would set up a Mastodon server for myself in my homelab, partly to give it a go, and if it went well, I'd eventually move over to it. Unfortunately, I didn't quite get there.

My first attempt was using Docker, I'm getting familiar with it, and I quite like it, however I wasn't able to connect to it in the end. My second attempt was also Docker, but with a different guide. No luck still.

After this, I decided I'd just install it directly in the VM. I followed the guide from the Mastodon website, got it installed and... it wouldn't load properly. Started googling, and the couple of things I found all said "Ubuntu 22.04 just doesn't work for some reason, use 20.04 like Mastodon recommend". Looks like it's time to manually deploy a VM again.

I finished the night off deploying the VM once again with Ubuntu 20.04 LTS instead of using my 22.04 template, it'll take longer but hopefully this time it'll work. And hopefully tomorrow, Mastodon will work.