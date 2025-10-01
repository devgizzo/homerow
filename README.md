# Homerow bindings

The purpose of these keybindings is to start, focus and quit 18 of your favorite apps with the keyboard using a single hand on the homerow.
No finger gymnastics, no need to look at the keyboard. Your other hand can be on the keyboard aswell or on the mouse, this doesn't impact switching speed.
You can keep your eyes on the screen.

Having your applications under the same shortcuts no matter which platform, Linux, MacOs or Windows enables muscle memory over time. Over time navigating between apps will be instant.
Depending on your desktop platform the mouse can come along towards the new app in focus. Either on the same monitor or on another monitor.

## Linux

For Linux I have configuration files for Keyd and Kanata. Two different key mappers to choose from.
Keyd is lower latency, Kanata is multiplatform so you can stay close to the same configuration file for different platforms.

The mappings use Super + F1 until Super + F18 for launching the applications.
To enable support for F13 and up on linux (wayland) you have to configure the following file

```
cp /usr/share/X11/xkb/symbols/inet ~/.config/xkb/symbols/inet
```

and then modify the entries on the .config inet file like below

    key <FK13>   {      [ F13                    ]       };
    key <FK14>   {      [ F14                    ]       };
    key <FK15>   {      [ F15                    ]       };
    key <FK16>   {      [ F16                    ]       };
    key <FK17>   {      [ F17                    ]       };
    key <FK18>   {      [ F18                    ]       };

The launching of the applications in your distro is something you should take care of yourself using a script. I have modified Gnome Dash to Panel extension to show the shortcut letters next to dash icons and to handle the keyboard shortcuts. It is in the linux folder. I am not planning on maintain my own version for long though, I might switch to script or waybar in the future. Basically it is handy to have a dash that shows where you are and where you can go, but the longer you use the shortcuts the less you need them in your vision.

Guides to install [Keyd](https://github.com/rvaiya/keyd/tree/master) and [Kanata](https://github.com/jtroo/kanata) can be found on github. Both basically use a systemd service to launch an executable with the corresponding config [kanata.kbd](https://github.com/devgizzo/homerow/blob/main/linux/kanata.kbd) or [keyd.conf](https://github.com/devgizzo/homerow/blob/main/linux/keyd.conf) 

## MacOs

MacOS works through [Raycast](https://www.raycast.com/) for assigning shortcuts to launch apps. These shortcuts can then be called from other applications.
For MacOS I first worked with [Karabiner-elements](https://github.com/pqrs-org/Karabiner-Elements), you can install this with the [karabiner.json](https://github.com/devgizzo/homerow/blob/main/macos/karabiner.json) found in the macos folder.
This works but isn't ideal. You need to maintain a bit of lag between opening a keyboard layer and selecting an option on the layer, else you end up typing letters instead.

However Kanata can also be installed on macos. So I have created a [kanata.kbd](https://github.com/devgizzo/homerow/blob/main/macos/kanata.kbd) config file to support this. Kanata needs the Karabiner driver for this. So if you installed Karabiner-Elements you already have this installed.
For MacOS Kanata is more stable and the keyboard layers are more solid. So I am not moving back.
Anyway, this solution also uses Raycast to assign the shortcuts that launch or focus the apps.

Kanata is a bit of a hassle to install on MacOS though, because of the conflict with Karabiner itself, while it uses its driver and because of security issues. For me it is worth it though.

## Windows

A Windows version is easily created from the linux Kanata.kbd config. So far I have not done this yet.

## Other key mappings

* My bindings also provide A + space to call a menu to launch arbitrary apps
* Caps Lock and ctrl are swapped and a tap on Caps Lock which is ctrl results in toggling the visibility of the Gnome Dash for reference on where to go or which apps are open.
* A + Q to quit apps
* Z layer provides cursor movement single step and some other common text operations.
* X layer provides cursor movement single step with selection
* C layer provides cursor movement per word
* V layer provides cursor movement per word with selection
* Q layer provides shortcuts to open, close and navigation browser tabs

You might find these useful or you can comment them out or remove them.

## The downsides of homerow keymapping

In some rare cases you might trigger a layer when typing because of holding keys while typing.
But the biggest downside is latency. You might notice some letters print slower to the screen.
But you gain lightspeed navigation!

## Launching and quiting applications

Applications are assigned left to right on the keyboard, Super F1 till F10...

### Hold A key

| layer key | shortcut      | function                                                                                            |
| --------- | ------------- | --------------------------------------------------------------------------------------------------- |
| W         | Super + F1    | Launch application 1                                                                                |
| V         | Super + F10   | Launch application 10                                                                               |
| Q         | Super + Q     | Quit current application                                                                            |
| Space     | Super + space | Launch a menu (like arcmenu) for launching arbitrairy apps that are not covered by the keyd layers. |

![](images/a%20layer.png)

### Hold F key

Next applications Super F11 till F18 are assigned left to right aswell...

| layer key | shortcut    | function              |
| --------- | ----------- | --------------------- |
| Q         | Super + F11 | Launch application 11 |
| X         | Super + F18 | Launch application 18 |

![](images/f%20layer.png)

## Copy / Paste

Move your hand one row down from the home row.

### Hold Z key

| key | shortcut | function |
| --- | -------- | -------- |
| X   | Ctrl + x | Cut      |
| C   | Ctrl + c | Copy     |
| V   | Ctrl + v | Paste    |

## Common operations

### Hold Z Key

| key | shortcut  | function                |
| --- | --------- | ----------------------- |
| A   | Ctrl + a  | Select all              |
| S   | Ctrl + s  | Save                    |
| D   | Backspace | Remove text to the left |
| F   | Ctrl + f  | Find text               |

## Navigation (move cursor one character at a time)

### Hold Z Key

| key | shortcut    | function              |
| --- | ----------- | --------------------- |
| I   | Up arrow    | Up                    |
| K   | Down arrow  | Down                  |
| J   | Left arrow  | Left                  |
| L   | Right arrow | Right                 |
| U   | Home        | Move to begin of line |
| O   | End         | Move to end of line   |
| P   | Page up     | Move a page up        |
| ;   | Page down   | Move a page down      |

![](images/z%20layer.png)

## Navigation (selecting one character at a time)

### Hold X Key

| key | shortcut    | function              |
| --- | ----------- | --------------------- |
| I   | Up arrow    | Up                    |
| K   | Down arrow  | Down                  |
| J   | Left arrow  | Left                  |
| L   | Right arrow | Right                 |
| U   | Home        | Move to begin of line |
| O   | End         | Move to end of line   |
| P   | Page up     | Move a page up        |
| ;   | Page down   | Move a page down      |

## Delete

### Hold X Key

| key | shortcut | function                                                                  |
| --- | -------- | ------------------------------------------------------------------------- |
| D   | Delete   | Backspace is in the same location but on the Z key layer. This is delete. |

![](images/x%20layer.png)

## Navigation (move cursor one word at a time)

### Hold C Key

| key | shortcut    | function              |
| --- | ----------- | --------------------- |
| I   | Up arrow    | Up                    |
| K   | Down arrow  | Down                  |
| J   | Left arrow  | Left                  |
| L   | Right arrow | Right                 |
| U   | Home        | Move to begin of line |
| O   | End         | Move to end of line   |
| P   | Page up     | Move a page up        |
| ;   | Page down   | Move a page down      |

![](images/c%20layer.png)

## Navigation (selecting one word at a time)

### Hold V Key

| key | shortcut    | function              |
| --- | ----------- | --------------------- |
| I   | Up arrow    | Up                    |
| K   | Down arrow  | Down                  |
| J   | Left arrow  | Left                  |
| L   | Right arrow | Right                 |
| U   | Home        | Move to begin of line |
| O   | End         | Move to end of line   |
| P   | Page up     | Move a page up        |
| ;   | Page down   | Move a page down      |

## Undo / redo

### Hold V Key

| key | shortcut         | function |
| --- | ---------------- | -------- |
| Z   | Ctrl + Z         | Undo     |
| X   | Ctrl + shift + Z | Redo     |

![](images/v%20layer.png)

## Browser shortcuts

Move your hand one row up from the home row to access the browser specific shortcuts.

### Hold Q Key

| key | shortcut           | function             |
| --- | ------------------ | -------------------- |
| E   | Ctrl + shift + tab | Move to previous tab |
| R   | Ctrl + tab         | Move to next tab     |
| W   | Ctrl + W           | Close tab            |
| T   | Ctrl + T           | Open new tab         |

![](images/q%20layer.png)
