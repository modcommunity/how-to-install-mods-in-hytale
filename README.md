A guide on how to **download** and **install mods** in [Hytale](https://hytale.com/) on Windows, Linux and macOS.

Hytale modding works differently from almost every other game we write these guides for, and the difference is worth understanding before you download anything. Hypixel Studios built Hytale **server-side first**. Mods are installed by whoever hosts the world, not by each player, and the studio has said plainly that it does not intend to support client mods at all.

That sounds restrictive until you realise what it buys you: you can join any modded Hytale server without installing a thing. No client packs, no version juggling, no launcher profiles.

Our example is [BetterMap](https://www.curseforge.com/hytale/mods/bettermap), a server plugin that gives the in-game map persistent exploration, waypoints and cave rendering.

[**View Guide On TMC (Recommended Due To Better Formatting)**](https://moddingcommunity.com/blog/how-to-install-mods-in-hytale/)

## Table Of Contents
* [Requirements](#requirements)
* [Server-Side Modding Explained](#server-side-modding-explained)
    * [Singleplayer Is A Server Too](#singleplayer-is-a-server-too)
    * [Joining Someone Else's Modded Server](#joining-someone-elses-modded-server)
* [The Four Kinds Of Hytale Mod](#the-four-kinds-of-hytale-mod)
* [Where Mods Go](#where-mods-go)
* [Installing A Mod For Singleplayer](#installing-a-mod-for-singleplayer)
* [Installing A Mod On A Dedicated Server](#installing-a-mod-on-a-dedicated-server)
* [Installing With The TMC App](#installing-with-the-tmc-app)
* [Configuring Mods](#configuring-mods)
* [Per-World Mods](#per-world-mods)
* [Platforms](#platforms)
* [Updating And Removing Mods](#updating-and-removing-mods)
* [Troubleshooting](#troubleshooting)
* [Conclusion](#conclusion)
* [See Also](#see-also)

## Requirements
* A PC running **Windows**, **Linux** or **macOS**. Hytale has native builds for all three.
* A copy of **Hytale**, bought through [hytale.com](https://hytale.com/). The game is in early access and is not on Steam.
* Enough free space for whatever you install. Asset packs with lots of models and textures get large; plugins are usually small.
* A `.zip` extractor, though in many cases you will not need to unzip anything at all.

**NOTE** - Hytale has been in early access since January 2026 and is still moving quickly. Hypixel Studios have been openly self-critical about the state of the modding tools, describing gaps in documentation and systems that are still rough. Expect things to change, and expect a mod to occasionally break after an update.

## Server-Side Modding Explained
Hypixel Studios laid out a few principles when they published their modding strategy, and two of them shape everything in this guide:

* **Server-side first.** All Hytale modding is based on the host of the server or the host of the game. You should be able to join any modded Hytale server without downloading external mods or juggling client packs.
* **One community, one client.** They want to avoid an ecosystem where every server needs its own modded client, so the client stays stable and consistent while servers provide the variation.

In practice, that means a mod is installed **once**, by the host, and every player connecting gets the modded experience with a completely vanilla client.

### Singleplayer Is A Server Too
This is the bit that makes everything else make sense.

Hytale does not have a separate singleplayer mode in the traditional sense. When you create a singleplayer world, you are joining a local server that is just for you. So "the host" is you, and installing mods for singleplayer is the same operation as installing them on a server, in a different folder.

You then select which mods you want on a per-savegame basis, which is a genuinely nice model: one world with an overhaul, another vanilla, no profile switching.

### Joining Someone Else's Modded Server
You install nothing. Connect to the server and play.

The host's plugins and asset packs drive the experience and your client renders whatever the server tells it to. This is why the in-game server browser can do compatibility checks and show you only servers you can actually join.

## The Four Kinds Of Hytale Mod
Hytale modding splits into four technical categories, and knowing which one you are dealing with tells you what to expect.

| Kind | Format | What it does |
| ---- | ------ | ------------ |
| **Server plugins** | Java `.jar` | Extend the server programmatically. Minigames, economies, commands, custom logic. The most powerful category. |
| **Data assets** | JSON | Define core content: blocks, items, NPCs, world generation, loot and drop tables. |
| **Art assets** | Models, textures, sounds | The look and sound of everything. Hytale supports Blockbench for models and animations. |
| **Save files** | Worlds and prefabs | Whole worlds, or prebuilt structures used in creative tools and world generation. |

**Asset Packs** are the packaging format for the middle two. An asset pack is a zip or a folder with a `manifest.json` inside, containing a custom set of assets that override or add to the base game. They can be made in the in-game Asset Editor or by hand in a file browser, though the studio recommends the editor because the folder layout is strict.

BetterMap is a server plugin, so it is in the first category.

**NOTE** - There is no Lua or other text-based scripting in Hytale and the studio has said there will not be. Their plan is visual scripting, in the spirit of Unreal Blueprints, alongside Java for programmers.

## Where Mods Go
Two locations matter.

**The global mods folder**, used by everything:

```
C:\Users\<user>\AppData\Roaming\Hytale\UserData\Mods
```

**The per-world mods folder**, which each savegame also has:

```
C:\Users\<user>\AppData\Roaming\Hytale\UserData\Saves\<World Name>\mods
```

On Linux and macOS, the `UserData` folder is in the equivalent application data location for your system, with the same structure underneath.

Anything in the global `Mods` folder is available to any world. Anything in a world's own `mods` folder belongs to that world alone.

**TIP** - On Windows, paste `%appdata%\Hytale\UserData` into the File Explorer address bar to jump straight there.

## Installing A Mod For Singleplayer
1. Go to [CurseForge's Hytale section](https://www.curseforge.com/hytale) and find a mod. For this guide, open [BetterMap](https://www.curseforge.com/hytale/mods/bettermap).
2. Download it.
3. Open your `UserData\Mods` folder.
4. Drop the downloaded file in. Asset packs can stay zipped or be extracted as a folder; plugins go in as the `.jar`.
5. Start Hytale.
6. Open the **New World** menu and look under **Options**. Your installed mods and asset packs appear there.
7. Enable the ones you want for this world, and create it.

That last step is the one people miss. Putting a mod in the folder makes it available; you still choose it per world when the world is created.

CurseForge is the main host, which is unsurprising given that Hypixel Studios ran their $100,000 New Worlds Modding Contest with them. There were over 5,000 Hytale mods on the platform by early 2026 with more than 20 million downloads between them.

## Installing A Mod On A Dedicated Server
For a server you run for other people, the idea is identical and the folder is the server's own.

1. Download the mod.
2. Put it in the server's `mods` directory.
3. Restart the server.

BetterMap keeps everything it needs there, creating `mods/bettermap/` for its configuration and data on first run.

Players connecting to your server need nothing installed. That is the whole point of the model.

If you are setting up a server in the first place, our separate [Hytale server guide](https://moddingcommunity.com/blog/how-to-setup-a-hytale-server/) covers that.

## Installing With The TMC App
Since there is no Hytale mod manager yet, this is worth flagging. [The TMC App](https://moddingcommunity.com/tmc-app) is our own mod manager and server browser, with one-click installs and **sandboxes**: named mod profiles per game, each with its own load order and deployment method, switchable without re-downloading anything.

**Hytale is not in its supported games list yet**, but it is a good fit. The app works by knowing where a game's mods go and how it launches, both of which are four JSON files rather than code, and Hytale's `UserData\Mods` folder with no loader involved is about as simple a target as that system gets. Sandboxes would also map neatly onto Hytale's per-world mod selection.

The honest position: **the app is in very early development.** Its README says it is partially tested and we will not dress that up. Hytale itself is early access and moving weekly, so this is two young things pointed at each other. If you are up for that, trying it and reporting back is genuinely useful.

It is **open source** under GPL-3.0 at [github.com/modcommunity/tmc-app](https://github.com/modcommunity/tmc-app). Bug reports and feature requests go in [the issue tracker](https://github.com/modcommunity/tmc-app/issues), pull requests are welcome, and the repository documents the per-game format if you want to contribute Hytale support before we get to it.

Installing it:

* **Linux**: one line, no root and no package manager.

```bash
curl -fsSL https://raw.githubusercontent.com/modcommunity/tmc-app/main/scripts/install.sh | sh
```

* **Windows**: the `setup.exe` or `setup.msi` from the [releases page](https://github.com/modcommunity/tmc-app/releases). There is a portable build too, though it does not register the launcher entry or the `tmc://` link handler.
* **macOS**: the `.dmg` from the same releases page.

## Configuring Mods
There is no single standard, but the common pattern is a JSON config inside the mod's own folder under `mods`.

BetterMap is a good example. Its settings live in `mods/bettermap/config.json`, and it exposes things like exploration radius, map quality, update rate and whether exploration is shared between players:

```json
{
  "explorationRadius": 16,
  "updateRateMs": 500,
  "mapQuality": "MEDIUM",
  "shareAllExploration": false,
  "radarEnabled": true
}
```

Well-built plugins also add admin commands and permissions. BetterMap registers `/bm` commands, including `/bm reload` to pick up config changes without a restart, though it notes that some settings still need a full restart.

Read the mod's CurseForge description. With Hytale modding as young as it is, that page is very often the only documentation there is.

## Per-World Mods
Asset packs created in-game with the Asset Editor land in that world's own `mods` folder rather than in the global one. This is convenient while you are building something, and confusing the first time you start a second world and wonder where your pack went.

To use a pack you made in one world in another world, copy it from:

```
UserData\Saves\<World Name>\mods
```

into:

```
UserData\Mods
```

Once it is in the global folder it shows up in the options for every new world.

## Platforms
Hytale entered early access on **Windows, macOS and Linux**, and that is the full list. There is no console or mobile version, and the game is not on Steam.

Cross-platform play between those three desktop platforms is there, and broader cross-platform support has been part of the plan since the game was reacquired, but nothing beyond desktop exists to install mods on today.

## Updating And Removing Mods
There is no mod manager for Hytale yet, so both are manual.

* **Update**: download the new version from CurseForge and replace the old file in `Mods`. Check the mod's page for whether your config carries over.
* **Remove**: delete the file from `Mods`, or just untick the mod for a given world.
* **Disable for one world only**: leave the file where it is and untick it in that world's options.

**WARNING** - Removing a mod that added blocks, items or creatures from a world that used them can leave that world in a bad state, the same as in any block game. Back up the save folder before you strip mods out of an existing world.

## Troubleshooting
**My mod does not show up in the New World options.** Wrong folder. It needs to be in `UserData\Mods` or in that world's own `mods` folder, and an asset pack needs a valid `manifest.json`.

**I installed a mod but the world I am already in has not changed.** Mods are selected when a world is created. Existing worlds do not pick up newly installed mods on their own.

**The pack I made in-game is missing from my other world.** Asset Editor packs are saved to the world you made them in. Copy it into the global `Mods` folder.

**A plugin loads but its commands do nothing.** Check permissions. Hytale plugins use permission nodes, and commands generally need OP or an explicit grant.

**Everything broke after a Hytale update.** Expected, at this stage. Hytale runs weekly pre-release patches bundled into stable releases every few weeks, and mods need time to catch up.

**Players say they need to install the mod to join.** They do not. If somebody is telling you otherwise, they are describing how a different game works.

**Can I use client mods?** No. There is no client mod support and the studio has said there are no plans for any.

## Conclusion
Hytale modding comes down to a single idea: the host installs, everyone else just plays. Drop the file in `UserData\Mods`, tick it when you make a world, and you are done. For a dedicated server it is the same file in the server's own `mods` folder.

It is a genuinely different model from the BepInEx and mod loader setups in our other guides, and once it clicks it is much less work. The tooling is young and the documentation is patchy, which Hypixel Studios readily admit, so lean on mod descriptions and [docs.hytale.com](https://docs.hytale.com/) while things settle.

If you would like to help with something, the [TMC App](https://github.com/modcommunity/tmc-app) is open source, very early in development, and feedback on it would be genuinely appreciated.

## See Also
* [Hytale on CurseForge](https://www.curseforge.com/hytale)
* [Hytale Documentation](https://docs.hytale.com/) - Official docs for running servers and building mods.
* [Creating Content in Hytale](https://docs.hytale.com/creating-content/) - Asset packs, world generation and the editors.
* [Hytale Modding Strategy and Status](https://hytale.com/news/2025/11/hytale-modding-strategy-and-status) - The studio's own account of where modding stands and where it is going. Worth reading in full.
* [Official Hytale Discord](https://discord.com/invite/hytale)
* [Hytale Wiki](https://hytale.fandom.com/wiki/Hytale_Wiki)
* [TMC App](https://github.com/modcommunity/tmc-app)

Hytale is early access and changes fast, so this guide will drift more than most. If you find an instruction that no longer matches what you are seeing, please report it or open a [pull request](https://github.com/modcommunity/how-to-install-mods-in-hytale/pulls) on this guide's GitHub repository.

Join our [Discord server](https://discord.moddingcommunity.com) if you have any questions or want help with anything modding related!
