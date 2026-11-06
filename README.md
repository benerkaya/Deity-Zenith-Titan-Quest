# Deity Zenith Titan Quest

A Cheat Engine table for **Titan Quest Anniversary Edition** that lets you summon creatures from a list of **3895 entries** taken from the game's own database (creatures, NPCs and bosses), either as enemies or as allies that fight for you.

Author: **Bener Kaya**

---

## Features

- **3895 summon-list entries, sorted by region.** Pick a region first, then an entry. The list includes creatures, NPCs and special records; many entries are non-creature sound or effect records. Each region lists its bosses first, marked `Boss:`.
- **Real in-game names.** Entries use the creature's English in-game name (for example `Polyphemus ~ Cyclops`).
- **One summon key.** Press **F10** (or the key you choose) to spawn **1–20** creatures at once.
- **Two spawn spots.** Spawn **at your hero** or **next to your town portal**.
- **Two factions.** Choose **Hostile** (normal enemies) or **Player side** (allies on your team). Player side summons at your hero **follow you** like pets.
- **Multiplayer host support.** The lobby host can summon hostile or allied creatures, for example for NPC-vs-NPC duels.
- **Optional boss music outside arenas.** Off by default. When on, **enemy** bosses play their own boss track when you get close to them anywhere, not only inside boss arenas.
- **Compatibility checks.**
  - The table checks code signatures at the places it hooks and refuses to install a hook where the code does not match.
  - Unticking **Enable** restores the patches the table installed.
  - Game files on disk are never modified.

## Requirements

| | |
|---|---|
| Game | **Titan Quest Anniversary Edition**, Steam, Windows, build **2.10.21415** |
| Tool | **[Cheat Engine](https://www.cheatengine.org/)** |

On other game builds the code signature checks are expected to fail, and the table refuses the hooks that do not match.

## Files

| File | Contents |
|---|---|
| `Deity Zenith Titan Quest.CT` | The Cheat Engine table |
| `region_list.txt` | Every Summon entry per region exactly as shown in the table (region, position, index, record path, name) |
| `unit_list.txt` | Every entry with its record path and original file-based label |
| `README.md` | This file |

There is nothing to install. Keep the files together and open the `.CT` with Cheat Engine.

## Quick start

1. Start **Titan Quest Anniversary Edition** and load into a world. A **Custom Game** is the easiest place to start.
2. Start **Cheat Engine** and open **`Deity Zenith Titan Quest.CT`**.
3. Tick **Deity Zenith - Enable**. The table attaches to `TQ.exe` and checks the game version.
4. Choose a **Region** and a **Summon**, then set **Count**, **Where** and **Faction**.
5. Press **F10** in game.
6. Untick **Enable** before you close the game.

## Controls

| Entry | Options | Default |
|---|---|---|
| **Deity Zenith - Enable** | Turns the table on or off. Unticking restores the patches it installed | Off |
| **Region** | Greece, Egypt, Orient, Babylon, Hades, Ragnarok, Atlantis, Eternal Embers, Common | Greece |
| **Summon** | Creature to spawn, from the selected region | Ravenous Boar (Lv 9) |
| **Count** | 1–20 per key press | 1 |
| **Where** | At player / At portal | At player |
| **Faction** | Hostile / Player side | Hostile |
| **Summon Key** | F10, F11, Insert, Home, End, Page Up, Page Down, Pause, Middle mouse, Off | F10 |
| **Boss music outside arenas** | Off / On | Off |
| **Diagnostics** | Last result and status values (collapsed) | |

### Region and Summon

| Region | Entries | Bosses |
|---|---|---|
| Greece | 658 | 15 |
| Egypt | 413 | 13 |
| Orient | 430 | 17 |
| Babylon | 22 | 0 |
| Hades | 631 | 40 |
| Ragnarok | 636 | 26 |
| Atlantis | 283 | 17 |
| Eternal Embers | 660 | 61 |
| Common | 162 | 0 |

- Changing **Region** swaps the Summon list. It resets to that region's first entry within a quarter second.
- Expansion creatures are listed under their expansion: Hades = *Immortal Throne*, Ragnarok, Atlantis, and Eternal Embers.
- Base-game creatures are listed under the act where the game actually spawns them.
- **Common** holds creatures shared between acts or never placed in a regional spawn pool.
- Before you tick **Enable**, the lines show `??` like every other Cheat Engine entry.

### Names

- Names come from the game's own English text.
- Where two entries in one region share a name, a short note tells them apart: `(Lv 21)`, `(Champion)`, `(ambush)`, `(variant B)`.
- If they are still identical after that, the record's file name is added in `[brackets]`.
- Entries without a translated name keep a readable name made from their file name.

### Where

- **At player:** at your hero, the same spot as the developer console's `game.Spawn`.
- **At portal:** next to your own town portal. Cast **Return to Town** first, and stay in the area where the portal is.

### Faction

- **Hostile:** a normal enemy.
- **Player side:** joins your team and fights for you.
- With **At player**, a Player side summon also **follows you** like a pet.
- With **At portal**, it stays at the portal.

## Multiplayer

- **Singleplayer** and the **multiplayer host** can summon.
- **Clients cannot summon.** Diagnostics → Last result shows **21**. Ask the host to summon.
- Summons made by the host appear for everyone in the game.

## Boss music outside arenas

Normally a boss track only starts inside the map's boss arenas. With this switch **On**:

- An **enemy** creature that has its own boss track starts it when you come within its normal music range, wherever you are.
- **Allied** (Player side) and neutral bosses stay silent outside arenas.
- The game's own fade rules still apply. The music fades when you walk away or the boss dies. Another boss's track does not cut in until the current one has faded.
- **Inside real boss arenas, and with the switch Off, music works exactly as in the normal game.**
- Scripted music, such as quest event music, is not affected.
- Only creatures whose record has a boss track can play anything.
- The switch is **local to your PC**: in multiplayer it only changes what you hear.
- It is **Off** every time you tick Enable.

## Known limitations

- Works only on the game build listed above.
- The list is built from the game database, so it includes many non-creature records, such as effects, sounds and props, that are not valid summons, as well as quest helpers, statues, decorations and developer test monsters. Skip anything that does nothing or behaves strangely.
- **Player side** needs a real creature. Objects and statues are refused and removed again.
- There is a soft limit of **200 summons per Enable**. Untick and tick **Enable** to reset it.
- Spawning at the mouse cursor is not supported.
- Other players need their own copy of the table and the switch turned on to hear outside-arena boss music. This is untested.

## Troubleshooting

Open **Diagnostics** and check **Last result**:

| Last result | Meaning / what to do |
|---|---|
| **Spawned (1)** | Success |
| **No player (2)** / **No GameEngine (3)** / **No world/ObjectManager (11)** | The world is not ready yet. Wait until your hero is in the world. |
| **Busy (4)** | The previous summon is still being processed. Press the key again. |
| **Session limit (7)** | Soft limit reached. Untick and tick **Enable**. |
| **Create failed (9)** | The game could not create that record. Nothing was spawned. |
| **Stub integrity fail (12)** | The table's code was changed in memory. Untick and tick **Enable**. |
| **No portal (13)** | Cast **Return to Town** first. |
| **Portal area not loaded (14)** | Go back to the area where your portal is. |
| **Portal coords bad (15)** | The portal position looked invalid, so nothing was spawned. |
| **Option disabled (16)** | That option did not match this game build. Use At player / Hostile. |
| **Not a creature (18)** | Player side only works with creatures. |
| **Spawned, team not applied (19)** | The summon appeared but stayed hostile, because a safety check refused the team change. |
| **Spawned, follow not applied (20)** | The ally appeared on your side but does not follow you. |
| **Clients cant spawn; host must spawn (21)** | You are a multiplayer client. Only the host can summon. |

Other messages:

| Message | What to do |
|---|---|
| *Start Titan Quest Anniversary Edition first* | Start the game, or attach Cheat Engine to `TQ.exe` with the computer icon. |
| *This game version is not supported* | Your game build is different. Nothing was changed. |
| *Game.dll not found* / *Load into a singleplayer world first* | Enter a loaded world, then tick **Enable** again. |
| **Boss music outside arenas** jumps back to Off | Diagnostics → **Boss music OK** is Off: the music code did not match, so nothing was patched. Restart the game and tick **Enable** again. |

**Safe disable:** untick **Deity Zenith - Enable** before you close the game or Cheat Engine. This removes the patches the table installed and restores the original code at those places.

## Credits

Made by **Bener Kaya**.

Creature names and records come from the game's own `database.arz` and `Text_EN.arc`. Titan Quest and Titan Quest Anniversary Edition belong to their respective owners.
