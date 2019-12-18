# **Create a void world**

Now that you've set up your server with the proper tools, we need to create a void world with a single block inside of it, so that your map can benefit from the void that all maps have in common.

We'll use Multiverse Core to create the void world.  As a server operator (`/op` yourself from your server console), run `/mv create <worldname> normal -g VoidGenerator:. -t FLAT`.

This will generate the void world.  To teleport to the world, use `/mv tp <worldname>`.

See the [Multiverse Core GitHub project page](https://github.com/Multiverse/Multiverse-Core/wiki/Command-Reference) for a full list of `mv` commands.