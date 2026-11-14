# bigint mod
This is a Minecraft 1.3.2 mod that lets you teleport to any coordinates you want. And I mean any: `1e50`, `-123456789012345678901234567890`, `1e300`, whatever.
### Base
This thing is a jar mod for Minecraft `1.3.2`, singleplayer only. It needs `Java 8` or newer.
### Why?
There was another mod that could do this, but it was glitchy and laggy as hell, placing redstone crashed the game, and so on. So I made my own one that doesn't do that.
### How does it work?
The game itself keeps working with small normal numbers, and the huge part of your coordinates is stored separately (a floating origin). So physics, lighting, redstone and everything else work just like in vanilla, no matter how far you are. When you teleport really far, the world reloads for a second, that's normal.
### Teleporting
Just use `/tp`. Every coordinate can be a math expression with `+ - * / ^` and brackets, and you can use `x`, `y` and `z` (your current position) in any of the three arguments. `~` means relative to you, like usual. Don't put spaces inside an argument though, Minecraft splits commands by spaces.
```
/tp 1e50 140 0
/tp 1e50+10000 140 0
/tp x*2 140 0
/tp x*1e50 140 0
/tp 0 140 x*2
/tp 10^300 70 0
/tp ~1e6 ~ ~
```
Press F3 and you will see your real coordinates.
### What's out there?
The world is generated using your real coordinates. Up to 12,550,821 it's a normal world, and exactly at 12,550,821 the Far Lands start. Up to around 1e10 they still have grass on top, then from around 1e12 to 1e48 it's stone Far Lands stretched into endless walls, and from around 1e49 (so at 1e50 and 1e300 too) it's just an endless ocean, because that's where the noise generator overflows.

Fun fact: vanilla 1.3.2 doesn't actually have the Far Lands, one line in the noise generator gets rid of them. This mod turns that line off, so you get the real vanilla math without the patch.
### How to install
1) Back up your Minecraft 1.3.2 jar and your worlds first, seriously
2) Open the game jar with an archiver like 7-Zip. With the old launcher it's `.minecraft/bin/minecraft.jar`. With the new launcher it's better to make a separate version: copy `.minecraft/versions/1.3.2` to `.minecraft/versions/1.3.2-bigint`, rename the files inside to `1.3.2-bigint.jar` and `1.3.2-bigint.json`, change `"id": "1.3.2"` to `"id": "1.3.2-bigint"` in the json and delete the whole `"downloads"` part, otherwise the launcher will just download the original jar again
3) Delete the `META-INF` folder inside the jar
4) Copy everything from `bigint-mod-1.3.2.zip` into the jar, replacing files (there's a `net` folder in there too, copy it as well)
5) Run the game and turn on cheats for your world, otherwise you can't use `/tp`

To uninstall it, just put your backup jar back.
### Things to know
Only singleplayer. If other players are in your world over LAN, far teleports won't work. It doesn't work with ModLoader, Forge or other jar mods either, because it replaces 30 classes of the game, including `World` and `MinecraftServer`. In the End you can't teleport far, the End is small anyway.

When you teleport far you get kicked off your boat or minecart, a bed that ends up astronomically far away gets forgotten, and maps can show the wrong place. Also the Far Lands are heavy to generate, so it can lag a bit for the first few seconds when you arrive.

NOTE: don't open a world in vanilla after teleporting far in it. Vanilla doesn't know where you actually are and will put you in the wrong place. Worlds where you never teleported far are fine in vanilla.
