---
title: Welcome
permalink: /docs/home/
redirect_from: /docs/index.html
---

# hakchi2 CE v1.0.0

A fork of hakchi2 from ClusterM that focuses on bringing a number of improvements, including a better UI experience as well as support for modern hakchi1 versions.

## TeamShinkansen:

- /u/princess_daphie
- /u/DanTheMan827
- /u/skogaby

## New Features (since v2.21f):

### Under the hood improvements

- Updated the custom kernel and scripts to include the newest hakchi1 modifications!
- This includes support for:
  - USB-HOST without the need for hakchi1
  - SD support, with the ability to sync to the SD card (**for now, hakchi1 is still required, but only for flashing uboot.bin!**)
  - Automatic USB mode switching (system will not boot in USB-HOST mode if there is no USB hub attached at boot)
  - Separation of games for multiboot setups
- Automatic version detection
  - If hakchi2 is out of date, the newest version will download, including portable users
  - If the kernel or hakchi scripts on the system are out of date, the program will prompt you to update them

### UI Improvements 

- Integrated all changes from princess_daphie's personal fork of hakchi2, which includes the following:
- Improved original games management:
  - Original games are now actual games (instead of a simple on/off toggle)
  - Option to customize any detail
  - Option to customize cover art
  - Default covert art is automatically downloaded from the console when it is plugged in and modded while running hakchi2.
- Improved cover art management:
  - Default button to reset default cover art
  - Batch clearing of cover art in context menu
  - Batch scanning of covert art in `/art/` folder
  - Improved scanning of cover art in `/art/` folder
  - Cover art compression using nQuant
  - When cover size matches that of the console (228x204 for SNESC or 204x204 for NESC), it is not resized. It will be compressed if enabled.
  - Separate thumbnail support
- Show in Windows Explorer in context menu
- CTRL-A handler to select all games
- Added Export and Linked export features, including an Export button on the main interface
- Added option to disable redundant dialogs (i.e. Wow: Done!)
- Fixed outstanding issue with sorting not taking into account internal SortName field in games list and folders manager
- Added View menu:
  - Group by app type, including custom unrecognized apps (i.e. /bin/png)
  - Group original games at the top, at the bottom, or sorted in the list
- Many bug fixes from previous version.

## Complete Changelog for UI improvements

- Add: Default cover art button and option in pop-up menu to delete custom cover art and reset to default.
- Add: CTRL+A  selects all games.
- Add: DanTheMan827's export games functionality using SHIFT when synchronizing games.
- Add: Automatic download of original games cover art when a modded unit is connected.
- Add: Show original games cover when they are downloaded in cache (see previous item).
- Add: Compress cover art with nQuant (8bits quantizer), menu option in *Tools.*
- Add: Original games are treated as normal games by hakchi2 now. You can delete, change cover art, change info, at will.
- Add: *Reset original games* menu option under Tools -> Console Type, to import or undo changes for the original games.
- Change: desktop_entries/*.desktop now in a single data/desktop_entries.7z file for convenience.
- Change: Config file now separates all 4 different console versions for game lists instead of merging NES/Famicom and SNES/Super Famicom. Required for original games rework.
- Change: When running hakchi2 for the first time with an already modded unit connected, it will detect console type and bypass the first run console selection dialog, to avoid confusion. Slight 1000ms delay on first run introduced for this to work.
- Fix: Changes on current game is immediately saved when changing selection.
- Fix: *PersistentDeleteDirectory* internal method to assert temp directory deletion.
- Fix: When uploading games, prevent console reboot when an issue arises before any change has been applied.
- Fix: Fewer symbolic links used when uploading original games. Not required anymore. Only links required are /autoplay and /pixelart folders.
- Add: When importing cover art, image file is copied intact if it matches target dimensions (i.e. 228x204 on SNES/Super Famicom and 204x204 on NES/Famicom).
- Add: Thumbnail display and independent change option.
- Add: When important new games or changing cover art, if a matching "_small" file is found alongside the cover art, it will be used for thumbnail automatically.
- Fix: More reliable search of cover art when importing new games.
- Add: *Reload games* option under Files menu to reload game list (after making changes manually for instance).
- Change: Add notice on app title bar to differentiate this build from the original hakchi2. Using date as build number for now.
- Change: Add copyright and sortrawtitle to fields on *NesMiniApplication* (internal for now)
- Fix: Allow fewer characters in rom filename, to avoid conflicts when running the USB Mod.

- Switching language works again. (see this: https://developercommunity.visualstudio.com/content/problem/5735/when-vs-2017-rc-is-installed-resourcesdll-is-gener.html)
- CTRL-ALT-E on original games doesn't crash anymore.
- App will search for cover art in /art folder when resetting original games.
- Altered fuzzy search in FindCover routine to better match covers to games. Some false positives may still occur, but this allows many more proper matches as well.
- Minor fixes

- Attempt to implement/adapt **DanTheMan827's export linked games** branch *(should work)(testing required)*
- Fix original games cover art found during reset not being saved in .desktop file (thus not showing on console when syncing without manually editing the games to force .desktop update).
- Fix ListView context menu not being enabled in time according to (selected items > 0).
- Add **export button** and corresponding menu entry (for touch users and consistency).
- SHIFT-CLICK "Synchronize" does not export games anymore; use dedicated button or menu entry.
- Fix "Value cannot be null, parameter name: input " error on adding games with covers in /art/ folder under some conditions (issue #1)
- Resource changes
- Change internal directory delete function

- Add "Show in Windows Explorer" option in context menu
- Add F4 shortcut for "Show in Windows Explorer"
- Remove useless "Done" popup after deleting cover art in batch
- Fix folder icons broken when exporting or linking games
- Fix paths set to /var/games/ instead of /usr/share/games[/nes/kachikachi] when exporting games
- Fix save path to /var/saves/ instead of /var/lib/clover/profile/0 when exporting (linked or not)
- Fix unhandled exception when deleting a game right after adding it in list without clicking anywhere else

- Fix regression couldn't sync (Hotfix)
- Fix original games custom cover not being properly linked when doing linked export (thanks /u/Pretendtious)
- Add detection of custom covers for original games when they are copied manually outside of the program (thanks /u/therourke)
- Add disable nagging popups option (when enabled, almost all "Wow - Done" and redundant popups are eliminated) (this option is disabled by default) (thanks @gingerbeardman)
- Fix random exceptions when deleting games because of changes detected before deleting that were requested to be saved after.
- Add scan for new box art (in /art folder) for selected games in context menu
- Internal change "reset original games" task in WorkerForm, as a proper task

- Fix small problem with "scan box art for selected games" where original games wouldn't search for their "CLV-P-????" names
- Fix attempt for a specific user error when using an ext4 drive and googling images
- **Fix major issue** with sorting where internal sort name was only used to sort on the classic mini, but not in hakchi2's game list or folders manager!
- Add SortName to INesMenuElement to fix previously mentioned issue
- Add View menu
- **Add Original games sorting** to show them either at the top of the list, at the bottom, or sorted with other games as it was before!
- **Add "Group by app type" option to view menu.** This option will group games by their respective console/rom file type!
- Add internal non-destructive original games sync (for first use pop-up, to avoid deleting existing original games if present)
- **Modify first run select console dialog** to take into account console detection and allow resetting or not of original games
- Add workaround to prevent flickering ListView with groups
- Move reset original games to **Files -> Restore original games**
- Add **Tools -> Folders Manager** to access it without the need to sync or export

- Fix exception when changing language (caused by groups not being recreated after form reloading)
- Fix exception when loading file types that are not recognized by hackhi2 (not in AppTypeCollection)
- Add unrecognized file types sorted grouping instead of a single "unknown" group

- Fix Arcade and Atari 2600 games being detected as GameGear (old hakchi2 typo left in)
- Reworked grouping code to allow combining original games sorting AND group by app
- Fix exceptions with unknown apps (hopefully)
- Add custom app groups
