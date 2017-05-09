Right- and middle mouse-clicks can be simulated on Apple keyboards and touchpads with various combinations of keys and taps. This can present a problem in some drawing applications (like XFig) where you would need an extra hand to terminate a line... What's needed here is a set of single-key right- and middle mouse-click emulations. These might also come in handy in other situations, as they free up a hand (useful when holding a coffee mug) and prevent accidental clicks when merely doing a two-finger scroll on a touchpad.

It is a simple matter to assign right- and middle mouse-clicks to a some little-used keys, like the right-Alt and right-Command keys on any recent Apple keyboard. It doesn't matter much which keyboard you have specified in your Ubuntu setup, I usually pick the PC104 spec for my Apple Aluminum wireless US keyboard. Now, this is what you should do:

1. Install the "xev" package (if it isn't already installed), then in a terminal give the "xev" command. A little window opens with a small square: put the cursor in that square. Then hit the right-Alt and right-Command keys and watch the output for the keycodes, probably 108 and 134, and write them down. Keycodes do change from time-to-time, though, so check them yourself. Then close the little window by clicking on the X; this terminates xev.

2. Make a little script, like /usr/local/bin/keyboard (you need root privileges for that),
Code:
#!/bin/sh
xmodmap -e "keycode 108 = Pointer_Button3"
xmodmap -e "keycode 134 = Pointer_Button2"
xkbset m
where you should substitute the keycodes on your keyboard if different from mine. Make this script executable with the command
Code:
sudo chmod a+x /usr/local/bin/keyboard
3. Make sure that the "xkbset" package is installed, then find where your keyboard settings can be modified and enable control of the mouse with the keyboard, so that the "xkbset m" command in the script will work.

4. Finally, as user give the command "keyboard", and now those two keys should work as right- and middle mouse-clicks. If this works, then add the command "/usr/local/bin/keyboard" to the startup applications.

N.B. I'm a little vague on where these system settings for keyboard and startup programs are located. That's intentional, as their location has changed several times over the past years. You should look for System settings, or some such...

NN.BB. Usually I add a few more key assignments to the above script, like putting the §/± and `/~ key assignments right
Code:
xmodmap -e "keycode 94 = section plusminus"
xmodmap -e "keycode 49 = grave asciitilde"
Check these keycodes with xev as above. 

These key-assignments don't interfere with the system settings for the keyboard layout. For example, you can still in the layout specify the left-Alt key as the Compose key (for making accented letters on a US-keyboard); and the left-Command key (usually called left-Windows key...) as Third-level chooser to produce a EuroSign. 

Have fun with your new key assignments!
