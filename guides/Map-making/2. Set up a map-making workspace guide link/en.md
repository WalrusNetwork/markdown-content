# **Set up a map-making workspace**

The first challenge aspiring map makers face when creating their very first map is where _and_ how do they begin. In this guide, we will cover how you can create you own map making workspace (i.e. your very own Spigot server), on your own computer.  We'll also offer some helpful resources that our map team uses all the time, which you can take advantage of to bring your great map ideas to life.

This guide will only cover set up and use of a localhost server.  You can use various port-forwarding techniques to open up your local server to the world and allow your friends to join and build with you – we won't be covering any of those in this guide, but check out this [WikiHow on portforwarding your Minecraft server](https://www.wikihow.com/Portforward-Minecraft) if that's of interest.

## **Preparing the Server**

There are many different server software options which you can use, however, we recommend using PaperMC. You can find the [Minecraft 1.8.8 release here](https://papermc.io/legacy), or alternatively download and compile the source yourself by going to their [GitHub repository](https://github.com/PaperMC/Paper/tree/ver/1.8.8). Walrus runs on Minecraft 1.8, so it is important that your map making workspace also runs on Minecraft 1.8 to ensure map compatibility.

Once you have downloaded the `papermc.jar` file, place it into a new folder somewhere convenient and accessible. Call this folder `Build Server` or something else easily identifiable. This is where all your server files will be created. Next, navigate to this folder from your command line (see [Windows](https://www.poftut.com/how-to-navigate-list-files-and-directories-in-windows-command-line-with-dir/) or [OS X](https://www.macworld.com/article/2042378/master-the-command-line-navigating-files-and-folders.html)) and run `java -jar papermc.jar` to start the server. It is recommended that you create a script to quickly start the server for you. Read [the Spigot installation page](https://www.spigotmc.org/wiki/spigot-installation/#installation) for more info on that.

The first time you run the server, it will stop and prompt you to accept the [Minecraft EULA](https://account.mojang.com/documents/minecraft_eula). Open the `eula.txt` file generated in your root server folder with any text editor, and change `eula=false` to `eula=true`. Save this file and relaunch the server. You should now be able to connect to the server using `localhost` as the server address, in your Minecraft client.  Make sure to use whichever game version the server is on (see which server verison you downloaded from Spigot).

## **Installing Plugins**

Plugins are essentially server add-ons that people have coded over time, which you can easily add to your Spigot server – some of these plugins are very helpful map-making tools. Once you have started up your server for the first time (after having accepted the EULA), a new folder called `/plugins` will be created in the root server folder. To install the plugins, simply save each of the plugin `.jar` files into this folder and then restart the server. Use plugins that are specifically released for the Minecraft server version you are using. Some features or the whole plugin may not work if you use an older or newer version release.  See the online [Spigot plugins library](https://www.spigotmc.org/resources/) with all kinds of plugins that you can install on your server.

For map-makers, we recommend the following set of plugins.

### WorldEdit <small style="vertical-align:4px"><b class="label label-primary">Essential</b>&nbsp;<b class="label label-info">Building</b></small>

WorldEdit is a powerful world manipulation tool which allows you to change thousands of blocks in an instant and sculpt the world around you. It is particularly useful for copy and pasting sets of blocks, flipping or rotating your clipboard, creating various shapes through commands and a large set of brushes. It also adds teleportation functionality to your compass like you see while playing on our servers.

<table>
    <tr>
        <td style="padding-right:30px"><b>Downloads:</b></td>
        <td><a href="https://dev.bukkit.org/projects/worldedit/files">All Versions</a> • <a href="https://dev.bukkit.org/projects/worldedit/files/922048">Bukkit 1.8</a> • <a href="https://minecraft.curseforge.com/projects/worldedit/files">SinglePlayer Forge All Versions</a></td>
    </tr>
    <tr>
        <td><b>Tutorials:</b></td>
        <td><a href="http://wiki.sk89q.com/wiki/WorldEdit">Documentation</a> • <a href="https://youtu.be/SOOvommDpUA">World Edit Basics</a> (video) • <a href="https://github.com/sk89q/WorldEdit-Reference/releases/download/rev6/worldedit_ref_rev6.pdf">WorldEdit Cheatsheet</a></td>
    </tr>
</table>

### VoxelSniper <small style="vertical-align:4px"><b class="label label-info">Building</b></small>

VoxelSniper is a long-range sculpting tool which allows you to easily create detailed landscapes through a large selection of brushes and tools. The plugin shines when creating any sized natural landscape for your map.

<table>
    <tr>
        <td style="padding-right:30px"><b>Downloads:</b></td>
        <td><a href="https://dev.bukkit.org/projects/voxelsniper/files">All Versions</a> • <a href="https://dev.bukkit.org/projects/voxelsniper/files/796868">Bukkit 1.8.1</a></td>
    </tr>
    <tr>
        <td><b>Tutorials:</b></td>
        <td><a href="https://github.com/TVPT/VoxelGunsmith/wiki/Quick-Reference">Quick References</a> • <a href="https://youtu.be/WhqbDi6ICA8">Voxel Sniper Basics</a> (video) • <a href="https://vignette.wikia.nocookie.net/voxelsniper/images/0/0c/300px-Sniper_Cheat_Sheet_New.png/revision/latest?cb=20141029041722">Voxel Sniper Cheatsheet</a></td>
    </tr>
</table>

### WorldGuard <small style="vertical-align:4px"><b class="label label-info">World Management</b></small>

WorldGuard is a powerful world management plugin which can be used to toggle world flags to permit or deny certain events from occurring in the world. This is particularly useful for denying block physics, fire spread, or plant growth in your world.

<table>
    <tr>
        <td style="padding-right:30px"><b>Downloads:</b></td>
        <td><a href="https://dev.bukkit.org/projects/worldguard/files">All Versions</a> • <a href="https://dev.bukkit.org/projects/worldguard/files/881691">Bukkit 1.8.1</a></td>
    </tr>
    <tr>
        <td><b>Tutorials:</b></td>
        <td><a href="https://worldguard.enginehub.org/en/latest/">Documentation</a> • <a href="https://www.youtube.com/watch?v=eEijfFZ5AmU">How to use WorldGuard</a> (video)</td>
    </tr>
</table>

### Multiverse-Core <small style="vertical-align:4px"><b class="label label-primary">Essential</b>&nbsp;<b class="label label-info">World Management</b></small>

Multiverse-Core is another powerful world management plugin which allows your server to support multiple worlds. This allows you to generate different worlds for each of your map creations and quickly teleport between them with a simple command. Use this plugin in conjunction with the [VoidGenerator addon](https://www.spigotmc.org/resources/voidgenerator.25391/) to create empty void worlds to create your new maps in. To generate a new world with this plugin (and the VoidGenerator), use the following command: `/mv create <worldname> normal -g VoidGenerator -t FLAT`. You can then teleport to your world using `/mvtp <worldname>`!

<table>
    <tr>
        <td style="padding-right:30px"><b>Downloads:</b></td>
        <td><a href="https://dev.bukkit.org/projects/multiverse-core/files">All Versions</a> • <a href="https://dev.bukkit.org/projects/multiverse-core/files/898527">Bukkit 1.8.1</a> • <a href="https://www.spigotmc.org/resources/voidgenerator.25391/download?version=251490">VoidGenerator Addon</a></td>
    </tr>
    <tr>
        <td><b>Tutorials:</b></td>
        <td><a href="https://github.com/Multiverse/Multiverse-Core/wiki">Documentation</a> • <a href="https://www.youtube.com/watch?v=aFjDQykr7Cc">Multiverse-Core Tutorial</a> (video)</td>
    </tr>
</table>

### ArmorStandTools <small style="vertical-align:4px"><b class="label label-info">Tools</b></small>

ArmorStandTools (AST) is a set of helpful tools to quickly and easily dress and manipulate armor stands in-game without messing around with confusing commands. Simply use `/ast` to be provided with a full suite of manipulation tools to move the body parts, apply armor, give custom heads, give names, and toggle size. Put simply, this tool allows you to customize every aspect of armor stands!

<table>
    <tr>
        <td style="padding-right:30px"><b>Downloads:</b></td>
        <td><a href="https://www.spigotmc.org/resources/armor-stand-tools.2237/history">All Versions</a> • <a href="https://www.spigotmc.org/resources/armor-stand-tools.2237/download?version=175162">Spigot 1.8</a></td>
    </tr>
    <tr>
        <td><b>Tutorials:</b></td>
        <td><a href="https://www.spigotmc.org/resources/armor-stand-tools.2237/">Commands</a> • <a href="https://www.youtube.com/watch?v=vpnL0vFps8s">Armor Stand Tools Tutorial</a> (video)</td>
    </tr>
</table>

### FastAsyncWorldEdit (FAWE) <small style="vertical-align:4px"><b class="label label-info">Building</b>&nbsp;<b class="label label-info">Tools</b></small>

FAWE is an extension to WorldEdit which heavily improves performance, especially for large scale edits, and adds a considerable amount of additional useful commands and features. From melting brushes to visual previews, this plugin is an absolute must for WorldEdit users.

<table>
    <tr>
        <td style="padding-right:30px"><b>Downloads:</b></td>
        <td><a href="https://www.spigotmc.org/resources/fast-async-worldedit-voxelsniper.13932/history">All Versions</a> • <a href="https://www.spigotmc.org/resources/fast-async-worldedit-voxelsniper.13932/download?version=212574">Spigot 1.8</a></td>
    </tr>
    <tr>
        <td><b>Tutorials:</b></td>
        <td><a href="https://github.com/boy0001/FastAsyncWorldedit/wiki">Documentation</a> • <a href="https://github.com/boy0001/FastAsyncWorldedit/wiki/Commands">Commands</a> • <a href="https://www.youtube.com/watch?v=Fj4DBoWp1ZQ">Fast Async World Edit Tutorial</a> (video)</td>
    </tr>
</table>

### <b style="color:red">C</b><b style="color:red">o</b><b style="color:orange">l</b><b style="color:orange">o</b><b style="color:gold">r</b><b style="color:gold">e</b><b style="color:green">d</b> <b style="color:green">S</b><b style="color:blue">i</b><b style="color:blue">g</b><b style="color:purple">n</b><b style="color:purple">s</b> <small style="vertical-align:4px"><b class="label label-info">Tools</b></small>

When creating a sign, simply put an `&` followed by one of the Minecraft formatting codes to transform your text. For example, `&l&cHello!` would create <b style="color:red">strong red text</b>.

<table>
    <tr>
        <td style="padding-right:30px"><b>Downloads:</b></td>
        <td><a href="https://www.spigotmc.org/resources/colored-signs.31676/history">All Versions</a> • <a href="https://www.spigotmc.org/resources/colored-signs.31676/download?version=236565">Spigot 1.8</a></td>
    </tr>
    <tr>
        <td><b>Tutorials:</b></td>
        <td><a href="https://www.spigotmc.org/resources/colored-signs.31676/">Usage</a> • <a href="https://minecraft.gamepedia.com/Formatting_codes#Color_codes">Color Codes</a></td>
    </tr>
</table>

### ViaVersion and ViaRewind <small style="vertical-align:4px"><b class="label label-info">Tools</b></small>

ViaVersion will allow you to connect to your 1.8 server with newer versions of Minecraft, while ViaRewind allows connection with 1.7 to the server. These plugins are definitely not required for your map making workspace but could be of interest to those that prefer to use versions of Minecraft that are not 1.8.

<table>
    <tr>
        <td style="padding-right:30px"><b>Downloads:</b></td>
        <td><a href="https://www.spigotmc.org/resources/viaversion.19254/history">All Versions ViaVersion</a> •  <a href="https://www.spigotmc.org/resources/viarewind.52109/history">All Versions ViaRewind</a> • <a href="https://www.spigotmc.org/resources/viaversion.19254/download?version=304458">Spigot 1.8 ViaVersion</a> • <a href="https://www.spigotmc.org/resources/viarewind.52109/download?version=293346">Spigot 1.8 ViaRewind</a></td>
    </tr>
    <tr>
        <td><b>Tutorials:</b></td>
        <td><a href="https://github.com/ProtocolSupport/ProtocolSupport/wiki">Documentation</a></td>
    </tr>
</table>

### CommandBook <small style="vertical-align:4px"><b class="label label-info">Tools</b></small>

CommandBook adds a large array of essential commands which help you manage your server. From teleportation, item giving, mob spawning, and slapping, this plugin provides command shortcuts and other useful functions.

<b class="label label-danger">Note:</b> The last official pre-compiled release for CommandBook is for Minecraft 1.7.9 and does not fully work on newer server versions. In order to get a recent version, you must download the plugin source from their [GitHub repository](https://github.com/EngineHub/CommandBook) and [compile it yourself by following their instructions](http://wiki.sk89q.com/wiki/CommandBook/Development#Compiling). 

<table>
    <tr>
        <td style="padding-right:30px"><b>Downloads:</b></td>
        <td><a href="https://dev.bukkit.org/projects/commandbook/files">All Versions</a></td>
    </tr>
    <tr>
        <td><b>Tutorials:</b></td>
        <td><a href="http://wiki.sk89q.com/wiki/CommandBook">Documentation</a></td>
    </tr>
</table>

Now that you have a very solid selection of map-making tools, start up your server and begin building your maps!

## **Standalone Software**

There is a lot of standalone software that you may find useful when creating your map (these tools are not the same thing as Spigot plugins, but are great nonetheless). These applications are used outside of the Minecraft client and outside of your server, to manipulate and make changes to your world. When using these, make sure to create backups of your world in case something bad happens to your world. Here are a few of our favorites.

### MCEdit (Unified) <small style="vertical-align:4px"><b class="label label-primary">Essential</b>&nbsp;<b class="label label-info">Building</b>&nbsp;<b class="label label-info">World Management</b>&nbsp;<b class="label label-info">Tools</b></small>

MCEdit is a versatile map utility, designed for editing Minecraft maps. From making large scale changes, applying filters, to importing schematic files, MCEdit is an absolute must-have for all map makers.  It is most often used to [prune extra chunks from the region files](http://docs.oc.tc/guides/packaging/pruning_chunks) in order to reduce the overall size of the world file, which is something that must be done to all new map submissions.

We strongly recommend using MCEdit Unified over MCEdit 2.

<table>
    <tr>
        <td style="padding-right:30px"><b>Downloads:</b></td>
        <td><a href="https://www.mcedit-unified.net/">Website</a> • <a href="http://elemanser.com/filters.html">Filters</a></td>
    </tr>
    <tr>
        <td><b>Tutorials:</b></td>
        <td><a href="https://www.mcedit-unified.net/tutorial">Tutorial</a> • <a href="https://www.youtube.com/watch?v=Bpuq2LIUy1E">How to Use MCEdit</a> (video)</td>
    </tr>
</table>

### NBTExplorer <small style="vertical-align:4px"><b class="label label-info">Tools</b></small>

NBTExplorer is a tool used to edit NBT data present in all your world files. Only use this tool if you understand what you're doing, and always store a backup of the world you are editing.

<table>
    <tr>
        <td style="padding-right:30px"><b>Downloads:</b></td>
        <td><a href="https://github.com/jaquadro/NBTExplorer/releases">Releases</a> (Windows/Linux)  • <a href="https://www.minecraftforum.net/forums/mapping-and-modding-java-edition/minecraft-tools/1262665-nbtexplorer-nbt-editor-for-windows-and-mac">Releases</a> (Windows/Linux/Mac)</td>
    </tr>
</table>

### WorldPainter <small style="vertical-align:4px"><b class="label label-info">Building</b></small>

WorldPainter is an interactive Minecraft world builder which allows you to sculpt and mold the terrain to your exact liking with incredible ease. You can just raise landscapes, paint biomes, vegetation, rivers, cliffs, mountains, and so much more. Once finished you can export your [painted world](http://i.imgur.com/XN2NBBS.png) to a [Minecraft world](http://i.imgur.com/BKlu3tt.jpg) file with incredible results.

<table>
    <tr>
        <td style="padding-right:30px"><b>Downloads:</b></td>
        <td><a href="https://www.worldpainter.net/">Website</a></td>
    </tr>
    <tr>
        <td><b>Tutorials:</b></td>
        <td><a href="https://youtu.be/c6dULt6oEn0">World Painter Tutorial</a> (video)</td>
    </tr>
</table>

## **Web Tools**

### MCStacker <small style="vertical-align:4px"><b class="label label-info">Tools</b></small>

MCStacker allows you to create complex commands using an easy to use visual interface for such things as entity summoning or creating item spawners. Make sure you are using the generator version that corresponds to the Minecraft version that the server is running.

<table>
    <tr>
        <td style="padding-right:30px"><b>Website:</b></td>
        <td><a href="https://mcstacker.bimbimma.com/mcstacker1.10.php">mcstacker.bimbimma.com</a></td>
    </tr>
</table>

### Minecraft Heads <small style="vertical-align:4px"><b class="label label-info">Tools</b></small>

Minecraft Heads has an extensive database of both Mojang and custom heads which you can use to add extra details to your map, such as a flowerpot, bush, Kraken, candles, and so so much more. Search their database to find the head you want then use the premade give or setblock commands (for the appropriate server version you're using) to get the heads.

<table>
    <tr>
        <td style="padding-right:30px"><b>Website:</b></td>
        <td><a href="https://minecraft-heads.com/">minecraft-heads.com</a></td>
    </tr>
</table>

## **Final Notes**

There is a huge range of tools that you could use for map making, though these are the ones we feel are the most useful for new and experienced map makers. Don't feel bad if your first map doesn't turn out how you had hoped. We all start somewhere, and with enough practice you will only get better and some day create that amazing map.