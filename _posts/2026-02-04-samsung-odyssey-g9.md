---
layout:
title: "Big F***ing Monitor"
subtitle: "Repairing a Samsung Odyssey G9 Monitor."
date: 02-04-2026
post_class: electrical
tags: [electrical, repair, PCB, computer]
---

On January 16, a day much like any other, I was browsing Facebook Marketplace as I am want to do several times a day, one must always be optimizing his dealflow. This ordinary day was made quite special by my finding for sale a Big F***ing Monitor for $90, broken of course. But pay keen attention to the description:

![Original Listing]({{ site.baseurl }}/assets/img/samsung_g9/og_listing.png)

The purveyor notes "Monitor does not turn on. Seems like an issue with the internal power supply." Now, I'm not one to trust a Marketplace listing, but even for parts, this is probably worth more than that, so I shot him an offer:

![Conversation]({{ site.baseurl }}/assets/img/samsung_g9/convo.png)

And the next day I had it in my office.
Just as the seller described, the monitor did absolutely nothing, no lights, no warming, no buzz, a good sign that the power supply was in fact the culprit. I connected the monitor to line voltage through the multimeter in amperage mode and measured no current, not even inrush current.

Figuring out how to remove the back was a real struggle, and my methods left quite a few scars on the perimeter of the shell.

![Perimeter Scarring]({{ site.baseurl }}/assets/img/samsung_g9/scarring.jpg)

Once free of the rest of the monitor I was able to test the power supply on its own.

*Now at this point I feel it is my responsibility to tell you that this is not a tutorial, this is blog where I am chronicling my process including my poor judgement and potentially very dangerous mistakes. Do not do what I am doing. Please and thank you.*

A confession: I don't really know how switching mode power supplies work. I was always more into signal processing and embedded devices while in college; I did not take a single class on power electronics. All I knew was generally what each stage was supposed to be doing and which parts I shouldn't touch.

So naturally, I turned to the LLM.

I was probably out of free Claude tokens when I started this because I started my diagnostic with Deepseek:

>I am repairing a Samsung G9 Odyssey power supply P/N BN4400976A. After the initial visual inspection (no obvious faults, e.g. burning or corrosion), I connected it to line voltage. There is no voltage at CNM804, nor at JP818. In fact, the fuse, FP801S (T5AH250V) has blown and the board is not powering up at all. 
>Am I correct in assuming that I first ought to just replace this fuse? My thinking is that even if there is a fault elsewhere, I cannot determine that until I replace it. 

The numbers probably don't mean all that much to you, but Samsung seems to have a fairly standard topology (maybe I'm using that word incorrectly) across all of their television/monitor switching mode power supplies, and I figured the numbers might yield useful searches for the LLM.

Anyhow, I asked Deepseek to summarize its response to this prompt, that it may fairly represent itself in this public article:
<blockquote>
<h3>What the AI Said (That I Absolutely Should Have Listened To)</h3>

<p>In its infinite robot wisdom, my AI assistant laid out a perfectly sensible, safety-obsessed repair plan. It kindly informed me that:</p>

<p>A blown fuse is a symptom, not the problem. Replacing it without finding the root cause is like putting a new bandage on a severed artery and going for a jog.</p>

<p>It then begged me — in that polite, emotionally neutral way that AIs have — to do the following:</p>
<ul>
    <li>Test the bridge rectifier and switching FETs first (because they're almost always the actual culprits).</li>

    <li>Build a Dim Bulb Tester — a magical device involving an incandescent light bulb that limits current and prevents catastrophic failure. The assistant described it as "the most important tool for repairing switch-mode power supplies."</li>

    <li>Do NOT, under any circumstances, just replace the fuse and plug directly into mains. It used all-caps and bold text. It mentioned "loud pop," "more component damage," and "another blown fuse."</li>
</ul>
</blockquote>

I am not a smart man:

>Alright, I found the transistors QP801CS and QP802CS to be shorted. they are model MMF60R190QS. I removed them and replaced them with GC20N65F, an equivalent transistor., as well as changed out the fuse. 
>I realize I probably should have used a Dim Bulb Tester, but I got hasty and just plugged it in to Line voltage. 
>There was arcing across the transistor area, seemingly local to QP802CS. The board is pretty scorched but the transistors themselves seem fine. Caps CP804 CP820 and CP805 all show sign of scorching, from the inside out.

In my defense it was getting quite late.

And Deepseek's summary of itself (Good lord, one model that really needs to learn some brevity):
<blockquote>
<ul>
<li>"Stop. Disconnect immediately."</li>
<li>The original shorted FETs were victims, not the cause. The real killer was probably the PWM controller IC.</li>
<li>Those exploding capacitors? Innocent bystanders.</li>
<li>Scrub carbon tracks off the PCB. Sniff for burnt components. Desolder and retest everything.</li>
<li>At this point, just buy a replacement board.</li>
</ul>
</blockquote>

That last point was enough to turn me off Deepseek for the time being, I'm no quitter. 

You may witness the carnage for yourself:

![Burnt Caps]({{ site.baseurl }}/assets/img/samsung_g9/burnt_caps.jpg)

I spent a couple of days reading up on the design of the power supply and repair/diagnostic methodology specific to TVs. I managed to track down a schematic for a very similar power supply board, a BN44-00852A. I even built a **dim bulb tester**.

[Dim Bulb Tester]({{ site.baseurl }}/assets/img/samsung_g9/dim_bulb_tester.jpg)

