---
sidebar_position: 3
---
# Slash command choices
Welcome to the sequel of my take on slash commands tutorial! This guide is mainly dedicated to choices around slash commands and how to use them! It is advised to read on what’s in the guide if you’re new to this to avoid making mistakes.

# What are choices?
Choices are custom options for a `string` type of a slash command option. You know the select menu with custom options? It’s exactly that except it’s a slash command option instead.

# Notes
This feature is not the same as autocomplete, the difference between both is that, choices are forced custom options with no custom input allowed from the user when autocomplete is the opposite of that and are more of suggestions based on the user’s current input.

With that being said, do not think of choices as autocomplete.


# Getting started
When it comes to choices, they can be treated in two ways

* **customID**
* **replies**

Treating choices as an custom id can allow you to do various things such as having each specific code for each choice chosen by the user himself. However, treating choices as **replies** will have you very limited experience as by this point, it will be a regular reply with nothing special happening after that.


# Setting up choices

Let's start with the customID way, so here's a little ordinary slash option code:
```js
$createApplicationCommand[$guildID;choice;slash command choices showcase!;true;false;slash;[{
  "name": "option",
  "description": "options example",
  "required": true,
  "type": 3
}]
```
Seems normal right? We can then expand it further by adding `"choices":` with it's names and values like this
```js
$createApplicationCommand[$guildID;choice;slash command choices showcase!;true;false;slash;[{
  "name": "option",
  "description": "options example",
  "required": true,
  "type": 3,
"choices" : [{
"name" : "choice 1",
"value" : "value1"
}]
}]]
```
