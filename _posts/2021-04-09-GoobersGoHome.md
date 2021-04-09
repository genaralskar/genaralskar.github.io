---
title: "Goobers Go Home"
date: 2021-04-09
excerpt: "A game about some goobers"
header:
    teaser: /assets/images/goobers/gooberSplash.png
categories:
  - devlog
  - game
tags:
  - C#
  - unity
---
I wanted to make a 2D platformer, so I made Goobers Go Home! It's still a work in progress, so not playable anywhere yet, but I'll probably release an early build at some point.

### Story
The idea behind the progression of the levels is the Goober's ship crash landed on a planet and they were scattered all over. You have to get back to the ship, and to do so have to go through a few different environments, starting low in the caves, and making your way up high to the mountains.

Each level would introduce a new concept, or expand/increase the difficulty of a previous concept. Starting from basic platforming and jumping, introducing obstacles, adding player health, adding jump refreshers and finally additional jumps. Then putting them all together, and possible having more environmental mechanics added too, like slippy floors or strong winds in the mountains maybe.

I'm debating whether you will play the same Goober the entire time, or if every few levels you take the role of a different Goober.

## Character Controller/Abilities
You are a ball, and a bit bouncy too. You get the ability to jump, multiple times too. You can also get some hearts that increase how many hits you can take. Pretty simple stuff.


## Levels
Level 1 is hardly a level really, more of a short intro. You spawn in and move to the right, run into the beam and get taken up. Then the title card shows up and it fades to black. There are a lot of foreground and background elements here working with some parallax to give a good look to everything. It can take a bit of time to setup something like that since they were all made in Unity's tilemap system.
![level1]

The second level introduces jumping. You get a large brown mushroom, which gives you the ability to jump. Then you go through some simple platforming.
![level2]

Level 3 introduces some hazards and more platforming. You even get a heart at the end so you can survive taking some damage now. Also, by some hazards I mean there's actually quite a bit of spikes. And speaking of spikes...
![level3]
I created a script to help automatic the placement of spikes! Each set of spikes is inside a container that lets me choose how wide a row I want to make, then instantiates the proper amount of spike sprites and sizes the collider accordingly.  
![spikes1]  
It even has a handy outline to show you where the spikes will be  
![spikes2]

Level 4 is where you're introduced to the jump refreshers. When you collect a small brown mushroom you get an additional jump, at least until you touch the ground again. Since this level involves a lot of jumping it had to be more spread out that previous levels. Again, I use coins and now mushrooms to help guide the player where to go. The right side of the level (cut off in the picture) is another area where the player unlocks a permanent double jump. This is also the level were I started using Tiled instead of Unity's built in tilemap, and wow was it so much better! (I'll talk about this later)
![level4]

### Future Levels
Level 5 will take place in some grassy, hilly area. That's where you end up at the end of level 4. I know at some point I want a level in the mountains, because I have some nice wintery music I wanna put in. I think after that the Goobers make it back to the ship, and the game will be over! We'll see how much I can do with the two simple power ups.

## Tilemap

### Unity's tiles
At the time of writing this, it's been a while since I've used Unity's tilemap system so I can't talk to in depth about it, but I do remember it being kind of a pain in the butt. I think selecting tiles, creating the tilemaps, making sure you painting on the right layer (or if it even had layers?). It doesn't sit as a good or neutral memory in my mind, but I couldn't tell you why exactly, again, it's been a while. Instead let me tell you about Tiled.

### Tiled
This is a program designed specifically to make tilemaps, and it is amazing! I had discovered and used it on a previous project, [2DPG]({{ "/game/devlog/2dpgDevlog/" | absolute_url }}), and decided to give a go for a platformer. Again, I don't remember much about Unity's tile system, but I know Tiled is better. Setting up tile sheets is a breeze, setting up colliders is fairly easy, the importer plugin SuperTiled2Unity automates a bunch of stuff like render layers and colliders, even placing prefabs! It was an enjoyable experience, and I wish I had used it since the start of the game.

[level1]: /assets/images/goobers/level1.jpg
[level2]: /assets/images/goobers/level2.jpg
[level3]: /assets/images/goobers/level3.jpg
[level4]: /assets/images/goobers/level4.jpg
[spikes1]: /assets/images/goobers/spikes1.jpg
[spikes2]: /assets/images/goobers/spikes2.jpg