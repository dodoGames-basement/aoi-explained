---
sidebar_position: 3
---
# Sub commands

Sub commands is a way to add extra commands to an existing slash commands up to 50 with each of them having their own purpose and their own descriptions as well!

:::note
Ensure your bot has permissions to create slash commands in the server you're gonna create in otherwise this guide won't work.
:::

Let's say that if we want two sub commands then we will add them using `$createApplicationCommand` json options like this:
```js
module.exports = {
name: "sub",
code: `$createApplicationCommand[$guildID;slash;sub commands showcase!;true;slash;[
{
  "name": "sub1",
  "description": "an sub command example!",
  "type": 1 
},
{
  "name": "sub2",
  "description": "second sub command example",
  "type": 1 
}
]]`
}
```
:::caution
It's worth noting that normal slash options cannot be added to an existing slash command
:::

Here's how sub commands look in general:
![sub commands preview](https://cdn.discordapp.com/attachments/647127947144069120/1029354603055161384/unknown.png)

In case, we want an sub command to have a option then we're gonna modify our sub commands to include one user option as a example:
```js
module.exports = {
name: "sub",
code: `$createApplicationCommand[$guildID;slash;sub commands showcase!;true;slash;[
{
  "name": "sub1",
  "description": "an sub command example!",
  "type": 1,
  "options": [
       {
          "name": "user", 
          "description": "example option", 
          "required": true, 
          "type": 6
        }
        ] 
}]]
`
}
```
Running this code will create a sub command named `sub1` with the option name `user`!

# Responding to Sub Commands
Create a slash command code for reply then add the following:
```js
$onlyIf[$interactionData[options._subcommand]==sub_slash_name;]
```
To make things clear, `sub_slash_name` is the sub command name to respond to so in our example we have sub command named `sub1` so we replace `sub_slash_name` with `sub1` and it should work! Let's have an example about this:
```js
module.exports = [{
name: "slash-name",
type: "interaction",
prototype: "slash",
code: `$interactionReply[hi an reply from sub command!, awesome!]
$onlyIf[$interactionData[options._subcommand]==sub_slash_name1;]`
},
{
name: "slash-name",
type: "interaction",
prototype: "slash",
code: `$interactionReply[hi an reply from sub command!, awesome!]
$onlyIf[$interactionData[options._subcommand]==sub_slash_name2;]`
}]
```

Now that you learned on how to create sub commands, feel free to go into an adventure of developing slash commands for your bot!