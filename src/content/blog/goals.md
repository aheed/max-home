---
title: "Project Goals"
excerpt: ""
featuredImage: "./images/max_sharp.png"
publishDate: "2025-05-20"
publish: true
categories: ["Tech", "Progress"]

seo:
  title: ""
  description: ""
  image: "./images/max_sharp.png"
---
## Main goals
- Near zero budget. It's for fun. Creating this game does not make business sense. The world does not need another disappointing game full of ads or other desperate ways to make money. Ads to cover costs are acceptable in principle, but it should be non-intrusive. Hypothetically it could be fun with in-game ads, like sponsored airstrips.

- Naive graphics. Coder art and reused (free) assets will suffice. Gameplay should always be fun even without state-of-the-art graphics. Graphics doesn't have to be much better than [the original C64 Blue Max](https://en.wikipedia.org/wiki/Blue_Max_(video_game)), but object movements should be smoother.

- Multiple platform support. Ideally the game should be playable on all popular mobile devices and any reasonably modern desktop computer.

- xD. The game should contain both 2D with isometric 2.5D-like game experience and 3D graphics. The idea is to write business logic code once and reuse for both 2D levels and 3D levels.

- Keyboard, touch screen and joystick support

- It should be self explanatory enough and performant enough for a non tech savvy non-gamer to get started, play and enjoy the game on a mobile or desktop device.


## Tech
Unity was chosen for it's wide use and for the multi platform support. The current demo version is built for WebGL (webassembly) and is therefore playable in almost any web browser.  

PC controls can support keyboard and joystick input, as supported by Unity's so called "new input system" (terrible name. What will they call the next generation input system?)

Controls obviously are a little different on a touch screen device than on a PC.  
  
## Possible improvements
The list could be long.
- Use the physics engine. Today the movements of almost all moving objects is controlled explicitly in C# code. Using Unity's phsics engine could be a cheap way to enable things like ricochet shots. It could even give a performance boost.
