---
title: "Sylphlings"
date: 2021-07-20
excerpt: "A cute game about a closed species"
header:
    teaser: /assets/images/sylphlings/header.jpg
categories:
  - devlog
  - game
tags:
  - C#
  - unity
---
For the past few months, I have been working with the people at [https://www.sushlings.com/](https://www.sushlings.com/) (rebranding to Sylphlings) to create a game for them. Sylphlings is a closed species, which basically is a fictional "race" of characters that an artist makes, and people buy the individual characters so they can do stuff with them, like commission art of the character or make plushies or something. You may find more info [here](https://www.deviantart.com/closed-species). I've been seeing a lot of "adoptables" on Twitter lately and it's kinda the same thing.

There is an embeded video at the [bottom of the page](#videos) of dev videos showing progress and features.

## The game
Along with characters users can purchase, you can also acquire other items for your character. Tools, boosts, clothes (although they don't show on the character art, but you still get them in their inventory). It reminds me a bit of Neopets, where you could get your pet, play games on the site, buy stuff for them, that kinda thing. That's sorta the vibe the game is going for. I'll talk a bit about parts of the game I've worked on.

I should point out, I haven't worked on any of the art. Most of it was created by Saunt and the art team. Other temp art is open-source art being used as a place holder.

### Database
The biggest challenge with this project was definitely connecting it to the database. All the info for players and items and whatnot is there, and I knew I wanted to keep it there. The client(player) should have *no* control over what they have. So anytime the player views their inventory, or buys/sells something, it's always doing the work on the server then just pulling that info again and showing it to the player. The game basically works as a front end to the database/server's backend.  

I had never worked on database stuff before, so this was certainly a challenge. I had to figure out a lot of about getting the information, pushing information to the database, and getting it all work and display inside of Unity. I learned a lot and also learned about callbacks, which how did I not know about them before? I've been implementing them in my code a decent amount now because they're pretty useful!

### The Hub
![Hub](/assets/images/sylphlings/header.jpg)
The hub is the main area of the game, and where the player starts. It connect to different buildings which will have different things to do inside. Some examples include a shop, a library, and a crafting building. The pond also links players to the fishing minigame, and more is still to be added.

The player can move and interact with everything simply with the mouse. One hope is that this can be played on mobile, so keeping the controls simple to just clicking is good. I'm taking a lot of inspiration from Club Penguin (the old one) for how the players move and interact with things. Hovering over certain interactable objects also shows a small text description of what the object is, and other things are possible like animating or changing the sprite when you hover the mouse over something.

### Shopping!
![A Shop](/assets/images/sylphlings/shop1.jpg)
Setting up the all the inventory interactions, ui, and on top of that shopping was kinda of a pain in the butt! *Thankfully* I've been torturing myself with inventory systems for the past few years and all that experience can in very handy. There's some cool features of the inventory displays including selecting an item to show info on it, the player inventory displays the current amount of an item a player has, and a nifty page feature where you can cycle through your inventory if you have more items than can be displayed at once (this was was pretty fun to figure out).

### Fishing
Fishing was big on the list, and is the first minigame being created! There are different fishing areas, that I refer to as fishing holes, that hold different fish. Each hole requires a different bait to be able to fish at. Bait can currently be bought at the store, but might be obtainable other ways in the future, like through crafting or a minigame. Fish shadows appear around the fishing hole, which you click to start fishing in a way similar to Animal Crossing or Harvest Moon. You wait for an indicator to appear and if you  click fast enough, you might catch something good!
![Fishing](/assets/images/sylphlings/fishing1.jpg)
(Very much dev art, the (i)'s are the placeholder fish shadows)

### Dialog
Dialog isn't a huge part of the game, but something that can add a bit of life to things. There are actually two kinds of dialog, what I'll call "Box Dialog" and "World Dialog."

Box Dialog is dialog that pops up in a dialog box. It shows a customizable image and name for who's talking and you can move through the dialog by pressing the continue button. This could be for talking to characters, examining objects, or just getting some information.
![Box Dialog](/assets/images/sylphlings/dialog1.jpg)

World Dialog is dialog that appears in the world, and not in the box. It can show up over an object or character's head and cycle through dialog at a fixed rate, like once very 3 seconds. This can be used to give the player some quick info, like a sign, or some inconsequential dialog like "sure is hot today." It's used in the library too, when you enter the library greets you with a short message that appears above her head.
![World Dialog](/assets/images/sylphlings/dialog2.jpg)

## Videos
<iframe width="560" height="315" src="https://www.youtube.com/embed/videoseries?list=PLw_1-UMpRux9_08b6Mnkg7p-tA1fsx9Xg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>