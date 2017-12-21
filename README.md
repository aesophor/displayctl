# displayctl
A handy utility to handle various works related to the display.
 
This script is written with the intention of **dealing with display resolution, brightness, wallpaper, and lockscreen using just a single utility**. You may apply several effects (e.g., blur, dim, or both...etc) to your wallpaper and lockscreen. It provides a caching mechanism to let you lock your screen faster. 
 
The configuration of displayctl (like the path to your daily wallpaper, default display resolution, default screen brightness...etc) are stored in the X resource database, so that **these values can be managed within a single file**, instead of being scattered across numerous scripts/configs.
 
## What It Does
![example](https://github.com/aesophor/displayctl/scrot/example.png)
 
* Set display resolution and brightness.
 
* Set desktop wallpaper / lockscreen with the following effects:
  * regular
  * blur
  * dim
  * blur + dim
  * blurry screenshot (for lockscreen only)
 
* Caching - to make lockscreen faster.
  * **displayctl uses the cache for lockscreen automatically (if exists)**
  * the cache is at /tmp/bg.png
  * use **displayctl --clear-cache** or simply **displayctl** if you want to apply new effects
 
* Sometimes when I quit Skyrim, the resolution did not revert back correctly. Now I only need to type
```
displayctl
```
and then the resolution will go back to the original.
 
* Now everything related to the display can be managed within a single file (~/.Xresources).
![config](https://github.com/aesophor/displayctl/scrot/config.png)
 
## Screenshots
![dim](https://github.com/aesophor/displayctl/scrot/dim.png)
 
![blur](https://github.com/aesophor/displayctl/scrot/blur.png)
 
![scrot](https://github.com/aesophor/displayctl/scrot/scrot.png)
 
## Dependencies
* i3lock-color - i3lock fork with additional features.
* imagemagick  - Apply dim effect to images.
* feh          - Setting wallpapers.
* xrandr       - Setting display resolution.
* xbacklight   - Setting display brightness.
* xrdb         - Getting configuration from X server resource database.
 
## Manual Installation
git clone this repo and then take the script, or...
```
git clone https://github.com/aesophor/displayctl
```
 
download the script directly with wget.
```
wget https://raw.githubusercontent.com/aesophor/displayctl/master/displayctl
chmod +x displayctl
```

Secondly, add the following lines to your .Xresources (or .Xdefaults, which depends on your setting). You may need to modify them a bit.
```
! Displayctl
! ============================================================
Display.monitor:         eDP1
Display.resolution:      1920x1200
Display.brightness:      60
Display.wallpaper:       /path/to/your/wallpaper
Display.lockscreen:      /path/to/your/lockscreen_bg
```

Finally, put .functions in your home directory. This file contains an important function to get your own configuration of displayctl from the X resource database.
Also make sure to include the following line in your .zshrc (or whatever shell config that you are using). This script needs it!
```
source ~/.functions
```

Then you may logout current user session, restart X, and enjoy!
 
## Usage
Some examples
* Set display resolution and wallpaper upon X server starts
If you aren't using any Display Manager like me, simply put the following line at the end of your i3 config. This will set both display resolution and wallpaper for you.
```
exec --no-startup-id /usr/bin/bash /path/to/displayctl
```
 
* Set wallpaper with both blur and dim effect.
```
displayctl -w --blur --dim
```
 
* Lockscreen with both blur and dim effect.
```
displayctl -l --blur --dim
```
 
* Lockscreen with blurry screenshot effect (Slower, since caching does not work well with this one.)
```
displayctl -l --scrot
```
 
* Clear previous cache. Clearing previous cache before applying new effects to your lockscreen.
```
displayctl --clear-cache
```

* See help message.
```
displayctl -h
```
 
## TODOS
- [x] ~~separated desktop wallpaper and lockscreen wallpaper.~~
