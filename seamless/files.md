---
order: B
icon: file-code
---

# Files

Inside of the folder you just created, we are going to add JSON files for different outline rules. These rules define how outlines of different blocks merge if they are next to each other. 

An outline rule in its simplest form looks like this:

```json /minecraft/seamless_rules/sunflower.json
{
  "blocks": ["minecraft:sunflower"],
  "directions": ["up", "down"],
  "connecting_blocks": ["minecraft:sunflower"]
}
```

- First we have the `blocks` list. This is where you put all blocks (or tags) that apply to this rule. Think of this as the block you are looking at.
- The `connecting_blocks` list specifies which blocks (or tags) should be able to connect with the blocks in the `blocks` list. 
- The `directions` list contains all directions in which the rule should work. This can be `north`, `east`, `south`, `west`, `up` and `down`.

The file name can be whatever you want, but it would make sense to describe the rule.

## Blockstates

Optionally, you can specify blockstates too:

```json /minecraft/seamless_rules/door_upper.json
{
  "blocks": ["#minecraft:doors"],
  "blockstates": {
    "half": ["upper"]
  },
  "directions": ["down"],
  "connecting_blocks": ["#minecraft:doors"],
  "connecting_blockstates": {
    "half": ["lower"]
  }
}
```

This means: any block in `#doors` with a state of `upper` for the property `half`, will connect to any block in `#doors` with a state of `lower` for the property `half`.

You can specify more than one state too, for example:

```json
"blockstates": {
  "age": ["0", "1", "2"],
  "half": ["lower"]
}
```

!!!
Creating these files can get quite time consuming, so the next page lists some shortcuts you can use.  
!!!

## Recursion

When looking at a block and a match is found, Seamless will check the connecting block for other connecting blocks. This could go on forever! Keep this in mind, as you will often need to create outline rules that are more specific, to keep the outlines from spreading to disconnected blocks.
