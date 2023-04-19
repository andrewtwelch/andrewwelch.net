---
title: "#100daysofhomelab - Day 5 - Finishing an IPAM Migration"
date: 2023-04-15T19:37:46+09:30
draft: false
tags: ["100daysofhomelab", "homelab"]
---

## Gotta track 'em all!

From the early days of having a homelab bigger than a single media server, I've tried to keep track of the IP addresses I'm using in a reasonable way. Of course, I started with a spreadsheet in Google Sheets, but eventually settled on phpIPAM, purely because we used it at work at the time.

My phpIPAM instance had survived a number of moves from web server to web server, but would always end up with little issues over the place, usually not breaking the core functionality, but would cause logging to fail. As a result, I decided to rethink what I would do for it.

In the end, I found that someone had a Docker container for it, spun it up... and left it for a month. As I've added servers, they've gone in there, but allocating IP addresses would always involve checking both instances as well as manually verifying. There's also a bunch of old records in the old instance.

So, for today, I went about consolidating to the new instance, and cleaning out any old records. This gives me a clean slate, which will be useful when expanding my lab for various things.

## A side note

I also had to make a change to my firewall this morning, as I realised that my website was behind the same Nginx Proxy Manager instance that was geo-restricted to Australia. Eventually this will be behind a Cloudflare tunnel, but for those outside of Australia, hello for the first time!
