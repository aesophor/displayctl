# displayctl
A handy utility to handle various works related to the display.
 
Inspired by [betterlockscreen](https://github.com/pavanjadhaw/betterlockscreen) by [pavanjadhaw](https://github.com/pavanjadhaw/), this script is written with the intention of **dealing with display resolution, brightness, wallpaper, and lockscreen using just a single utility**. You may apply several effects (e.g., blur, dim, or both...etc) to your wallpaper and lockscreen. It provides a caching mechanism to let you lock your screen faster. 
Different from betterlockscreen, displayctl does not generate cache for every lockscreen style. Instead, it only generate cache for the one that you need. The rectangle drawing part is taken from his script.
In Addition, the configuration of displayctl (like the path to your daily wallpaper, default display resolution, default screen brightness...etc) are stored in the X resource database, so that **these values can be managed within a single file**, instead of being scattered across numerous scripts/configs.

## What It Does
* Set display resolution(xrandr) and brightness(xbacklight).
 
* Set desktop wallpaper(feh) / lockscreen(i3lock-color) with the following effects:
  * regular
  * blur
  * dim
  * blur + dim
  * blurry screenshot (for lockscreen only)
 
* Provides a caching mechanism to make lockscreen faster.
  * **displayctl will use the cache for lockscreen automatically (if exists)**
  * the cache is at /tmp/bg.png
  * use **--clear-cache** if you want to apply new effects

## Screenshots
Currently empty here. I'll fill this up eventually.

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
Any else...?
