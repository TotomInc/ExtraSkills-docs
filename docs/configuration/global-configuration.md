---
sidebar_position: 1
---

# Global Configuration

> A configuration guide about the `config.yml` file.

## Before Starting

- Message format is handled by `MiniMessage`, which is a lightweight message format with HEX support:
  - [Preview MiniMessage format in your browser](https://webui.adventure.kyori.net/)
  - [MiniMessage Format documentation](https://docs.adventure.kyori.net/minimessage/format.html)

- Default colors used in the configuration are from the [Australian FlatUI Colors Palette](https://flatuicolors.com/palette/au).

## General

### Action-Bar

:::info
An action-bar is a small text that is displayed at the bottom of the screen, above the player hotbar.
:::

Configuration property **`action_bar:`**

- `enabled` - if true, action-bar module is globally enabled for the plugin.
- `enable_for_skill_experience_gained` - if true, action-bar module will be used when a player gain skill experience.
- `disable_on_max_level` - if true, action-bar module is disabled when a player reach the max level of a skill.
- `skill_experience_gained_format` - the format of the action-bar message when a player gain skill experience. This message can contain the following placeholder values:
  - `{reward}` - the amount of skill experience gained.
  - `{skill}` - the name of the skill formatted with a capital letter at the first letter of each word.
  - `{skill_capitalize}` - the name of the skill formatted in upper case.
  - `{skill_lowercase}` - the name of the skill formatted in lower case.
  - `{experience}` - the current amount of skill experience, formatted with 0 digits.
  - `{experience_2f}` - the current amount of skill experience, formatted with 2 digits.
  - `{experience_required}` - the amount of skill experience required for level-up, formatted with 0 digits.
  - `{experience_required_2f}` - the amount of skill experience required for level-up, formatted with 2 digits.
  - `{level}` - the current skill level.
  - `{player_name}` - the name of the player.
- `skill_max_level_format` - the format of the action-bar message when a player gain skill experience but is at max skill level. This message can contain the same placeholder values as `action_bar.skill_experience_gained_format`.

### Boss-Bar

:::info
A boss-bar is a progression-bar that is displayed at the top of the screen, with a caption.

This is used by default for major game bosses such as the Ender Dragon or the Wither.
:::

Configuration property **`boss_bar:`**

- `enabled` - if true, boss-bar module is globally enabled for the plugin.
- `enable_for_skill_experience_gained` - if true, boss-bar module will be used when a player gain skill experience.
- `disable_on_max_level` - if true, boss-bar module is disabled when a player reach the max level of a skill.
- `type` - type of the boss-bar, can be one of the following values `PROGRESS, NOTCHED_6, NOTCHED_10, NOTCHED_12, NOTCHED_20`.
- `color` - color of the boss-bar, can be one of the following values `PINK, BLUE, RED, GREEN, YELLOW, PURPLE, WHITE`.
- `display_time` - time in seconds that the boss-bar is displayed.
- `skill_experience_gained_format` - the format of the boss-bar message when a player gain skill experience. This message can contain the same placeholder values as **`action_bar.skill_experience_gained_format`**.
- `skill_max_level_format` - the format of the boss-bar message when a player gain skill experience but is at max skill level. This message can contain the same placeholder values as `action_bar.skill_experience_gained_format`.

### Title

:::info
A title is a text displayed in large on the middle of the screen.

It can contains 2 lines, a title and a description.
:::

Configuration property **`title:`**

- `enabled` - if true, title module is globally enabled for the plugin.
- `enable_for_skill_level_up` - if true, title module will be used when a player level-up a skill.
- `skill_level_up_title` - the format of the title's title (first line). This message can contain the same placeholder values as **`action_bar.skill_experience_gained_format`**.
- `skill_level_up_description` - the format of the title's description (second line). This message can contain the same placeholder values as **`action_bar.skill_experience_gained_format`**.

### Sound

Configuration property **`sound:`**

- `enable` - if true, title module is globally enabled for the plugin.
- `enabled_for_skill_level_up` - if true, title module will be used when a player level-up a skill.
- `skill_level_up_sound` - ID of the sound, list of available sounds can be found in this [soundlist](https://www.digminecraft.com/lists/sound_list_pc.php).
- `skill_level_up_sound_source` - sound chanel to play the sound, can be one of the following values `MASTER, MUSIC, RECORD, WEATHER, BLOCK, HOSTILE, NEUTRAL, PLAYER, AMBIENT, VOICE`.
- `skill_level_up_pitch` - pitch of the sound, can be a value between 0 and 2 where 1 is the normal sound.
- `skill_level_up_volume` - volume of the sound, can be a decimal value between 0 and 1.

## Gameplay

### Abilities

This section contains the configuration for special properties of abilities.

For a list of all existing abilities and their description, see [this page](/docs/abilities.md).

:::caution
If you need to customize an ability level-up rate or triggers, please check `abilities.yml`.
:::

Configuration property **`abilities:`**

#### Haster

Configuration property **`haster:`**

- `duration_in_ticks` - duration of the potion effect, in ticks (_1 seconds = 20 ticks_).
- `potion_effect` - potion effect to apply to the player, you can find [a list of all available potion effects](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/potion/PotionEffectType.html).
- `amplifier` - potion effect amplifier, where 1 is the base value (e.g. 3 is Haste III).

#### Farseeing

Configuration property **`farseeing:`**

- `experience_multiplier` - experience multiplier added to the block break experience.

### Skill experience

- `use_global_experience_expression` - if true, the `"global_experience_expression"` formula will be used to calculate experience required on all skills. This is useful if you want all skills to have the same experience requirements.
- `global_experience_expression` - the experience expression formula. For more details about an expression syntax, see [this page](/docs/configuration/expressions.md).

  The following placeholder values can be used inside the expression:

    - `level` - the new level of the skill.

### Worlds and regions

You can disable the plugin (disable experience gain and skills) in specific worlds or regions (_WorldGuard regions_).

- `disabled_gamemodes` - list of gamemodes that will disable the plugin if the player has one gamemode from this list.
- `disabled_worlds` - list of worlds where the plugin will be disabled if the player is in one of those worlds.
- `check_player_block_placed` - if true, the plugin will keep a list of blocks that have been placed by players. If the player tries to interact with this block, the plugin won't register the interaction. This is useful especially to prevent infinite skill experience gain when a player has Silk-Touch.

  **It is recommended to leave it to `true`.**

### Economy

:::tip
If you want to use economy integration, you need to install [Vault](https://www.spigotmc.org/resources/vault.34315/).
:::

This plugin can integrate with your existing server economy, thanks to [Vault](https://www.spigotmc.org/resources/vault.34315/).

- `enable_gain_money_on_skill_levelup` - if true, enable economy support when player level-up a skill.
- `money_skill_levelup_expression` - the expression to calculate the amount of money to give to the player when he level-up a skill.

  The following placeholder values can be used inside the expression:

    - `level` - the new level of the skill.
