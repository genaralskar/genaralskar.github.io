---
title: "Prototypes"
date: 2020-06-18
categories:
  - game
  - blog
tags:
  - game
  - unity
toc: true
---

Over the 3 or so years of learning Unity I spent a lot of time making little prototypes for games or game ideas to see how they worked. I really helped me figure out some stuff about how specific systems worked and I always learned something new.
From rolling a ball, to moving a player, to working with AI, building RPG systems/skills, working with audio and rhythm games, and so many other things, anytime I wanted to learn how to do something I'd sit down and build something.
I'll try and compile all that stuff into this post and post as many playable builds of things that I can. Most of this stuff is exploring a single mechanic, getting the code to work, then dropping it for some other thing I wanted to figure out.

**If the Twitter embeds aren't showing the videos, try using a different brower. I noticed they don't show up on Firefox for some reason, but Chrome seems to work fine**

## PUCK BALL!!! With a P!
This was basically the first game I ever made in Unity during my intro scripting course. It wasn't even a school project, this was just something I made on the side. I learned a lot, but is no doubt a mess at this point compared to what I know now.
Maybe I'll go back and remake it one day.

[Play on itch.io](https://genaralskar.itch.io/puck-ball) (Controllers required)

[Github](https://github.com/genaralskar/Unity-Projects/tree/rigidbodyPlayerController/Bullet%20Ball%20Prototype)


## Roller Ball
I think I was watching some lets play of marble madness or a similar game and got inspired to make this. I think the biggest thing I learned from this was using rigidbody torque instead of just adding force to an object. It really added a lot to the feel of the "game." I got to a point where you could roll around some terrain, jump of a booster, and flip gravity (sort of). The problem with changing the gravity was that the ball was still spinning the same way, so if you're rolling forward, start to move upwards and hit a ceiling, the ball will start moving backwards, because that's the way it's rolling. I supposed now I could go back and just rotate the ball with the gravity so its keep rolling in the same direction.

I guess I don't have any videos of this and I can't find the project currently :c. If I find it I'll update this page with it


## Idle Game
I really like idle games, so I decided to try my hand at making one. This was early on in my game dev "career," so there was still a lot I didn't know how to do well, but I gave it my all! There is a lot of stuff running in update if I recall. At the time I didn't really know a better way to update stuff like sliders or timers or whatnot. Kinda funny considering I barely ever use Update for anything other than inputs anymore (and with Unitys new input system I might even be able to stop doing that!). Unfortunatly when I opened the project I was greeted by a mess of broken UI elements. Bummer.

<span><img src="{{ "/assets/images/prototypeIdleGame.png" | absolute_url }}" alt="" /></span>


## Grapple Mechanics
I wanted to try to make a 3d grappling hook but most tutorials I found never were about what I had in mind. I people think of grappling hooks, at least in terms of video games, as more like the hookshot when what I wanted, which was more like the grappling hook from Wind Waker (ironicly enough). I wanted something you swing around on instead of something that pulls you're looking. I think I settled on create a joint at where the player is looking, so the player just swings on that.
<div style='position:relative; padding-bottom:calc(53.25% + 44px)'><iframe src='https://gfycat.com/ifr/advancedzealousfrigatebird' frameborder='0' scrolling='no' width='100%' height='100%' style='position:absolute;top:0;left:0;' allowfullscreen></iframe></div>


## Inventory Systems
Ooohhh boy, here's something that I keep deciding to make for some reason. I've had so many different iterations of these things, but they got better and better everytime. I remember the first time doing it I was so confused. The tutorial I was using had so many things named "slot" something or other and I had no real idea of how things where connecting. This is mostly related to the frond end of the inventory, which IMO is a lot harder to figure out than back end stuff. Things like item slots, item dragging, item swapping/equipping. There's a lot to it. I do remember taking a night to sleep on it and waking up in the morning with a much better understanding of it, and that's not the last time that's happened either. Anytime I have a hard time figuring something out, I always sleep on it. I find it almost always helps when trying to understand how something works or figuring out a problem.


## Various RPG
Speaking of inventories, I have a terrible habit of trying to create rpgs/rpg like systems in game. On example is one of the first RPG like games I tried making, based very much on Runescape. I got player movement, camera movement, gathering and some basic inventory stuff done, but that's about it unfortunetly. But this would not be my last foray into the subject, which at least 2 other projects with very similar elements in them.
<div style='position:relative; padding-bottom:calc(53.25% + 44px)'><iframe src='https://gfycat.com/ifr/lonelyadventurousichidna' frameborder='0' scrolling='no' width='100%' height='100%' style='position:absolute;top:0;left:0;' allowfullscreen></iframe></div>

*Piggy One.* This time I put some focus into a dialog system for the game and managed to come up with something I was pretty proud of. It uses Unity's built in animation state machine for a dialog tree, where each state is a dialog section.
<a class="twitter-timeline" href="https://twitter.com/GenaralSkar/timelines/1273749985763323909?ref_src=twsrc%5Etfw">RPG Game Stuff - Curated tweets by GenaralSkar</a> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script> 

*Gnomey One.*
Another game is a similar style, wasn't meant to be very RPG heavy, mostly like a crafting game. I'll go more into in the **Build A House** section down below.


## 3D Platformer
I think this was just after I beat RIME, an incredible game, and it inspired my to try something out of my own. I believe the movement was also inspired by a talk from a creator of Overgrowth. I got basic movement down and had just started working on an edge climbing mechanic, before moving on to something else. The edge movement stuff mostly worked except if the wall curved a bit, I was still trying to figure that out at the time but never finished it.
<div style='position:relative; padding-bottom:calc(53.25% + 44px)'><iframe src='https://gfycat.com/ifr/dizzyhorribleeskimodog' frameborder='0' scrolling='no' width='100%' height='100%' style='position:absolute;top:0;left:0;' allowfullscreen></iframe></div>


## Top Down Fighter
This one was gonna be fun. Basically you have a sword that swings in wide arc around you, and you move around attacking enemies and deflecting their bullets back at them with your sword. It was supposed to be a simple game, something I could actually finish and call done, but considering it ended up here you can probably guess how that turned out. I did spend some time with a health system in this on though, and some enemies even had armor you had to knock off before you could damage their health, which was fun.

I'll have to look around for the project for this, hopefully I still have it somewhere.

## Kingdom Builder
This one was fun. Bascially you have a pool of people in your kingdom that automatically get assigned to buildings to gather resources. The more resource you get, the more buildings you can make, which in turn gives you more resources. Its really fun to get a ton of little guys and just watch them run around to the different buildings.
<div style='position:relative; padding-bottom:calc(53.25% + 44px)'><iframe src='https://gfycat.com/ifr/nicewanbluetonguelizard' frameborder='0' scrolling='no' width='100%' height='100%' style='position:absolute;top:0;left:0;' allowfullscreen></iframe></div>


## Rigidbody Navmesh Agents
For a school project one semester we needed a way to knock around AI. So I worked on a way to switch the enemies from AI Navmesh Agents (to walk around) to rigidbodes (to knock around) and back again.
<div style='position:relative; padding-bottom:calc(53.25% + 44px)'><iframe src='https://gfycat.com/ifr/inbornmasculinecottontail' frameborder='0' scrolling='no' width='100%' height='100%' style='position:absolute;top:0;left:0;' allowfullscreen></iframe></div>


## AI Royale
This was a test of creating an AI system that worked in a battle royale setting, but also using scriptable object behaviors for inputs which lead to some pretty cool stuff. Basically, instead of one script having all the states for a character, it would
ask an attacked scriptable object what it should do, more specifically where to move and where to look. Doing this, it was possible to swap the scriptable objects at runtime, which allowed for a change in behavior. So you could go from wandering, to following another player, to running from another player, back to wandering just by swapping out the scriptable object behaviors. The coolest thing (in my opinion) about this is it didn't have to be AI. You could swap the behavior for one that used player
inputs! since all it did was tell the player where to move/look, just move it/face it where the player wants it! This lead to the ability to take an AI that's wandering about and easily let the player take control whenever they wanted!

I think this really affected the way I think about character controllers, seperating the inputs from input processing is super powerful. It ended up popping up, entierly unintentially, in another project called Build A House. I build the player controller with the intention of it being a single instance/single player game, but at some point duplicated it and realized I could easily turn it into it's own AI! Since the movement basically just took in a position or object to interact with, I could create an AI controller that told it where to move to/what to interact with very easily.
<div class="video-container">
<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/fEjWA4GYdWc" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>


## Rhythm Game
I had an idea for a Rhythm fighting game. Basically two players tap the same note at the same time (probably on opposite ends of a phone screen). When you tap a note your fighter in the middle of the screen does some fighting moves against the other
players fighter. And if you miss a note the opponent fighter takes some damage. I think the prototype ended being a bullethell type game where enemies fire at you in beat with the music. 

The biggest thing I learned from this was about syncing moving objects to the music. It's not enough to just spawn on beat, because sometimes the game freezes for a bit, or the framerate isn't consistent, so you could have multiple objects spawn on the same
frame, or a few frames too late (which can cause syncing issues), and not be where they should be. Instead, they need to be offset from their previous positions by some Audio deltaTime instead of Time.deltaTime. Unity has a different timer running for its audio, but as far as I know doesn't have a deltaTime feature
for it, so one must be created, BUT using it would result in objects being moved to their proper positions even if spawned at a "wrong" frame. I never implemented this, but did write it down somewhere for future reference if I ever decide to take a crack
at another rhythm game.

<a class="twitter-timeline" href="https://twitter.com/GenaralSkar/timelines/1273749700743553024?ref_src=twsrc%5Etfw">Rhythm Game Stuff - Curated tweets by GenaralSkar</a> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script> 


## Procedural Dungeon Crawler
A lot of this was just figuring out the dungeon generation itself, which was quite a challenge. I eventually ended up with a node based system with prebuilt rooms, where the rooms were just connected to each other at their doors.

<a class="twitter-timeline" data-height="1000" href="https://twitter.com/GenaralSkar/timelines/1273748454934581248?ref_src=twsrc%5Etfw">Procedural Dungeon - Curated tweets by GenaralSkar</a> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script> 


## Build A House
This started out as a simple crafting game, but of course started getting more and more complicated to make it more interesting/fun. I still need to go back and finish it, there wasn't too much work left on it.
This is about where I decided I had to add little AI buddies running around
<div style='position:relative; padding-bottom:calc(53.25% + 44px)'><iframe src='https://gfycat.com/ifr/frequentobviouskoi' frameborder='0' scrolling='no' width='100%' height='100%' style='position:absolute;top:0;left:0;' allowfullscreen></iframe></div>
And here you can see gathering/crafting
<div style='position:relative; padding-bottom:calc(53.25% + 44px)'><iframe src='https://gfycat.com/ifr/illfatedlongbushsqueaker' frameborder='0' scrolling='no' width='100%' height='100%' style='position:absolute;top:0;left:0;' allowfullscreen></iframe></div>
[More videos of the project](https://gfycat.com/@genaralskar/collections/o26DpxKW/gnomy-game-gh79)

## Minigolf
