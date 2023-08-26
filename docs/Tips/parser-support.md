---
sidebar_position: 3
---

# Setting up aoi.parser

Aoi.parser is an extension for aoi.js parser system that adds features such as ephemeral messages for interaction error messages from `$onlyIf`, including the ability to use different types of select menu such as select menu for [channels](https://aoi-parser.vercel.app/documentation/parsers/component#channelinput) and other types like `{reply:}`, etc.

## Understanding what you do

When you setup aoi.parser, you agree that all of your usage of parsers will be changed to aoi.parser ones. We recommend viewing [aoi.parser docs](https://aoi-parser.vercel.app/documentation/parsers/embed) for viewing aoi.parser usages of parsers like components, embeds, etc (you may have to scroll down to see all of them though).

:::info
If you want to use the original version of parser then you may use advanced setup which allows you to choose on which parser to change to aoi.parser one.
:::

## Setting up parser support

Run the following command to your terminal:

```js
npm i @akarui/aoi.parser@latest
```

After the package is installed, add the following code to your index.js.

```js
// Enable aoi.parser.
const { Util } = require("aoi.js");
const { setup } = require("@akarui/aoi.parser");

setup(Util);
```

If you got no errors after restart then you're good to go.

## What use cases are aoi.parser for

**Example Use Cases:**

* You want to use ephemeral for interaction error messages alongside with `{interaction}` option.

* You want to try different types of select menu.

* You want to make the bot use discord's reply feature from an function like `$sendMessage` in normal commands.

* You want to control on what mentions are allowed in bot commands with allowedMentions Option inside functions like `$sendMessage`

* Using slash option parsers for creating slash commands using `$createApplicationCommand`

**Examples you don't need aoi.parser for:**

* Using components parser inside functions like `$sendMessage` in normal commands (you can do that already without aoi.parser).

* Using files parser for functions like `$sendMessage` in normal commands (you can do that without it as well).

* Using slash option parsers for creating autocomplete commands (you can do it without it with this guide from [official Aoi.js Docs](https://aoi.js.org/docs/guides/interactioncommands#autocompleterespond-functions--examples)). + Note that it's up to your liking of which method you prefer for creating slash options so this is not a force.

&#x20;

## Examples of aoi.parser features

Buttons including embeds inside `$sendMessage`: &#x20;

```js
$sendMessage[{newEmbed:{title:embed}{description:click on the button below}}
{actionRow:{button:hello:1:helloButton}}
]

// Fact: this code also works without aoi.parser 
// As said in the not needed cases to use aoi.parser.
```

Interaction error from `$onlyIf` with ephemeral option including interaction option:


```js
$onlyif[disabled!=disabled;
  Error.
{options:{ephemeral}}
{extraOptions:{interaction}}
]
```

Using select menu for selecting Text channels Only:

```js
$sendMessage[{newEmbed:{title:menu}}
{actionRow:{channelInput:channelMenu:select a channel:1:1:no:{channelType:0}}}
]
// Use $interactionData[values[0]] for returning the selected channel id from the select menu when responding to select menu for channels in an interaction cmd.

```

