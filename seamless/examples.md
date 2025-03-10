---
order: D
icon: light-bulb
---

# Examples

Some examples for reference

## Beds

Let's take a look at how you would create an outline rule for beds.

A bed has the parts `foot` and `head`. Both parts face the same direction. So, for the foot we need to connect to where it's facing, and for the head in the opposite direction.

```json bed_foot.json
{
  "blocks": ["#minecraft:beds"],
  "blockstates": {
    "part": ["foot"]
  },
  "directions": ["/state:facing"],
  "connecting_blocks": ["/same"],
  "connecting_blockstates": {
    "facing": ["/same"],
    "part": ["/!same"]
  }
}
```

```json bed_head.json
{
  "blocks": ["#minecraft:beds"],
  "blockstates": {
    "part": ["head"]
  },
  "directions": ["/state:facing+opposite"],
  "connecting_blocks": ["/same"],
  "connecting_blockstates": {
    "facing": ["/same"],
    "part": ["/!same"]
  }
}
```

Because we use a tag in `blocks`, beds from other mods would automatically work too, provided that the mod developer has added their beds to the tag.

## Chests

If a chest is large, it has the types `left` and `right`. Both blocks face in the same direction. If a left chest faces north, the right chest would be to the east, so rotating clockwise once. The Ender Chest is included in the tag but does not have a double variant, so we should exclude it.

```json chest_left.json
{
  "blocks": ["#c:chests", "#forge:chests", "!minecraft:ender_chest"],
  "blockstates": {
    "type": ["left"]
  },
  "directions": ["/state:facing+1"],
  "connecting_blocks": ["/same"],
  "connecting_blockstates": {
    "facing": ["/same"],
    "type": ["right"]
  }
}
```

For right chests facing north, the left one would be in the west direction, so three clockwise rotations.

```json chest_right.json
{
  "blocks": ["#c:chests", "#forge:chests", "!minecraft:ender_chest"],
  "blockstates": {
    "type": ["right"]
  },
  "directions": ["/state:facing+3"],
  "connecting_blocks": ["/same"],
  "connecting_blockstates": {
    "facing": ["/same"],
    "type": ["left"]
  }
}
```
