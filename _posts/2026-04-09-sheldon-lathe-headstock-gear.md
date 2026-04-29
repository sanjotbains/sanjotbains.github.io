---
layout: post
title: "Sheldon Lathe Headstock Gear"
subtitle: "A 3D printed solution to a Formica problem."
date: 2026-04-09
post_class: 3dprinting
tags: [tools, shop, machining, lathe, Onshape, 3D printing, sheldon]
---

A quick one today. The gear that transmits power to the carriage feed for turning/threading on the Sheldon MW56P is missing a couple of teeth. 

Unfortunately, in my zeal to get this machine cleaned up and operational I did not get any pictures of the gear train with its 20 years of undisturbed old oil caked on there. The grime was so great that I originally believed this gear to be iron. 

You can imagine I was quite disappointed to find this, as I do not have gear cutters, nor a milling machine for that matter. I had then resolved to simply 3D print the gear.

After pulling the gear, it was submerged with its brethren in the parts washer for the night and scrubbed clean the next day. It's micarta with a pressed in brass bearing! (The manual calls it out as a "Formica" gear.) Really was a pleasure to see this. 

![Broken Headstock Gear]({{ site.baseurl }}/assets/img/sheldon/broken_headstock_gear.webp)

![Reverse Gear from Parts List]({{ site.baseurl }}/assets/img/sheldon/reverse_plate_parts_list.png)

Its twin, the forward feed gear is brass. It seems that the second gear was chosen to be the sacrificial piece should the carriage crash as it is engaged regardless of whether one is feeding right or left. 

<!-- Insert image of right-left selection -->

There is one more Formica gear in the assembly, connnecting the selector gearing assembly to the feed ratio gearbox (which will get its own article). These Formica gears do more than offer break points in crash scenarios-- they quiet the geartrain considerably, anyone that's heard a straight cut gear transmission can attest.

<!-- Insert image of end gearing irl -->
![End Gearing Assembly]({{ site.baseurl }}/assets/img/sheldon/end_gearing_assembly_parts_list.png)

Anyhow, some measurements with the calipers and some educated guessing (later confirmed) led me to believe the gear was 16 Diametral Pitch with a 14.5 degree pressure angle.

![Scratchpad Detail 1]({{ site.baseurl }}/assets/img/sheldon/scratchpad_gear_1.jpg)

I made this part during the week or so I was trying out Onshape (6.5/10, undercooked) and the spur gear creator tools makes the bulk of the work trivial.

The gear features some bosses that position it laterally on its shaft-- just some raised profiles with a chamfer.

![Gear Model in Onshape]({{ site.baseurl }}/assets/img/sheldon/onshape_gear.gif)

Now came the issue of the bushing. I could certainly mail order some bronze bushings from McMaster-Carr, or even bronze stock, but why bother when I can simply drive 1 mile to Lowe's and pick up cheap self-lubricating bronze bushings?

And that's what I did. I brought two home with me and modeled a "press-fit" (hard push into the desk) bore into the part to match. 
>Notice the measurement of the bore shrink in the scratchpad image! 

![Scratchpad Detail 2]({{ site.baseurl }}/assets/img/sheldon/scratchpad_gear_2.jpg)

Of course, the bushing bore does not match the the shaft diameter, but this was anticipated; I planned to machine the bores on the lathe before installation to ensure a perfect fit. Machining these self-lubricating bushings is always annoying-- can't really gronk on it in the chuck, there's sticky bronze dust everywhere, a "good" surface finish probably means you've smeared the pores shut. I machined it in a collet to avoid crushing the sintered structure. I am willing to live with the third point, as the bushing is oiled internally via Gits cup. There is now forevermore bronze dust in the lathe.

![Installed Gear]({{ site.baseurl }}/assets/img/sheldon/end_gearing_assembled_2.jpg)

Unfortunately, at some point while taking this apart I lost one of the washers. *If only I had a lathe, I could just make a new one ;)*

Anyhow, the feed ratio gear box still needs work before I really can use the power feed or do any threading, so that's next on the list.