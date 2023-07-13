Boxer
=====

Setup is covered by Oscar Liang: <https://oscarliang.com/radiomaster-boxer/#How-to-Setup-Radiomaster-Boxer>

Note: he says:

> IMPORTANT: Go to the Hardware page in System setup, and turn off ADC Filter!

This seems to be quad vs wing thing - for quads is best to turn it off (and leave things to the FC s/w) as explained by JB in [this video](https://www.youtube.com/watch?v=hQZImPgbaj8). I _suspect_ this applies to ArduCopter as well, i.e. it does the same kind of filtering that Betaflight.

Note: it's now possible to turn this off on a per-model basis - <https://oscarliang.com/adc-filter-model-option/>

On this page, OL recommends also turning off ELRS dynamic power at the same time - <https://oscarliang.com/random-twitches-during-flight/#Turn-off-your-ADC-filter> - however, I suspect, it's off by default.

Recon HD goggles
================

The USB-C out seems to be genuinely HDMI only (I thought DisplayPort was a mandatory element for USB-C video output - put using them with a USB-C DisplayPort cable did not work) and it seems the HDMI must be connected before powering up the goggles.

The goggles came with firmware that was two versions older than currently available at the point in time when they shipped.

The internal fans make _a lot_ of noise.

I tried both a normal 12V and a 9V power adapter, that I had laying around, and both worked fine - a 5V adapter (the most common kind) won't meet the minimum voltage requirement.

If you don't have a suitable power adapter just use the LiPo setup - using a power adapter is just a bit more convenient because you don't have to worry about the battery running out of power.
