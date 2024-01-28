This is a fork of the original DOOM source with modifications to allow it to compile on linux. 

To view the blog post that details how this work was done see this link. [Insert Link]

But in short to run this you will need to make sure you have xephyr installed, because you need to create an 8-bit display for DOOM to run
```
sudo Xephyr :2 -ac -screen 640x480x8
```

You need a DISPLAY environment variable set so that when you launch the executable, it goes to the right Xephyr window. You also need to set the environment variable `DOOMWADDIR` so that Doom knows where your doom1.wad or doom.wad file is, if you don't have it in the same directory as your Linux executable.

You will also need to add a linux folder in the linuxdoom-1.10 folder (That is where the build expects to executable to go). To quickly see what has changed compared to the master branch go to [this link](https://github.com/id-Software/DOOM/compare/master...diego-crespo:DOOMLEARN:master)

This work would not have been possible without this helpful video [How To Compile Vanilla Doom (Linux Doom)](https://www.youtube.com/watch?v=9JgQfQHHhTw) and Fabien Sanglard's [Game Engine Black Book DOOM](https://fabiensanglard.net/gebbdoom/). If you are instead looking for a faithful, minimalist, and historically accurate port of DOOM, but that runs on modern hardware, look no further than [Chocolate Doom](https://github.com/chocolate-doom/chocolate-doom)
