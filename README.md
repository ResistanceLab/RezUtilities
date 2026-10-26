# RezUtilities

A Decal plugin for Asheron's Call (ACE servers): **RezSalvage**, **RezChest**, **RezAutoVendor** and **RezRadar** in one DLL with one window.

| Tab | What it does |
|---|---|
| **Salvage** | Combines your partial salvage bags with the Ust, filling each bag up to the value cap (75,000 on stock ACE) without ever going past 100 units. Manual, automatic, or forced after a set time; the mini HUD has a Combine button. |
| **Chest** | Loots a chest quickly with your VTank loot profile: opens it (key only if it's locked), identifies everything at once, and picks up the keepers back to back. Optional **jump looting** hops in place and picks up while in the air, where the server skips the pickup animation. |
| **Vendor** | Sells to a vendor from a VTank loot profile (`.utl` Sell rules, UtilityBelt AutoVendor profiles work as they are), one batch per server round trip instead of fixed waits. Automatic when a vendor opens, or Sell Now / Preview. |
| **Radar** | Draws the dungeon you're in inside a compass-style ring, straight from the client's own map data, with doors, chests, portals, NPCs, monsters and players marked. |
| **Mini HUD** | Opens the **MMD HUD**: the Chest looter's status lines, MMDs earned this session and per hour (with Clear Stats), plus Spawn Cache, RZ AutoSalvage, Force Value Combine, RZ Force Combine and Sell Now in one small window (Force Value Combine and Sell Now read Stop while running). Also opens the Salvage and Chest mini HUDs. |
| **Update** | Shows the installed build and checks this repository for a newer one. |

## Requirements

- Decal with Virindi View Service
- For the **Chest** and **Vendor** tabs: VTank (RezTank or Virindi Tank) with VTClassic. Salvage and Radar work without it.
- For **Salvage**: a Ust in your inventory.

## Install

1. Download the newest `RezUtilities…dll` from [Releases](https://github.com/ResistanceLab/RezUtilities/releases).
2. Put it in a folder of its own, for example `C:\Games\Decal Plugins\RezUtilities\`.
3. Open the Decal Agent, click **Add**, pick the DLL, and make sure it's checked.
4. **If you used RezSalvage, RezChest, RezAutoVendor or RezRadar on their own, uncheck them** in the Decal Agent. RezUtilities includes all four; leaving the old ones on runs everything twice. (RezUtilities warns you at login if it sees one.)
5. Start the game. Chat shows `[RezUtilities] RezUtilities… loaded: Salvage, Chest, Vendor, Radar`.

**Settings** live in a `Settings` folder next to the DLL, per server and per character:

```
Settings\Server\<server>\              Salvage.ini, Vendor.ini, Autovendor\ (the Vendor's .utl profiles)
Settings\Server\<server>\<character>\  Salvage.ini, Chest.ini, Radar.txt, RadarUiLock.txt
Logs\                                 errors.txt and one folder of logs per part
```

Keep every RezUtilities build in the same folder (the updater does) and your settings stay with it. If that folder can't be written to, RezUtilities uses `Documents\Decal Plugins\RezUtilities\` instead and says so at login.

Your settings from before are copied in the first time each character logs in: from RezUtilities v1.02's `Documents\Decal Plugins\RezUtilities\` folder, or from the old RezSalvage, RezChest, RezAutoVendor and RezRadar folders (chests, keys and loot profiles, value caps, vendor settings and profiles, mini HUD positions, radar settings). The old files are left as they were.

The Salvage, Chest and MMD **mini HUDs** remember where they were and whether they were open, per character: open at logout means open again, in the same spot, at the next login.

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
| `/rzu` (`/rezutilities`) | Show/hide the window. `/rzu salvage`, `/rzu chest`, `/rzu vendor`, `/rzu radar`, `/rzu minihud` open it on that tab; `/rzu mmd` shows/hides the MMD HUD; `/rzu update [cancel]`; `/rzu version` |
| `/rzs` (`/rezsalvage`) | Salvage: `combine`, `stop`, `preview`, `cap 75k`, `auto on/off`, `delay 5`, `force on/off/120`, `verbose`, `status`, `hud` |
| `/rzc` (`/rezchest`) | Chest: `start`, `sel`, `stop`, `chest`, `key`, `profile`, `close`, `report`, `loop`, `auto`, `jump`, `jumpms`, `pausevt`, `hud`, `status`, … |
| `/rav` (`/rezautovendor`) | Vendor: `sell [profile]`, `preview`, `check <profile>`, `stop`, `enable on/off`, `testmode on/off`, `batch 99`, `status`, `profiles`, `sync`, … |
| `/rr` | Radar: settings toggle, `show`/`hide`, `lock`, `size`, `zoom`, `level`, `names`, `time`, … |

Each one has a `help` subcommand with the full list (`/rzs help`, `/rzc help`, `/rav help`, `/rr help`).
