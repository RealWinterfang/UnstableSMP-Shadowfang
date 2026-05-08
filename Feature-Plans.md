# Feature Plan

## Overview
This document outlines the planned features for **UnstableSMP-Shadowfang**.

The plugin is intended to provide:
- per-player gameplay customization
- cosmetic player customization
- server moderation tools
- combat and stasis utility features
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

### Orbital Strike Nukes & Stab Shots
Add custom offensive utility mechanics for high-impact gameplay.

**Notes**
- Define activation conditions, range, cooldowns, and damage behavior
- Clarify whether these are command-based, item-based, or event-triggered
- Make all damage, effects, and permissions configurable

### Totem Stasis
Allow a stasis totem system that stores and later teleports a player.

**Targeting**
- Coordinates may be set using `x y z`
- Coordinates may also be set using `crosshair crosshair crosshair`

**Behavior**
- When the stasis totem pops, the player should be teleported to the coordinates that were set

**Notes**
- Define whether the location is stored per player or per item
- Clarify activation, teleport timing, and any cooldowns
- Make targeting behavior configurable

### Stasis Rod
Add a rod-based stasis utility feature.

**Targeting**
- Coordinates may be set using `x y z`
- Coordinates may also be set using `crosshair crosshair crosshair`

**Notes**
- Define whether the rod binds to a saved location or current aimed block
- Clarify use limits, cooldowns, and permission requirements
- Make targeting behavior configurable

### Mafia Tagging
Allow administrators to tag or untag players with `/mafia` commands.

**Requirements**
- Use `/mafia tag <player>` to apply the mafia tag
- Use `/mafia untag <player>` to remove the mafia tag
- The target player must currently have an active invisibility effect when tagged
- If a tagged player's invisibility effect expires, start a 10-second timer
- After 10 seconds, teleport the tagged player below bedrock into the void
- Define whether untagging cancels a pending teleport
- Commands should be protected by permission nodes
- Make delay and teleport behavior configurable

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
/mafia tag <player>                        - Tag a player while they have active invisibility
/mafia untag <player>                      - Remove a player's mafia tag
```

### Command Notes
- All nickname and skin commands should require permission nodes
- Consider validating nickname length and formatting
- Define whether skin input refers to a username, skin preset, or external lookup source
- `/mafia tag` should fail if the target does not currently have invisibility
- Consider adding feedback for active timer state and pending void teleport behavior

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
- Orbital strike and stab shot settings
- Stasis rod and stasis totem targeting settings
- Mafia tag timer and teleport settings

---

## Persistence

The following data should persist across restarts:
- player nickname changes
- player skin changes
- per-player KeepInventory state, if implemented that way
- mafia-tagged player state, if intended to survive restarts
- stasis locations, if stored persistently

---

## Design Notes
- Permission nodes should gate nickname and skin commands
- Server freeze should optionally disable external skin API requests for stability
- Configuration should stay consistent between command-based control and file-based control
- Mafia tagging should explicitly define what happens if invisibility is refreshed before the timer ends
- Stasis targeting should clearly support both direct coordinates and crosshair-based selection
