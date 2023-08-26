---
sidebar_position: 3
---

# creating context menu commands

In this guide, you will learn on how to create context menu commands for both users and messages using `$createApplicationCommand`.

## Types

* `message`: context menu commands made for messages when you right click on a msg or when you long tap on a message to trigger the context menu command from Mobile.
* `user`: context menu commands made for users when you right click on them or when you long tap on a user to trigger the context menu command from Mobile.

## Creating two context menu cmds

Let's say we want to have a context menu cmd, one for user type for the sake of reporting them, second is for remind me system, we can do the following:


```javascript
// For users
$createApplicationCommand[global;report This User;;true;user]

// For messages
$createApplicationCommand[global;remind Me;;true;message]

// note: descriptions are not required if you're creating context menu commands in the function meaning that you can leave them blank.
```


This will create two example context menu commands as said above.

## Responding to context menu commands

To respond to context menu commands for both types, you must use the prototype `slash`  because all the types in `$createApplicationCommand` only works on prototype `slash` including context menu commands.

Additionally, you can use `$interactionData[targetId]` for returning the id of both message and user where you right clicked on them from discord desktop or from mobile when going to `Apps` option after long tap on a message/user as well.&#x20;

Now finally, let's create an example context menu command that responds to an interaction of an context menu for command handlers.


```js
module.exports = {
name: "context-menu-command-name",
type: "interaction",
prototype: "slash",
code: `$interactionReply[Hi!, you have just triggered this context menu!]`
}

```


And now you have a context menu command ready to be used! You're free to do whatever you want to your context menu commands now.
