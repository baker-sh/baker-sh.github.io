---
layout: post
title: AUR Chrome Beta Package fails MD5 check
subtitle: Here’s how to bypass it!
categories: scripts
tags: [script, linux]
---

OK so being on the bleeding edge can sometimes have it’s downfalls and this is one of mine.

The AUR package downloads the latest Chrome Beta but sometimes the MD5 check in the package has not been updated BUT I still want to install it.

Run this to install google-chrome-beta and bypass the MD5 check: –

```bash
yaourt --m-arg "--skipchecksums" --noconfirm -S google-chrome-beta
```

Now if you are here to find out how to bypass the MD5 check then I doubt if I have to tell you why this can be dangerous :).

Happy browsing.
