---
sidebar_position: 3
---

# Disabling logs

Want your own ready message instead of getting your bot name logged with an invite to official aoi.js support server? well, you can use `aoiLogs` Option.

# Example
```js
const { AoiClient } = require('aoi.js')

const bot = new AoiClient({
   token: "DISCORD BOT TOKEN"
   prefix: "DISCORD BOT PREFIX"
   intents: ["Guilds", "GuildMessages", "MessageContent"],
   events: ["onMessage", "onInteractionCreate"],
   aoiLogs: false,
   database: { 
     type: "aoi.db",
     db: require("@akarui/aoi.db"),
     tables: ["main"],
     path: "./database/",
     extraOptions: {
         dbType: "KeyValue" 
     },
 }
 })
```

You can revert that by setting `aoiLogs` option to `true` again.

:::tip
You can also use `aoiWarning` option to disable the update message of aoi.js when an new version releases (setting it to `true` will disable the update message, otherwise `false` would do the opposite.)
:::