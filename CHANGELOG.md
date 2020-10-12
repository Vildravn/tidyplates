---------------------------
6.20.0
---------------------------
Shadowlands compatibility
* Core: Updated the TOC versions.
* Core: Replaced UNIT_HEALTH_FREQUENT with UNIT_HEALTH
* Core: Remove newbie tooltips (GameTooltip_AddNewbieTip was removed) 
* Core, Hub: Fixed lua errors caused by backdrop system changes



---------------------------
6.19.4
---------------------------
* Core: Fix for combo widget.
* Core: Updated the TOC versions.


---------------------------
6.19.3
---------------------------

New Features:
* Core: Damage Absorbs: Absorbs will appear as a lighter shade of the current bar color.
* Core: Added feature to statusbar widget (Tail Bar) enabling Absorb Display (11.30.2018)

Changes:
* Unit Filter: Inactive Units: Quest Mobs are considered 'Active', unless you are in an instance
* Hub: Renamed Color.lua to ColorThreat.lua



---------------------------
6.19.2
---------------------------

* Core: nil frame bugs
* Hub Widgets: Fixed duplicate code
* AuraWidget: Fixed "Absolute Corruption"
* Aura Widget: Purgeable Effects: Needs testing!
* /hub should now bring you to the current profile panel, rather than always going to "Damage"
* Debuff coloring should look correct now; Fixed the tga file color
* Combo Point Widget now uses a single graphical frame, and re-parents to the target nameplate.  
	- This is to prepare for a large combo widget update
	- The new widget will be called "Combat Widget", since it'll display more than just combo points
	- This update, no new features are added; I just want to see if the anchoring system has issues
* Unit Filter: Removed QuestInfo override on Inactive Units



---------------------------
6.19.1
---------------------------

* Fixed Hub PlaySound Error

---------------------------
6.19.Alpha2
---------------------------

* Aura Widget: Migrated to 8.0 UnitAura function 

---------------------------
6.19.Alpha1
---------------------------

* HealerTrack - Error Fix - Needs testing
* Tank Track - Error Fix - Needs Testing
* Combo Point Widget - Fixed errors, events, combat event update - Needs more testing
* Changed castbar catcher to use new return value structure (Fixes Statusbar error)
* Updated sounds to SOUNDKIT ( IG_MAINMENU_OPTION_CHECKBOX_ON = 856)  (Fixes TidyPlatesUtility error)

---------------------------
6.18.11
---------------------------
* I got injured a few weeks ago, halting my progress, so I may have broken some things, and then forgot to fix them...

* Core: Different hiding method for Blizzard nameplates.  Might be a unreliable?  Changed to fix tainting issues.
* Core: Updated the TOC versions.

* Threat Line: The widget will auto update with no fading.
* Core: Increased the Target & Mouseover FrameLevels
* Hub: Filter: "Filter Players" will now filter players full-time.
* Core: unit.reaction will default to "HOSTILE" if it can't be determined  (Should mitigate color.lua reaction color error)

* Off-Tank Aggro: Party/Raid Threat  IsTank()  (unitid.."target") somethingerother?


---------------------------
6.18.10
---------------------------
* Core: RAID_TARGET_UPDATE, Full update
* Core: Reverted unit.reaction gather function to using UnitSelectionColor.
* Aura Widget: Removed the wonky Hide call.

---------------------------
6.18.9
---------------------------
* Utility: Replaced GetAggroCondition()
* Core: Added RAID_TARGET_UPDATE event to core
* Aura Widget: Added some missing ClearAllPoints()
* Core: Updated unit.reaction function.  Now uses UnitReaction().  What a concept!
* Threat Line Widget: Fixed anchor point..  the widget itself needs some work, though.

---------------------------
6.18.7
---------------------------
* Utility: Replaced GetAggroCondition()

---------------------------
6.18.7
---------------------------
* Core: Restored the WidgetReset function; Not quite ready to take that plunge.
* Aura Widget: Some fixes and tweaks
* Cure: Added, TidyPlates:GetThemeName()


---------------------------
6.18.4
---------------------------
* Major Internal Changes Warning!

* Core/Utility: Totally and utterly removed all the caching that we used to do to store Guild names, Titles, Classes, etc.
	IsGuildMate and IsFriend have been bypassed, so those functions don't do anything. Consquently,
	the associated features are temporarily disabled.

* Core: The Widget Reset function has been removed, which will possibly cause some problems with Non-Hub themes, but will help
	to fix some memory leakage.  I want to avoid repetitively destroying/creating frames, so now the Hub functions will attempt
	to call widget:UpdateConfig() and recycle/reconfig the old frames instead of nil-ing the old ones and creating new ones.

* Combo Points: Now displays a 6th when you're using Deeper Strategem.  Anticipation will still use the 5+Overlap method to display.
* Combo Points: Chi does not show up on Brewmaster Monks

* Hub: Tapped Color on Healthbars is now working again
* Themes: Fixed some elite/level display problems
* Hub: Active/Damaged Units: On NPCs, if the unit has a target, it's considered active.

* Hub: Guildmate and Friend colors are temporarily disabled.


---------------------------
6.18.3
---------------------------
* Mini Mob Headline is now Off by Default
* Neutral Unit Headline is now Off by Default
* Neon Level Text field width increased (to fix 100+ not being displayed correctly)
* Fixed TotemIcon nil field error
* Fixed Approximate Health
* Fixed text shadow flag
* Fixed friendly auras appearing when using "Show Dispellable.."
* And more little fixes

---------------------------
6.18.2 - Happy Legion Day!
---------------------------
* Typo in Quest display

---------------------------
6.18.1 - Happy Legion Day!
---------------------------
* RESTORED the "Use Blizzard Font" from the Hub/Profile panel.  This will use the STANDARD_TEXT_FONT
* Note: "Force Blizzard Font" has been renamed to "Force Multi-lingual Font" to make its purpose clear.
* Renamed/Repurposed "Filter NPC" to "Filter Enemy NPC"
* Added: "Filter Non-Titled Friendly NPC".. Which hides friendly NPCs that DON'T have a title, such as "Innkeeper".
* Added: Experimental: Quest display on Headline Status Text.

---------------------------
6.18.Beta21
---------------------------

* "Force Blizzard Font" added to the Tidy Plates main panel.  This will use the Fritz Quadrata family,
	and possibly fix localization issues
* REMOVED the "Use Default Blizzard Font" from the Hub.  See above.

# Fixed "Spotlight on Casting" Opacity
* Fixed "Bar Width" shrinking

* Better nil handling
* Layering improvements
* In Hub\Templates, changed OnEvent handler to OnShow and removed panel:RegisterEvent("PLAYER_ENTERING_WORLD")
	(This will keep it from being called until the panel is shown)

* Broke Guildmate and Friend coloring.  I'll fix at some point.
* On the good side, No more caching of NPC roles!  They can be read instantly, now.

* Cleaned up some ancient cludgy code.

* Introduced more bugs. (It always happens!)


---------------------------
6.18.Beta20
---------------------------
Aura Widget typo fix
Hopefully final fix for Blizzard Bars appearing
Temporarily restored the outdated UseTankVariables and UseDamageVariables functions
Tinkered with the ShadowOffset

---------------------------
6.18.Beta19
---------------------------
Isolated the theme parser to TidyPlatesParser.lua

Loading themes via functions:
	TidyPlates:SetTheme(themeNameString)
	TidyPlates:GetTheme()

Deprecated:		(Converted to Dummy functions, will be removed)
	TidyPlates:ActivateTheme(themeNameString)
	TidyPlates:ReloadTheme()

Moved "Use Default Blizzard Font" down to the bottom of the Settings page
	Didn't seem to be in the right place under "Health Bars"
Advanced is now "Funky Stuff".  Why?  Because I've been drinking?  Perhaps..
Hub: Fixed Unit Filter Alpha
Rejiggered some things in the Panels
	Hub/Profile Panels are now under the Tidy Plates tree
Renamed some of the Core files
Cleaned up some old rotten code in Core and Panel


---------------------------
6.18.Beta18
---------------------------
Panel fix

---------------------------
6.18.Beta17
---------------------------
Off-Tank Highlighting is back!  (/hub, jump to "Threat")

Specialization Profiles are Back!

And with them, new errors to find.

Also, it's painful to look at code that I haven't touched in 5 years



---------------------------
6.18.Beta15
---------------------------
Cooldown fixes, perhaps?

---------------------------
6.18.Beta13
---------------------------
Aura Widget..  made it so OmniCC and the like won't mess with cooldown animations.


---------------------------
6.18.Beta11
---------------------------
More futzing with the Aura widget.  Stacks should show up.  Dispellable stuff might show up.


---------------------------
6.18.Beta10
---------------------------
Combo Point Widget should now update properly.


---------------------------
6.18.Beta9
---------------------------
Aura Widget is now about 90% complete

Fixed some errors when Personal Resource Frame is used (alpha.lua:30)


---------------------------
6.18.Beta8
---------------------------
Aura Widget is now about 80% complete

Under the Tidy Plates options panel, you can now disable cast bars


---------------------------
6.18.Beta7
---------------------------
Personal resource bar should work on it's own.

Class widget repair

Cast bar alpha
Tradeskill bypass on castbar

Tank autoswap may work correctly on your class;  Works fine for druids!


---------------------------
6.18.Beta6
---------------------------
Level coloring + text should be improved.

FULLY hiding the Blizzard frames.. success!  Thanks N!

CVar stuff

Some health status text should now be working


---------------------------
6.18.Beta5
---------------------------
Raid Icons should be working

Flickering is still a bit of a problem.

Frame rates are lower than desired.

I need to work on the widgets (auras, healer tracking, tank tracking, etc.)


---------------------------
6.18.Beta4
---------------------------
Class colors working better?
The new Cast Bars have been written.  Hopefully they work.  I've only been testing near the target dummies.


---------------------------
6.18.Beta3
---------------------------
Class Colors should be working.  On health bars, at least.  I briefly tested them.
Nameplates are not (and can not be) generated for enemies who are not in pvp conditions.  (This has been the case for years)

Cast bars..  Early next week, I hope.

Calm down, take a deep breath.  It's Friday, July 22nd!  It's time for beverages!


---------------------------
6.18.Beta2
---------------------------
More things are working!

Notably absent...
Cast Bars
and more

I have not tested the aura widget... although it MIGHT work.



---------------------------
6.18.Beta1
---------------------------
Nameplate-pocalypse!!!!!!!

99% of the previous nameplate system has been replaced by Blizzard for Legion.

Rebuilding has been slow, since I'm (apparently) a grown-up, now. ;-)

BUT, progress is indeed being made!

The internal widgets are disabled, which means the Aura timers are not working.  I'm rewriting the entire bloody system because we now have a good way to capture that data without all the trickery that was previously required.  (Blizzard does love us!)

Again, progress is being made!

Many things are broken, so I expect that many of you might want to check back with Tidy Plates in a week or so.

Happy questing!


---------------------------
6.17.1
---------------------------
- Core: New value: unit.healthmaxCached, which is updated on target and mouseover.
	(This uses the UnitHealthMax API function to store real health data.)
- Core: Where available, uses the healthmaxCached to create real numbers.
- Core: Figured out what the other statusbar is.. incoming heals.  But you guys already knew that.  Hiding that stuff, for now.
- Hub: If healthmaxCached doesn't exist, the real health value won't be shown.  (Percent will still work)

---------------------------
6.17.0
---------------------------
- Partially updated the core to the new internal Blizzard nameplate layout.  Seems to fix a bunch of things for me.  ymmv
- Not sure what some of the new bits and pieces are for... futher investigation is needed.

---------------------------
6.16.1
---------------------------
- Threat System: Disabled 'Other Tank' functions, for now; They're broken, and causing secondary issues to develop.

---------------------------
6.16.Beta: Quick Notes
---------------------------
This is a MAJOR update to Tidy Plates, and many things have changed.

Here are some of the bigger changes:

* The Hub has been revamped and some rearranging has been done.
* Quick Fix - Quick Setup:
	1. Use '/tp' to reselect your Theme (and Profile)
	2. Use '/hub' to check your settings...

* Some settings have been pruned; If there was something important that got
	removed, let me know...

* Numerous Bug Fixes & Improvements
* Numerous Bug "Additions"? (Quite possible!)

I sincerely apologize for any inconvenience these changes may cause...

Think of this: Changes mean that this addon is being actively developed and
	maintained, rather than withering, as many addons do...



--------------------------------------
6.16.Beta8
--------------------------------------
* Hub: Threat: Highlight Mobs Tanked by Other Tanks:  It was a mess. Rewrote and tested with hunter pet, and it's working well in that condition.
	- To do:  Reimplement Combat Log melee swing detection, and test in 5-man and Raids

--------------------------------------
6.16.Beta7
--------------------------------------
* I haven't been keeping track of changes.  Warlords- yay!

Things still needing testing...
* Healer Tracking
* Tank Target-Of-Mob Tracking

--------------------------------------
6.16.Beta6
--------------------------------------
* Some fixes, some additions..

Things still needing testing...
* Healer Tracking
* Tank Target-Of-Mob Tracking


--------------------------------------
6.16.Beta5
--------------------------------------
* Lots of things that I didn't write down because I'm busy playing Warlords of Freakin' Draenor woot!
* Fixed some bugs
* Added some new bugs, probably
* Lots of changes to the Hub.  Feedback is good.  Be polite, please!

* Migrated to new Dropdown Menu and Hub Function system; Your settings will be a bit borked until you go to /hub

--------------------------------------
6.16.Beta4:
--------------------------------------
* Themes: Migrated Quatre, Grey, and Graphite to the new system
* Hub/Themes: New function definition process, makes it easier to add themes
* Numerous bug fixes..  Can't remember.  Been leveling my druid.  Sleep; Need more of.

--------------------------------------
6.16.Beta3:
--------------------------------------
* Hub/Aura Widget: Fixed an issue which would prevent your auras from showing up (Previous configuration conflict)

--------------------------------------
6.16.Beta3:
--------------------------------------
* Widget/Combo Points: Fixed?

--------------------------------------
6.16.Beta2:
--------------------------------------
* Widgets/UnitCache: Fix for mouseover bug
* Class Coloring: Fixed IsInInstance() issue.. maybe?
* Hub:  Removed "Default" choice from the Friendly and Enemy Coloring Modes  (Yeah, this will make current settings funk-up...  but it cleans out that redundant choice)

--------------------------------------
6.16.Beta1: Full-ish List of Changes:
--------------------------------------

Core:
* Core/Panel: !! The Bundled themes no longer create a "Damage" and "Tank" copy !!
* Core/Panel: Introduced a new menu set, called Profiles, which will load the appropriate "Damage", "Tank", or "Healer" Hub profile.
* Core/Panel: When the selected theme is invalid, it'll fall-back to the first available theme.
* Core/Panel: Added a Slash Command alias, "/tp" in addition to "/tidyplates"

Bundled Themes:
* Themes: Neon & Quatre now have CastProtected art.  About time!
* Neon: New Elite Icon, which looks more like I'd originally intended.  (Replaces the old Star)
* Removed "Blizzard Theme"...  Sorry guys...  There are core things that I want to get done, and fixing/maintaining
	that component is not a priority.  It will probably return, but don't hold your breath.

Widgets:
* Widgets/UnitCache: Replaced " (*)" with FOREIGN_SERVER_LABEL, which will fix unit-caching on certain server types.
* Widgets/UnitCache: Now using a Scanning Tooltip, which should prevent conflicts with TipTac and other Tooltip mods
* Widgets/Aura: Combat Log Event Handler now skips units which are group members, relying on the general
	Unit event handler for their updates.

Hub/General:
* Hub: Colorized 'Friendly' and 'Enemy' description titles, to improve readability.
* Separated Hub functions.lua into discrete category files
* Tweaked some names/descriptions
* Removed Threat Wheel widget from Hub
* Hub: Added a button to the Advanced category; "Clear Cache", which purges the stored Class/Description/Guild data
* Hub/Advanced: "Health Bar Width" (%) Allows you to tweak the relative width of the theme's Health Bar  (Experimental)

Hub/Colors:
* Hub/Reaction: New Color, "Tapped Unit"
* Hub/Color Function: Tapped Color will be applied, taking priority over Threat/Etc. functions

Hub/Scale:
* Hub: Scale: Added, Bring Target units to Spotlight Scale, Bring Mouseovers to Spotlight Scale

Hub/Health Bar View:
* Removed several of the Status Text choices; These will reappear in a more advanced "Custom Text" category  (Working on it...)
* NOTE: The CUSTOM/ADVANCED Status Text function hasn't been written, yet; Thus, it doesn't do anything at the moment...

Hub/Opacity:
* Hub: Opacity: Enemy & Friendly units now have their own independent Spotlight Modes
* Hub: Opacity: Spotlight Modes; Removal of some redundant and underused modes.
* Hub: Opacity: New Checkbox, "Spotlight Raid Marked"
* Hub: Opacity: Modified Checkbox, "Bring Mouseovers to Target Opacity" to "Spotlight Mouseover"
* Hub: Opacity: Modified Checkbox, "Bring Casting Units to Target Opacity" to "Spotlight Casting Units"

Hub/Aura Widget:
* Hub: Buffs & Debuffs: Replaced "Aura Widget Mode" Dropdown with Checkboxes: "Include My Buffs", and "Include My Debuffs".
* Hub: Buffs & Debuffs: The widget will now use a Smart Mode, where it first evaluates the checkboxes, then evaluates the Aura List.
* Hub: Buffs & Debuffs: Added the "Not" prefix to the aura list; This new mode allows you to blacklist auras from "Show My Debuffs" etc.

Framework:
* Hub: Quick Frame Templates now return the created frame twice (ie. assign two references with a single call, which helps with the Quick Frame setup)
* Fixed some Odd Mouseover Behavior
* Rearranged and removed some old Hub stuff.  Cleaning out functions, removing ancient code, removed items of questionable utility



---------------------------
6.15.3
---------------------------
* Combo Widget: Fixed monk and localization issues
* Blizzard theme; "Fixed" the graphic alignment?
* Aura Widget:  Support for Infinite Duration (0=Expiration Time) auras, like "Storm, Earth, and Fire".
* Hub; Cast Bar: Changed the logic of Friendly Unit cast bars.  Perhaps this will help Capacitor Totem visibility?

6.15.2
---------------------------
* Unit Cache:
	- In LUA, When a table gets large, it will be slower to search. For some users, this cache may be quite large....
	- New features will automatically remove old data, and speed up lookups....
	- Added a second level Cache, which is looked at FIRST; not a saved variable (ie. erased on logout).  This should reduce frequent lookups to the BIG table.
	- Added a 'lastSeen' feature, where the function will timestamp when the unit was seen, and remove any unit entry (on login) not seen for 60 days.
* Combo Widget: Monks get to see their Chi displayed in the Combo widget


6.15.1
---------------------------
Fix for mouseover (and many other things)
* Fixed: Core: IsHighlighted...  figured out that IsShown() now returns a bool, rather than 1/0.  *sigh*

Fix for Friendly Class Colors
* Fixed:  Hub;Functions;GetFriendlyClass: IsInInstance() now returns true or false, rather than nil or false.  Updated the function to match WoW 6.0

* Removed 5.x Specific core code.


6.15.0.1
---------------------------
* Curseforge Reupload

6.15.0
---------------------------
* TOC update to 60000
* WoD Update....
	* Fixed Target selection issue; UnitExists() now returns true/false, rather than 1/0
	* Fixed Mouseover issue; 6.0 no longer uses the Highlight region to indicate mouseover; Using Name text color change.
	* Fixed Elite/Dragon Texture being reshown; Using :SetAlpha(0) rather than nilling the texture.

6.13.4
---------------------------
* Core: Raised the default Dropdown Menu strata to TOOLTIP

6.13.3
---------------------------
* Core: Added XML Template, TidyPlatesDropdownDrawerTemplate
* Core: Dropdown Menu Replacement (Trying to fix Blocked Action/Protected UI Taint issues in Panels and Hub)
* Core: Updated PanelHelpers.CreateDropdownFrame to use "TidyPlatesDropdownDrawerTemplate" and Dropdown Menu Replacement
* Core: Alpha transition animation has been restored.  You can disable it in the /tidyplates panel.
* Themes: Fixed Neon and Quatre Headline font size (bumped them down a few pts)
* Widgets: UnitCache: Fixed Connected Realm Class Caching


6.13.2
---------------------------
* Widgets: Fixed UnitCache to account for changes to the guild roster format
* Themes: Update Grey and Graphite to the new font variable
* Themes: Reduced "Roboto Condensed" size to better match the old font

6.13.1
---------------------------
* Widgets: Re-Fixed Class Icon

6.13.0 (Cumulative)
---------------------------
* Core: Added: unit.isMini = boolean.  This will eventually replace "unit.platetype" and "unit.isTrivial". Not anytime soon, though.
* Widgets: Fixed the Class Icon widget. Finally.  Added class-colored borders to each icon.
* Hub: Added a new checkbox to "Scale"; "Auto-Scale Mini Mobs", which will downscale those tiny guys, ironically making it easier to target.
* Hub: Added a new checkbox to "Unit Filter", "Override Target Scale", which will maintain the filtered scale of Targeted Mobs.
* Hub: "Use Blizzard font" should work properly again.
* Hub: Moved "Health Bar" to the top of the Hub page
* Hub: Merged "Style" into "Headline Mode"
* Hub: Raised "Buffs & Debuffs" upward in the Hub page
* Hub: "Health Bar" gets a couple new choices; Namely, separate coloring options for Friendly vs Enemy plates.
* Hub: Pruned the Color Mode lists
* Hub: Removed the "Warning Border Glow Mode" selector; Don't worry!  There's still a Warning Glow, but it's turned on/off within the "Threat" category.
* Hub: Added an option to "Spell Casting", "Enable Friendly Castbars"
* Themes: More fixes for text issues.
* Themes: New Font: Started replacing "Accidental Presidency" with "Roboto Condensed" across the bundled themes.


6.13.Beta3
---------------------------
* Themes: More fixes for text issues.
* Widgets: Fixed the Class Icon widget. Finally.  Added class-colored borders to each icon.
* Hub: Added a new checkbox to "Scale"; "Auto-Scale Mini Mobs", which will downscale those tiny guys, ironically making it easier to target.
* Hub: Added a new checkbox to "Unit Filter", "Override Target Scale", which will maintain the filtered scale of Targeted Mobs.
* Core: Added: unit.isMini = boolean.  This will eventually replace "unit.platetype" and "unit.isTrivial". Not anytime soon, though.
* Quatre & Neon: Increased the text size by 1pt to reduce specific scaling concerns.


6.13.Beta2
---------------------------
* Removed the "Unit Spotlight" system, for the moment.  Don't worry- It will come back to the beta release!  I just need to get a solid release done to fix some issues.  Thanks for your patience :-)
* Replaced "Accidental Presidency" with "Roboto Condensed" for Quatre.
* Hub: "Use Blizzard font" should work properly again.


6.13.Beta1
---------------------------
* Moved "Health Bar" to the top of the Hub page
* Merged "Style" into "Headline Mode"
* Raised "Buffs & Debuffs" upward in the Hub page
* "Health Bar" gets a couple new choices; Namely, separate coloring options for Friendly vs Enemy plates.
* Pruned the Color Mode lists
* Removed the "Warning Border Glow Mode" selector; Don't worry!  There's still a Warning Glow, but it's turned on/off within the "Threat" category.
* Added a new category of features, "Unit Spotlight", which allows you to highlight specific mobs with color, opacity, and scale.  You could use it to highlight important mobs in Raids.
* Added an option to "Spell Casting", "Enable Friendly Castbars"
* New Font: Started replacing "Accidental Presidency" with "Roboto Condensed" across the bundled themes.  Looks similar, but contains more complete character sets; Important for non-English languages.



6.12.6
---------------------------
- Widgets: Combo Point: Anticipation "fix"
- Hub: Cached class colors in instances

6.12.5
---------------------------
- Widgets: Unit Cache: Stores non-local units with a " (*)" suffix.
- Hub: Class colors on cached units shoud work properly

6.12.4
---------------------------
- Core: New unit data: unit.rawName, strips the (*) from nameplate names.
- Core: The carrier frame is now globally labeled with a unique frame name.
- Hub: Healer Tracking: Now uses unit.rawName rather than unit.name
- Widgets: Aura Tracker: Now uses unit.rawName to associate on-screen PvP names
- Widgets: Unit Cache: Will now properly filter non-realm units (ex. coalesced or battlegroup)

6.12.2/3
---------------------------
- Revert fix for viewport mod interaction.  Needs a bit more external testing, apparently.

6.12.1
---------------------------
- TOC Bump
- Core: OnShowCastbar will now check for unit health before proceeding, hopefully avoiding errors when the Castbar's OnShow handler is called early.
- * Fix for Viewport Mods (specifically, Sunn), particularly, when the actual vertical viewport is decreased.

6.12.0
---------------------------
- Core: Compatibility Mode: Restored alpha-override behavior
- Hub: Warning Glow: Fixed InCombatLockdown() reference

6.12.Beta4
---------------------------
- I may have fixed some bugs.  Or maybe that was a dream.  Hard to recall whilst under Benadryl's spell.
- Ok, I definitely changed some things, and I'm not getting errors in game.  That's a good sign.
- Made some changes to (hopefully) fix 1) debuff tracking oddities, and 2) lua error using health text.

6.12.Beta3
---------------------------
- Added a workaround/fix to the broken Blizzard function, InterfaceOptionsFrame_OpenToCategory.  Slash command shortcuts for /hub and /tidyplates will now work properly.
- Added a Compatibility Mode checkbox to the interface panel.  This will fall back to older anchoring methods.
- Core: The OnShow handler will skip all data gather on that first cycle; The Alpha data is (still) unreliable, causing GUID association issues.

6.12.Beta2
---------------------------
- Updated 6.12 with the changes made to the castbar during 6.11.  (Since 6.12 inherits the 6.10 core, it didn't see the progression)
- Aura Widget: Fixed issue where aura is briefly shown, then hidden.  Should be fixed.
- Added a copy of the reference to healthbar and castbar. for Threat Plates Compatibility.

6.12.Beta1
---------------------------
- Reintegration of 6.10 Core, which includes reorganization and rebuilding of the main engine.

6.11.3
---------------------------
- Check unit.health on spell cast functions, to catch premature update calls.

6.11.2
---------------------------
- In reverting, I missed updating the TOC version for TidyPlatesHub.  Updated for 50300

6.11.1
---------------------------
- Core: Fixed a cast bar bug, where the sub-object references were not being updated.  Addresses certain "attempt to perform arithmetic on field 'health' (a nil value)" errors

6.11
---------------------------
- Basically, I've given up trying to quickly patch up 6.10.  I've reverted to 6.9.9, and made the changes necessary for it to work with WoW 5.3.  If you want the Performance Mode stuff, grab the old version, or keep an eye out for it to be Re-Beta'd as 6.12.

These are the changes that I've migrated:
- Spell Casting Update, for WoW 5.3
- Core: Set initial fonts during Init/Hooking.  Removes the possibility of :SetFont() errors.
- Combo Points: "Antic ipation" fix for non-english regions


6.10.4
---------------------------
- Core: Fixed a major typo. Should fix SetStyle/Headline Mode and ClassIcon LUA errors at the very least.  Might explain some of the other elusive bugs.

6.10.3
---------------------------
* Performance Mode:
By default this is NOT enabled, reverting to the older, slower, reliable method.
Using Performance Mode may break HHTD and other nameplate addons.
You may also experience 'hung' nameplates.  Please report these, and try to be as
specific as possible in describing the condition of the game when it occured.

- Core: (Since 6.10.2) Performance Mode:  This enables the performance improvements introduced in 6.10.
- Core: Reintegrated original Alpha locking
- Core: More reorganization, pruning of old, dead methods
- Core: Set initial fonts during Init/Hooking.  Removes the possibility of :SetFont() errors.  Not sure why I didn't do this years ago.
- Panel: Removal of latent "Show Minimap Icon" button code

6.10.2
---------------------------
- Panel: New Option: Performance Mode.  This enables the performance improvements introduced in 6.10.  By default this is NOT enabled.
- Using "Performance Mode" may cause problems with other nameplate addons.

6.10.1
---------------------------
- Panel: Reverted the dropdown menu init changes from beta4.  Seems to be messing up the panel.
- Core: Blizz Spell Shadow: More thoroughly hidden
- Hub: Threat/Warning Glow fix
- Core: Spelltext; "Font Not Set" error - Hopefully fixed


6.10
---------------------------
Beta 6:
- Reorganized event handling structure to rigorously check the visibility of the parent nameplate to prevent showing previously hidden nameplates or hiding previously shown nameplates

Beta5
- Combo Points: "Anticipation" fix for non-english regions?  need to test
- Core: Back to hooking the base plate.
- Healertrack: Strsplit fix  (thought I fixed that several months ago.. hmmm...)

Beta4
- Refactored a bit of the Core
- Panel: Dropdown menu will now init when the interface panel is shown, rather than on load
- other stuff.  too tired to remember.



- Reparent Tidy Plates Frames to UIParent, Reanchor back to base nameplate = Performance boost.  Sweet.

6.9.9
---------------------------
- Hub: Added "Selective Optional Text"
- Deprecated: 'customart' Texture and theme functions.  Please use the Widget system to create additional textures. (Removing unused textures provides a small performance improvement)
- Core: Reorganized the nameplate strata, removing an unnecessary anchor frame
- Core: Reorganized and relabeled some internal functions, adding a few extra comments
- Core & Aura Widget: Made some changes to reduce extraneous calls.
- Aura Widget: "Show Dispellable Auras" should work, now.  Ran some BGs, and things seemed to work.
- Hub: Added a warning, notifying the user when they're not using a Hub-compatible theme.
- Hub: Added a divider line between Headings
- Aura Widget: The old method of applying the aura widget has been re-added; The new method (described somewhere below) is still preferred!
- Hub: Added "Enable External Widgets" checkbox, to control the running of the Global widget functions described in 6.9.6  *

6.9.8
---------------------------
- Hub: "By Threat" Color Modes will pass through enemy class colors, when available, and then use Reaction colors.  (NPC-Pets will continue to use the "By Threat" colors)
- Hub: "By Threat" Warning Glow Mode now incorporates "By Enemy Healer", so it can be used for Pvp without changing config.
* These changes may evolve into more situationally reactive configs... we'll see!
- Widgets: HealerTrack: Should more reliably and quickly detect the spec of the enemy units.

6.9.7
---------------------------
- Fixed Tank Aura Watcher issue

6.9.6
---------------------------
- Performance improvement on Hidden mobs
- Aura Widget: Better association of Player characters, especially for friendly Buffs
- More extensive 'nil' strsplit error checking
- Hub: Added "Reaction" and "Spell Casting" color options
- Hub: Added reaction colors to 'By Threat' Functions
- Hub: The Widget creation and update functions will look for, and call: TidyPlatesGlobal_OnInitialize, TidyPlatesGlobal_OnContextUpdate, TidyPlatesGlobal_OnUpdate.
	TidyPlatesGlobal_OnInitialize() is called when a nameplate is created or re-shown
	TidyPlatesGlobal_OnContextUpdate() is called when a unit is targeted or moused-over.  (Any time the unitid or GUID changes)
	TidyPlatesGlobal_OnUpdate() is called when other data about the unit changes, or is requested by an external controller.
	* These functions can be used to create and maintain non-theme widgets.  Eventually, they may be implemented directly into the Core
	* Widget authors should hook the existing function, if it's present (No Returns):
	  Ex.	local OriginalFunction = TidyPlatesGlobal_OnInitialize
		TidyPlatesGlobal_OnInitialize = function (extended)
			if not extended.widgets.mywidget then extended.widgets.mywidget = CreateFrame("Frame", nil, extended) end
			if OriginalFunction then OriginalFunction(extended) end
		end

6.9.5
---------------------------
- Core: Reversion of scale and alpha handling to 6.9.Beta3 (Removal of transition effects)

6.9.4
---------------------------
- I need coffee.  Now.

6.9.3
---------------------------
- Tapped Mobs now apparently have the color: 0.53, 053, 0.53.... so I've updated the core to properly ID tapped mobs
- Mousing over a nameplate will temporarily bring that frame to FrameLevel 1, which should help targeting in crowds.
- A few other little things that I can't recall now.  I need sleep!

6.9.2
---------------------------
- More bug fixing, which seems to be a blessing in disguise, since it's yeilding some removal of redundancies, and (hopefully) incremental improvement in performance.
- Hub: Added a new Filter Item, "Filter Mini-Mobs".  This'll allow you to scale and fade those pesky mobs with mini-nameplates.  70% works well for me.

6.9.1
---------------------------
- Fixed: Raid Icon Bug?  (Changed some stuff around to even further reduce the chance of an out-of-order plate styling.)
- Increased default rate of Alpha/Scale Transitions.  Can be changed via, TidyPlates:EnableFadeIn(FadeRate)
- Added some additional code to check for nil values in the Default Filter Function.
- Added Players to the "Filter" Hub Mode

Note: Threat Plates v6.008 is not completely compatible.  Please use Tidy Plates v6.8.3

6.9
---------------------------
- Core: Added Scale Transitions.  Disable via, TidyPlates:DisableFadeIn() or /tidyplates panel
- Core: Added full Alpha Transitions. Disable via, TidyPlates:DisableFadeIn() or /tidyplates panel
- Core: Added a Tidy Plates Panel checkbox to control the Scale/Alpha fade feature
- Core: New unit variable: unit.platetype = 1 or 2, where 1 = normal Blizzard nameplate, and 2 = mini nameplates (seen on 'drone' mobs, for example)
- Core: Added code to correct value '0' scale from delegate functions
- Core: The SetHealthbarColor delegate will now control the statusbar-backdrop color in addition to the healthbar color:
	- 1. The SetHealthbarColor delegate gradient has been deprecated (It accepted two rgb sets - r1,g1,b1,r2,g2,b2 - which corresponded to the endpoints of a gradient)
	- 2. SetHeatlhbarColor now accepts two rgba sets - r1, g1, b1, a1, r2, g2, b2, a2 - which define the healthbar color+alpha and the backdrop color+alpha, respectively.
- Core: Deprecated "SetStatusbarWidthMatching" flag
- Core: Deprecated "style.frame" - Blizz made some changes, rendering this option obsolete.
- Aura Widget: Added a check for destination name in the Aura Widget  (Fixes "AuraWidget.lua:658" error)
- Aura Widget: Fixed Default Prefilter Errors
- Aura Widget: 'TidyPlatesWidgets.SetAuraPrefilter(function) replaces 'TidyPlatesWidgets.SetDebuffPrefilter'
- Aura Widget: 'TidyPlatesWidgets.SetAuraFilter(function)' replaces the previous method of assigning the Filter into each Widget instance via 'wiget.Filter'
- Aura Widget: Filter function now accepts these return values:  [show, priority, r, g, b], where 'show' indicates that the aura should be displayed, 'priority' indicates
	how important the debuff is to display, and 'r',  'g', and 'b' indicate the vertex color of the border highlight.  This can be used to colorize auras for different
	schools or types.
- Aura Widget: Square/Small Auras will now terminate/expire properly, and call for a delegate update.
- Hub/Aura Widget: Added "Track Dispellable Debuffs on Friendly Units", which will allow you to track and highlight debuffs on friendly units that need to be dispelled.
	"Magic", "Poison", "Curse", or "Disease".  Have I tested it?  Hahahaha..he.. um, no.
- Hub/Aura Widget: Removed prefix, "No"; Useless in the current evolution of the Hub Filter system.
- Hub/Aura Widget: "CC" prefix will highlight the aura with a Yellow border
- Hub: Added Health/Optional Text Mode: By Arena ID. I have no clue if it works.
- Hub: Aura prefilter should work properly, instead of letting everything through
- Hub: Multi-Mode Functions will cross-check the table index, preventing out-of-range values from throwing errors.
- Hub: Removed/Replaced distinct "By Low Threat", "By High Threat", and similar Modes from Scale, Alpha, Name, and Color Spotlight functions.  THESE HAVE BEEN REPLACED by
	a single setting under the "Threat" Category, allowing you to control the Threat Mode for all Threat functions.
- Raid Tank/Target Watcher: Fixed Tanks.lua nil 'for' limit
- Raid Tank/Target Watcher: Fixed unitid/raidid issue.
- Raid Tank/Target Watcher: Added combat-log detection of melee attacks against non-tanks. (Untested)
- GroupCache: Fixed an issue where class color was not available for the last friendly raid member to join a team.  (Note: The GROUP_ROSTER_UPDATE event is sometimes called
	before all the player data is available, leaving holes in the data table)

6.8.3
---------------------------
- Rogue Anticipation stacks are now displayed on the combo point widget
- AuraWidget.lua: Added some (currently inactive) code within aurawidget.lua for, "Personal Aura Tracker".  Feel free to mess with it.  Search for, "Personal Aura Tracker"
- AuraWidget.lua: Added some (currently inactive) code for highlighting abilities that can be activated.  Again, if you want to mess with it on your own, feel free.
- Made some changes to the Off-Tank Color feature; Enabling it will force detection of Off-Tanks, even if you are not a tank.  NOTE: There are still limitations inherent in the WoW-API which limits the ability of this feature to track all on-screen targets and target-ofs.

6.8.2
---------------------------
- TAPPED mobs now are a unit.reaction member
- Added "Filtered Unit Scale" to the Hub:Filter category
- Removed test code, which was accidentally causing Mages to get Priest coloring and Icon
- Support for Phanx's "Class Colors" addon, http://www.wowinterface.com/downloads/info12513-ClassColors.html


6.8.1
---------------------------
- "Tapped" units (colored light purple by the Blizz nameplate system) will now register as "Hostile NPCs" in Tidy Plates.  This is partially inaccurate, since the tapped mobs could be neutral (like target dummies), but there is no way to discriminate this from the plate.
- Fixed several tainted global variables
- Added custom Monk and Priest color lookups for class recognition.  (RAID_CLASS_COLORS is not completely accurate)
- Changed the way the class colors are stored, hopefully fixing some other class ID problems
- Disable Tanks module by default.  Add option button to hub.
- Hopefully Fixed Off-Tank coloring issue.

6.8
---------------------------
- Updated to 5.1 ToC and new nameplate object configuration:

Nameplate Stack WoW 5.1:

Nameplate_Frame
	NameplateChild_Frame1_Statusbars
		Statusbars_Child_Frame1_Healthbar				(Statusbar)
		Statusbars_Child_Frame2_Castbar					(Statusbar)
		Statusbars_Region_Texture1_Threat				(Texture)
		Statusbars_Region_Texture2_HealthBarBorder		(Texture)
		...
		...
	NameplateChild_Frame1_UnitName
		UnitName_Region_Fontstring1_Name				(Fontstring)


6.7.9
---------------------------
- Corrected another error in the spell cast watcher; "StopCastAnimationOnNameplate" is now properly referenced.  This only affects arena matches.  I don't do arenas, so this was never properly tested.  Let me know if more errors pop up.

6.7.8
---------------------------
- Corrected a typo in the spell cast watcher; "StartCastAnimation" is now properly, "StartCastAnimationOnNameplate".  Arena fans rejoice!

6.7.7
---------------------------
- Fixed: Monk Tank mode (Stance of the Sturdy Ox stance added to the shapeshift list)
- Corrected various threat values coming into the threat line widget
- Core: extended plate verification process
- Removed many unneeded local variables
- Combed files for any "_" that could be global

6.7.6
---------------------------
- Added code to verify healthmax values.
- Sets framelevel to 0.  Targetted plates are raised to 1, which still does obscure the chatbox and minimap.  This also occurs with the standard Blizz nameplates, and cannot be corrected without raising the strata or level of those other frames.
- Added a rudimentary localization framework.  To use: Create an addon named, "TidyPlatesHubXX" where the XX is the last two letters of the localization code.  Ex. "TidyPlatesHubDE".  Within the code for that addon, create a table called, 'TidyPlatesHubLocalization', and add the translations.  For example:
TidyPlatesHubLocalization["Style"] = "Translation of STYLE".   See TidyPlatesHub\Lists.lua for an example.  Future versions will add a "Dump" mode for outputting all the text that needs translating.
- Changed the background, anchoring, and font sizes in the Hub, for readability.
- Changed the core template, and added a 'default' style, which looks like the Blizzard nameplates.  (will be useful in a future version)


6.7.5
---------------------------
- Removed framestrata code from, MinimapCluster, PlayerFrame, and TargetFrame
- Threat Line Widget:  Shootin' from the hip, again.

6.7.4
---------------------------
- Fixed giant threat bar issue (Corrected group size ranges in GetRelativeThreat() utility function)
- Raised MinimapCluster, PlayerFrame, and TargetFrame to "LOW" framestrata to prevent nameplates from obscuring those UI elements.
- Currently, there is no way to fix the brief 'flash' of the Blizzard nameplate art before it becomes active; It's a bug for the Blizz folks to solve.

6.7.3
---------------------------
- Removed debug code from GroupCache.lua (Chat log spam)


6.7.2
---------------------------
- Aura Widget: Fixed error, where certain auras filtered by spellid were not being displayed.
- Group Cache: Fixed updates for friendly group class colors (hopefully!)
- Group & Unit Cache: Will not try to search the global unit cache for class information while you are in a dungeon (could slow things down, and it isn't needed)
- Core: Reverted to earlier method of discriminating nameplates
- Threat Line Widget: Added some code to prevent it from accidentally becoming REALLY long.

6.7.1
---------------------------
- Fixed Range Widget bug

6.7
---------------------------
Beta9:
	- Upgraded the TOC file version number to 50001
	- Added: TidyPlates:EnableFadeIn() and TidyPlates:DisableFadeIn() functions, to control the nameplate fade-in mechanic.  Default is Enabled.

Beta8:
	- Removed debug console output

Beta7: r506
	- Added "Stance of the Sturdy Ox" to the Tank Aura list.  This should fix some "By Threat" oddities.
	- Added Monk specs to the HealerTrack widget.
	- Added PLAYER_ENTERING_WORLD to Tank watcher events (to fix the line 39: nil errors)
	- (hopefully) fixed pauses while using the Arena mode with the Spell Cast Warning system

	- Jinx:
		- Right now, it looks like the debuff is applied by the server, not Your Character.  This is important because Tidy Plates ignores debuffs without a source.  In the beta, this debuff is properly displayed.

Beta6:
	- Capacitor Totem

Beta5:
	- Fixed: Bug where current theme selection would be lost when logging-in.

Beta4:
	- Added BUFFS to the aura widget.
	- Added texture coordinate function to tidyplates statusbar widget.  Usage/Example: healthbar.left = 0, healthbar.right = 1, healthbar.bottom = 0, healthbar.top = 1

Beta3:
	- The most visible change in Beta3 is the rearrangement of the Hub panel.  The debuff widget has been moved to its own category.
	- I've been working on a new way to control the health bar style.  I'm not sure when/if this code will become active.  I will probably post it as an alpha version after 6.7 is released.


Beta2:
What have I done so far?
	- Enhanced both the debuff widget and the spell cast warning module with support for Arena unitid event capture (via the standard event system, rather than the combat log).
	- Updated to MoP standards (which will work with 4.3, too)
		- Functions which have been renamed for MoP have been replaced by an internal function (provided by Tidy Plates) which is aware of the current client version, and will choose the appropriate function.
		- Tidy Plates now uses an internal button template, which replaces the UIPanelButtonTemplate2, which was removed in MoP



Testing
	- Need to test the Arena-Mode enhancements for the Debuff widget and Cast Warning system



Beta1 (r485)
	- Will do this later, too tired


------------------------------------------------------------------------------------------
Tidy Plates 6.6

6.6.2 (r465)
	- Fixed UnitCache Toolip 'nil' error

6.6.1 (r464)
	- Modified Unit Description Caching to work properly with addons that change the color of the tooltip text. (Like elvUI)
	- The Hub checks to see if the user has enabled any of the Aggro or 'By Threat' features, and automatically enables Blizz's Threat Warning feature. (which is required)

6.6.0
	- Under the "Style" category, all references to "Text-Only Plates" or "TextPlates" have been changed to "Headline Mode".  This change is intended to distinguish the style modifier from other references to "Text".  I'm sure some of you will hate this (can you come up with something better?), but I'm hoping that less cranky folks find the new grammar to be more intuitive.
	- To support the "Headline Mode" name change, I've added a new category.  Can you guess?  It's, "Headline".
	- I've grouped the "Color" and "Text" categories into "Color & Text", and moved them to the second-category position.  Why??  1: "Color & Text" controls the appearance of the default 'Health Bar' style.  2: Underneath, "Headline" controls the appearance of the 'No Bar' style.  Thus: This arrangement puts these options close to where the user selects the modes, in the "Style" category.
	- Square Debuff Icon Option: Added a new Debuff Widget option, "Debuff Style", which allows the user to select between the traditional "Wide" debuff format, or a more squareish "Compact" style.  The column count is increased to 5 for the "Compact" style.
	- Bookmark System: Added a "Bookmark" system to the Hub panels, which allows a user to jump directly to any of the categories
	- On certain themes, the position of your debuffs will be adjusted to allow the combo point widget to comfortably fit (on Rogues and Druids, only).  When the combo widget is disabled, the icons will "snug" themselves closer to the plate.
	- Using the '/hub' command will bring you to the Hub Configuration panel for your current theme
	- Added click sounds to the 'Copy' and 'Paste' buttons
	- Bug fixes and Memory optimization
	- Added a Prefilter option for the debuff widget cache
		* The hub enables the prefilter, when you're using the 'By Prefix" mode
		* Debuffs NOT on your list are not cached
		* This should save a ton of memory if you're using 'By Prefix'
	- Made some changes to the Unit Data Cache system to reduce memory use, and avoid certain 'lag' events...
		* Pet/Companion NPC titles are no longer cached
		* Cached unit guild and npc titles are now stored within the TidyPlatesWidgetData variable, keeping this data out of the base TidyPlates saved variables
		* Hub/Reset button will now clear the cached unit descriptions/titles and guilds
		* Unit descriptions (player guild name, or NPC role/title) will not be displayed while in an instance.  This is to avoid the CPU overhead that occurs when searching the database, which could be THOUSANDS of entries.  This is a direct cause for massive FPS drop, in some cases.
		* A side-effect of these changes is the clearing of user's stored guild names and NPC titles.  This is required to get the desired performance benefits.
	- Matched widget duration timer to default blizz interface standard (using 'floor' rather than 'ceil')
	- Fixed SpellId variable name in widgets\tank.lua
	- Spell Cast Monitor: If cast time is not greater than 0, make it a minimum of 1.5s
	- Added NameColorByEnemyClass
	- Minimize Hub now scale to 85%
	- Rearranged Name Color: By Friendly/Enemy class
	- Improved HealerTrack.lua, with help from Curseforge user, dakunesu.  Improves detection of healers in battlegrounds! Rockin!
	- Added a "Minimize" button to the /hub UI panel.  Clicking this will detach the Hub panel from the Interface Options window, and make it smaller.  Good for configuring stuff while playing.
	- The Copy & Paste buttons for the Hub panels now work with a unified Clipboard, so you can Copy & Paste between Tank and DPS panels.  Holding down "Shift" while clicking Copy or Paste will use the original Tank/DPS-specific caches.
	- New Hub Option: "Bring Casting Units to Spotlight Scale"
	- Unit Cache should filter out reputation names.  This fixes an issue occuring when "Colorblind" mode is active, causing Reputation to be displayed instead of an NPC's Title.
	- "Filter > Filter Inactive": When a unit is marked with a target/raid-icon, it's now assumed to be Active.
	- And more (ie. stuff I've forgotten about)

------------------------------------------------------------------------------------------
Tidy Plates 6.5

(r433)
	* The "By Class" function of Health Bar Color has been changed to, "By Enemy Class".
	* Added a Health Bar Color function called, "By Friendly Class".
	* Added some code to make built-in themes use the default Blizzard nameplate font when a non-latin language locale is detected
	* Updated combo widget artwork: higher resolution, etc.
	* Fixed file path to Neon's Target selection artwork

(r421)
	* Fixed the text-plate target and highlight art (I messed it up while cleaning duplicates)
	* Changed fonts... Neon, Graphite, Grey, and Quatre now use the same font, to keep the package size smaller.

(r420)
	* Added Text Modes: Level & Level and Health
	* Changed some panel text, colors, explanations
	* Added some Text-Only style functions
	* Cleaned theme folders (removed old art and consolidated duplicates)

(r409-411)
	* Changed some text descriptions to better explain the feature/option
	* Hub: Moved the two Text-Plate config options from 'Color' and 'Text', to 'Style'
	* Changed 'Frame' category to 'Advanced'
	* Added an option under 'Advanced'; "Enable Unit-Data Caching".  (Disabling this will stop non-party/pvp class-coloring)
	* Added a filter to the Unit-Data cache, to skip characters from other other realms
	* Unit-Data caching is bypassed while in an instance (Both PvP and PvE)
	* The caching system will peek at /who requests, and store the info on the Unit-Data table (Unless it's disabled)
	* Changed Neon's font to Accidental Presidency (Why?  Because I like it!)

(r406)
	* When "Show Party Aggro" (under Threat) is enabled, the "By Threat" spotlight systems for Opacity and Scale will now highlight your unfortunate party members.
	* The Health and Text colors mode, "By Threat" has been changed to, "By Threat (Auto-Detect).  The previous implementation has been renamed to "By Threat (Legacy)"
		* When using a tank stance, aura, or form, you'll see the "Safe" color when you have aggro, and the "Warning" color when you don't.  When NOT in a tank mode, you'll see the "Warning" color when you have aggro.
	* Changed default Spotlight Opacity to 100%

(r403)
	* Reversion of Default Scale to 100%/120%
	* By Class color modes will now apply coloring to both Friendly and Enemy players  (Removed option, "Show Class Color for Party/Raid Members")
	* By Class color mode will also source non-party/pvp colors from a cache.  Mouseovering a unit will add it to the cache.
	* By Threat color modes will automatically swap colors to match the tank status
	* Changed names of Color options to: Warning, Transition, and Safe

(r400)
	+ Fixed mouseover bug (Added a seed value for OpacityFullMouseover)

(r395)
	+ Various Bug fixes, new features, etc.
	+ Fixed Party member aggro alert

(r388)
	+ Introduction of Universal Hub Core, which centralizes the creation of the Hub UI Panels
	+ Modification of Hub Functions to support these changes (Many)
	+ "Damage" and "Tank" panels will look identical, with identical defaults.  Users can still change their settings, independently.
	+ These modifications will allow faster implementation of certain features, and will lead to a more extensive and useable configuration system
	+ Reset of Hub Settings (necessary, due to the relocation of saved variables)
	+ Added "By Health" and "By Low Health" modes to Scale, Colors, and Opacity.
	+ Added Low/High Health Threshold sliders, and color selection for Low/Mid/High Health
	+ Reorganized the Hub panel (in particular, the Opacity filter section is now under its own heading)

(r373)
	+ Improved theme format error handling
	~ Reversed changes to Graphite
	~ Reversed Neon font changes (If you liked the new font, I'll post instructions for modding)
	+ Added: Opacity Filter, "By NPC"
	+ Added: Health Bar Coloring Mode: "By Raid Icon" Colors
	+ Added: Health Bar Coloring Mode: "By Level Color"
	+ Added: Name Color Mode: "By Level Color"
	+ Added: Opacity, Scale, and Warning Glow Modes: "By Enemy Healer"
		+ Supported by the addition of a Healer Detection system
	+ Added: "By Threat (Auto-Detect") modes to Opacity, Scale, and Warning Glows
		+ Supported by the addition of some code to detect the current tanking state based on auras/stances/forms
		! Not quite finished

-----------------
6.4...

(r363)
- Fixed: Re-Added unit.spellIsShielded to cast color delegate
- Added: MaximumDisplayableDebuffs variable under Debuff Widget.  This will allow user-configurable debuff quantities.

(r358)
- Added: Tip text next to Hub Debuff widget config
- Fixed: Friendly Group unit class coloring
- Re-removed: Minimap button.  The code is still there, but hidden.  If you liked the button, use this command:   /run TidyPlatesOptions._EnableMiniButton = true; ReloadUI()

(r355)
- Fixed: List-to-lookup table conversion for Unit Filter, By Name
- Fixed: Hub/Tank slider ranges (They were not actually broken, just different from the Damage Hub)

(r350)
- Fixed: Incorrect Paths in TidyPlatesWidgets (causing several widgets to not work)
- Fixed: Hub Tank Panel, SplitToTable error

(r348)
- More messing around with debuff widget
- Cleaned up some of Neon's artwork
- Changed default Neon font to Headache
- Debuff & Buff display for Friendly units is internally complete, but is disabled until the Hub can be updated
- Debuff widget now provides .unit table from the underlying nameplate, to allow better filtering.

(r344)
- No clue

(r340)
- Fix for Debuff Widget empty table/sort error
- Corrected a mistyped line for indexing Aura_Dispell type

(r338)
- Debuff Priority works for "Show Specific" and "Show My Specific" modes, in addition to "By Prefix"
- Class Icon Widget: Returned to using internal artwork
- All textures are now Non-blocking (the game won't wait for textures to load into memory before it draws the scene), preventing texture changes from affecting frame rate
- The debuff widget (should now be called Aura Widget) will track buffs for friendly players

(r308)
- Debuff widget now uses single dimension tables to store cached data, to improve memory management
- Moved Widgets to their own addon/folder (For memory usage tracking)
- Statusbar gradients are now supported via additional return values in theme.SetHealthbarColor()...
	* return r1, g1, b1, [r2, g2, b2]
- The Debuff widget now supports 'priority' through the existing .filter function... example:
	* return showThisAura, auraPriority
- The Hub Panels will check the order of the debuffs in its list to determine priority.
- Class Widget no longer uses internal class artwork; Instead, the class icon is pulled from the Blizz UI library.
- If theme.SetCastbarColor returns nil, the cast animation will be skipped
	* This can be used to filter spell casting data
	* SetCastbarColor is passed the 'unit info' table, which contains: unit.isCasting, unit.spellName, unit.spellID, unit.spellInterruptible

6.3
-----------------

6.3.8 (r307)
* Removed: Toggle for Minimap button.  The minimap buttons does't work completely as-intended, so I've removing it for general release, sooner rather than later.

6.3.7 (r304)
* Fixed: LDB Icon Registration
* Modified: Minimap Icon Position
	- Note: The icon does not save a user-placed position, yet.

6.3.6 (r301)
* Fixed: UnitCache Error
* Fixed: Graphite Loading Error
* Added: Spell Cast Monitor will not look for casts from current target
* Added: Hub Option, Scale: Ignore Inactive/Undamaged Mobs
* Added: Hub Option, Alpha: Filter Inactive/Undamaged Mobs
* Added: Minimap/LDB Icon
* Fixed: Debuff Widget, Nil Raid Icon Lookup Index

6.3.5 (r295)
- Self-Test for DebuffWidget.lua added, in order to inform users of possible issues.  (I hope to address auto-updater bug)
- Cleaned up some code to reduce "double calls" to delegate and update functions

6.3.4 (r293)
- More Debuff Widget fixes
- Improved Debuff Widget memory usage

6.3.3 (r292)
- Debuff widget should gracefully handle certain aura events.  (GetSpellInfo errors)


6.3.2 (r291)
- Tidy Plates Hub: Debuff Widget: Spell IDs can now be used instead of spell names in the filter system.
- Fixed: Crazy debuffs during Firelands dailies.
- Aurainstance table (for debuff widget) and functions have been converted to a smarter format
- When auras are updated on your current target, the caching function will clear the cache before it repopulates the list.
- Increased the scope of name/elite status updates.  Hopefully this will accommodate the Firelands Smoldering/Blazing Elemental Bug.

6.3.1 (r289)
- Fixed debuff update stalling
- Added nil value error protection to debuff prefix sorter

6.3.0 (r284) 55,754
	* Updated functions for 4.2
	* Increased width of sliders in Hub
	* Opacity functions now use a transfer function to correct the opacity (currently, .5 does not translate to 50% opaque; it's more like 65%)
	* Channeled spells now move the cast bar in reverse.
	* Friendly/Enemy "V-key" Automation; In Combat, Out of Combat, Always
	* Debuff widget now Caches texture of debuffs (to fix sunfire phenomenon, and similar)

6.2 (r269)
-----------------
* The Hub gets a new category: Style
	- This new category has two menus for Friendly and Enemy nameplates
	- Users can select between two styles (Health Bars vs Text Only), and several different visibility conditions.
	- If you use the Text Only bars, you might want to check out the Name Text Color options, to spice up that text!
* Spell Cast Monitor name search will now strip the "-" from the combat log name, which should fix PvP cast association issues.
* Debuff Widget will now strip the "-" from combat log events, which should fix pvp association issues
* fixed a 'nil' error during pet/tank association
* "Avoid Overlap" has been updated for the new CVar types
* Fixed a bug where the debuff widget was not getting the correct data from the combat log

6.1
-------------

6.1.13
	- tweaked name color function

6.1.12
	- Fixed Hub/Tank NameTextColor errors
	- Updated description of "Vertical Position of Frame" to "Vertical Position of Artwork"

6.1.11
	NEW! Keyword filtering for the Debuff Widget
	- See Demo on Youtube: http://www.youtube.com/watch?v=2KjGFd0TgvM
	- By Prefix.. Mode for Debuff Widget
		- ALL, MY, NO, OTHER, CC
		- Using CC will eventually highlight the debuff on the widget, but for now it just acts as "ALL"

	- Fixed UnitChannelInfo interruptable spell argument bug
	- Found a bug; The Editboxes contained in my ScrollFrames seem to invisibly extend past the bottom of the scrollframe, which can block underlying UI controls.  I've dropped the editboxes to a lower frame level, which is a hack method of preventing problems with it interferring with controls anchored to the bottom of the scrollframe.  Will attempt to figure out a better solution.
	- Name text coloring modes
	- By Raid Icon modes for Opacity and Scale

6.1.8 (r227)
	- PTR bug fixes (Neon Threat Glow was turning green)
	- Debuff widget will clear aurainstance tables when combat ends (regen returns)
	- Added Health Text option: Approximate Health (will show 2 decimal places for thousands (k) and millions (M), with suffix)
	- Added Text option, "Use Default Blizzard Font"; This will use the font defined by the global variable, 'NAMEPLATE_FONT'.  This should improve the situation for non-latin charcter sets (this is for you, Chinese, Russians, Taiwanese, and Koreans.. xoxo)

6.1.7
	- Changed from thousand/million suffix for health text to using a thousands seperator
	- Restored PTR support (last time I checked)
	- Moved Quatre Raid Icon to similar position as Neon (to left side of health bar)

6.1.6
	- Added Events for UNIT_SPELLCAST_NOT_INTERRUPTIBLE, UNIT_SPELLCAST_INTERRUPTIBLE, (This hopefully improves the situation for spells that are uninterruptible being misrepresented)
	- Added Threat Wheel to Hub
	- Reverted to original health % mode (does not show % when full health)
	- WoW 4.1 Compatibility (works on 4.0.x and 4.1)

r206
	- The update function for debuff icons are now exposed via, widget.Poll
	- Added Events for UNIT_SPELLCAST_NOT_INTERRUPTIBLE, UNIT_SPELLCAST_INTERRUPTIBLE
	- Added Threat Wheel to Hub/function set
	- Reverted to original health % mode; ie. does not show % when full health.  if you like it the other way, edit TidyPlatesHub\functions.lua.  I like it this way, and dammit, it's my software ;-)
	- WoW 4.1 Compatibility (should work on 4.0.x and 4.1, concurrently.  I have not tested on the PTR, though)



r199	- Raid Tank Coloring in Tank mode.  Automatically used when in "By Threat" Modes.
		- Theme list is now Alphabetized
		- Better handling when previous theme selection does not exist
		- Debuffs of the same spell-id are now handled more securely
		- Reset button in main panel will now reset variables on 'click', turn enemy plates ON and friendlies, OFF
			- 'shift-clicking' will clear and restore the variables, and reload the ui
		- Reset buttons in hub panels also now have a 'click' behavior to reset the variables without reloading the UI
			- 'shift-clicking' will still clear the tables and reload the ui
		- First-run config, turns off friendly nameplates by default
		- Added a link to the Blizzard "Names" panel via the Tidy Plates theme chooser panel

r186	- Default Hub Values changed to more closely resemble 6.0.8 defaults  (Blue, Orange Scheme, Threat Warning Glow/Triangles turned On)
			- A variable reset may be required to revert to the defaults
		- First-run config, "friendly unit bug" fix

6.0
-------------
r104-108
TidyPlatesWidgets:GetThreatCondition now sources its group data from the group info table
unit.threatValue...
	0 - player has less than 100% raw threat (default UI shows no indicator)
	1 - player has 100% or higher raw threat but isn't mobUnit's primary target (default UI shows yellow indicator)
	2 - player is mobUnit's primary target, and another unit has 100% or higher raw threat (default UI shows orange indicator)
	3 - player is mobUnit's primary target, and no other unit has 100% or higher raw threat (default UI shows red indicator)

r101-103:
- Created a group information watcher.
TidyPlatesUtility.GroupMembers = {} a table
Subtables/Values:
.Names = {} Returns a name if you pass it a unitid
.Tanks = {} If you pass it a name, it will tell you if the unit is a tank
.Class = {} Returns a class if you pass it a name
.Role = {} Returns a role if you pass it a name
.UnitId = {} Returns a unitid if you pass it a name
.Type = "solo" Returns the group type; "solo", "party", "raid"
.Size = 1 Returns the size of the group
TidyPlatesUtility:EnableGroupWatcher() a function
TidyPlatesUtilityisableGroupWatcher() another function
- Spell Cast Monitor will now catch channeled spell events (Note: Channeled spells do not animate in reverse. Bite me.)
- Created a group member aggro watcher. (Gonna change this to be under TidyPlatesUtility)
Pass it a name of a party membmer, and it'll tell you if that person has aggro
TidyPlatesWidgets:EnableAggroWatch()
TidyPlatesWidgetsisableAggroWatch()
TidyPlatesWidgets:GetThreatCondition(name)
- Removed the troubleshooting panel.
- Changed "Notes" in TOC
- Spell cast watcher now watches the combat log for casting associated with marked units (raid icons), and will display the cast warning on those units in lieu of a GUID or name.
- Spell Cast events now trigger the SetAlpha functions (in addition to the scale and text functions)
- Spell Cast events send this data to the delegate functions, in addition to normal unit information:
unit.isCasting = true
unit.spellName = spell
unit.spellIsShielded = notInterruptible

r92-100:
- The LoadTheme function is now accessible to external software, via: TidyPlates.LoadTheme("name").
- Removed the '.InterfacePanel' interface panel pointer variable.  Replaced with .ShowConfigPanel, which is a function that is called when the wrench icon is clicked
- Threat Line (Tug) widget scales to frame width (default of 100)
- Added Name text color delegate, SetNameColor
- Sets a unique frame level for each plate (up to 125)
- Raises frame level of current target to a high frame level (126), and return it to previous when done.


r83-91:
- bug fixes
- layering tweaks
- changed default hitbox size to match original
- Grey and Neon tweaks

r82:
- fixed: highlight region used to occasionally turn on when the nameplates would show.
- fixed: Selection box couldn't be turned off in Neon
- fixed: depth/layering  (ok, i went back to using active alpha override, rather than virtual parenting)

r81:
- Fixed Neon/Tank saved variables

r80:
- More bug fixes (Threat line widget "pet")

r79:
- Bug Fixes

r78:
- add icons for the "configure theme" functions
- making any changes in the interface panel will now apply the changes in real-time (no more 'apply' button)

r77:
- Removed and restructured some of the OnUpdate code (to prevent some nil errors)
- Added interface panel option for the cast watcher, directly in the /tidyplates panel  (so any theme can use it)
- Click on theme name in theme chooser window to bring up linked panel (supplied to, theme.InterfacePanel = panelframe)

r72-76: (38,606)
- Anchoring and event handling fixes
- The theme loader will now call 'theme.OnActivateTheme' (a theme function) when the active theme is changed.  it passes two value to the function: the active theme table, and the active theme name.
- The theme loader will call the theme.OnActivateTheme with nil values for ALL themes when a theme is changed.  See the Neon/Tank functions.lua for how and why it's supposed to be used.
- Numerous bug fixes
- The new casting system has been finished.  Neon/Tank will activate it automatically, but you can use '/run TidyPlates:StartSpellCastWatcher()' to enable it for any theme.


r70:
- Massive changes.  Your themes may not work...
- Removed Cvar for Bloattest
- Added external access for plates tables
- Changed MANY names for things.  See the TidyPlatesDefaults.lua file for the new format names.  To enable an element, use the .show tag under each element.  (No more options.showName = true, etc)
- Added "spelltext" which replaces one of the special text fields.
- removed specialtext fields.  replaced with "spelltext" and "customtext"
- Returned to Virtual Parenting (Tidy Plates Frames are NOT children of the base nameplate.  They are just anchored)
- Elite segments have been removed from the healthborder and threatborder.  Use multi-style if you want different textures
- Elite icon has been added to replace elite segments
- Skull icon texture can now be changed
- Cast bar will continue to display on previous target when you change targets (guesstimated)
- Cast bar will start on a target if you change TO that target, and they are casting a spell (guesstimated)
	- The cast bar may not register interupts fully.  But, it will let you know that the unit is casting.  Quit whining, you babies.
- Preliminary Spell Cast Monitor, in place.  Not yet activated.  You can find this code under the widget folder, in SpellCastMonitor.lua, if you want to enable/play with it.
	- At this stage of development, If you can't figure out how to enable it on your own, YOU SHOULDN'T.
- Changed the update functions a wee bit to try and reduce CPU load.  Some plates may not be updating correctly.  Complain wisely (ie. with specifics) and it shall be fixed.
- Added a selection box item to the visual elements.  find it under, theme.target


5.15
-------------


r67-68:
- Mass Update queue will now kill the other mass update requests if a full update was scheduled
- Messed about with Neon/Tank, and added some new code to test, regarding aggro and friendly unit debuffs.

r66:
- lil' Core changes

r59-r65:
- Numerous bug fixes (some of them pretty big)
- "Culling of Old Widget Code"
- Various optimizations
- Reordering of updates (Delegate functions will get updated on TidyPlates:Update() calls, regardless of the 'unit' table having changed)

The R65 release contains the test version of Graphite.

r58:
- Lil' bug fixes

r54-57:
- Neon now keeps a "Known targetOf list" table, which delegate functions access to highlight non-tanked targets
- Added a simple Combat Log Analyzer to Debuff Widget (To report debuff cancelation back to ID'd units)
- Tank role recognition in Threat Line Widget
- Totem Icon Widget Included in WidgetLib.  Not yet in Neon.
- Changed internal cast bar code in prep for cast warning system (slated for 5.16).  oddities might occur.  I'll fix as discovered

5.14
-------------
r50-53:
- fixed nil values during set scale
- adjusted neon font to 'Qlassik', size, and position for better clarity
- added some comments to the default theme file
- threat line widget will not update on a unit until there is a threat table; meaning, if you're solo, you won't see anything.

r47-49:
- Commented-out improved cast bar code; Saved for another cycle
- removed unit.targetOf determination; too much cpu utilization
- some optimization of the OnUpdate function to improve fading performance
- Fixed color picker widget being placed under the interface options window
- theme.SetAlpha functions should just return a single value, for absolute alpha (0.0-1.0).  additional returns are ignored
- The theme template table (the one with all the default values) has been changed to no longer look like the Grey theme.  The Grey theme's media is now stored in its own folder.  Choosing "None" as a theme option will show name-text, only.
- TP previously tried to associate arena, party, raid member guids to a nameplate (by name).  This has been removed due to cpu considerations
- Changelog has been updated ;-)


r46:
- Still cranky
- fixed the Avoid overlap thingy
- added some update throttling for threat line widget
- commented out some friendly unit guid identification code

r44:
- I'm exhausted and sick and I don't want to even think about this stupid changelog thing and it's a miracle that I'm actually uploading this and I'm going to go to my freaking bed so I can be less cranky in the morning. I'm also hungry, dammit.

r43:
- Improved Fade
- Added a unit.targetOf variable, which the core will attempt to fill, depending on if there is a path to that unit (target, mousover, raid1target, party2target, etc.. doesn't fill from arena, yet)
- Added a .backdrop tag to the statusbars in the style table for themes; The image will appear behind the statusbar.

r40:

* Improved Tug-o'-Threat Widget
- Widget will try to acquire threat data from raid members

* Nameplates will now fade in when they appear

* Improved Cast Bar
- Will now try to estimate the cast of a
unit, without being targeted.


5.13
-------------
r37:
* Fixed Alpha == 0 update problems (Not updating name, health)
* Fixed Neon panel (Not holding values)

r36:
* Modified layering
* Mainstream Release!

r35:
* Updates and fixes to Neon (including Unit Level)
* Inclusion of Graphite (just a peek at an upcoming theme)
* Layering adjustment
* Removal of some beta debug code

r31:
* New theme callback function: OnContextUpdate. Triggered when the GUID of a unit is updated.
* SetThreatColor will trigger for every unit, with no filtering, allowing the designer to use the
Threat Glow for other purposes (such as debuff tracking)
* Neon and Grey Panels are parented to their own category.
* Neon Panel has been updated
* New Neon features:
- Threat glow border
- Class Icon
- Debuff Widget Config

r30:
- Modified the theme table preprocessor to fill in values on the incoming theme table, rather than generating a totally segregated table.
- The style application function will now use that updated custom theme table
- Theme styles can be modified in real-time, and updated with TidyPlates:ForceUpdate()
- Theme reload will only be required when new styles are added, after the initial loading. (to multi-style themes)

r28:
- Added SetCastbarColor function

r26:
- Added SetThreatColor function

- Modified the core to reduce the workload on data updates.
More specifically, I've made new paths for update requests
which avoid updating every single piece of data when only
a single value has changed.
- Cleaned up some code, and added some new comments


In-Progress
--------

* Restore Fade-In
* Smart Aura Mode
* Reorganize Themes to make 'em prettier.
* Ku-theme
* Metro-theme
* Customization
* Core Anchoring Options

* Tidy Plates 7.0 Theme Format
* Cube Frame Widget
* "Resolution Independence"
* Easy Scaling

In Progress
---------------------------
* Aura Widget: Filtering Expansion
* Health Text Display Customizer (3 channel)
* Font Tweaker
* Raid Icon to Target/Spotlight Opacity
* Hub + Neon Theme: Raid Icon Repositioning Test; Raid Icon appears above the health bar, unless Auras are displayed.
* "Highlight" Feature, to bind a key to Mark units to a Saved List, which can be used for Spotlight Functions
* Combo Point vs Debuff Widget Repositioning, within style?
* Drowndown Frame: 	Add: - Description Text Field on Top, which displays tooltip Text, Textures, Close/Cancel Button

