---
layout: post
title: "Windows 10 on phones, Sprites and Mysterious Lines"
date: 2016-03-11
---

[Sprites](http://en.wikipedia.org/wiki/Sprite_(computer_graphics)), loved by many, despised by a few. The concept of combingin multiple images into one file is certainly not an invention of the Web 2.0 or CSS 3; it's been around since at least the 70's if we believe the above Wikipedia page.

For certain image assets we use sprites, and they get assembled automatically os part our main grunt job, by Mr [spritesmith](https://github.com/Ensighten/grunt-spritesmith) to be precise. It's quite neat; it combines the images and substitutes the values in our Sass/CSS. And it does a pretty good job at it!

However, our tester (Yes, they're great people. They are the source for most of my posts here so far :) ) had noticed some weird lines on both of our WP10 test phones. Not on the tablet, and I couldn't reproduce it in my [MSEdge  VM](https://dev.windows.com/en-us/microsoft-edge/tools/vms/). Now thank god I knew that the graphics we had the issues with were sprites. I would have probably found out quite quickly looking at the page and the CSS, but these are the kind of things I can imagine overlooking easily. And looking at the sprited (that's a word, right?) png showed that the _weird lines_ match neighbouring images! Yay! The problem is identified (And that's probably the most significant step in debugging).

[Extensive googleing](https://www.google.com/?q=windows+10+sprites) has not led to the answer to the "*Why* can't WP10 handle sprites properly?", but thankfully a solution was easily thought of:
Since it was literally fractions of pixels that showed up only at certain zoom levels (we have very diligent testers!), simply adding some padding to the affected sprites solved the problem. And who would have guessed, Mr [spritesmith](https://github.com/Ensighten/grunt-spritesmith) comes with a 'padding' option I could easily add to the job!

I'd show the code, but it's literally `padding: 2`, just like in the [documentation](https://github.com/Ensighten/grunt-spritesmith#padding) so here you go. Not veyr exciting, but a coworker found my blog and I now have to actually keep posting here or I'll look like a quitter or something.

N
