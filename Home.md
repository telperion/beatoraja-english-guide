**Note:** If you have problems or questions about beatoraja or BMS, or have any comments on the guide, please make a post on the [Discussions Page](https://github.com/wcko87/beatoraja-english-guide/discussions). I actively monitor the Discussions page for messages.

Please **don't create issues in beatoraja's issue tracker!** The issue tracker is not for troubleshooting.

# What is beatoraja?

beatoraja is an open source BMS Player in active development.
- [beatoraja on Github](https://github.com/exch-bms2/beatoraja)

If you're here just for more information about BMS (and not beatoraja), check out the links below. These links are useful even if you are using LR2 or some other [BMS player](BMS-Overview#what-is-a-bms-player).
- [What is BMS?](BMS-Overview)
- [Where do I download BMS songs?](Downloading-Songs#where-do-i-find-songs)
- [Difficulty ratings and difficulty tables](Difficulty-Tables)

Another popular BMS player is Lunatic Rave 2 (LR2). Most of this guide is for beatoraja.
- Instructions for setting up LR2 can be found here: [Reddit LR2/BMS Setup Guide](https://www.reddit.com/r/lunaticrave2/wiki/index)

Note that judge timings and gauges in beatoraja differ slightly from LR2. There a version of beatoraja that has been modified to use LR2 judge timings and gauge (but it does not support beatoraja's internet rankings). It can be found [here](https://github.com/wcko87/lr2oraja).

----------
# Getting Started with beatoraja

#### 1. Download 64-bit Java
- [Download Java from here](https://www.java.com/en/download/manual.jsp). Make sure to get a **64-bit** version of Java.
- beatoraja may not run properly on 32-bit java. Refer to [this error description](#2-invalid-maximum-heap-size--xmx4g) for more details.
- We suggest Java 8, as it has JavaFX included. beatoraja is compiled with Java 8, though it will still work on later versions of Java as long as JavaFX is present. Refer to [this error description](#4-error-could-not-find-or-load-main-class-bmsplayerbeatorajamainloader) for more details.

#### 2. Download beatoraja
- [Download beatoraja from here](https://mocha-repository.info/download.php).
- Make sure you download the beatoraja release from [Mocha Repository](https://mocha-repository.info/download.php), not the source code from Github!
- If `beatoraja.jar` is absent from your beatoraja directory, you probably downloaded the source code instead of the program itself.
- If you downloaded the ".exe" version of beatoraja (available from 0.8.1 onwards), you may have issues applying the [Locale Fix](#locale-fix) later. You can still apply the Locale fix, but you need to download the [beatoraja-config.bat](https://github.com/wcko87/beatoraja-english-guide/tree/resources/beatoraja-configs) file separately and place it in your beatoraja folder. Due to the locale issues, I **do not recommend** using the .exe version.

#### 3. Run beatoraja
- Run beatoraja by starting `beatoraja-config.bat`. Do not run beatoraja by launching the beatoraja.jar directly. If you wish to make a shortcut, point the shortcut to `beatoraja-config.bat`.
- If you are on mac/linux, use `beatoraja-config.command` instead.

### LOCALE ISSUES: READ THIS BEFORE PLAYING
As BMS has a largely Japanese community, there's a high chance that you might run into some encoding/locale issues later on. It might be best to take some pre-emptive steps to resolve this beforehand.

----------
# Locale Fix

### Effects of locale issues
Not being on the correct locale can cause some issues in beatoraja. Most of the time, if you are experiencing crashes in beatoraja, it is due to a locale issue. Thankfully, there is an easy fix for all these crashes.

The problems locale issues will cause:
- On skins like ModernChic or LITONE5 which have option names in Japanese, these option names will not save. When beatoraja is closed, the skin-specific settings will be reset.
- On skins like LITONE5 which have folder names in Japanese, beatoraja might not be able to access resources inside those folders, and this can cause beatoraja to crash.
- If you load a bms with file or folder names containing Japanese characters or garbled characters, certain parts of the bms may not load properly. Playing the bms twice in a row may cause beatoraja to crash.


### Fixing locale issues
There are two ways to fix locale issues in beatoraja. This fixes all the problems listed above.

- **Method 1:** Switch to Japanese locale on your PC
- **Method 2:** Run beatoraja using the UTF-8 encoding (Recommended solution)

Method 2 is highly recommended. If you are running beatoraja using the UTF-8 encoding, switching to Japanese locale is **NOT** required (I have not once switched to JP locale). Also, even if you are already using the Japanese locale, switching to UTF-8 encoding is still recommended, as this resolves crashes that happen if a BMS folder name is garbled.

**Note:** Opening .zip files is another reason frequently cited for switching to JP locale. Switching just for this reason is not recommended however, as there are better solutions to this. [More info here - locale issues when opening zip files](Downloading-Songs#locale-issues-when-opening-zip-files).

### How to run beatoraja with UTF-8 encoding
- **Remark:** If you don't want to try applying the fix manually, you can instead just replace your `beatoraja-config.bat` file with this file [over here](https://github.com/wcko87/beatoraja-english-guide/tree/resources/beatoraja-configs), which already has the fix applied.

The UTF-8 fix is applied by making a simple edit to the `beatoraja-config.bat` file (note that `beatoraja-config.bat` is what you are using to open beatoraja).

Open up `beatoraja-config.bat` (or `beatoraja-config.command`, depending on which you use to start beatoraja), and add `-Dfile.encoding="UTF-8"` to the end of the `_JAVA_OPTIONS=` line.

**Note:** The `-Dfile.encoding="UTF-8"` argument must be placed *outside* of the inverted commas `''`. This sounds odd, but the setting will do nothing otherwise. There must also be a space before `-Dfile.encoding="UTF-8"`.

The line should look like this:
```
set _JAVA_OPTIONS='-Dsun.java2d.opengl=true -Dawt.useSystemAAFontSettings=on -Dswing.aatext=true -Dswing.defaultlaf=com.sun.java.swing.plaf.gtk.GTKLookAndFeel' -Dfile.encoding="UTF-8"
```

Skin settings might reset after switching to UTF-8, because the skin settings may have been saved in the default encoding. It shouldn't be too much trouble to set the skin settings again, since you only need to do this once.

It might be possible that switching encodings might cause your player config file (in player/player1/config.json) to be unreadable. If the config file can't be fixed, you may have to replace the config file with a new one.

### How to replace (clear) your config file
1. Backup the player's config.json (player/player1/config.json)
2. Clear the contents of the file and replace it with just the characters `{}`. This forces beatoraja to generate a new config.json file from scratch (Note: beatoraja won't start without the `{}` in the file).
3. After the player profile has been cleared, open the beatoraja config again, go to the skin select menu and make sure a skin is properly set (i.e. not blank) for each of the important categories (e.g. 7KEYS, DECIDE, RESULT, SKIN SELECT). beatoraja crashes if it tries to load a blank skin.

**Note:** The player's config.json is different from the config.json you see in the main beatoraja folder! The player's config json is in the `player/player1` (or player2 etc) folder, and contains settings that are specific to the player profile, like skin settings.

There should be no more crashes / issues after that.


----------
# Configuring Beatoraja

This covers some of the more important things to configure when first starting the game. Refer to [beatoraja Configuration](Configuration) for more detailed information on what you can configure in beatoraja.

### In Config Menu (before starting game):

Go to the `Resources` tab to add your song folders. (add them under BMS Path, not Table URL!)
If you are looking for songs/charts, see [downloading songs/charts](Downloading-Songs) for more information.

If you wish to use [difficulty tables](Difficulty-Tables), add table links to the Table URLs and click `Load difficulty table` to load all the listed difficulty tables into the game.

If you are using a IIDX controller with axis input, you might want to turn on `ANALOG SCRATCH` under the `Input` tab. This needs to be turned on individually for each mode (7KEYS, 5KEYS, etc). See [Analog Scratch](Configuration#analog-scratch) for more information.

Most of the settings under `Play Option` can be configured in game.

It might also be good to get a good skin for beatoraja too. Skin settings can be set in the `Skin` tab.
- [List of beatoraja skins](List-of-beatoraja-Skins)
- Note: beatoraja 0.8.0 and above comes with the ModernChic skin pre-packaged.

If you play on the P2 side (turntable on right), you can switch to P2 in the skin settings.


### In Game (during music select):

Press 6 on the keyboard to open key config.

In the key config, you should have binded the START and SELECT buttons (default Q and W on keyboard). Hold START, SELECT or START+SELECT to access the three play options menus. These menus cover the majority of the play options available in the config.

Press F12 to open skin settings in-game.

Check the [Music Select](Music-Select) page to find out what else you can do in this screen.

### In Game (during play):

Before the song starts, the game gives you some time to adjust your scroll speed settings.
- Double-tap START to turn on the SUDDEN+ lanecover
- Hold START + turn turntable to adjust lanecover height (white number)
- Hold SELECT + turn turntable to adjust green number (related to scroll speed)

The song will not start until you have finished adjusting.
A full explanation on sudden+, scroll speed and green number is given here: [Scroll Speed and Green Number](Scroll-Speed-and-Green-Number)


----------
# How to navigate menus

The turntable (scratch up / scratch down) is used to scroll through menus.

Notation: keys 1 to 7 are the keys from left to right. White keys are 1,3,5,7 and black keys are 2,4,6.

Generally, white keys go forward in menus and black keys go backward.
However, in beatoraja, each key actually has a slightly different purpose.

- Key 1: Go forward / start song
- Key 3: Go forward / start song on practice mode
- Key 5: Go forward / start song on autoplay mode
- Key 7: Go forward / play selected replay
- Key 2,4: Go back / change sort order if you are on topmost level
- Key 6: Select replay


----------
# Common Issues

### [Discussions Page](https://github.com/wcko87/beatoraja-english-guide/discussions)
If you need help and the section below does not answer your questions, please visit the [Discussions Page](https://github.com/wcko87/beatoraja-english-guide/discussions). I can try to provide a bit of tech support / answer questions there.

### Can't start up beatoraja - beatoraja-config.bat opens and closes instantly

Just before the .bat file closes, it actually displays an error message telling you what went wrong. Unfortunately, it closes too quickly to view the error message.

There are two ways you can view the error message:
1. Open command prompt in the beatoraja folder, and type `beatoraja-config.bat` to run beatoraja from the command prompt. This lets you view the error message because the command prompt doesn't automatically close.
2. Open beatoraja-config.bat in a text editor like notepad, and type `pause` on a new line at the bottom of the file. The "pause" command will prompt you to "Press Any Key to Continue" before the command window closes. You can remove the pause command after you're done diagnosing errors.

Here are the common errors you might see:

#### 1. java not found
- Then java is either not properly installed, or is installed but has not been added to the PATH environment variable. If you are not sure how to add java to PATH, reinstalling java should automatically add it to PATH for you.

#### 2. Invalid maximum heap size: -Xmx4g
- Then you are currently using 32-bit java. 64-bit java is recommended for running beatoraja.
- To check whether your current java installation is 32-bit or 64-bit, open command prompt (windows+R, type "cmd", enter) and type `java -version`. If you are on 64-bit java, it should say something along the lines of `64-Bit Server VM`. If you don't see that, you are on 32-bit java.
- You can technically run beatoraja on 32-bit java. This can be done by removing the `-Xmx4g` flag from beatoraja-config.bat. However, this is not recommended as the `-Xmx4g` flag is what allows beatoraja to run with a memory cap of 4GB rather than the default 1GB cap.

#### 3. beatoraja.jar is not found
- There should be a beatoraja.jar in the same folder as beatoraja-config.bat. If there is no beatoraja.jar, you probably downloaded the source code for the game instead of the game itself. beatoraja.jar is the main game executable, and so is definitely necessary.

#### 4. Error: Could not find or load main class bms.player.beatoraja.MainLoader
- You might experience this error if you are on Java 9+ or using OpenJDK on Linux. This may be because JavaFX isn't included with your Java installation.
- If this is indeed the case, you may have to install JavaFX manually.
- If you are on Java 8 (Java 1.8) on Windows, you will definitely have JavaFX installed, so this shouldn't be the issue.
- If you have trouble installing JavaFX (especially on mac or linux), one option is to use [Liberica JDK 8](https://bell-sw.com/pages/downloads/), which is a version of Java that has JavaFX included by default.
  - **Note:** You need to select "Full JDK" instead of "Standard JDK" when downloading Liberica. Only the Full JDK includes JavaFX.


### I added songs, but I can't see the folders in game

Try restarting beatoraja first. The songs might show up after a restart.

If the songs still don't show up, there are a few possible causes.

#### You placed your songs in the beatoraja folder

i.e. you did something like this:
```
beatoraja 0.8.2
 '-> etc etc (beatoraja files)
 '-> songs
     '-> BOFU2016
     '-> BOFU2017
```
If your songs are in the beatoraja folder, beatoraja may not be able to read the songs. In general, I recommend having your song directory be **separate** from your beatoraja directory. Something like this:
```
BMS
 '-> BOFU2016
 '-> BOFU2017
 '-> MISC

beatoraja 0.8.2
 '-> etc etc (beatoraja files)
```
In general it is a good idea to keep your song folders separate from the game client. This is because you may upgrade or change your BMS client, but you will still be using the same BMS songs.

#### An error occurred while adding songs
This might have happened if you notice a bunch of errors in the command window and the song adding process halts suddenly.
- If this indeed happened, try to find out which is the offending BMS that caused the song adding to crash.
- If you can figure out which BMS is causing the issue, it would be nice to report it to the developers so that the problem can be identified.

#### A BMS folder is placed next to a song folder
This might have happened if you only see a few songs in your songwheel, and don't see any subfolders.
- Don't put song folders next to subfolders in your BMS song folder. We may not be able to differentiate between song folders and subfolders when this happens.

    This is an example of song folders next to subfolders. Don't do this.
    ```
    BMS
    |-> BOFU2016
    |-> song1
    '-> song2
    ```
    You can organize your BMS folder like this instead:
    ```
    BMS
    |-> BOFU2016
    '-> Misc Songs
        |-> song1
        '-> song2
    ````


### My skin settings are not saving

This is usually a symptom of locale issues. See [Fixing locale issues](#fixing-locale-issues) for more information, and make sure the UTF-8 fix is applied.
- If you had applied the UTF-8 fix manually, there is a chance that you did not apply it correctly.
- Also, do not run beatoraja through the beatoraja.jar file. The UTF-8 fix does nothing if you are not running beatoraja by starting beatoraja-config.bat.
- It is possible that you have also somehow corrupted your player config file. In that case, you might want to [reset your player config file](#how-to-replace-clear-your-config-file).


### My scores are not saving

Scores will always save after exiting the song (as long as you have hit at least 1 note in the song before exiting). If your scores aren't saving, it is most likely because you have some assist option on. Check out the following pages:
- [Assist and Miscellaneous Options](Configuration#assist-and-miscellaneous-options)
- [Random and Gauge Settings](Configuration#random-and-gauge-settings)

If your scores suddenly vanished, it may simply because you switched between [LN, CN and HCN modes](Configuration#ln-cn-and-hcn-mode). Scores are saved separately between the modes, for charts that have at least one long note in them.


### I connected my controller but my turntable does not work!

You probably did not bind the controller in the key config. Even the turntable needs to be assigned to F-SCR and R-SCR in the key config for it to work. Press 6 on the keyboard to open the key config in game.

If that was not the reason, there are a few other possible causes:
- Take note that the controller must be plugged in before starting beatoraja.
- If you have multiple controllers connected, make sure the correct controller device is selected in the key config. Press 2 on the keyboard in the key config menu to change the controller selection.
- Take note that the key config is set separately for each key mode. Notably, 5Keys and 7Keys have separate key configs. Press the left/right arrow keys on the key config menu to switch key mode.
- If the controller only does not work in the music select menu, this may be because you have the wrong "Music Select" setting in the key config menu. Press 1 on the keyboard to switch the "Music Select" setting. "2dx sp" means the 7Keys key config is used for music select. "2dx dp" means the 14Keys key config is used, and "popn" means the 9Keys key config is used.
- If the turntable is behaving wierdly, this may be due to analog scratch being set incorrectly. See: [Analog Scratch](Configuration#analog-scratch)


