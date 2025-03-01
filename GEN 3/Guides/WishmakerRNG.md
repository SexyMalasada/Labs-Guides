# Wishmaker Jirachi RNG Guide

This guide is meant to teach you how to RNG a Wishmaker Jirachi from the ENG Colosseum Bonus Disc.<br>
The process is presented here as done on, and with examples in `BizHawk` (which runs an mGBA core); but it can be followed in `mGBA` and `VBA` just as well, with specifics to the latter noted where relevant.

## Getting Started

What you'll need:

- [Finder-Toolbox](https://github.com/Lincoln-LM/Finder-ToolBox) (an old fork of PokéFinder with some extra functionalities)
- [Jirachi Finder](https://github.com/Lincoln-LM/Jirachi-Finder/)
- [Gen 3 RNG Lua Scripts](https://github.com/Wi-Fi-Labs/PokeRNG-LuaScripts/tree/main)
- [BizHawk 2.8-rc1](https://github.com/TASEmulators/BizHawk/releases/tag/2.8-rc1); [VBA rr 23.6](https://github.com/TASEmulators/vba-rerecording/releases) or [mGBA](https://mgba.io/downloads.html) emulator
- [Dolphin](https://dolphin-emu.org/download/) emulator (official build with an integrated VBA connection)
- A copy of Pokémon Ruby or Sapphire
- A copy of the ENG Colosseum Bonus Disc

## Preparation & Basic Info

Wishmaker Jirachi is generated when the the GBA is connected to the GameCube (Dolphin) running the Colosseum Bonus Disc, with it's stats being decided during this interaction by checking a value in the Ruby or Sapphire game's save, called a `Checksum`.<br>
Contrary to what you may think, most of this RNG is actually done on a Gen 3 game (Ruby or Sapphire), rather than being an actual GCN RNG, as the process essentially consists of preparing a new Ruby or Sapphire save with a specific `Checksum` value, in order to obtain your desired target WISHMKR Jirachi!<br>

If you wish to learn more about what the `Checksum` is, please refer to [this page](https://bulbapedia.bulbagarden.net/wiki/Save_data_structure_(Generation_III)).<br>

_Important note: If you have an official PokeFinder 4.0.0 version or later installed, keep in mind you will need to have a separate `profiles.json` file just for Finder-Toolbox, in order to avoid conflicts. Follow [this PokeFinder profiles](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/MISC/DS/PokeFinderProfiles.md) management guide for more info!_

## Step 1: Searching for a target

Open [Finder-Toolbox](https://github.com/Lincoln-LM/Finder-ToolBox) and select the `Stationary` option under the `Gen 3` tab.<br>
In the new window, open the `Searcher` tab, and configure it as follows (example image below):
- Method: `Wishmaker`
- Filters: `IV ranges`, `Shiny` and `Nature` options as you desire.<br>

_Note 1: No profile setup is required to be loaded for the searching of Wishmaker Seeds and spreads._<br>
_Note 2: Because the seed values for Wishmaker RNG are only 16-bit (4 digits), the available IV spreads and Nature combos are very limited! A well known example of this limitation is that there are **only** 9 different Shiny Wishmaker Jirachi possible combos!_ <br>

Once you're satisfied with your search parameters, click `Search` and let Finder-Toolbox run the search.<br>

After it has found some results select a suitable IV spread & Nature combo, and note down the respective target seed somewhere.<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/Wishmaker1.png"/></p>

## Step 2: Start a New Game

Before opening the emulator, ensure there is no save for your game (Ruby or Sapphire) in the saves folder (`SaveRAM` folder for `BizHawk` and `Battery` for `VBA` folder). Once you've confirmed this, you can now and launch your emulator & game. You must ensure that you are using the `Dead Battery` method in order for this RNG to work properly. If you don't know what this is or how to do it, I recommend you check out the [RS Dead Battery](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3InitialSeedRNG.md#dead-battery-rs) guide!<br>  
Once you've set up your emulator for `Dead Battery`, reboot the core (reload game in `VBA`), launch the `RS_RNG_BizHawk_SM` script with the Pandora tab open, and start a New Game.<br>
You can choose to RNG a specific TID and/or SID if you wish, but its not a requirement for Wishmaker Jirachi RNG. If you still wish to for whatever reason though, be sure to check out the [Gen 3 TID/SID RNG](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3TIDSIDRNG.md) guide if you don't know how to, keeping in mind you would be doing it with the `Dead Battery` method.<br>
As soon as you're in the back of the moving truck and able to open the menu, pause the game, make a save state and a note of your obtained TID & SID by checking the script on bottom right corner of the screen. You can then close the script - **but not the game!**<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/Wishmaker2.png" width=480 height=320/> <img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/Wishmaker3.png" width=480 height=320/></p>

## Step 3: Finding Checksum save parameters

Open [Jirachi Finder](https://github.com/Lincoln-LM/Jirachi-Finder/). This tool makes it possible for you to essentially 'configure' a new save's parameters for you to get the desired `Checksum` value, that will match your target Jirachi `seed` (example image below).<br>

Start by inputting the TID & SID you obtained above in the `IDs` field, and then configure things like `Name`, `Gender`, `IDs`, `Clock`, and `Starter`. If you don't particularly care about any of these, I suggest to just use whatever values get you closer to your target seed (ie `Checksum`) as displayed in the small box at the center-bottom area of the tool.<br>
Once you're done with those, you can then fiddle with the `Game Options` settings. It is **strongly** recommended to set the `Text Speed` as 'FAST' (the reason is addressed the next step).<br>
Lastly, configure the `Playing Time` until you get the desired Checksum - It is advised to allow for a play time of _at least_ `10:00 minutes`, in order to be able to safely walk to Route 103 and back, and obtain the PokéDex. The `F` (or frame) field of the target playing time must also **ALWAYS** be a value of 23 or larger!<br>
If necessary you can go back to one of the previous parameters and adjust it slightly until you get a combination of parameters that gives you the desired result.<br>

After you've successfully found such a combination of parameters, you can double check if your desired spread will be obtained with this Checksum by configuring the `Info>Time` section of the tool with a `Starting Time` of -1F from your `Playing Time`, a `Wait Time` of just 1F, and then clicking `Generate`.<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/Wishmaker4.png"/></p><br>

Once the above is done you can then proceed to the next step.<br>

_Important Note: It is imperative that you don't run into any wild encounters during your playthrough as those can change your final Checksum value considerably. For this reason you should leave the `Pokémon` section with no checks, and use save states when playing through the save, so that you can restore it in case you accidentally run into any._

## Step 4: RNG the save parameters

Now that we have found all the parameters our save needs to have in order to RNG our `Checksum` value, it's time we move onto the RNG process itself.<br>
It's important to note that when saving the game at your target `Playing Time` in order to RNG the `Checksum`, there will be a certain delay in `F` frames depending on your `Text Speed` settings; for 'FAST' settings these values are `61F` in `BizHawk` and `62F` in `VBA`. For other `Text Speed` settings you must calibrate the delay yourself.<br>

Start by opening the `RS_Checksums_RNG_Bizhawk` lua script in a text editor like NotePad, and navigate to the section shown below, editing the required values as follows (don't forget to save the file after editing):
- `local savePath`: paste here the location of your save file with double `\\` between folders
- `local targetSeed`: your target Jirachi seed in hexadecimal
- `local targetHour`: the target playtime hours (usually always 0)
- `local targetMinute`: the target playtime minutes you got from Jirachi Finder in the previous step
- `local targetSecond`: the target playtime seconds you got from Jirachi Finder in the previous step
- `local targetSixtiethSecond`: the target playtime frame (F) you got from Jirachi Finder in the previous step
- `local delaySecond`: the delay in seconds (if not using 'FAST' Text Settings)
- `local delaySixtiethSecond`: the delay in frames/advancements (61 for `BizHawk`; 62 for `VBA` if using 'FAST' Text Settings)

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/Wishmaker5.png"/></p><br>

Once you've edited the script, you can now go back to your emulator, and load the `RS_Checksums_RNG_Bizhawk` script in the Jirachi tab. Your previously obtained TID & SID should be visible in the bottom right corner, as well as all the target parameters you input above.<br>
You should also see a playtime value after `Base Save Time` - this is the target playtime you must aim for, calculated with the delay you input in the script.<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/Wishmaker6.png" width=480 height=320/>

Proceed now to un-pause, configure and quickly play through your game in order to have all of your parameters matching settings you configured in Jirachi Finder in the previous step, until you obtain the PokéDex:
- Configure the Game Options
- Set the Clock in your room
- Pick the correct Starter
- Walk to Route 103 and back to the Lab, battling (and beating) the rival in the process **without engaging in any Wild battles** (use save states)
- Obtain the PokéDex & Poké Balls when back at the Lab in Littleroot

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/Wishmaker7.png" width=480 height=320/> <img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/Wishmaker8.png" width=480 height=320/></p>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/Wishmaker9.png" width=480 height=320/> <img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/Wishmaker10.png" width=480 height=320/></p><br>

Once you've done all of the above, open the menu and save your game **ONCE**. After doing so, select the save option again, this time pausing the emulator at the **second** `Yes/No` prompt, and make a save state.<br>
If you've done everything correctly so far, all you need to do now is to let the RNG advance until the `Time` in the lua script matches `Base Save Time`, taking care to make a new save state once you're close to it, and manually advancing the RNG so as to not miss it.<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/Wishmaker11.png" width=480 height=320/><br>

Once you reach your `Base Save Time`, hold A and un-pause the game, so as to save the game at that point and if you did everything correctly, obtain your desired Jirachi Seed or `Checksum` value, listed in the `Jirachi Seed` line of the script!<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/Wishmaker12.png" width=480 height=320/>

## Step 5: Transferring the Jirachi from the Bonus Disc

Now that you have RNGd your RS save to receive the Jirachi you want, it's time to proceed with the final step: the transfer from the Bonus Disc.<br>

Start by opening [Dolphin](https://dolphin-emu.org/download/), and configure it to open it's integrated VBA emulator whenever you load a GCN disk. To do this, click the 'Controllers' button, and configure `Port 2` as 'GBA Integrated'. You can also click the 'configure' button and set the key-binds for the integrated GBA key binds, but this is not strictly necessary (it's recommended to use different ones from those you use for Dolphin itself if you do though).<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/Wishmaker13.png"/></p><br>

Once that's done you can now launch your Colosseum Bonus Disc, which will also open the integrated VBA in a separate window. Select the Gift Jirachi option and proceed until you're at the prompt screen shown below and pause the emulator.<br>
Right-click on the GBA window to load the ROM for your RS game, as well as importing the relevant save file (it accepts both `Sav` & `SaveRAM` files just fine). Once you do this, the GBA should load Ruby or Sapphire with your RNGd save.<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/Wishmaker14.png"/></p><br>

From here, un-pause your emulator and proceed in Dolphin. You should see the GBA screen loading at the same time or thereabouts, as the cutscene showcases it in the Bonus Disc.<br>
If the connection is successful, you should see the following progress as showcased below. Once the Jirachi has been transferred, right-click on the GBA screen and select to 'Export Save Game' to the original location of your `BizHawk` or `VBA` save. After this is done you can now close Dolphin.<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/Wishmaker15.png"/></p>
<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/Wishmaker16.png"/></p>
<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/Wishmaker17.png"/></p><br>

Finally once the transfer is complete, you can reload your GBA emulator and respective lua script in order to confirm the stats of the Jirachi you obtained do indeed line up with the one you RNGd for!<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/Wishmaker18.png" width=480 height=320/>

***
_The contents of this guide were all written by SexyMalasada and partially based on guides written by [DevonStudios](https://devonstudios.it/)._<br><br>
_[< Back to the Gen 3 Guides page](https://github.com/Wi-Fi-Labs/Labs-Guides/tree/main/GEN%203)_