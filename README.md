# displayctl
Set resolution, brightness, desktop wallpaper, and lockscreen wallpaper using a single tool, with various image effect.

Your desktop/lockscreen wallpaper path **no longer scatters across numerous scripts**.

Example configs are provided under `examples/`.

* Example usage:

![example](/assets/example.png)
 
* Configuration file:

![config](/assets/config.png)
 
 
## Overview
* Set display resolution and brightness.
 
* Set desktop wallpaper / lockscreen with the following effects:
  * regular / blur / dim / blur+dim
  * blurry screenshot (for lockscreen only)
 
* Caching - to make lockscreen faster.
  * **displayctl uses the cache for lockscreen automatically (if exists)**
  * the cache is at /tmp/bg.png
  * use `displayctl --clear-cache` before applying new effects (or simply `displayctl`).

## Advantages
* Now everything related to the display can be managed within a single file (~/.Xresources).

* The path to the desktop wallpaper / lockscreen wallpaper **no longer scatters across numerous scripts**.
 
* Sometimes when I quit a game, the resolution did not revert back correctly, and I have to run xrandr, but now I only need to type `displayctl`, 
and then the resolution will go back to the original.


## Screenshots
![dim](/assets/dim.png)
 
![blur](/assets/blur.png)
 
![scrot](/assets/scrot.png)
 

## Dependencies
* i3lock-color - i3lock fork with additional features.
* imagemagick  - Apply dim effect to images.
* feh          - Setting wallpapers.
* xrandr       - Setting display resolution.
* xbacklight   - Setting display brightness.
* xrdb         - Getting configuration from X server resource database.
 
 
 
## Manual Installation
#### Getting the script. 
git clone this repo and take the script, or...
```
git clone https://github.com/aesophor/displayctl
```

### Preparing configuration files. 
copy displayctlrc to ~/.x
```
cp displayctlrc ~/.x/.
```
 
And we have to **include ~/.x/displayctlrc in .Xresources** (or .Xdefaults, which depends on your setting).
```
! displayctl configuration file
#include "/home/aesophor/.x/displayctlrc"
```
 
Modify .displayctlrc according to your needs. Use xrandr to find your display monitor and resolution.
It should look something like this...

![configs](/assets/configs.png)



### Reload .Xresources
Also you may need to reload your .Xresources. Type this in terminal.
```
xrdb -merge ~/.Xresources
```
 
Then you may start using `displayctl`

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
 

## Todo
- [x] separated desktop wallpaper and lockscreen wallpaper.


## License
Available under the [MIT License](https://www.github.com/aesophor/displayctl/LICENSE).
