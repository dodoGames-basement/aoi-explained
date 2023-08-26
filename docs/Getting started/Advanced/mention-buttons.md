---
sidebar_position: 3
---

# Mention buttons

Mention buttons is a way to return the mentioned id of the users in interactions so that it can be used for purposes such as moderation commands using buttons, economy give money, etc.

# Before getting started
If it wasn't obvious, you need to have the event `onInteractionCreate` added to your bot first so the example code included in this wiki can work otherwise the button isn't going to respond. 

It's worth noting that you can also use `$findUser` or `$findMember` rather than `$mentioned` as both returns the mentioned user id!

# Example code
```js
module.exports = [{
    name: "mentionButton",
    code: `
    $title[mention Button]
    $description[Press the Button!]
    $color[Random]
    $addButton[1;Example;primary;customID_$mentioned[1;true];false]`
    }, {
      type: "interaction",
      prototype: "button",
      code:`
    $interactionReply[The mentioned user id is $advancedTextSplit[$interactionData[customId];_;2].]
    
    $onlyIf[$advancedTextSplit[$interactionData[customId];_;1]==customID;]`
    }]
```

# How it works
We add our buttons using `$addButton` function as the first thing to do!

Here below the example code, we modify our button's custom id to include `$mentioned` function so that we can return the mentioned user id in the button command hence it would be `customID_$mentioned[1;true]`.

Since it's not ideal putting the custom id name in `name:` property, we remove it and instead use `$interactionData[customId]` to return the current custom id specified in `$addButton` function! We will then add our first `$onlyIf` at the bottom of the interaction's code to check if the button has been clicked by returning it's custom id.

To return the mentioned user id, we will use `$advancedTextSplit` to separate the custom id and the id of the user mentioned as we have included `_`  within the custom id's name which makes it much easier to do that.

Finally, we will then add `$interactionReply` to respond to the button and another `$advancedTextSplit` to return the id of the user mentioned! By default, it returns your id if you mentioned no one otherwise return the id of the user you have just mentioned! 

After that, you're ready to go as our mention button should work now.