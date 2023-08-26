---
sidebar_position: 3
---
# Making $uptime shorter

by default you're aware that `$uptime` returns the long date format if you don't like this and want to change it then this page is for you! Luckily, $uptime allows you to change on how it should behave!

## humanizing $uptime

You can make $uptime return a short date format with the **humanize** option

```js
$uptime[humanize]
```

## MS format

If for some reason you want the function to return a ms number then set the `$uptime` function to `ms`&#x20;:

```
$uptime[ms]
```

## Outputs
Here's a preview of what they look like:

![Output of $uptime with ms option](https://cdn.discordapp.com/attachments/647127947144069120/1035898830262120458/unknown.png)


![Output of $uptime with humanize option](https://cdn.discordapp.com/attachments/647127947144069120/1035899272379498557/unknown.png)

