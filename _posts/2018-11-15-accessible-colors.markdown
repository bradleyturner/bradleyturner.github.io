---
layout: post
title:  "Building accessibility into our color systems and tools"
date:   2018-11-15 20:19:12 -0400
categories: jekyll update
excerpt: "I updated our color system to make it easier to meet WCAG AA contrast requirements."
image: "color.png"
---

In the summer of 2018 I expanded and updated our color system while keeping accessibility top of mind, making it easier for our product teams to ship products that met WCAG AA contrast requirements.

I ended up turning this work into a tool called <a href="http://www.contraast.design">contraast.design</a> that allows other designers to use our approach for their own color systems–presenting my work at an A11yBay meetup, the 2019 Accessibility Camp in San Francisco, and on <a href="http://www.rubberducking.fm/5">an episode of the Rubber Ducking podcast</a>.

## Updating our color system was our chance to put accessibility first

Throughout my time at Handshake the colors we use in the product have evolved multiple times as we iterated on the look and feel of our product and UI system. 

<div class="reflection">
  <p>Supporting illustrations are currently missing and will be added soon!</p>
</div>

We decided to update and expand our color system in the summer of 2018. I was excited about taking that opportunity to embed some accessibility principles in the system so our product teams would have an easier time shipping accessible products.

There were quite a few designers who were writing articles and sharing their approaches to color systems and accessibility at the time, but they all seemed to involve quite a bit of guess and check. I wondered if we could make it simpler.

## Starting with an audit – what are we using color for today?

To start this project I audited our current products to understand how color had been used so far. I wanted to make sure the design team was aligned on what our use of color was for so that we could evaluate an updated system through that shared understanding.

After some synthesis and discussion, we agreed we were using color to accomplish these 3 things:

* **Direct attention** – Color was being used to reinforce hierarchy and direct users’ attention toward specific UI elements and away from others.
* **Reinforce meaning** – Colors like red, yellow, and green were being used to layer on meaning in addition to other affordances like shape, copy, and iconography
* **Communicate brand** – The colors we were using were meant to inject a bit of joy and fun into the job search process, differentiating us from our competitors

## Auditing our design and engineering processes – what does a good color system accomplish?

We knew how we’d been using color in product. The next question we had to tackle was how should we design the system in a way that was useful for our designers and engineers?

I interviewed designers and engineers across the company, synthesized the interviews, and identified 3 core themes:

### Make it easy to understand acceptable contrast
One of the most common questions that would come up during design reviews in our product development process was “Is that color accessible?”.

The underlying question there was actually “Does that combo of background color and foreground text/icon color meet WCAG AA contrast requirements?”. Getting the answer to that question likely required a designer to open up a contrast checking tool and check it manually.

While our current system had guidelines that showed what colors were accessible with white or black text, they didn’t account for using foreground and background combos where neither color was black or white. 

We had an opportunity to fix that.

### Solve for real use-cases
One common theme I heard from interviews with engineers was that the color variables we had previously defined didn’t seem to line up with real use-cases.

The previous color stacks we had looked nice as a system, but weren’t consistently used across component variants and states, resulting in many edge cases where we’d end up having to introduce new colors that weren’t part of the system, resulting in fragmented code and designs.

### Empower designers, don’t limit for the sake of limits
At this point in Handshake’s design history we didn’t have super intentional brand guidelines or visual design direction… We didn’t want people to one-off their hex codes when they wanted to try something new or different. Too constrained = not going to use the system at all…

## Building our “perfect” color system
With these themes in mind I sketched out some frameworks of what our ideal system might look like. 

Ideally we’d have a simple set of rules for contrast across levels of darkness where you could know which colors would work together regardless of hue.

The levels of darkness we chose should account for all of the levels of darkness we need to support in our UI across all of the states we were designing for.

We should have an easy way to add or edit the hues within our system as our brand representation evolves over time.

### Digging into the math behind contrast to maintain it across hue
Starting with WCAG guidelines on contrast, I tracked down how rgb values are used to calculate contrast and then figured out how to convert from rib to hsl so that we could have hue as a variable and relative luminance as the other. With this model I was able to see all of the possible hex values within a certain hue that would have the same level of contrast with any other color. For each hue this produced a long list of values with varying levels of saturation. Since at the time we generally leaned toward more saturated colors, I decided to pick the most saturated version of each color for the first pass at the system. (Spoiler alert: that wasn’t a great idea…)

### Determining necessary levels of contrast
To determine how many levels of color we needed, I took screenshots across the product and converted them to black and white to understand to understand how many levels of darkness we were using at the time.

I wanted to minimize the number of levels we were using to make the system simpler, so I tested a few options, mocking up screen with those levels in grayscale. In the end I determined that 9 shades would be sufficient for all of the UI we were supporting.

I calculated the relative luminance of each of those grays to put back into the system to determine our levels across hue.

### Choosing hues
Since we didn’t have strong opinions or rationale behind our current hues we were using, I decided to spread out our hues around our brand colors to make sure they were as different from each other as possible.

Embed usage/meaning in levels, allow them to adapt regardless of hue, expand the hues, build guidelines

## Testing my initial proposal led to more iteration
Now that I had a first pass at the initial system I wanted to stress test it in our current UI to make sure it wouldn’t break down or fall short for our designers.

The main takeaway from testing out the system was that some hues got way too bright at lower levels. For example, this green alert looked very bright compared to its informational blue counterpart. This was a result of picking the most saturated color for each hue. Some hues can be much more vibrant at lower levels contrast than others.

After some research I learned about the {} color model with includes a variable called gamma. This is basically a measure of how pure a color is. If we wanted the colors across different hues to carry similar amounts of weight we would need to control the gamma as well.

I added that to my calculations, updated my proposal, tested again with real screens, and coordinated a testing period with the design team so they all had a chance to use the new colors in their designs before we made it official and rolled them out.

## Making sure the design team knew how to use the system
Now that we had a new set of colors to use I supplemented those colors with guidelines that outlined which levels passed contrast requirements and how we expect to use the different levels across our components, features, and products.

I documented this in our design system site and our Sketch component library and color plugin.

## Updating the product to use the new colors
From previous experience tweaking our color system I knew that implementing these updates in our codebase would require manual review and answering quite a few open design questions. Instead of pairing with an engineer and using their time I got my own local version of our codebase running on my laptop and submitted pull requests for review that only required a small amount of engineering effort to review.

When I encountered old UI that used previous 1-off colors in UI I partnered with the PM and Designer that owned that part of the product to update the UI to use our new color system effectively.

We knew some color changes might be noticeable to our users or result in questions to the support team so we proactively communicated the changes to our customer success organization.

After we implemented the new system across the product we were able to remove an outdated and poorly maintained system called “High Contrast Mode,” which had created a separate stylesheet for users who had that feature turned on. This sped up our build times and made it so users with low-vision had a first class experience instead of having to dig into our settings to turn on a toggle that made the product usable for them.

## Sharing my approach with the accessibility community
After sharing my approach internally I was encouraged to make a public tool that would allow other design teams to take a similar contrast-first approach to their color picking.

I picked up my outdated React knowledge and built a minimal version at contraast.io, presenting my work at a Bay Area Accessibility Meetup and at the annual Accessibility Camp in San Francisco.

## There’s plenty of room for improvement
Since I worked on this project in the summer of 2018 designers have done their own colors system work that goes deeper than my approach. Also during that time our brand at Handshake has evolved, resulting in improvements to our system. Design tools have also evolved, creating space for more impact.

### The community is taking this further
Since I worked on this, more designers have built color systems that put accessibility first and allow for more fine-grained control of the colors you choose.

Most of these systems allow you to vary hue slightly as you change levels to make your chosen colors feel less muddy our muted.

### Our brand system is becoming more opinionated and locked down
Our brand system has evolved since this last pass at our color system, with stronger opinions about hues and contrast levels.

While my initial approach allowed us to more easily design and ship experiences that met AA contrast requirements, the colors I chose didn’t communicate the brand voice that we wanted.

### Building contrast into color pickers
In the future, I’d love to see these systems evolve to be embedded in the tools we use today like Sketch and Figma. Instead of needing to trigger a plugin that checks contrast, imagine if our tools told us up front when our UI might be inaccessible for users with vision impairments.
