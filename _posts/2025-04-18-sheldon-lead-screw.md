---
layout: post
title: "Diagnosing lead screw resistance on a Sheldon WM56P"
date: 2025-04-18
post_class: technical
tags: [machining, lathe, sheldon, power-feed]
---

> I DID NOT WRITE THIS. THIS IS FOR TESTING NEW THEME STUFF.

Before pulling the apron, isolate the fault to a subsystem. The end gear train and the apron's internal worm fail differently — and disassembly order matters.

## Isolating the drag

With the half-nuts disengaged, rotate the lead screw by hand at the left bearing. If resistance is present and *consistent* regardless of apron position, the fault is upstream of the apron entirely.

```python
# Quick isolation logic
def check_subsystem():
    # 1. Disengage half-nuts
    # 2. Rotate lead screw by hand at left bearing
    # 3. Consistent drag → fault in screw or bearing, not apron
    return "localized"
```

If the drag varies as you traverse the carriage, the apron worm is the more likely culprit.

## What the end gearing tells you

The end gear train on the WM56P is exposed when you pull the cover on the left end of the headstock. Look for:

- Burrs or chips in the gear teeth from a previous breakage
- Misalignment in the intermediate stud
- A cracked or loose key on the lead screw gear

In my case the intermediate gear had a hairline crack at the hub — invisible until I loaded it with a bit of torque by hand.
