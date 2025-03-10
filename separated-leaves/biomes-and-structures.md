---
order: C
icon: tools
---

# Biomes & Structures

## Biomes

+++ 2.6.0+

In order to not destroy any trees in custom biomes, Separated Leaves does not separate leaves in unknown biomes. Separated Leaves only works in biomes using a namespace that have registered at least one rule. This means that if a mod adds a biome without modifying any trees, the biomes won't get recognized by Separated Leaves. To fix this, add an empty rule.

```json /[namespace]/separated_leaves/biomes.json
{
  "leaves": [],
  "logs": []
}
```

This way, all leaves in custom biomes of the namespace will work correctly

+++ 2.5.0

For every namespace you add files for, you need to provide a `biomes.json` file alongside the other files. In there, you can specify which biomes should be added to the mod.

If `all` is set to `true`, Separated Leaves will work in any biome with the namespace.

```json /[namespace]/separated_leaves/biomes.json
{
  "all": true
}
```

If you need to specify certain biomes, set `all` to `false` and use the biomes list.

```json /[namespace]/separated_leaves/biomes.json
{
  "all": false,
  "biomes": [
    "minecraft:plains",
    "minecraft:taiga"
  ]
}
```

!!!danger
In version `2.5.0`, a `biome.json` file is required for the mod to work.
!!!

+++

## Structures (1.19+)

Structures with custom trees may break when using the mod. If this is the case for a certain structure, add it to the tag `data/separated_leaves/tags/worldgen/structure/allow_mismatched_leaves.json`.