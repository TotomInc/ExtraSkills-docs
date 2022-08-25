---
sidebar_position: 3
---

# Expressions Usage

## What is an Expression?

An Expression is a formula that will be used inside the plugin with interpolated values.

The plugin is using a library called [EvalEx](https://github.com/uklimaschewski/EvalEx#supported-functions). Feel free to check out the examples available.

## Creating an Expression

Let's take the `global_experience_expression` configuration property as an example.

We will create an Expression to calculate the experience required for the current skill level.

Our Expression looks like this:

```
IF(level == 1, 100, 100 * level * 1.33)
```

Let's understand what's going on here.

The `IF` Expression from EvalEx is documented as this `IF(condition, value_if_true, value_if_false)`.

1. If level is equal to 1, set the experience required to 100.
2. If level is not equal to 1, use a formula to calculate the experience required.

  - The formula `100 * level * 1.33` contains a placeholder value `level` which will be replaced by the player's skill level.
  - For example, if the player is as level 5, the result will be `100 * 5 * 1.33 = 665`.
  - Placeholder values are integrated by myself into the formula, **you can't put whatever you want in the formula**. Those placeholder values should be documented in every section that contains an Expression.
