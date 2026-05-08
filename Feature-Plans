# Feature Plan

## Overview
This document outlines the planned features for **UnstableSMP-Shadowfang**.

The plugin is intended to provide:
- per-player gameplay customization
- cosmetic player customization
- server moderation tools
- configurable behavior through commands and a config file

---

## Planned Features

### Per-player KeepInventory
Allow KeepInventory behavior to be controlled on a per-player basis rather than only globally.

**Notes**
- Should be persistent across restarts
- Should be configurable through commands and config
- Consider per-world and per-group overrides

### Nickname and Skin Changer
Allow administrators to change player nicknames and skins.

**Requirements**
- Nickname changes persist across restarts
- Skin changes persist across restarts
- Commands should be protected by permission nodes
- Reset options should restore default values
- Random nickname and skin assignment should be supported

### Anti-Armour-Breaking
Prevent armour from breaking due to durability loss.

**Notes**
- Define whether durability loss is fully prevented or capped
- Make behavior configurable

### Server Freeze
Provide a complete server lockdown mode.

**Effects**
- Blocks movement
- Blocks commands
- Blocks interactions
- Blocks inventory access
- Blocks item dropping
- Blocks mining
- Blocks block placing

**Optional Behavior**
- Freeze external skin API lookups during server freeze for stability

### Accelerated HP Regeneration and 2× Food Effectiveness
Modify survival behavior to make recovery faster.

**Effects**
- Faster health regeneration
- Food restores hunger/saturation more effectively

**Notes**
- Multipliers should be configurable
- Should be possible to enable one without the other

### Full Configuration Support
All features should be configurable through:
- commands
- a central config file

**Recommended**
- Global toggles
- Per-world overrides
- Per-group overrides

---

## Commands

```text
/unstablesmp nick <player> <nickname>      - Set another player's nickname
/unstablesmp skin <player> <skinName>      - Change another player's skin
/unstablesmp resetnick <player>            - Reset a player's nickname
/unstablesmp resetskin <player>            - Reset a player's skin
/unstablesmp randomnick <player>           - Assign a random nickname
/unstablesmp randomskin <player>           - Assign a random skin
```

### Command Notes
- All nickname and skin commands should require permission nodes
- Consider validating nickname length and formatting
- Define whether skin input refers to a username, skin preset, or external lookup source

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
- External skin API behavior

---

## Persistence

The following data should persist across restarts:
- player nickname changes
- player skin changes
- per-player KeepInventory state, if implemented that way

---

## Design Notes
- Permission nodes should gate nickname and skin commands
- Server freeze should optionally disable external skin API requests for stability
- Configuration should stay consistent between command-based control and file-based control
