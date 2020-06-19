---
layout: post
title: Super Simple PICO-8 Beginners Guide
tags: pico8 gamedev jekyll blog github-page
---

The historic [itch.io bundle for racial justice and equality](https://itch.io/b/520/bundle-for-racial-justice-and-equality) has just recently ended, generating over 8 million dollars in sales with all proceeds donated to the [NAACP Legal Defense and Educational Fund](https://www.naacpldf.org/) and [Community Bail Fund](https://secure.actblue.com/donate/bail_funds_george_floyd).
  
Included in that bundle was a download for [PICO-8](https://www.lexaloffle.com/pico-8.php) which I've been spending a lot of my time with recently, and I want others to get involved too.

## What is PICO-8?

[Lexaloffle](https://www.lexaloffle.com/) loved the idea of creating games with NES-style limitations, but wanted to keep the code simple to jump into. I myself have looked into making NES games but honestly I don’t want to mess around with memory addresses and registers in a piece of hardware from the 80’s, so it feels like PICO-8 was developed for people like me in mind.

![PICO-8 Terminal](https://raw.githubusercontent.com/mik3ds/mik3ds.github.io/master/images/picostart.png)

> **First time using Pico-8?** Press ‘ESC’ to swap between the terminal and code editor, and enter RUN in the terminal to launch the game.

  

## Getting Started: Game Loop

It takes three functions for a PICO-8 game to launch and run.
Here they are:

*function _init()  
end*

*function _update()<br>
end*

*function _draw()<br>
end*

![PICO-8 Game Loop](https://raw.githubusercontent.com/mik3ds/mik3ds.github.io/master/images/pico1.png)

Lets start with this code as a beginning point and expand on each function one by one using an example project that lets you move a ball around the screen using the arrow keys.

### init

[init](https://pico-8.fandom.com/wiki/Init) is the launching point of the program. This function will be run immediately as the game launches. Its common for bigger games to end _init() by running a function to display the main menu, which in turn can then run a function to begin playing the game.

### update

[update](https://pico-8.fandom.com/wiki/Update) is called every frame. This is used to update any variables that we will then be using in the next function to draw objects onto the screen.

### draw 

[draw](https://pico-8.fandom.com/wiki/Draw) is called every frame immediately after update(). This is where we can draw shapes and sprites directly onto the screen, often using variables from the update() function.

## Bringing it all together

Lets think about our init function for a project like this. A circle appears in the middle of the screen which we can then control with the arrow keys. What would we need to keep track of in a situation like this? Probably the location of the ball, which we can store as X and Y coordinates.

If we think of the project as it’s three functions of init(), update() and draw(), and apply that to what we want to achieve, we can start to form a plan.

**1 - Initialize the X and Y coordinates of the circle in init()**

**2 - Update the coordinates if needed in update()**

**3 - Draw the circle on to the screen in draw()**

For the init function, we can ignore the updating aspect and focus on what is needed to get the project up and running, and for this example that would be the X and Y coordinates of where the circle spawns.

Here’s the code:

*function _init()<br>
	xpos = 64<br>
	ypos = 64<br>
end*

![Setting X and Y Coordinates](https://raw.githubusercontent.com/mik3ds/mik3ds.github.io/master/images/pico2.png)

We initialize the X and Y coordinates because PICO-8 uses a function called circfill() to draw circles, which takes in four parameters.

**circfill(xpos,ypos,radius,colour)**

The radius and colour will stay constant so we can set these manually in draw(), but the X and Y coordinates will change frame by frame, and storing them as variables makes this possible.

Here’s the draw function:

*function _draw()<br>
	cls()<br>
	circfill(xpos, ypos, 10, 8)<br>
end*

cls() clears the screen, and circfill() draws in the circle at the X and Y coordinates, with a radius of 10 and using colour 8.

We can use ‘ESC’ to swap back to the terminal and RUN our game.

![PICO-8 Red Ball](https://raw.githubusercontent.com/mik3ds/mik3ds.github.io/master/images/pico3.png)

The red ball should be appearing, but we haven’t set any controls yet.

Let’s take a look at the update function:

*function _update()<br>
	if (btn(0) and xpos > 0) xpos -= 1<br>
	if (btn(1) and xpos < 127) xpos += 1<br>
	if (btn(2) and ypos > 0) ypos -= 1<br>
	if (btn(3) and ypos < 127) ypos += 1<br>
end*

if (btn(0)) returns true if button 0 is held down on that frame. Each line of our update function checks a different movement key to see if it is held down and updates our circles X and Y position accordingly, moving one pixel per frame. We also limit the possible X and Y coordinates to the values of 0 and 128, which is the PICO-8’s screen size in pixels.

Here it is all together:

*function _init()<br>
	xpos = 64<br>
	ypos = 64<br>
end*

*function _update()<br>
	if (btn(0) and xpos > 0) xpos -= 1<br>
	if (btn(1) and xpos < 127) xpos += 1<br>
	if (btn(2) and ypos > 0) ypos -= 1<br>
	if (btn(3) and ypos < 127) ypos += 1<br>
end*

*function _draw()<br>
	cls()<br>
	circfill(xpos, ypos, 10, 8)<br>
end*

![Completed Example Code](https://raw.githubusercontent.com/mik3ds/mik3ds.github.io/master/images/pico4.png)

![Red Ball moving in PICO-8](https://raw.githubusercontent.com/mik3ds/mik3ds.github.io/master/images/pico5.gif)

From here it’s pretty simple to keep adding to. If you want some ideas to go further with this example, you could:

- Double the movement speed or increase it over time
- Create a pickup item that changes the circle colour when touched
- Make the circle able to shoot around the screen
- Replace the circle and background with a sprite and map

Thanks for following along, if you've read this far I love you and I hope everything goes well with your game dev projects! Follow me on [Twitter](https://twitter.com/mikecdev1), add me on [LinkedIn](https://www.linkedin.com/in/michael-clark-12258b173/) if that's your thing, and take a look at a few more examples of what PICO-8 can do here:

[https://www.lexaloffle.com/bbs/?tid=31411](https://www.lexaloffle.com/bbs/?tid=31411)
![PICO-8 Doom 3D Clone Test](https://raw.githubusercontent.com/mik3ds/mik3ds.github.io/master/images/picoex1.png)
[https://www.lexaloffle.com/bbs/?tid=29233](https://www.lexaloffle.com/bbs/?tid=29233)
![PICO-8 The Story of Zeldo Splash Screen](https://raw.githubusercontent.com/mik3ds/mik3ds.github.io/master/images/picoex2.png)
[https://www.lexaloffle.com/bbs/?tid=2145](https://www.lexaloffle.com/bbs/?tid=2145)
![PICO-8 Celeste Splash Screen](https://raw.githubusercontent.com/mik3ds/mik3ds.github.io/master/images/picoex3.png)

