---
title: "Unity LPC Character Workflow"
date: 2020-09-15
excerpt: "Some tools and things I've made"
header:
    teaser: /assets/images/lpc/theBois.jpg
categories:
  - game
  - devlog
tags:
  - unity
---
## LPC Character Workflow
I have recently started "working" (more of experimenting) on a game and have been using the LPC system for my sprites. LPC stands for [Liberated Pixel Cup](https://lpc.opengameart.org/), and is basically a standard for pixel art style/sizing. This includes environment tiles as well as characters, which is what this is concerned with.

I wanted to try to make a character customizer with this system, as it seems to lend itself to it pretty well. This meant lots and lots of sprites and animations for each item, and clips for each way the item could move. Idle, walk, slash, thrust, magic, shooting, and dying; and each is 4 directional variations, excluding the dying one. That's a lot, not something that could be easily done with one man. Unless...

Tools! I made a few tools to help make this workflow easier and faster and actually feasible to complete. I did another post on tools [here]({{ "/game/devlog/Tools/" | absolute_url }})

### Multi Sprite Slicer
Unity has, as far as I can tell, no built in way to slice multiple spritesheets at the same time. After some research I was able to find a way to do it through script, and made my own version. The slices are ordered and named in the same fashion as how Unity does it. You can choose how large each cell is, and where the pivot for the sprite should be. Just open the tool, choose your setting, select all the sprites you which to slice, and hit go!

<div style='position:relative; padding-bottom:calc(53.25% + 73px)'><iframe src='https://gfycat.com/ifr/sorrowfuloblongamericankestrel' frameborder='0' scrolling='no' width='100%' height='100%' style='position:absolute;top:0;left:0;' allowfullscreen></iframe></div>

Some things I still need to add are padding, and I need to see if there's a way to delete cells with no information in them, ie blank sprites.

### Animation Clip From Sprite
Creating animations with sprites is a bit of a pain as you have to add the sprites one by one to each animation. What this tool does it let you choose a pre-sliced sprite sheet (thus the need for the previous tool), choose a frame rate and a name, and automatically create an animation clip from it! Speeds up the process a lot, especially with so many animations.

<div style='position:relative; padding-bottom:calc(53.25% + 73px)'><iframe src='https://gfycat.com/ifr/sickvelvetydairycow' frameborder='0' scrolling='no' width='100%' height='100%' style='position:absolute;top:0;left:0;' allowfullscreen></iframe></div>

### LPC Specific Animations
This is where things start becoming more specific. Each replaceable piece needs animations for each of the animation types, as listed above (the walking and stuff), but thankfully since it's standardized all the sprite cells and things are in the same place! So this is a modified version of the Animation Clip From Sprite tool above, just some added functionality like creating some folders for each replaceable piece for better organization, and choosing which type of animation the sprite sheet follows, so it knows how many cells to animate and whatnot. This even supports the [Universal LPC Sprite Sheet](http://gaurav.munjal.us/Universal-LPC-Spritesheet-Character-Generator/#) so you can import entire animation for a specific piece, or a character if you don't want them to be customizable.

<div style='position:relative; padding-bottom:calc(53.25% + 73px)'><iframe src='https://gfycat.com/ifr/officialuncommonfowl' frameborder='0' scrolling='no' width='100%' height='100%' style='position:absolute;top:0;left:0;' allowfullscreen></iframe></div>

### Populate LPC Override Controller

<div style='position:relative; padding-bottom:calc(53.25% + 73px)'><iframe src='https://gfycat.com/ifr/honoredathleticboutu' frameborder='0' scrolling='no' width='100%' height='100%' style='position:absolute;top:0;left:0;' allowfullscreen></iframe></div>

Unity has a system of [Animation Override Controllers](https://docs.unity3d.com/Manual/AnimatorOverrideController.html), where you take a base animation controller and just replace the animation clips, which allows for easy customization. It uses all the same logic as the base controller, but allows for custom animations for whatever you want. So like the same logic to activate/blend a walk cycle, but different animations for a human walk cycle, orc walk cycle, and dwarf walk cycle (or whatever other animations you want to replace). There is unfortunately no build in way to automate this, (you have to drag each clip into each slot manually), so that's what this tool does.

LPC has a bit of a layering system where each piece of clothing can be overlaid on top of a base sprite and it will still look like it's one sprite (so like the handle of the knife won't show up over the hand or anything). This means they also have the same animations as the body sprite, so using the override controllers means there's one place the animation logic is stored, and the appropriate animations are just replaced.

So once all the animation clips for the sprites are created, an animation override controller can be created, and the tool can be used. Select all the clip you want to replace the old ones, select the override controller, and use the tool, and it will go through at match, by name, the selected clips to the proper slots in the override controller. They're matched by the last work in the clip separated by a space, for example `HEAD_Hat walkUp` would get matched by the `walkUp` part of the name, so you can still have descriptive naming, but they have to follow that convention.

Looking at it now, it's not actually specific to this LPC system, it could really be used for anything if the naming convention is followed.