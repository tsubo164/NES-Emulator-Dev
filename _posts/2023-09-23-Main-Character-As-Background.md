---
layout: post
title:  "Main Character as Background"
author: Hiroshi Tsubokawa
tag: NES Emulator
---

I realized that some of NES games are rendering their main character as
background. For example, "Kung Fu" ("スパルタンX” in Japan), the four enemy
characters can come in the frame at once. I wondered why they're not flickering
caused by 8 sprite limit in a scanline. One character obviously uses at least
two sprit in width.

![Kung Fu tiles and sprites]({{ site.baseurl }}/assets/img/2023-09-23-01.png)
When I show background grid and sprite boxes, I saw the main character is rendered
in background. It is always placed at center of the frame except for the beginning
and end of stages. During the time, the main character is still in the background
and uses many tiles with offsets as he walks forward.

I would like to implement the feature that visualizes scroll of background so that
I can look into the details on how the games are grogrammed.

Go ahead and check my emulator in github.
[Famulator Famicom/NES Emulator](https://github.com/tsubo164/Famulator)
