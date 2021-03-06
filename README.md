<h1 align="center">mineflayer-collectblock</h1>
<p align="center"><i>A small utility plugin for allowing users to collect blocks using a higher level API.</i></p>

<p align="center">
  <img src="https://github.com/TheDudeFromCI/mineflayer-collectblock/workflows/Build/badge.svg" />
  <img src="https://img.shields.io/npm/v/mineflayer-collectblock" />
  <img src="https://img.shields.io/github/repo-size/TheDudeFromCI/mineflayer-collectblock" />
  <img src="https://img.shields.io/npm/dm/mineflayer-collectblock" />
  <img src="https://img.shields.io/github/contributors/TheDudeFromCI/mineflayer-collectblock" />
  <img src="https://img.shields.io/github/license/TheDudeFromCI/mineflayer-collectblock" />
</p>

---

## Showcase

You can see a video of the plugin in action, [here.](https://youtu.be/5T_rcCnNnf4)
The source code of the bot in the video can be seen in the examples folder, [here.](https://github.com/TheDudeFromCI/mineflayer-collectblock/blob/master/examples/collector.js)

### Getting Started

This plugin is built using Node and can be installed using:
```bash
npm install --save mineflayer-collectblock
```

This plugin has a relies on [mineflayer-pathfinder](https://github.com/Karang/mineflayer-pathfinder) for pathfinding. That plugin should be loaded first.

### Simple Bot

The brief description goes here.

```js
// Create your bot
const mineflayer = require("mineflayer")
const bot = mineflayer.createBot({ username: "Player" })

// Load pathfinder
bot.loadPlugin(require('mineflayer-pathfinder').pathfinder)

// Load collect block
bot.loadPlugin(require('mineflayer-collectblock').plugin)

function collectGrass() {
  // Find a nearby grass block
  const grass = bot.findBlock({
    matching: require('minecraft-data').blocksByName.grass_block.id,
    maxDistance: 64
  })

  if (grass) {
    // If we found one, collect it.
    bot.collectBlock.collect(grass, err => {
      if (err) // Handle errors, if any
        console.log(err)
      else
        collectGrass() // Collect another grass block
    })
  }
}

// On spawn, start collecting all nearby grass
bot.once('spawn', collectGrass)
```

### Documentation

[API](https://github.com/TheDudeFromCI/mineflayer-collectblock/blob/master/docs/api.md)

[Examples](https://github.com/TheDudeFromCI/mineflayer-collectblock/tree/master/examples)

### License

This project uses the [MIT](https://github.com/TheDudeFromCI/mineflayer-collectblock/blob/master/LICENSE) license.

### Contributions

This project is accepting PRs and Issues. See something you think can be improved? Go for it! Any and all help is highly appreciated!

For larger changes, it is recommended to discuss these changes in the issues tab before writing any code. It's also preferred to make many smaller PRs than one large one, where applicable.
