---
title: "Scratch"
excerpt: ""
featuredImage: "./images/max_sharp.png"
publishDate: "2025-05-18"
publish: true
categories: ["Tech", "Progress"]

seo:
  title: ""
  description: ""
  image: "./images/max_sharp.png"
---

# Cast (Hall of fame?)

## Blue Max
The hero

Oh yes, there is a backstory. From the original game manual:

*\"You are Max Chatsworth. Known by your mates as 'The Blue Max' you
wear the very name of the medal given by the Axis powers to shoot
down your plane!  Now, you must earn the title.  To be successful
you  must  make a final assault on three specially marked targets
within the city.  You have only one aircraft and very little time
to accomplish this most difficult of missions.\"*


### Zaxxon
  The original isometric villain. This is the enemy boss robot from the eponymously titled 1981 arcade game.
  Blue Max was never forgiven for the axonometric perspective ripoff.
  Zaxxon finally had his rocket launchers repaired (both of them, including the one that never worked even in the 80s).
  Thusly rearmed, Zaxxon is now returning from his 2.5-dimensional realm for isometric vengeance. And he is packing a seemingly endless supply of missiles.

### Manfred von Richthofen
  AKA The Red Baron, the most famous of aces.
  No WWI aerial combat game could possibly be complete without an appearance by this guy.
  Although this was a real life person his ghost is still summoned for game level boss duty. And he is not happy about it.

### King Kong
Hobbies include skyscraper climbing. Prefers blondes. What is a big ape doing here? Nobody knows, but he seems to be a magnet for biplane fighter action.

### Bob Polin


### Peter Adams


### Mystery boss
  All we have seen so far is a plane shadow. Appears when you least expect it. What aircraft is this elusive villain piloting?


Why Blue Max? Why now?
So.
In conclusion the answer must be why not?

Goals
  Near zero budget. It's for fun. Creating this game does not make business sense. The world does not need another disappointing game full of ads or other desperate ways to make money.
  Ads to cover costs are acceptable in principle, but it should be non-intrusive. Hypothetically it could be fun with in-game ads, like sponsored airstrips.

  Naive graphics. Coder art and reused (free) assets will suffice. Gameplay should always be fun even without state-of-the-art graphics.
  Graphics doesn't have to be much better than [the original C64 Blue Max](https://en.wikipedia.org/wiki/Blue_Max_(video_game)), but object movements should be smoother.

  Multiple platform support. Ideally the game should be playable on all popular mobile devices and any reasonably modern desktop computer.

  The game should contain both 2D with isometric 2.5D-like game experience and 3D graphics. The idea is to write business logic code once and reuse for both 2D levels and 3D levels.

  Keyboard, touch screen and joystick support

  It should be self explanatory enough for a non tech savvy non-gamer to get started, play and enjoy the game on a mobile or desktop device.


Tech
  Unity was chosen for it's wide use and for the multi platform support.
  The current demo version is built for WebGL (webassembly) and is therefore playable in almost any web browser.
  Controls obviously are a little different on a touch screen device than on a PC.

  It turns out 
    Collision detection in a 3D level obviously require objects to overlap in all 3 dimensions.
    
Possible improvements
  Use the physics engine. Today the movements of almost all moving objects is controlled explicitly in C# code. Using Unity's phsics engine could be a cheap way to enable things like ricochet shots. It could even give a performance boost.

## Lessons learned
Everything should be scriptable. For so many reasons. I did not mention this among the project goals, it's just something I take for granted with any project.
I was a bit shocked to find there is no easy way to automate builds with Unity. It's point-and-click. That would be OK for a toy, not for a serious development environment.
There is a service named "Unity Build Automation" provided by Unity. This a managed service. An attempt to lock Unity game developers into Unity's own eco system. Using any other kind of automation seems discouraged.
Who wants "Unity Version Control"? Not me. The appears to be a free plan for Unity Devops, but I'm still not interested.

---
Unity Build automation:
https://www.youtube.com/watch?v=2v9BLSG02Go&t=4s
https://game.ci/docs/docker/docker-images/

docker run -it --rm unityci/editor:ubuntu-2020.1.1f1-android-0.3.0 bash
  The image is > 6GB  !!


## What?
This project is a variant of the classic video game Blue Max. More than merely a port, there are extra levels and quirks not found in the original game.

## Why?
It's about curiosity. Why do we play games? What makes a game exciting?
As a kid you don't ask such questions. You just play. Video games were amazing and the C64 was a thing of magic.

At 50+ it's different. I'm not much of a gamer. I don't keep up with the latest releases and I do not own any console.
Many game genres do not appeal to me. Idle games? You earn resources by waiting. `<irony>`Great.`</irony>`

Recently I browsed for free games on Steam and I was not impressed. One game was clicking a banana. That was it, just click it and score points. It was not moving or anything. Not challenging in any way. That game has fans!

Were the games actually better in the 80s or is just me being old and grumpy? Is it possible to feel the same excitement again as we once did?

I think creating a game to your own liking is the ultimate gaming experience. It's a great way to play and to learn marketable skills at the same time.

I remember a conversation back in the C64 days while playing a racing game with a friend (it might have been Pole Position). 
He wanted guns to shoot the opponent cars. I argued it was a sports game so of course you can't have guns. Now I think he was right. It would have been awesome to get a power-up out of the blue that would let you shoot your opponents! It's a game, let's make it fun.

Why Blue Max?
Of all C64 releases, Blue Max was certainly not the most advanced or the best looking graphically. It's usually not mentioned on top 10 lists, but it's my personal favourite. It was so well crafted and it had a wonderful mix of challenge and mystery. And there was more than one approach to playing a level, you could strafe at low altitude or stay safe and drop bombs from above.

So that's the game I'm going for: Blue Max with unreasonable additions, built on a modern game engine.
I want cameos from other games and movies. I want anachronisms. I want references to 80s cultural phenomena. I want sarcastic comments about the absurdity of finding friendly airstrips deep in enemy territory. No use trying to hide plot holes or defects. We are not fooling anyone so let's emphasize those things instead. And have fun.


## How?
The game is developed in Unity. The current version is built for WebGL and is available online. It is very much a work in progress.

## Who?
I am a semi retired SW engineer with many years of professional dev experience. Embedded, frontend, backend, testing, management. I have done it and I have seen technologies and trends come and go.

My experience in game development is quite limited. That is one of the reasons I'm having a go with this project.

