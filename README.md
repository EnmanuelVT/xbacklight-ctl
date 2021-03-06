# xbacklight-ctl

Manage your brightness and get desktop notification feedback with this simple script. It's a good idea to map this script to keys in your WM or DE. You can search how to set XF86BrightnessUp and XF86BrightnessDown in your WM.

<img src="https://github.com/EnmanuelVT/xbacklight-ctl/blob/main/doc/xbacklight-ctl-notifications.gif" width="600">

```
xbacklight-ctl up       # Increase brightness by 10% (configurable)
xbacklight-ctl down     # Decrease brightness by 10% (configurable)
xbacklight-ctl up 30    # Increase brightness by 30%
xbacklight-ctl down 80  # Decrease brightness by 80%
xbacklight-ctl max      # Set max brightness (configurable)
xbacklight-ctl min      # Set min brightness (configurable)
xbacklight-ctl set 50   # Set brightness to 50 percent 
```

Your brightness it's never going to be lower than your min brightness, so you won't get a black screen if you accidentally set your backlight to 0.

## Installation

Use your favorite AUR helper

```
yay -S xbacklight-ctl-git
pacaur -S xbacklight-ctl-git
```

Or install it manually with the PKGBUILD and `makepkg -si`, I'm pretty sure that you know what you are doing.

## Configuration

Your configuration file it's located in $XDG_CONFIG_HOME/xbacklight-ctl/rc.cfg (~/.config/xbacklight-ctl/rc.cfg).

You can set:

```
# This is the amount of percent that is going to increase or decrease.
PERC=10
MAX=100
# If you set this to 0, you will get a black screen when you reach the minimum brightness.
MIN=10
# Length of time to spend fading the backlight between old and new value.
TIME=100
# Number of steps to take while fading.
STEPS=20
# Receive desktop notifications with notify-send.
NOTIFY=yes
```

## Keymapping example in Qtile

```
  Key([], "XF86MonBrightnessUp", lazy.spawn("xbacklight-ctl up"), desc="Increase backlight"),
  Key([], "XF86MonBrightnessDown", lazy.spawn("xbacklight-ctl down"), desc="Decrease backlight"),
```

## Notification problems

If you are not receiving the notifications, there is probably a problem with your notification server. To test this, please run `notify-send "I'm working"`.  If nothing happened, please [refer to the archwiki](https://wiki.archlinux.org/index.php/Desktop_notifications#Notification_servers).

They have been tested in dunst and the GNOME notification daemon. Please report an issue if you can't get notifications in your notification server.
