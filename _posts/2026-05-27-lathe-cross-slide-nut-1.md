---
layout: post
title:  "Cross Slide Nut Prototype"
subtitle:  
date: 2026-05-27
post_class: 3dprinting
tags: [3d printing, Fusion, machining, Sheldon, lathe, prototyping]
---

While disassembling the cross slide of the lathe for cleaning, I came upon a troubling sight. The nut for the lead screw is entirely wollered, chewed, worm, screwed if you will. 
Obviously I need to replace this with a cast iron or bronze reproduction but I need the lathe to actually do that, so I thought I'd print a temporary replacement.

![Leadscrew Nut Threads]({{ site.baseurl }}/assets/img/sheldon/cross_slide/nut_threads.jpg)

As always, I started with a sketch:

![Nut Sketch]({{ site.baseurl }}/assets/img/sheldon/cross_slide/scratchpad.jpg)

 As you might be able to read in the above drawing, I wasn't quite sure how to locate the "height" of the actual threaded portion that accepts the lead screw.
 The screw thread itself is an ACME 1/2"-8 (left-hand), an oddball thread, seemingly exclusively used in Sheldon cross slides, at least going by online mentions.
 >*Two start versions of this thread seem to be much more common, but that's not helpful right now.*

 Were the thread intact, one could measure to the minor diameter of the bore from either end to determine the center, but the uneven surface makes this impossible. I considered measuring from the surface of the inserted screw, but I really couldn't be arsed to drive to the shop for it. Instead, I resorted to a tried-and-true heuristic approach-- scanning the surface.

 ![Nut Scan]({{ site.baseurl }}/assets/img/sheldon/cross_slide/cross_slide_nut.jpg)

 I imported this into Fusion as a canvas and used it to approximate the position of the bore.
 Most of the modeling thereafter follows trivially, except for the non-standard thread.
 > The great thing about standards is that there are so many to choose from.

<center><iframe src="https://gmail3378138.autodesk360.com/shares/public/SH90d2dQT28d5b602811bf6c0038fa1ad092?mode=embed" width="600" height="600" allowfullscreen="true" webkitallowfullscreen="true" mozallowfullscreen="true"  frameborder="0"></iframe></center>

I had to create a custom thread profile and place the file in the Fusion libraries. It was fairly to create the profile by editing the existing ACME thread file, changing the TPI for the 1/2 in screw and just deleting the others. 

The first test print was almost perfect, and I might have even left it, but I printed it in PLA, very thin with very sparse infill; it cracked almost immediately while adjusting the gib.

![PLA Nut]({{ site.baseurl }}/assets/img/sheldon/cross_slide/pla_nut.jpg)

I printed it again in PETG, on Bambu's strength preset. While I was at it, I did a small press pull on the thread faces to get a slightly looser fit. (The first print was pretty tight on the unworn ends).

![Installed Nut]({{ site.baseurl }}/assets/img/sheldon/cross_slide/PETG_nut.jpg)

> I had already installed it by the time I thought to take a picture, but surely that's even better proof of the scheme's success.

> It'll be a while before I can get this nut made. It'll be part of a different post, but I made quite the goof removing the gearbox and leadscrew today. 