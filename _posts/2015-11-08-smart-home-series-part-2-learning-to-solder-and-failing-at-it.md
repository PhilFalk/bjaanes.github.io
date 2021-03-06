---
id: 446
title: 'Smart home series – Part 2 &#8211; Learning to solder and failing at it'
date: 2015-11-08T18:45:29+00:00
author: Gjermund Bjaanes
layout: post
guid: http://gjermundbjaanes.com/?p=446
permalink: /smart-home-series-part-2-learning-to-solder-and-failing-at-it/
dsq_thread_id:
  - 4300949387
categories:
  - Uncategorized
tags:
  - Arduino
  - IoT
  - Programming
  - Raspberry Pi
  - Smart home series
---
It took longer than I wanted to get to Part 2, but I was waiting on several parts from China. 

Note to self: buying cheap stuff from China might be very slow! I knew this, but still sucked.

<!--more-->

I was also missing a lot of soldering equipment, which I found out every time I sat down to actually attempt this.

I needed a WiFi component for my Arduino, so I bought a ESP8266 WiFi Shield from SparkFun:

[<img class="alignnone wp-image-448" src="http://gjermundbjaanes.com/wp-content/uploads/2015/11/sparkfun.jpg" alt="Sparkfun ESP8266 WiFi Shield" width="270" height="270" srcset="http://gjermundbjaanes.com/wp-content/uploads/2015/11/sparkfun.jpg 600w, http://gjermundbjaanes.com/wp-content/uploads/2015/11/sparkfun-150x150.jpg 150w" sizes="(max-width: 270px) 100vw, 270px" />](http://gjermundbjaanes.com/wp-content/uploads/2015/11/sparkfun.jpg)

<a href="https://www.sparkfun.com/products/13287" target="_blank">https://www.sparkfun.com/products/13287</a>
  
<a href="https://www.sparkfun.com/products/11417" target="_blank">https://www.sparkfun.com/products/11417</a>

The only problem with this is that you need to solder on the headers/pins for it. So that is what I did (spoiler alert: and failed at).

&nbsp;

# The Equipment

## Soldering Iron

Well, yeah. Of course.

I bought myself a Dremel 2000-01 Versa Tip Precision Butane Soldering Torch.

I bought this particular one because it was wireless (gas) and it could solder AND do other things like shrink tubes with hot air. Pretty sweet in my opinion. Worked really well too!

[<img class="alignnone wp-image-449" src="http://gjermundbjaanes.com/wp-content/uploads/2015/11/Dremel.jpg" alt="Dremel Soldering Iron" width="301" height="407" />](http://gjermundbjaanes.com/wp-content/uploads/2015/11/Dremel.jpg)

<a href="http://www.amazon.com/Dremel-2000-01-Precision-Butane-Soldering/dp/B00MJW08JK" target="_blank">http://www.amazon.com/Dremel-2000-01-Precision-Butane-Soldering/dp/B00MJW08JK</a>

&nbsp;

## Solder Wire

I have a few spools of solder wire, but for this particular one, I actually just used whatever came with the Dremel.

I am sure there are huge differences between different solder wires, but I am not quite there yet.

&nbsp;

## Second Hands

I am not sure if &#8216;Second Hands' is the correct name of this, but I know could not have done it without it.

It holds the pins and the board while soldering, and that was completely crucial. Don't try to do this stuff without it.

[<img class="alignnone wp-image-450 " src="http://gjermundbjaanes.com/wp-content/uploads/2015/11/IMG_0642-e1447004160900.jpg" alt="Second Hands" width="304" height="405" />](http://gjermundbjaanes.com/wp-content/uploads/2015/11/IMG_0642.jpg)

&nbsp;

## Brass Sponge

For cleaning the tip of the soldering iron, I read that brass sponges were better to use than regular sponges. So that is what I used. It worked really well to wipe off solder... stuff?

[<img class="alignnone wp-image-451" src="http://gjermundbjaanes.com/wp-content/uploads/2015/11/BrassSponge.jpg" alt="Brass Sponge" width="330" height="273" />](http://gjermundbjaanes.com/wp-content/uploads/2015/11/BrassSponge.jpg)

&nbsp;

# The Soldering

I learned the technique from a Youtube video (I mean, why not?).

The result turned out a hundred times better than my previous attempts.

If you have no idea how to do this, you should check out this video:

<iframe width="560" height="315" src="https://www.youtube.com/embed/f95i88OSWB4" frameborder="0" allowfullscreen></iframe>

&nbsp;

And this is the result after watching that video.

[<img class="alignnone wp-image-452" src="http://gjermundbjaanes.com/wp-content/uploads/2015/11/IMG_0641.jpg" alt="The result of the soldering" width="493" height="370" />](http://gjermundbjaanes.com/wp-content/uploads/2015/11/IMG_0641.jpg)

&nbsp;

Looks pretty OK, I think. However...

&nbsp;

# It didn't work!?!

Turns out, I did something wrong. Or the hardware was broken before I event got it. I can't upload to the Arduino after inserting the shield. I just get this error message:

<pre class="lang:default decode:true ">avrdude: stk500_recv(): programmer is not responding
avrdude: stk500_getsync() attempt 1 of 10: not in sync: resp=0x00</pre>

&nbsp;

And this happens no matter what code I try to upload to it while the shield is on.

The internet tells me this can be because of several things, but only one thing seems possible to me: the shield is broken. The reason I believe that is that the Arduino works just fine when I don't have the shield on it.

&nbsp;

I will however, give this another shot. I have already ordered a new one from sparkfun, so I hope I might be even better next time.

I also ordered a few non-shield versions of the ESP8266 so that I can still continue developing, even if I should fail again.

&nbsp;

Perhaps I should have practiced on some less important things first? Yes, I should have. I really should have... *sigh*. Nothing do to about that now.

I think the soldering technique was decent; I just messed up somewhere. It happens.