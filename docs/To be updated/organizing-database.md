---
sidebar_position: 3
---
# Organizing database

If you're a aoi.js user then you already know that by default aoi.js database would store all of variables data into a single file named `main_scheme_1.sql` inside `database` folder within `main` folder.

Normally this should not bother you but if you want a little advanced stuff to your aoi.js bot then you will learn on how to create multiple tables for the database to store each specific variable dedicated to a specific table!

## getting started

:::info
As aoi.js v6 uses **aoi.db** as the main database, this guide will use **aoi.db** option as the main example!
:::

you need to add `database` object to your main bot client options

example

```js
const {AoiClient} = require("aoi.js");

const bot = new AoiClient({
token: "Discord Bot Token",
prefix: "Discord Bot Prefix",
intents: ["MessageContent", "Guilds", "GuildMessages"],
events: ["onMessage"],
database: {
        type: "aoi.db",
        db: require("@akarui/aoi.db"),
        tables: ["main"],
        path: "./database/",
        extraOptions: {
            dbType: "KeyValue"
        }
    }
})
```


As you can see, this does nothing until you change stuff there like path and tables, you can add many table names like server-settings, eco-data, etc depending on what features your bot offers:

```js
const {AoiClient} = require("aoi.js");

const bot = new AoiClient({
token: "Discord Bot Token",
prefix: "Discord Bot Prefix",
intents: ["MessageContent", "Guilds", "GuildMessages"],
events: ["onMessage"],
database: {
    type: "aoi.db",
    db: require("@akarui/aoi.db"),
    tables: ["main", "main2", "main3"], // And so on that you can even add many!
    path: "./database/",
    extraOptions: {
            dbType: "KeyValue"
        },
  },
})
```

## Saving variable data to a specific table

Now that we have a multiple tables stored within our `database` folder, you can force variables function to save data to a specific table!


Here are the list of functions with support for tables:

## Global vars

`$setVar[varname;value;table?]`

`$getVar[varname;table?]`

## Guild vars

`$setGuildVar[varname;value;Id?;table?]` &#x20;

`$getGuildVar[varname;guildID?;table?]` &#x20;

## Channel vars

`$getchannelVar[varname;channelID?;table?]`&#x20;

`$setchannelVar[varname;value;channelId?;table?]`&#x20;



## Global user vars

`$setGlobalUserVar[varname;value;userId?;table?]`

`$getGlobalUserVar[varname;userID?;table?]`&#x20;



## Message vars

`$setMessageVar[varname;value;messageID?;table?]`&#x20;

`$getMessageVar[varname;messageId?;table?]`&#x20;



## Local user vars

`$setUserVar[varname;value;userId?;Id?;table?;]`&#x20;

`$getUserVar[varname;userId?;guildID?;table?]`&#x20;



## Custom variables to a specific table

Now that you have multiple tables, you can make each custom variables to a specific table!

Example:


```js
bot.variables({
variable: "value"
} ,'table name') 
```




this way you can benefit from database tables a lot
