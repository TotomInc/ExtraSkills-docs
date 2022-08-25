---
sidebar_position: 2
---

# Abilities Configuration

> A configuration guide about the `abilities.yml` file.

## General

In this configuration file, each ability contains the same properties.

Each ability configuration property will be found under **`abilities.<skill_name>.<ability_name>`**.

- `enabled` - if true, the ability will be enabled.
- `base_value` - the default value of the ability at level 1. This value is used as a percentage value, a chance to trigger the ability.
- `value_gained_per_level` - the percentage value gained **per ability level** (not skill level). This value will be used like this: `base_value + (value_gained_per_level * (skill_level / level_up_rate))`
- `unlock_level` - the skill level required to unlock this ability, at level 1.
- `level_up_rate` - the multiple that the ability levels up at based on the skill level. For example, a skill level 10 means the ability is at level 2 if the `level_up_rate = 5`.
- `max_level` - the maximum level of this ability.
- `blocks` - a list of blocks that will be used as triggers for this ability.
- `entities` - a list of entities that will be used as triggers for this ability.

## Example Ability Configuration

Let's create an example ability configuration for the Lucky Miner ability.

```yml
abilities:
  mining:
    lucky_miner:
      enabled: true
      base_value: 2.0
      value_gained_per_level: 2.0
      unlock_level: 5
      level_up_rate: 5
      max_level: 10
      blocks:
        - DIAMOND_ORE
        - DEEPSLATE_DIAMOND_ORE
```

- Each ability configuration can be set under `abilities.<skill_name>.<ability_name>`.
- Enable the ability with the `enable` property.
- Define the `base_value` of the ability to `2.0`, which is equal to **2% trigger rate** at ability level 1.
- Set `value_gained_per_level` of the ability to `2.0`, which means our ability will **gain 2% more trigger rate** at each level.
  - For example, at ability level 5 our ability will have a 10% chance to trigger.
- This ability will be unlocked when the player reach the Mining skill level 5, defined in `unlock_level`.
- Define the multiplier in which the ability level-up based on the skill value with `level_up_rate` (_formula is as simple as `skill_level / level_up_rate`_).
  - If the Mining skill is at **level 25**, the Lucky Miner ability level will be at **5**.
- Define a `max_level` for the ability.
- Define a list of blocks that are eligible and will trigger this ability.
