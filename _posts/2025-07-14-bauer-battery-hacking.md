---
layout: post
title: "Bauer Battery Hacking"
subtitle: "Modifying a battery adapter to work with higher current tools."
date: 2025-07-14
post_class: electrical
categories: tools shop
---

>This article is dated to reflect the time of development/completion, not writing.

I have always been a big fan of Harbor Freight. The HF always offers three tiers of tools in every category; for hand tools this is the Pittsburgh, Quinn, and Icon lines (I'll talk about these another time). Of interest today is the cordless power tools; here we have Warrior, Bauer, and Hercules. One should typically disregard the lowest tier entirely. The Warrior power tools are manufactured e-waste, sold to people who need to make one hole and then put this thing away in a cupboard for a couple of years until it is needed again. (I once bought a pack of Warrior drills on a whim and threw the whole thing away after snapping a ⅜" bit in green Doug Fir).

<!-- TODO: Add tier photo here -->
![Harbor Freight Tool Tiers](https://external-preview.redd.it/we-have-a-new-category-economy-good-better-best-v0-qOjzjCv3lGrL9FRDkPdzCQPcuYYRburUWczWo-up7Qg.jpg?width=640&crop=smart&auto=webp&s=d6ea4c07198a1b4f2be593f9228bcfde05069429)

I've never bought any of the Hercules tools as it is my opinion that if you really plan on investing in a fleet of cordless tools, you should probably pay a little more and buy into Team Red or Yellow. I'm hardly the jingoistic type but I've chosen DeWalt as they still make many of their tools here in the states and perhaps more importantly it is what they carry more of at the Lowe's, which is generally quieter than the Home Depot in my town.

With any power tool brand, what you are buying into is the batteries. I've built a charger/storage shrine to my DeWalt batteries in my shop, and even though I know I have enough now, battery sales catch my eye more often than tool sales (≤ $10/Ah).

What is really the sweet spot at the Harbor Freight is their Bauer line-up, especially for filling in those rarely seen holes in my capabilities. For tools I need once in a blue moon, I look to Bauer. To date I've bought from them: the mini-SDS (after seeing [this video](#TODO-link-to-TTC-or-Project-Farm) on air hammers), and the subject of today's spiel — this metal-cutting circular saw, which was in the open box section for a measly **$23.98**.

![New open-box Bauer cold saw]({{ site.baseurl }}/assets/img/bauer/unboxed_saw.jpg)

Now I know what you'll say: "Well, they get you on the batteries." But I, cool-ly, perhaps snidely, certainly contemptuously, say "Yah, no shit that's why I didn't buy any." And then we laugh boisterously because who in their right mind is buying batteries from Harbor Freight — we all have battery adapters, probably the same one: on July 13, 2022, I bought [this one](#TODO-amazon-link).

This adapter has worked wonderfully for many years on my SDS, but attaching it to the cold saw does nothing, not even a blip. So what gives?

Taking a closer look at the input terminals of the tools, one notices an obvious discrepancy: the SDS has only three inputs and the saw four! The battery adapter I've been using also only has terminals for those three outputs, but interestingly only interfaces with two of the battery's contacts: B+/−. 

![Battery Adapter Terminals]({{ site.baseurl }}/assets/img/bauer/adapter_terminals.jpg)

The DeWalt batteries have 8 terminals: B+, TH, ID, C1, C2, C3, C4, and B−.

[![DeWalt 20V Max battery contacts](https://upload.wikimedia.org/wikipedia/commons/thumb/c/cb/Contacts_on_DeWalt_20V_Max_battery.jpg/400px-Contacts_on_DeWalt_20V_Max_battery.jpg)](https://upload.wikimedia.org/wikipedia/commons/c/cb/Contacts_on_DeWalt_20V_Max_battery.jpg)


>These tool batteries (most of them, excepting the Powerstack varieties and one other I should have looked up) use widely available 3.7V LiPo cells wired in series — 5 of them specifically, for 18.5V nominal. It's a little more complex than that: larger battery sizes use pairs of cells wired in parallel for more capacity, and there are different cell formats in use (20700s, 18650s, some pouch types, etc.). The terminals labeled C1–C4 provide individual cell voltages for balance charging, though in my more ignorant youth I did use C3 and C4 to power 12V electronics — definitely not recommended by the manufacturer. TH routes to a 10kΩ thermistor to B+, and ID connects to an identification resistor — thankfully we are spared from the handshake protocols Team Red suffers from.

Let's compare this to the Bauer battery:

[![Bauer battery contacts](https://preview.redd.it/kh3b041jxdm31.jpg?width=640&crop=smart&auto=webp&s=4e4fe1bd0420cb8bc9e1776c9d0da4e0cc22582a)](https://preview.redd.it/kh3b041jxdm31.jpg?width=640&crop=smart&auto=webp&s=4e4fe1bd0420cb8bc9e1776c9d0da4e0cc22582a)

*Shocked face.*

It's… almost the exact same… almost like they copied??? Lmao yeah ofc they did, who cares.

Unfortunately, the mapping isn't one-to-one — for instance, the TH pin is actually tied to B− here, also just a 10kΩ thermistor, but we can't use it.

After poking around online, I found threads of people discussing values for the Bauer ID resistor, with some suggesting 10kΩ and some 15kΩ, depending on the current capacity of the battery pack. I've got a box of resistors — let's try it.

Here, I've taken apart the Amazon battery adapter to see what's going on. There's a little 10kΩ resistor standing in for the thermistor to B−, but nothing for the ID pin.

![Battery Adapter Innards]({{ site.baseurl }}/assets/img/bauer/adapter_innards.jpg)

To test the functionality, I connected the power terminals to my bench power supply with test leads running from negative, through a resistor, to the ID terminal. I tried 10kΩ — no dice. No 15k's in my box, no 30k's to put in parallel, not even a 14.7k, so I jumped straight up to 20k. Lo and behold, the motor starts spinning up — but stops abruptly. Peeking at the power supply, I see the current draw quickly hit the 10A limit of this cheap little thing. Okay, onto the real thing.

Adapter internals dangling from the butt of the saw, precariously pushed into the battery — a veritable Prometheus. Resistor pinched between B− and ID; another hand, the right, pinches the switch. The motor starts slow and then picks up pace, that characteristic electronic not-quite-screech, not-quite-hum of a cheap BLDC motor, whirring on.

I've got pictures from here on out, so we can go back to the usual dry tech-blog prose I guess.

I momentarily considered pulling up KiCad and designing a replacement PCB for the adapter. I decided to just solder the resistor directly to the back of the ID and B− terminals inside the tool — something of an inverse sunk-cost thing, the wisdom to not polish a turd.

I attacked the silastic with an X-Acto at first, but quickly abandoned it in favor of this little 12V rotary tool, also from HF. (A horrible little thing — vibraty and weak, certainly no NSK — but indispensable considering what I paid for it and the infrequency of its use.) The little brass wire wheel made quick work of it. 

![The turd polisher]({{ site.baseurl }}/assets/img/bauer/turd_polisher.jpg)

A touch of solder and quite a bit of heat and it's done. I tried it again before buttoning the whole shebang up, of course. Goes back together quite easily, but the added length of the adapter does make it a bit unwieldy — a project for another day. Maybe I'll finally take the red PETG out of its vacuum bag.

![The unpolished turd]({{ site.baseurl }}/assets/img/bauer/unpolished_turd.jpg)
