# speedUpYourMac - version 1.0
Lessons and scripts to clean up and speed up your Mac OS. Nothing new to see here, but useful.

These scripts only do a subset of things you can do to improve your aging Mac's performance. See the following link for more help:
- https://macpaw.com/how-to/speed-up-mac

Overall, to speed up your Mac, you can:
- Shut down programs/Apps you're not using (e.g. don't infinitely keep Word open)
- Empty trash (rm -r ~/.trash/* )
- Empty Downloads (rm -r ~/Downloads/* ) --  move important stuff out of it first.
- Use activity monitor (or Terminal) to find and kill memory-hungry and/or CPU-intensive processes
- Remove start-up programs in System Preferences --> Users & Groups --> Login Items
- Turn off viz fx @ System Preferences > Dock (uncheck "Animate opening applications", "Automatically hide", "Show the Dock")
- Delete browser add-ons / extensions you dont want, need, or use (E.g. Chrome Preferences --> Extensions)
	- Also: Clear all your browsing data (e.g. Chrome Preferences --> Clear browsing data ; check all from all time)
- Reindex spotlight: System Preferences > Spotlight --> Privacy --> "+" --> add your HD --> then remove it with "-"
	- Or terminal: `sudo mdutil -E /`
- Limit spotlight indexing: if you have an external hard drive that is always attached, Spotlight may be trying to index it all the time, which can be resource-heavy and slow.
	- This was completely unnecessary for me when the connected hard drive was just a CarbonCopyCloner clone back up of my Mac.
	- Just add that to list of things Spotlight shouldn't search.
	- System Preferences > Spotlight --> Privacy --> "+" --> add your HD --> then remove it with "-"
- Reduce desktop clutter 
- Empty caches 
- Uninstall unused Apps 
- Clean up HD/SSD storage drive (Caches, logs, apps, widgets, hidden trash, large and old files)
	- Move large unused files (movies, music, etc) to an external storage drive
- Update Mac OS software (or hardware if have money to do so)
- Try creating a new profile and using that to "start over" since it won't have tons of unfound clutter, caches, logs, etc.
- Free up RAM (sudo purge, memory clean app, or this script)
- Reset SMC (turn off, hold Shift+Control+Option+PowerButton for 10 sec, disconnect battery if possible, hold power button for 5 seconds, reconnect battery, turn on or reset PRAM as below )
- Reset PRAM (turn off, press power button and immediately hold cmd+opt+P+R, continue holding as computer starts, eventually release keys, may hear a chime)
- Replace hard drive with solid state drive


# What can be done by speedUpYourMac

- Speed up Terminal by cleaning out files that slow it down
- Empty Mac Trash (moves it to same trash dir as all else in this program)
- Move contents in Downloads to dated folder in DeskDrawer to be optionally cleaned out, deleted later
- Reduce desktop clutter 
- Empty caches (also removes lots of browsing data)
- Free up RAM
- Reindex spotlight
- Identify directories with large files

# Possible future helpers:
- Help remove Apps entirely by finding associated files (not just the App in the Applications folder)
- Help compress files (gzip) and directory structures into zips, or gzipped tarballs


# Scripts

- `speedUpMyMac`
	- wraps over all other scripts
	- other scripts can be used directly or accessed by `speedUpMyMac scriptname`
	- Use `speedUpMyMac auto` to do all steps (including emptying trash) in one step.
- `speedUpMyTerminal`
- `freeUpMyRAM`
- `cleanUpMyCaches`
- `declutterMyDesktop`
- `rebuildSpotlightIndex`
- `diskUsageThisDirAndAllSubDir`
- `diskUsageThisDirAndAllSubDirLoop`
- `declutterMacDownloads`
- `declutterMacTrash`
- `emptyMyTrash`
- `viewDeskDrawer`

# Helper scripts

- `dirIsCluttered`
- `dirIsEmpty`
- `moveToDeskDrawer`


# General Notes:

- All wrap-over scripts that move files to trash, move it to `~/Documents/DeskDrawer/speedUpMyMac/trash`, not `~/.trash`
- Use `speedUpMyMac emptytrash` to finalize those operations.
- DeskTop clean-up moves all DeskTop items to ~/Documents/DeskDrawer/Desktop/*date*
- Use `speedUpMyMac auto` to do all steps (including emptying trash) in one step.





# Usage:

	speedUpMyMac -1234567adlvh

        -1 speed up terminal : move ASL and plist files to DeskDrawer trash (dated)
	-2 declutter mac Desktop : move Mac Desktop contents to DeskDrawer (dated)
	-3 declutter mac Downloads : move Mac downloads to DeskDrawer (dated)
	-4 declutter mac trash : move Mac trash contents to DeskDrawer trash (dated)
	-5 declutter Caches :  move Mac Caches contents to DeskDrawer trash (dated)
	-6 Free up RAM
	-7 Reindex Spotlight
	-a All / Auto : Run all previous steps.
	-d Get disk space used by current directory.
	-l Loop over sub-directories in current directory, and get disk space used by each.
	-v View DeskDrawer in Finder








## Deeper Explanations of each script

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

- Move .asl files located in `/private/var/log/asl/` to trash
- Move Terminal plist file to trash
- Empty trash when you feel comfortable.

```
sudo mv /private/var/log/asl/*asl ~/.trash/

mv ~/Library/Preferences/com.apple.Terminal.plist ~/.trash/
```

OR use the wrap-over here:

```
speedUpMyTerminal
```

