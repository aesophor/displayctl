<div align="center">
<h3>DISPLAYCTL</h3>
<img src="https://github.com/aesophor/displayctl/raw/master/assets/main.png">

`Wallpapers (Desktop/Lockscreen) with Effects (Normal/Dim/Blur)`
`Resolution` `Brightness` `Lockscreen` 
</div>

## Why Do I Need This?
Are you running a Window Manager without a DE? Ever experienced the inconvenience of running `xrandr` to set resolution, `feh` for wallpaper, `light` for brightness, and `i3lock` for lockscreen (I use these tools, in my case).

I wrote displayctl to eradicate these problems. Now you can handles these tasks with a single script!

## Dependencies
* imagemagick
* ffmpeg
* xrandr
* [light](https://github.com/haikarainen/light)
* [i3lock-color](https://github.com/PandorasFox/i3lock-color)

## Installation
It supports manual installation only for now, sorry! Supports for common distributions will be added later!
* Manual Installation
```
$ git clone https://github.com/aesophor/displayctl.git
$ cd displayctl && cp displayctl ~/.local/bin/displayctl
```

## Configuration
Add this line to your `~/.Xresources`
```
! displayctl
#include "/home/aesophor/.x/displayctlrc"
```

Then create the configuration file in `~/.x/displayctlrc` 
```
! displayctlrc
! ===================================================================================
Display.monitor:         eDP1
Display.dpi:             112
Display.resolution:      1680x1050
Display.brightness:      30
Display.wallpaper:       /home/aesophor/Pictures/Wallpapers/Nature/Rainy.jpeg
Display.lockscreen:      /home/aesophor/Pictures/Wallpapers/Landscape/Pebble.jpeg
```

## Usage
Lockscreen cache can be located at `/tmp/lock_cache.png`. It will be stored there for faster lockscreen invocation. 

To use the lockscreen with another effect, run `displayctl -c` to clear the cache first.
```
$ displayctl                  # Restore resolution, brightness, and wallpaper to last session 
$ displayctl -d               # Restore resolution and brightness to last session
$ displayctl -l               # Invoke lockscreen (i3lock-color required)
$ displayctl -l -d -b         # Invoke lockscreen with dim + blur effect
$ displayctl -w -d -b         # Set wallpaper with dim + blur effect
$ displayctl -e 1280x800      # Mirrors display to an external monitor
$ displayctl -c               # Clears lockscreen cache
```

## Gallery
The effects demonstrated below can be applied to Desktop Wallpapers as well.

* Lockscreen (Normal)
![None](https://github.com/aesophor/displayctl/raw/master/assets/main.png)

* Lockscreen (Dim)
![None](https://github.com/aesophor/displayctl/raw/master/assets/dim.png)

* Lockscreen (Blur)
![None](https://github.com/aesophor/displayctl/raw/master/assets/blur.png)

* Lockscreen (Dim + Blur)
![None](https://github.com/aesophor/displayctl/raw/master/assets/dimblur.png)
## License
Available under the [MIT License](https://github.com/aesophor/dotfiles/blob/master/LICENSE).
