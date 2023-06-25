Boxer
=====

Setup is covered by Oscar Liang: <https://oscarliang.com/radiomaster-boxer/#How-to-Setup-Radiomaster-Boxer>

Note: he says:

> IMPORTANT: Go to the Hardware page in System setup, and turn off ADC Filter!

This seems to be quad vs wing thing - for quads is best to turn it off (and leave things to the FC s/w) as explained by JB in [this video](https://www.youtube.com/watch?v=hQZImPgbaj8). I _suspect_ this applies to ArduCopter as well, i.e. it does the same kind of filtering that Betaflight.

Note: it's now possible to turn this off on a per-model basis - <https://oscarliang.com/adc-filter-model-option/>

On this page, OL recommends also turning off ELRS dynamic power at the same time - <https://oscarliang.com/random-twitches-during-flight/#Turn-off-your-ADC-filter> - however, I suspect, it's off by default.
