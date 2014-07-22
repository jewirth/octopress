---
layout: post
title: "SpartanPong"
date: 2011-08-14 20:00:00 +0200
comments: true
categories: ["FPGA", "Tinkering", "VGA"]
---
Just out of curiosity, I tried to create a VGA signal with the <a href="http://www.xilinx.com/products/boards-and-kits/HW-SPAR3E-SK-US-G.htm">Xilinx Spartan-3E Starter Kit</a>. It all ended up as a Pong game with some funny behavior. Feel free to <a href="http://snej.de/downloads/SpartanPong.rar">download the project files</a> (created with Xilinx ISE WebPack 12.1) or just watch the video. The project runs at 640x480@60Hz. I learned about the VGA signal timing from <a href="http://www.epanorama.net/documents/pc/vga_timing.html">here</a> and of course by playing around a lot ;o)

<div style="text-align: center;">
<iframe allowfullscreen="" frameborder="0" height="270" src="http://www.youtube.com/embed/mkv2xCkXeN4" width="480"></iframe>
</div>

<br />

<hr><br />
<p style="line-height: 75%;"><small><strong>Comment from Anonymous:</strong> can you please explain why you thoroughly how you ball is moving?and why you took the cnt value=5000??<br /><br />
<strong>Answer:</strong> I suppose you mean 50000, right? Well, that's the speed of the animation as I preferred it. As you can read in the comment above "animation rate = 25 MHz / 50000 = 500 pixels per second". So, 50000 is the amount of cycles I have to wait to get a result of 500 pixels per second. The less I wait, the faster the animation goes. So, increasing this value slows down the animation speed. Play with the value ;)</small></p>
