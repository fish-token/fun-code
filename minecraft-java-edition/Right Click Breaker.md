# What Does It Do?

This command alters the outcome of some right click actions. Actions that get altered include:

- Block Placing (uses the block and creates a ghost block instead)
- Bucket Using (attempts to collect or place the contents but flickers and ultimately doesn't succeed)
- Entity Spawning (flickers the appearance of the entity then disappears)

**Clarifications:**

- This command will not ruin or do any harm (itself) to your world or server.
- This command should not cause any performance issues on your world or server.
- This command was discovered on version 1.21.11, so it might not work otherwise.

## What's The Setup Process?

Just follow the steps below!

- Place a `repeating command block` down and open it
- Put the command (look in the **Code** section) in it
- Toggle `Always Active` to make it run constantly
- Press `Done` or hit `Enter` on your keyboard

The effects should take place immediately.

## Code

```mcfunction
tp @a ~ ~ ~
```

## What's The Removal Process?

Just destroy the `repeating command block` to stop all effects immediately.
