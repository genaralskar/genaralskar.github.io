---
title: "FG Stream Helper"
date: 2021-04-09
excerpt: "I made a tool to help with fighting game streams!"
header:
    teaser: /assets/images/fgStreamHelper/overview.jpg
categories:
  - devlog
tags:
  - C#
---
## [Click me to download it!](https://github.com/genaralskar/FG-Stream-Helper/releases)

So a while ago, I wanted to start streaming some smash bros, or my friend was starting a tournament or something, I don't actually remember the details, BUT I started working on a stream overlay! I set up all the text elements then realized that updating all of them would start to become a pain in the butt! Open the left name text, change that, open the right name text, change that, open the bracket text, change that, and having to do that for the score text each time a game ends too!? I figured I could come up with something much better. Queue, FG Stream Helper! (The below gif is a slightly outdated interface)

![demo gif](/assets/images/fgStreamHelper/demo.gif)  
I made a tool to help speed up the process! You just put in the information you want and it exports it to individual text files that can be read by the text fields in your streaming software! You can even grab a set from smash.gg and it will fill in the info for you!  

Here's what the current version looks like
![current layout](/assets/images/fgStreamHelper/overview.jpg)

## Process
I first thought of making it in Unity, but then thought that might be a bit too much for something so simple. I had run into WPF at some point and thought about giving that a go! It certainly took a while to figure it out, but it was simple enough it wasn't too hard. I don't think I'm fully using the capabilities of the software yet either (no surprise haha). I "hard coded" the positions and layout of the interface, but I'm pretty sure there's a way to modularize it. I'd like to do this with the player section to be able to add some custom amount of players without coding them all individually.

### Pictures
I wanted to have the ability to export pictures along with the text, so you could have their current character next to their name or something. For the most part, I got it to work! Except sometimes it doesn't... Sometimes it likes to export the picture next to the one you want and I have no idea why. The path is always correct, it just sometimes grabs the wrong file. I imagine it's something to do with the actual File stuff in C#, which I have no control over, or there's something about copying images with it that I'm messing it. So for now I've just set it as an "experimental" feature. You can still use it, but it's not guaranteed to work 100% of the time.

### API
The API to grab sets for smash.gg was also a pain to implement. I'd never worked with API or anything before, so there was certainly a steep learning curve, and most of the tutorials I found for it were about setting up a server-side API, not about getting that information, which was even more frustrating. Eventually though, I got it to work, yay! It got the names of both players, the current bracket name for the set, and the scores for each of the players! Now it's time to use it in a real tournament and oh looks it's broken...

When I used it the first time on an actual stream it wouldn't get the info for the set. Great. I thought maybe smash.gg had changed their api since I made the program (it had been a while between when I made it and when I used it). But a little bit later I tried it again and now it worked? Uhhh... Well, a bit of digging, and it seems to only break during a set in progress. So I check if there's an example to get a set in progress, and it's the same syntax as getting any other set. Ok, so maybe it's returning something wrong? Lo and behold, if a set is in progress and a player has a score of 0, the api returns their score as null rather than 0. And whatever I'm using for getting that info doesn't like that as it's trying to set a float to null, which C# doesn't like apparently.

So until I find out how to check if the value is null before assigning it, I now just reset the scores to 0 instead of get them from the set. I figure you're mainly going to be grabbing the info at the start of a new set, which means the scores will be 0 anyway, so it shouldn't be a big deal.

## Future
There's a few things I'd like to implement. I'd like to modularize the players as I said before. I'd like to add hotkeys to update the scores. I'd like to properly grab the scores from the api. I'd also like some kind of logo/icon for the program.

But right now, I'm really happy with it. It does what it's supposed to, it's easy to use, and I even without the smash.gg importing I was able to use it to great success during a tournament stream.