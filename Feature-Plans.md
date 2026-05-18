# Feature Plan

## Overview
This document outlines the planned features for **UnstableSMP-Shadowfang**.

The plugin is intended to provide:
- per-player gameplay customization
- cosmetic player customization
- server moderation tools
- configurable behavior through commands and a config file

## Links to the Plugin
- BuiltByBit: [Death Sound Plugin - UnstableSMP](https://builtbybit.com/resources/death-sound-plugin-unstablesmp.102879/)
- Modrinth: [Death Sound Plugin - UnstableSMP](https://modrinth.com/plugin/death-sound-plugin-unstablesmp)
- Curseforge: [Death Sound Plugin - UnstableSMP](https://www.curseforge.com/minecraft/bukkit-plugins/death-sound-plugin-unstablesmp)
- SpigotMC: [Death Sound Plugin - UnstableSMP](https://www.spigotmc.org/resources/death-sound-plugin-unstablesmp.134661/)
- Support Discord: [Join here](https://discord.gg/ckPnDAGJkV)

---

## Planned Features

### Per-player KeepInventory
Allow KeepInventory behavior to be controlled on a per-player basis rather than only globally.

**Notes**
- Should be persistent across restarts
- Should be configurable through commands and config
- Consider per-world and per-group overrides

### Nicknames
Allow administrators to change player nicknames.

**Requirements**
- Nickname changes persist across restarts
- Commands should be protected by permission nodes
- Reset options should restore default values
- Random nickname assignment should be supported

### Armour Break Cap
Prevent armour from breaking due to durability loss.

**Notes**
- Define whether durability loss is fully prevented or capped
- Make behavior configurable

### Server Freeze
Provide a complete server lockdown mode.
- For example something like maintenance, or whitelist mode

**Effects**
- Blocks movement
- Blocks commands
- Blocks interactions
- Blocks inventory access
- Blocks item dropping
- Blocks mining
- Blocks block placing

### Faster Regeneration and 2× Food Effectiveness
Modify survival behavior to make recovery faster.

**Effects**
- Faster health regeneration
- Food restores hunger/saturation more effectively

**Notes**
- Multipliers should be configurable
- Should be possible to enable one without the other

---

## Commands

```text
/unstablesmp nick <player> <nickname>      - Set another player's nickname
/unstablesmp resetnick <player>            - Reset a player's nickname
/unstablesmp randomnick <player>           - Assign a random nickname
```

### Command Notes
- All nickname commands should require permission nodes
- Consider validating nickname length and formatting

---

## Configuration

### Goals
- Every feature should be togglable
- Runtime command controls should match config options
- Config should support future expansion cleanly

### Recommended Config Areas
- Feature toggles
- Permission bypasses
- Per-world settings
- Per-group settings
- Regeneration multipliers
- Food effectiveness multipliers
- Freeze behavior options

---

## Persistence

The following data should persist across restarts:
- player nickname changes
- per-player KeepInventory state, if implemented that way

---

## Design Notes
- Permission nodes should gate nickname commands
- Configuration should stay consistent between command-based control and file-based control
