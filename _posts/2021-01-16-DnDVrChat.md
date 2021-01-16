---
title: "D&D In VR Chat"
date: 2021-01-16
excerpt: "A breakdown of my thoughts and challenges of running a session in VR"
header:
    teaser: /assets/images/dnd/vrcity1.jpg
categories:
  - game
  - devlog
  - dnd
tags:
  - unity
---
## Prelude
For a while I've had this thought about running some DnD sessions in VR chat. During college I attended a VR conference and they had a presentation for VR Chat. Before that, I thought that VR Chat was just some place to do social stuff, meet people or whatever, in VR, but after seeing some of the awesome things people were able to make with it I started getting ideas for what I could make with it. One such idea was running a DnD game in VR chat; creating a world that holds character sheets, lets you roll dice, place minis and object on the map. I even had an idea where the entire thing took place on a large battle mat, to scale with the players, while the DM was giant, like they were using a normal sized battle map. After a bit of research though, this idea quickly died when I learned you couldn't do custom code in your worlds. A bit disappointing, but I did learn they were in the process of making a system where you *could* write your own code, but for now I put the idea on the back burner.

Cut to several years later when I remember I wanted to try this, so I check in with VR Chat again, and lo and behold they have have released Udon, their coding system! A node based, visual scripting system that has access to most of Unity's and C#'s functionality (with some stuff hidden for security reasons) and the dream lives again! Time to download it and start learning how it works. I'm not particularly fond of visual scripting as it turns out. I find it slow, tedious, annoying to find what I need, and very messy. This is my first real experience with something like this, so I'm sure overtime I'd figure it out but if there's some way *not* to, I'm all for it. Queue [Udon#](https://github.com/MerlinVR/UdonSharp)! Someone made a compiler that compiles C# into Udon! Well, with those barriers out of the way, time to get creative!

## Challenges
Needless to say, it did not go entirely smoothly. I didn't really expect it too, I've learned that even a problem that seems simple will stop you in the least expected way.<br>
I should preface this by saying, I have yet to run the actual session. These are simply the problems I have faced during planning/potential issues I can foresee.

### Udon
One of the more annoying problems is working around Udon's limitations. There are a few things about it that keep popping up that keep making me rethink how I need to do something. One issue is client/server relations; figuring out how to get/send information to the proper player, mainly hiding things the DM does, while allowing all player interactions to be public. I'll talk more about that in [THE BOOK](#THE-BOOK) section.

Another problem is communicating between scripts. Usually to achieve complex functionality, I break it down into several scripts that each do a specific thing; pretty basic object oriented programming stuff. Then just get/set references to what is needed, and send data through for processing. The problem is, it can be difficult to do that with Udon as you can't really send data through. To call a method on another script you have to use the SendCustomEvent function which only takes a string as a parameter, which is the function name you want to call. This has led to a few annoying workarounds I've had to do.

For example: spawning dice. Usually, I would have a script with a list/array of all the dice (in order), then one public method that takes a single int value: `SpawnDice(int index)` This would take the index parameter, and use it get the proper die from the list/array, then move/rotate/enable/do whatever else needs done to it. Then just call `SpawnDice(value)` from somewhere to spawn a die! The problem comes in with that last part. With Udon, you can't send info through the function call, so I can't specify an index value in this case. Instead, on the SpawnDice class, I have to create a method for each possibility, `SpawnD4()`, `SpawnD6()`, `SpawnD8()`, then each method calls the `SpawnDice()` with the appropriate value. Not the end of the world, but still a bit annoying, and makes building larger/more complex systems much more difficult.

### DnD
>Okay, I just wanna say I wrote a lot more here than I thought I would haha. A lot of this is interesting to speculate on, and important for me to get right so my players, and me, can have fun with this. There is a lot of overthinking going on here. I have some great players, I know whatever happens they'll have fun because we just like playing together, *but* that doesn't mean I can't try hard and make all the other DM's in my group jealous with how over the top this might be.

Now the question is, what to make the session about? While thinking of a story/story hooks that would work for this concept, I ran into a few walls too. One problem I'm been trying to get better at as a DM is openness, trying to let the players decide what they want to do instead of a more-or-less linear storyline they follow. Now, for one-shots that's a bit different, and with something like this even more so. The main issue I see with playing DnD in VR is the inherent linearity of it, due sole to have to have actual, built out sets. These take time to make, and they are rigid once in play, there's very little room for improve when it comes to location, and even NPCs. It wouldn't be a lot of fun to just walk around an empty town, or talk to thin air instead of an actual "person." So, the story has to be fairly linear, because if the players do/go somewhere unexpected/unprepared you can't really improv it. I mean, you could, but then you'd have to be doing theater of the mind, in the game world, in VR. It seems a bit too disconnected/immersion breaking at that point, which can be a problem.

**Character sheets** are also more-or-less out of the question. I recreating character sheets/inputting all the data for each character is a lot of work, and not something I'm willing to invest in at the moment. If there was a way to have a web browser in game that could solve one issue, and just have the player's character sheets online, but I don't think there is currently a way to do that. So that leaves lots of looking back and forth from VR to your computer screen/some paper in the real world, which is tedious and more immersion breaking. Now, if these were characters the players knew fairly well, they might have memorized some skill checks, but still I don't expect that from everyone, and for a one-shot that's out of the question.

Another problem that pops up is **combat.** Not having a character sheet in game, heck, even just having to make an entire combat system in VR Chat (which I'm not doing btw) is a problem. Also, I run sessions for a 6 person group, which means a LOT of downtime during combat, which I don't want my players to spend bored, just standing around doing nothing in VR. In my case, combat is probably best done out of VR on some tabletop software, FoundryVTT in my case, and probably best done once per session (which is pretty par for the course since it takes up so much time anyway).

**So what kind of stories does this leave?** Can't be anything too open, minimal skill checks, (somewhat) minimal NPCs, minimal combat. **Roleplaying** sessions probably fit best here. Talking to NPCs, players talking to each other, stuff like that. The biggest problem with this is an asset one, having enough unique characters/being able to swap to them at will/taking their place in the world when swapping to them. It's a lot of extra work over already having to act all the characters out. And heaven forbid you have to have two or more NPCs have a conversation together! There's a lot of suspension of disbelief the players will have to do, which is made inherently difficult with it being in VR.<br>
**Investigation/mysteries** are probably pretty good too, although that requires a lot of prep for VR, since instead of just saying "There are some bloody footprints leading away from the crime scene," you have to actually make bloody footprints leading away from the crime scene.<br>
**Puzzles** could be another good one, but this also involves making all the puzzles, making assets for the puzzles, programming all the puzzles, and hoping they're not to easy so they aren't all done in like 30 minutes.

Another consideration is **time.** Do you try to make enough content to last for an average session, in my case 3-4 hours? Or, just do what you do and if it's only an hour long just have it be that? How is time spent in a normal DnD session vs how will it be spent in VR? What to players to do waste time, and will they be able to do those same things in VR? There are actually a lot of questions and thoughts I have about wasting/stretching time, how it differs from video games and DnD, and transferring video game concepts to DnD (which I might make a post about later), but something I've failed to mention up to this point is that **this is, for all intents and purposes, more like a video game than DnD.** Well, a little of both but a lot more video game-y than regular DnD. And making a 4 hour long video game is hard enough in itself. The combat will eat up some time, and roleplaying too, but will players be able to roleplay as effectively?

Actually, **concerning roleplay,** it might not be that different. Players already imagine/act out a lot of what they're doing, which shouldn't be too different in VR. One issue might be players not in VR might have difficulty with this, but it still might allow for more/more interactive expressions than a webcam (which is what we're currently doing). I'm just thinking of Whose Line Is It Anyway, where they just act out all the props, but it still feels like they're there. Maybe that won't be just a big deal after all.

## Unity
Alright, enough Dnd talk lets get to the game stuff! What do we need, how much, how to make it work (hopefully), yada yada.

### The World
The smart solution for something like this would be something small, something simple, so of course I decided to have it take place in part of a large city... I originally had plans for something smaller, but then I had an idea for a better story so I went with that instead. I think I'm really better for it, because it really shines light on what the limitations/challenges for something like this are. The biggest one I have, in terms of the actual 3D world building, is performance.

![City overview, still a work in progress][city1]

Making sure a large-ish city runs at a good framerate, even on lower end hardware, is hard. There is quite a bit I had to do to make sure it runs well, and even still I'm not sure it will be smooth for everyone as I have a fairly beefy PC. But, I'll still talk about what I did, and what I wish I could do/might do in the future to help even more.

First off, Prefabs! I am using an asset pack that has lots of premade building prefabs, each one made of more prefabs of the different buildings parts. This can lead to a lot of variation, easy editing, faster rendering, and best of all, a smaller file size. Having static building meshes would probably save the most space, but it wouldn't allow for easy creation/editing of buildings.

Next, LODs! While the building assets I'm working with don't actually have LODs, I can still tie their renderers into Unity's LOD groups and have them turn on/off. The biggest issue with this is they don't seem to actually fade away, they more pop in and out, which can be a bit ugly, but I'm more than willing to have it be a bit ugly if it means a sizeable performance increase, which in my case, it did!

![lod0]

![lod1]

![lod2]

![lod3]

Finally, Occlusion Culling. This basically hides any object that is behind another object. If they camera can't see it, it just won't render it. The performance increase you get from it is incredible, and since you're on the streets surrounded by buildings most of the time, not a lot is actually being rendered. The main issue comes in with standing somewhere high up where it can't cull a lot, but in my current case that's not something what will happen often, and certainly won't be required for the one-shot.

<div style='position:relative; padding-bottom:calc(53.25% + 44px)'><iframe src='https://gfycat.com/ifr/maleimmenseaustralianfreshwatercrocodile' frameborder='0' scrolling='no' width='100%' height='100%' style='position:absolute;top:0;left:0;' allowfullscreen autoplay='0'></iframe></div>

Biggest downside of occlusion culling is just building the world with it. You have to bake the object's occlusion info, and if you move them afterwords, like relocate a building, it will use the old info for where to hide it. So the building might disappear even if you should still be able to see it. So instead I just clear the baked info while I'm working on it and I'll bake it at the end when I upload the world. Even still, with just the LODs I'm getting close to constant 90fps for the entire thing, so that's promising.

### The Characters
I mentioned this a bit above, and I'll briefly touch on it here, but making all the characters will take a bit of time. I have to make sure I use enough unique characters to its not too repetitive, and I also have to *make* all the characters. At the very least make VR Chat avatars from preexisting models, which is still a bit time consuming. I could just use other people's avatars, but then getting them in the world as "actual characters" would be difficult, and finding models that wouldn't be too immersion breaking/that would fit in this world could prove difficult.

## THE BOOK
I know I said I'd talk about what I have been lovingly referring to as THE BOOK, but this post is long enough as it is so I think I'll leave for another day (sorry). I'll leave with a brief overview of what is though. It's basically meant as the DM's notebook. It will hold all needed notes, allow for switching between characters quickly, spawning dice, teleporting around the map, and maybe a few other functions. You can open and close it, and it more or less just looks like a magical book to the players, which I think is pretty cool. I'll try and post more about it when I finish the session and give my thoughts about it then.

![the book][book1]


[city1]: /assets/images/dnd/vrcity1.jpg
[book1]: /assets/images/dnd/thebook1.jpg
[lod0]: /assets/images/dnd/lod0.jpg
[lod1]: /assets/images/dnd/lod1.jpg
[lod2]: /assets/images/dnd/lod2.jpg
[lod3]: /assets/images/dnd/lod3.jpg