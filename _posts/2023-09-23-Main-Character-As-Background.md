---
layout: post
title:  "Main Character as Background"
author: Hiroshi Tsubokawa
tag: NES Emulator
---

I realized that some NES games are rendering their main character as the
background. For example, "Kung Fu" ("スパルタンX” in Japan), the four enemy
characters can come in the frame at once. I wondered why they're not flickering
caused by the 8 sprite limit in a scanline. One character obviously uses at least
two sprite in width.

![Kung Fu tiles and sprites]({{ site.baseurl }}/assets/img/2023-09-23-01.png)
When I show the background grid and sprite boxes, I see the main character is rendered
in the background. It is always placed at the center of the frame except for the beginning
and end of stages. During the time, the main character is still in the background
and uses many tiles with offsets as he walks forward.

I would like to implement the feature that visualizes scroll of background so that
I can look into the details on how the games are programmed.

Go ahead and check my emulator on github.
[Famulator Famicom/NES Emulator](https://github.com/tsubo164/Famulator)
