---
order: B
icon: file-code
---

# Files

In the folder, add a JSON file for every tree type you want to support. You can name these whatever you want, but the name of the tree would make sense. So our file could be named `morado.json`.

The file exists of two parts. The leaves list and the logs list. Inside the leaves list, add all Leaves that can connect to each other. In the logs list, add all Logs that all leaves from the leaves list can connect to.

```json /atmospheric/separated_leaves/morado.json
{
  "leaves": ["atmospheric:morado_leaves", "atmospheric:flowering_morado_leaves"],
  "logs": ["#atmospheric:morado_logs"]
}
```

The lists accept both Blocks and Block Tags. You can even use both in the same list. 
Almost every mod has got tags for their log variants, but if such a tag does not exist, you can put the separate logs in the list yourself. As well as the default log, it should contain the stripped, wood and stripped wood variants of the log.

!!!danger
It is important to make separate files for every **tree**, not every **wood type**. Oak and Azalea leaves can both connect to Oak Logs, but for the best experience, they should not be able to connect to the wood through each other. Thus they should be split into two files.
!!!
