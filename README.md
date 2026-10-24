# RezUtilities

A Decal plugin for Asheron's Call (ACE servers): **RezSalvage**, **RezChest** and **RezRadar** in one DLL with one window.

| Tab | What it does |
|---|---|
| **Salvage** | Combines your partial salvage bags with the Ust, filling each bag up to the value cap (75,000 on stock ACE) without ever going past 100 units. Manual, automatic, or forced after a set time; the mini HUD has a Combine button. |
| **Chest** | Loots a chest quickly with your VTank loot profile: opens it (key only if it's locked), identifies everything at once, and picks up the keepers back to back. |
| **Radar** | Draws the dungeon you're in inside a compass-style ring, straight from the client's own map data, with doors, chests, portals, NPCs, monsters and players marked. |
| **Update** | Shows the installed build and checks this repository for a newer one. |

## Requirements

- Decal with Virindi View Service
- For the **Chest** tab: VTank (RezTank or Virindi Tank) with VTClassic. Salvage and Radar work without it.
- For **Salvage**: a Ust in your inventory.

## Install

1. Download the newest `RezUtilities…dll` from [Releases](https://github.com/ResistanceLab/RezUtilities/releases).
2. Put it in a folder of its own, for example `C:\Games\Decal Plugins\RezUtilities\`.
3. Open the Decal Agent, click **Add**, pick the DLL, and make sure it's checked.
4. **If you used RezSalvage, RezChest or RezRadar on their own, uncheck them** in the Decal Agent. RezUtilities includes all three; leaving the old ones on runs everything twice. (RezUtilities warns you at login if it sees one.)
5. Start the game. Chat shows `[RezUtilities] RezUtilities… loaded: Salvage, Chest, Radar`.

Your settings from the old plugins are copied over the first time RezUtilities starts: chests, keys and loot profiles, value caps, mini HUD positions and radar settings. They now live in `Documents\Decal Plugins\RezUtilities\` (`Salvage`, `Chest` and `Radar` folders). The old folders are left as they were.

## Updates

RezUtilities checks this repository at login and then every hour.

- **New build found:** RezUtilities downloads it, checks its SHA-256, and installs it next to the old one. The new build loads the next time you start the game.
- **Channels:** test builds only follow test builds, and releases only follow releases. RezUtilities never downgrades.
- **Run AC as administrator once:** this lets RezUtilities point Decal at the new file directly. Without it, the update replaces the running file at the next start instead.
- **Turn off downloading:** put an empty `noautoupdate.txt` next to the DLL. You'll still be told when there's a new build.
- **Check right now:** the **Update** tab's **Check for Update** button, or `/rzu update`. While it runs the button reads **Cancel Update**; the tab shows the status, a download progress bar and the release notes.

## Commands

| Command | |
|---|---|
| `/rzu` (`/rezutilities`) | Show/hide the window. `/rzu salvage`, `/rzu chest`, `/rzu radar` open it on that tab; `/rzu update [cancel]`; `/rzu version` |
| `/rzs` (`/rezsalvage`) | Salvage: `combine`, `stop`, `preview`, `cap 75k`, `auto on/off`, `delay 5`, `force on/off/120`, `verbose`, `status`, `hud` |
| `/rzc` (`/rezchest`) | Chest: `start`, `sel`, `stop`, `chest`, `key`, `profile`, `close`, `report`, `loop`, `auto`, `hud`, `status`, … |
| `/rr` | Radar: settings toggle, `show`/`hide`, `lock`, `size`, `zoom`, `level`, `names`, `time`, … |

Each one has a `help` subcommand with the full list (`/rzs help`, `/rzc help`, `/rr help`).
