---
layout: post
title: "iOS 5, Safari and squished SVGs "
date: 2016-03-08
---

Today I've been told we have a bug on the site. Nooo! Well, what was the bug? Some of our new shiny new SVG logos appear squished in Safari on an iPad 2 with iOS 5.

I mean, I don't like Safari, but hey, we need to support all the browsers.

Now, I'm quite new to the team, so I had no idea where to start, so I did the usual: Check CSS, react components, image, PNG fallbacks.. All seemed fine, especially since some of the other graphics showed just fine.

To note down: The svgs-images are embedded using the <img> tag.

I was pretty certain it had to be something with the image files themselves, as that was the only thing different between the ones that worked and the ones that didn't. Oddly enough, opening just the SVG image itself saw it rendered fine in iOS Safari. Re-exporting from Illustrator for the web, minifying, simplifying: No result.

Then, I found [Firebug Lite](https://getfirebug.com/firebuglite)! And I was happy (as iOS 5 does not support the tethered web debugging you get with iOS 6 upwards).

Investigating the DOM with firebug lite showed that the `NaturalWidth` and `NaturalHeight` attribute is different for the new files, compared to the old files. Weird, this isn't set in the sass... Where is it set?

Not sure whether the wrongly shown images are due to [this webkit bug](https://bugs.webkit.org/show_bug.cgi?id=82489), probably not, but reading through it brought me close to the solution...

It's in the svg code itself! And, hey ho, when looking at the source for the old images I saw indeed `height` and `width` values, which aren't present in the new ones. Quickly added them, et voilà, it works.

Now I can rest in peace and blame both Adobe for (presumably) changing the way Illustrator saves SVGs when you 'Export', and Apple for, well, for having this 'bug' in iOS 5. Shame on you, both!

What have I learnt? Well, not learnt per se, but confirmed that there's a solution for every problem<sup>*</sup>.

<sup>*</sup>Exceptions prove the rule.
