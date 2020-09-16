---
layout: post
title: Renew Let’s Encrypt Synology – 4 Step Guide
subtitle:
categories: scripts
tags: [script, synology nas]
---

How to renew Let’s Encrypt certificates on a Synology NAS.

1. Open TCP port 80 on your router and forward to your NAS.
2. `ssh` into your NAS.
3. `sudo su -` (to get root).
4. run `syno-letsencrypt renew-all -vv` (this will renew all your certificates).

Done.

Now that you have your certificates renewed don’t forget to close port 80 again on your router.
