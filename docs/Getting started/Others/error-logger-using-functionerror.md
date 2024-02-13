---
sidebar_position: 3
---

# Error logger using functionError

Sometimes in aoi.js, you want to make your bot log errors so you or your bot team can then investigate on why it's occurring. In this guide, you will learn on how to make error logger system using `onFunctionError` event by aoi.js.

For getting started head over to the [#getting-started](error-logger-using-functionerror.md#getting-started "mention").

## Getting started

To start off, you need to add the following into your `events:` options:


```js
const { AoiClient } = require("aoi.js")

const client = new AoiClient({
    token: "Discord Token",
    prefix: "Discord Prefix",
    intents: ["MessageContent", "GuildMessages", "Guilds"],
    events: ["onMessage", "onInteractionCreate", "onFunctionError"], 
    database: {
        type: "aoi.db",
        db: require("@akarui/aoi.db"),
        dbType: "KeyValue",
        tables: ["main"],
        securityKey: "a-32-characters-long-string-here",
    }
})
```


`onFunctionError` will then enable the ability to log errors of an bug occurring upon running an command!

Now we will make an example error logger command that sends an error each time an problem occurs in one of the commands for an specific channel with **channel** property.


```js
module.exports = {
type: 'functionError',
channel: "CHANNEL ID", // You can also use variables if you want.
code: `$title[Error In $guildName]
$description[Function: $handleError[function]
Command: $handleError[command]
Error: $handleError[error]]
$color[Red]`
}
```


After filling up the channel id you want to on the **channel** property, you will notice that everytime an error occurs when using the certain commands, then it will send the error with the server name (as shown in the example) with the command name and the code error itself to the channel you specified off using it's id.

## Conclusion

Now you have an error logging system that is perfectly working with no issues. You can customize anything to your liking including changing the way on how should the errors be shown.
