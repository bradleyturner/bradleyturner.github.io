---
layout: post
title:  "Building accessibility into our color systems and tools"
date:   2018-11-15 20:19:12 -0400
categories: jekyll update
excerpt: "Work in progress... Stay tuned."
image: "color.png"
---

[TLDR]

## Updating our color system was our chance to put accessibility first
When I started at Handshake as a product designer, I knew very little about digital accessibility. Eventually we started improving some of our features that weren’t designed and built with varying levels of ability in mind and it became clear to me just how much room we had to improve.

When we decided to update our color system, I wanted to keep contrast top of mind so it would be easier to design new features that would be accessible for users with varying levels of vision.

There were quite a few designers who were writing articles and sharing their approaches to color systems and accessibility, but they all seemed to involve quite a bit of guess and check. I wondered if we could make it simpler.

## We’ve already been using color in our product. What have we been using it for?
To start this project I audited our current products to come up with a list of use cases and requirements for the next iteration of our color system.

**At a high level we were using color to accomplish 3 different things:**
- Direct attention – Reinforce hierarchy and direct users’ attention to specific UI elements
- Reinforce meaning – Add meaning in combination of other affordances like shape, copy, iconography, etc
- Communicate brand – Communicate our brand characteristics

## A great system improves our ability to ship great product. What does the system need to do for us?
We knew what the colors we chose needed to allow us to accomplish. The next question we had to tackle was how to structure the system in a way that allowed us to design and build efficiently and effectively.

After interviewing designers and engineers across the company and identifying themes, I consolidated the feedback into 3 core principles that would guide our system:
- Start with accessibility
- Solve for real use-cases
- Empower designers, don’t limit for the sake of limits

### Start with accessibility
One of the most common questions that would come up during design reviews in our product development process was “Is that color accessible?”

The underlying question there normally was “Does that combo of background color and foreground text/icon color meet WCAG AA contrast requirements?”

Our current system had guidelines that showed what colors were accessible with white or black text, but were inconsistent across hues and didn’t account for using our foreground and background combos where neither of them were black or white.

I wanted to build a system that made it easy to answer that accessibility question without needing to turn to a contrast checker tool.

### Solve for real use-cases
This system needed to allow us to ship great products, not just look beautiful as a system. To make sure this system was actually going to allow us to deliver great product we needed to make sure we continually tested our new system with real product use cases and showed examples so they team knew how to effectively use the system.

### Empower designers, don’t limit for the sake of limits
At this point in Handshake’s design history we didn’t have super intentional brand guidelines or visual design direction… We didn’t want people to one-off their hex codes when they wanted to try something new or different. Too constrained = not going to use the system at all…
