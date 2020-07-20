# speedUpYourMac
Lessons and scripts to clean up and speed up your Mac OS. Nothing new to see here, but useful.

# Scripts

- speedUpMyMac 
-- wraps over all other scripts
-- other scripts can be used directly or accessed by `speedUpMyMac scriptname`



# General Notes:

- All wrap-over scripts that move files to trash, move it to ~/.speedUpYourMac/trash , not ~/.trash
- Use "speedUpMyMac emptytrash" to finalize those operations.
- Use "speedUpMyMac auto" to do all steps (including emptying trash) in one step.


# Speed up Terminal
Online help from following links:

- http://osxdaily.com/2014/04/30/speed-up-terminal-app-mac-osx/
- https://discussions.apple.com/thread/1982140?tstart=0


Problems:

- Terminal may open up or get ready upon opening slowly.
- The same may happen with new Terminal tabs.
- Tab completion may be slow.
- Copy/pasting text in Terminal may cause freezing/slowing.

Solutions:

- Move .asl files located in /private/var/log/asl/ to trash
- Move Terminal plist file to trash
- Empty trash when you feel comfortable.

sudo mv /private/var/log/asl/*asl ~/.trash/

mv /Users/___USERNAME___/Library/Preferences/com.apple.Terminal.plist ~/.trash/

OR use the wrap-over here:

speedUpMyTerminal

