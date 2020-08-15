---
title: "The Cube Finalized!"
date: 2020-08-15
excerpt: "A mysterious cube lurks beneath the surface. Can you figure out its secrets?"
header:
    overlay_image: /assets/images/theCube/cubebanner.png
    teaser: /assets/images/theCube/theCube.png
    actions:
      - label: "Play Now"
        url: "https://genaralskar.itch.io/the-cube"
categories:
  - game
  - devlog
tags:
  - unity
---

## A mysterious cube lurks beneath the surface. Can you figure out its secrets?

Hidden deep in the recesses of the earth lies a strange cube. It seems to operate on some kind of magic, but no one has been able to figure it out yet.

### I made a previous post on this with some more info! Check it out [Here]({{ "/game/thecube/" | absolute_url }})



This one has been a long time coming. Originally designed as a puzzle for my current D&D campaign, it took longer than expected for the party to get to this point, so I didn't actually finish it until about a week before they got there. This is the first time I have been a DM, so when I had everything for the campaign planned out I thought we'd be through it in a few weeks. Cut to 6 months later and we're just now finishing up, haha.

I started building out The Cube at the start of the campaign because, again, I thought we'd get there pretty quick. I started planning a little while before, making maps and notes on what goes where and how things affect each other. The nature of the puzzle itself, with all the twisty turny bits, made it a bit difficult to get my head around, and the puzzle itself went through some iterations to both simplify some parts but also to implement some new ideas.

## Inspiration
![hallway][hallway]

This puzzle, along with a lot of my interests was inspired on some puzzles from Runescape. The crystal/light puzzle was inspired by the quest Temple of Light, where you needed to place some reflectors/colored crystals to redirect beams of light to certain spots on the map. In my version though you're not redirecting light, just recoloring it, but the crystals must be placed in the correct spots to produced the correct colors.

The coin puzzle was inspired by the quest Eyes of Glouphrie. There is a coin exchange puzzle where different shapes and colors of coins represent different values, and you must insert the correct coins to get to the proper value. My version is a bit simpler with only shape determining value, but you must also figure out the value of the shapes on the doors to know what the proper value is.

The coin door puzzles actually came in a bit late into the planning of The Cube. I came up with the idea a while before, and wanted it to be a physical puzzle for my players to interact with (like I'd build a box and coin props and stuff). But due to Covid, and me moving away, that just wasn't to be, unfortunately. So I added it into The Cube. I had to do a bit of refactoring and replanning, but I feel like I managed to integrate it pretty well.

I also wanted this to be something rather difficult, something that would take a while to figure out. It's sort of inspired by Myst in that sense, just having to try a bunch of stuff until something works. I feel like most of the puzzle is figuring out how everything works together, and once you get that it's easy enough to put everything in the right spot.

## Play Testing
![cube spinnger][spinny]
As mentioned before, I "finished" the game less than a week before the play session. I didn't do much, if any testing really, on the build version of the game; I just assumed it would work the same as the editor version. I was wrong.

As we started the session, the first, and one of the biggest issues, popped up. You couldn't actually interact with the coin inventory, which meant you couldn't actually progress. I had noticed that the UI didn't updated properly when I tested out the build, but it did update when I actually picked up some coins, so figured it was just some Unity thing, but of course it wasn't. I figured out that it was due to trying to access something in Awake that had yet to be assigned. Simple fix, just moved that part to Start instead. Now it worked! The UI update properly at the start, and you can actually use the coins now!

My players are thankfully very forgiving, and as we were all in the same game dev program, very understanding as I fixed the problems that popped up. I don't think there were anymore game breaking issues, but quite a few game design/level layout issues.

I think the next one I noticed was I forgot to put a vital bit of info on the coin comparitor, which told that the triangle shape = 1 unit. Simple enough fix, tell the players, then update it for the next build.

Then I discovered, or at least my players discovered, some doors were missing. Mostly doors that were meant to block the players off from certain areas. I thought I had everything placed but I guess I was wrong. That's what I get for not double checking everything.

At this point I realized, mostly due to my players pointing it out as a possible solution, was that the color of the lights on the 2 floors corresponded with the colors of the first two crystals you place down. Red crystal on first floor, red lights. Blue crystal on third floor, blue lights. Stands to reason the third crystal, a green one, should go on the second floor with the green lights. I had not intended this, and started to really appreciate how far play testing and help your game. I added the different color lights to differentiate between floors, so when you teleport there was a simple visual indication that you were somewhere else, and you can figure out which floor you're currently on by the color. I didn't realise they matched the gem colors, and would have changed them if I knew it would confuse the players.

I also noticed that if you removed a crystal from the pedestals on the second floor, where the crystal focuses are supposed to go, all the coin doors would reset. This was an untended consequence of how I opened/closed the colored doors by calling their colors. The crystal, the pedestals, and coin doors were set to the color White, which was used as a sort of empty color, and don't open to anything, but the pedistal would call all doors of that color to close when a crystal was removed, including white. So when a crystal was removed from the "white" pedestals it closed all the white doors, all the coin doors.

One other thing I ended up changing in the final release was adding a few spots to the "color helper" item. This item was to help show which colors go where. I just added a few more colors to it to make it clearer where things go.

## Final Thoughts
![teleporter][teleporter] 

Overall it'd call it a sucess. My players were pretty brain dead by the end of the night, but when all the crystals were in place the ending screen showed up (thank goodness (I also didn't test it haha)). I'm able to call it finished, and it can be beat. It's not often I actually get a project to that state.

[cube]: /assets/images/theCube/cubebanner.png
[hallway]: /assets/images/theCube/cs2.png
[teleporter]: /assets/images/theCube/cs3.png
[spinny]: /assets/images/theCube/cs1.png