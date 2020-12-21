## MCP-Reborn [![Build Status](https://github.com/Hexeption/MCP-Reborn/workflows/Java%20CI/badge.svg)](https://github.com/Hexeption/MCP-Reborn/actions?workflow=Java+CI)

#### MCP-Reborn is a MCP (Mod Coder Pack) for minecraft for making modded clients for minecraft and researching its code.

#### Based on: MCPConfig and ForgeGradle by MinecraftForge Team.

### :warning: WARNING :warning::  You CAN'T publish any code generated by this tool.

### Supported versions:

| Version     | Support |
| ---      | ---       |
| 1.16.4| ✔         |
| 1.16.3| ✔         |
| 1.16.2| ✔         |
| 1.16.1| ✔         |
| 1.15.2| ✔         |
| 1.15.1| ✔         |
| 1.15| ✔         |
| 1.14.4 | ✔         |
| 1.14.3 | ✔         |
| 1.14.2 | ✔         |
| 1.14.1     | ✔       |
| 1.14 | ✔     |
| 1.13.2 | ✔   |
| 1.13.1 | ✔    |
| 1.13 | ✔    |
| 1.12.2 | ❌    |
| 1.12.1 | ❌    |
| 1.12 | ❌    |

### Known issues:

~~There's no sound in game during debugging.~~

### How to use

- Import the build.gradle in Intellij.

- Run the setup in the mcp folder in intellij - you may need to select View > Tool Windows > Gradle to get this option.

<img width="284" alt="373de4ebc77d5079584370dd7fbe8745" src="https://user-images.githubusercontent.com/4052647/46925924-71b7b680-d026-11e8-9c29-e3ed2e43f810.png">

- This will generate the decompiled source code, which you can now find in the "src" folder in the project. Modify that
  source to change the code as you please.

- To test your modified code, go back to the Gradle tasks list (where you ran setup), and run the "runclient". This will
  compile your new, modified game and run it, to allow you to test.

- Once you have reached a final result you are happy with, there is a bit of a process to turn it into a JAR file that
  can actually run from the game launcher. Go to the "build" folder in the gradle tasks, an run the "build" task. This
  will generate the new executable JAR file in the "build/libs/" directory.
  <img width="266" alt="a647ab0eb336062ffd80c8e053e10266" src="https://user-images.githubusercontent.com/4052647/46925963-a297eb80-d026-11e8-8b02-cb621b559511.png">

- With that jar generated, open your Minecraft versions folder. On Linux, this defaults to ~/.minecraft/versions. On
  windows, it's in Appdata/Roaming/.minecraft/versions. Find the variant your modded version is based on (that is, if
  you modded 1.16.4, find the 1.16.4 folder). Duplicate that folder, and rename it. For me, I was modifying villagers so
  I called it "1.16.4_villager_mod".

- Go into that folder and delete the original Minecraft's JAR file. Then, rename the JSON file to be identical to the
  folder name. For me, that made it "1.16.4_villager_mod.json".

- Using a text editor, find the first instance of "downloads": . This tells Minecraft where to obtain the game JAR file.
  If you leave this in, Minecraft will automatically download the vanilla JAR. But we want to run your new modded JAR.
  So delete everything from that "downloads": through the client, server, and server_mappings headers, which finally end
  in `/server.txt"}},`. Once you remove that, this section should
  hold `"assets": "1.16", "complianceLevel": 1, "id": "1.16.4"`. The last thing we need to do in this JSON file is to
  change that ID field to match the name of the folder and the JSON file. So in this case, we want "id":"
  1.16.4_villager_mod".

- Now, take your new JAR file from the build/libs/ directory, and copy it into this same version folder, and, for the
  final time, rename it to the name we've been using everything - 1.16.4_villager_mod.jar.

- Using an archive manager (Ubuntu comes with one built in; Windows users can download 7zip), open the base version's
  JAR file (in this case, 1.16.4.jar, which you'll find in its folder), and your JAR file. You'll need to copy 4
  files/folders from the base JAR into your new one.

1. The folder "assets"
2. The folder "data"
3. The file "pack.png"
4. The file "pack.mcmeta"

-Finally, still in that archive manager, delete the META-INF folder from your new JAR.

-Your files should all be configured now. In the Minecraft launcher (close and reopen it if it's already open), go to
Installations in the upper left, and then create a new installation. Name it whatever you want. For the version, select
your version you made (1.16.4_villager_mod.jar). Create it, then go back to the launcher home screen by clicking Play in
the upper left. In the lower left, select your new custom version, and hit the big green Play button.

### How to add Optifine

[![](http://img.youtube.com/vi/ocz1tPI_YSE/0.jpg)](http://www.youtube.com/watch?v=ocz1tPI_YSE "How to add Optifine to MCP Reborn")

### Creators:

* Hexeption
* kingdevnl

#### Special thanks to: **MinecraftForge** Team who made this tool possible. ❤

