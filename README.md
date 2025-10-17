# Homerow bindings

The quickest way to navigate between applications is through keyboard shortcuts. But how many shortcuts can you reach blindly?
My solution provides navigation between a maximum of 18 applications using a single hand on the keyboard.
Applications that use the mouse don't break this workflow. Press and go.

Having your applications under the same shortcuts no matter which platform, Linux, MacOs or Windows enables muscle memory over time. Navigating will be instant.
Depending on your desktop platform the mouse can come along towards the new app in focus. Either on the same monitor or on another monitor.

## Linux

For Linux I have configuration files for Keyd and Kanata. Two different key mappers to choose from.
I went back and forth between both and I currently prefer Kanata over Keyd.
Kanata is multiplatform so you can stay close to the same configuration file for different platforms.

The mappings use Super + F1 to Super + F18 for launching the applications.
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

The launching of the applications in your distro is something you should take care of yourself using a script. I have [modified Gnome Dash to Panel extension](https://github.com/devgizzo/dash-to-panel) to show the shortcut letters next to dash icons and to handle the keyboard shortcuts. It is in the linux folder. I am not planning on maintain my own version for long though, I might switch to script or waybar in the future. Basically it is handy to have a dash that shows where you are and where you can go, but the longer you use the shortcuts the less you need them in your vision.

Guides to install [Keyd](https://github.com/rvaiya/keyd/tree/master) and [Kanata](https://github.com/jtroo/kanata) can be found on github. Both basically use a systemd service
to launch an executable with the corresponding config [kanata.kbd](https://github.com/devgizzo/homerow/blob/main/linux/kanata.kbd) or [keyd.conf](https://github.com/devgizzo/homerow/blob/main/linux/keyd.conf) 

## MacOs

Keyboard navigation shines even more on a macbook with macos. Just keep your application windows maximized,
no need to fiddle with touchpad to manage windows.

MacOS works through [Raycast](https://www.raycast.com/) a menu app for assigning keyboard shortcuts to launch
apps. Kanata then remaps this to keyboard layers for easy access to the shortcuts. Under the hood it just calls
the Raycast shortcuts. Anyway, so I have created a [kanata.kbd](https://github.com/devgizzo/homerow/blob/main/macos/kanata.kbd) config file to support this. 

Kanata is a bit of a hassle to install on MacOS though, because of the conflict between Karabiner and
Karabiner driver and because of security issues and because of working with launchctl services manually.

Somebody created a [install script](https://gist.github.com/Jaycedam/4db80fc49c1d23c76c90c9b3e653c07f) for the whole setup, if you are lucky it works out of the box.
Or you can go through the [install guide manually](https://github.com/jtroo/kanata/discussions/1537)

What the steps to install contain: 

1. installing Karabiner driver kit (already installed if you are already using Karabiner-Elements)
2. installing Kanata from homebrew
3. writing and modifying 3 .plist files and installing them as root
4. setting privacy and allow input permissions

After installation set Raycast to open at option + space.

Then add your favorite apps to the Raycast menu
and add aliasses and keyboard shortcuts to them as per below:

| favorite | alias | keyboard shortcut |
|----------|-------|-------------------|
| 1        | w     | option + 1        |
| 2        | e     | option + 2        |
| 3        | r     | option + 3        |
| 4        | t     | option + 4        |
| 5        | s     | option + 5        |
| 6        | d     | option + 6        |
| 7        | f     | option + 7        |
| 8        | g     | option + 8        |
| 9        | c     | option + 9        |
| 10       | v     | option + 0        |
| 11       | q     | option + F1       |
| 12       | w .   | option + F2       |
| 13       | e .   | option + F3       |
| 14       | a .   | option + F4       |
| 15       | s .   | option + F5       |
| 16       | d .   | option + F6       |
| 17       | z .   | option + F7       |
| 18       | x .   | option + F8       |

The aliases are just visual queues within the raycast menu for you to see which keyboard shortcut is which.
It is used as shortcut reference.

## Windows

A Windows version is easily created from the linux Kanata.kbd config. So far I have not done this yet.

## Kanata plus homerow mod

I have also created a [kanata-homerow.kbd](https://github.com/devgizzo/homerow/blob/main/linux/kanata-homerow.kbd) file for linux and [kanata-homerow.kbd](https://github.com/devgizzo/homerow/blob/main/macos/kanata-homerow.kbd) for macos.\
This combines my custom key mappings with the traditional homerow mod keys as listed below:

| layer key | shortcut          | layer key | shortcut           |
|-----------|-------------------|-----------|--------------------|
| a         | left cmd / super  | ;         | right cmd / super  |
| s         | left option / alt | l         | right option / alt |
| d         | left control      | k         | right control      |
| f         | left shift        | j         | right shift        |

This however means that layers are ontop of each other. Especially on the left hand. In order to differentiate between them there are a few quirks to avoid conflicts.
1. You have to combine left hand homerow keys with right hand normal keys and vice versa. Just like typing uppercase.
2. This left / right split is only necessary on potentially conflicting keys, so not on special characters, numeric or function keys.
3. When left cmd / super or left shift is combined with other modifier keys, then keys should be pressed simultaneous as a chord.

Examples:

1. cmd + k, cmd can be held down first with the left hand, k can be pressed with the right hand.
2. cmd + shift + k, cmd and shift have to pressed as a chord with the left hand, then k can be pressed with the right hand.
4. cmd + option + w, cmd and option should be pressed as a chord using the right hand, then w can be pressed with the left.

## Other key mappings

* My bindings also provide A + space to call a menu to launch arbitrary apps (arcmenu or raycast or anything else)
* On linux Caps Lock and ctrl are swapped and a tap on Caps Lock which is ctrl results in toggling the visibility of the Gnome Dash for reference on where to go or which apps are open. On MacOS I set this to toggle dock visibility and set caps to command because it's the most used modifier key on macos. 
* A + Q to quit apps
* Z layer provides cursor movement single step and some other common text operations.
* X layer provides cursor movement single step with selection
* C layer provides cursor movement per word
* V layer provides cursor movement per word with selection
* Q layer provides shortcuts to open, close and navigation browser tabs

You might find these useful or you can comment them out or remove them.

## The downsides of homerow keymapping

One of the downsides of my mapping method is that it prevents traditional homerow mods.
If you are used to type shift, ctrl, alt and super using the homerow keys that method will overlap my usecase.

In some extremely rare cases you might trigger a layer when typing because of holding multiple keys.
In other cases you expect the layer to pick up faster like in combining text editing and normal typing. You can adjust the timeout values
to mitigate these problems. And if needed add a few ms pause between regular typing and layer switching. 

## Launching and quiting applications

Applications are assigned left to right on the keyboard, Super+F1 till F10 on linux, Option+1 till Option+0 on macos.
Now the shortcuts documented below are linux shortcuts only. If needed you can lookup the macos equivalent in the kanata.kbd file.
The mapping is very similar on macos.


### Hold A key

| layer key | shortcut      | function                                                                                                                    |
|-----------|---------------|-----------------------------------------------------------------------------------------------------------------------------|
| W         | Super + F1    | Launch application 1                                                                                                        |
| V         | Super + F10   | Launch application 10                                                                                                       |
| Q         | Super + Q     | Quit current application                                                                                                    |
| Space     | Super + space | Launch a menu (like arcmenu on linux or raycast on macos) for launching arbitrairy apps that are not covered by the layers. |

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
