---
order: C
icon: zap
---

# Shortcuts

Sometimes, if there are many blockstates, many files are needed. To avoid having to make tons of almost identical files, there is some handy stuff you can use to make things much easier.

## Excluding Blocks

Sometimes, a tag might contain exceptions, so you need to exclude blocks from it. This is done by putting an exclamation mark in front of the block you want to exclude. 

```json
"blocks": ["#c:chests", "!minecraft:ender_chest"]
```

You can exclude entire tags too.

```json
"blocks": ["#minecraft:buttons", "!#minecraft:wooden_buttons"]
```

## Directions

In the `directions` list, instead of specifying an explicit direction like `north`, you can work with the sate of the targeted block. The blockstate property has to be a directional property, like `facing` or `axis`.

```json
"directions": ["/state:facing"]
```

This makes Seamless only search for matches in the direction that the block itself is facing. 

You can use the opposite of the direction as well, north would become south and up would become down.

```json
"directions": ["/state:facing+opposite"]
```

Instead of `opposite`, you can use numbers as well, for horizontal directions. The value represents the amount of clockwise rotations, `north` -> `east` -> `south` -> `west` -> `north`. Rotating twice would have the same effect as `opposite`.

```json
"directions": ["/state:facing+3"]
```

Rotating and opposite do not work with axis properties.

## Blocks

If you use tags or multiple blocks in the `blocks` list, you may not want to make them all connect to each other, but only to their own block. In the `connecting_blockstates` list, you can do exactly that.

```json
"connecting_blocks": ["/same"]
```

For example, I want to make all wool blocks connect to each other, but only to their own color. I could make 16 files for every color, but this is much easier.

```json
{
  "blocks": ["#minecraft:wool"],
  "directions": ["north", "east", "south", "west", "up", "down"],
  "connecting_blocks": ["/same"]
}
```

## Blockstates

Just like with `connecting_blocks`, you can use `/same` in the `connecting_blockstates` object too. The outlines will only connect if the state is the same, or not the same, with `/!same`. In the example below, `facing` has to be the same and `part` has to be different.

```json
"connecting_blockstates": {
  "facing": ["/same"],
  "part": ["/!same"]
}
```

If a blockstate property returns a direction or number, like `facing` or `age`, you can add things after a "+" just like in the `directions` list. 

```json
// adding one
"age": ["/same+1"]
// subtracting two
"age": ["/same+-2"]

// rotating clockwise once and twice
"facing": ["/same+1", "/same+2"]
// the opposite
"facing": ["/same+opposite"]
```
