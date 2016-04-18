---
layout: post
title: "Synology Backups and a Power Cut"
date: 2016-04-18
---

I ordered a Raspberry Pi 3 the other day and it arrived today yay! When I got home I obviously was very keen to plug it in and give it a go, so I unplugged a plug, and thought.. *Oh crap*

A couple of weeks ago I started a Backup task for all my photos on my NAS. So my DS410 has eagerly been uploading hundreds of gigabytes of DNGs to S3 24/7, and was about 25% finished (yay under 2 months left to be done!). And I just pulled the plug. Smart move, Nik, smart move.

Plugged it back in, logged in and luckily saw no drive errors, which is a wonder seeing that the oldest drive in the bunch has 41620 hours "Power-On Time" (the youngest has 5862 hours).

Restarted the Backup (apparently it was 'Never backed up' before), and it started uploading.. 10MB.. 20MB.. 0%. I logged into my AWS account to check it hadn't deleted the 250GB it had already uploaded.. it didn't.. Mysterious, what was it doing? We got to ~ 60MB uploaded, and suddenly.. 26% done! Thank the lord it picked it back up, and I feel a bit saver about this backup now.

Next step will be downloading it onto an RS815+ at home from the S3 backup. Redundancy, accessibility and cost-efficiency. Yada-yada..

Oh, and the Raspberry Pi? Well, I realised I don't actuall have a USB keyboard at home, so that'll have to wait until some other time, too.