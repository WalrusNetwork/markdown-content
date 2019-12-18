# **Convert your PGM map**

Former maps made for the 'PGM' (Pvp Game Manager) plugin use an XML and world format that won't quite work with the plugin which Walrus runs on.  This guide is intended for experienced map-makers who have maps previously made for PGM, on how they can convert their map to standards that work on our server.  PGM is also alluded to as Project Ares in this document (Ares maps ran under the PGM plugin).

Converting the XML will be covered first, followed by the Minecraft world conversion.

**You do not need to convert your map if it is in the repository.** The Map team handles maps currently in our repository. This guide is for you to take advantage of if you own a map that has not yet been submitted to us.

If at any point something doesn't quite make sense, or if you have further questions, please ask one of our Map team specialists in [Discord](https://discord.gg/eySJYEb).

- **[Converting The XML](#converting-the-xml)**
- **[XML Breakdown](#xml-breakdown)**
- **[XML Templates](#xml-templates)**
- **[Converting The Minecraft World](#converting-the-minecraft-world)**
- **[Final Notes](#final-notes)**


## **Converting The XML**

While the XML syntax used for PGM and our plugin are relatively similar, there are some fundamental differences that you will begin to notice as you start working with the new protocol.

You can find the documentation for XML code [here](https://docs.walrus.network/). Please note that many features are still being documented, so certain details may currently be missing. If something doesn't quite make sense, feel free to ask someone on our Map team for clarification.

### **Critical Changes**

These are the changes that are critically different in our XML verion, in comparison to PGM. This is not an exhaustive list of all the changes, but instead, are the main differences which we feel are the most important to bring your attention to as soon as possible.

Before you get stuck into that though, just some terminology. Module is the term that PGM used for a feature that a map could adopt in its XML, such as spawns, kits, wools, and so on. Our code uses the term _facet_ for these things instead as it makes more sense in terms of the overall internal infrastructure of the plugin. They mean the same thing.

#### **Kits**

The first largest changes that you will likely notice between is the way that kits are defined. Previously, there were a number of different syntaxes that you could use to create a kit, however, now there is only one. It is similar to how kits were defined in protocol 1.4+, but has some noticeable differences. A side by side comparison of the same kit for both of the protocols has been provided below to demonstrate the main differences.

<div class="row">
    <div class="col-md-6 col-sm-12">
        <div class="panel panel-danger">
            <div class="panel-heading"><b>Project Ares</b> <small>Protocol 1.4.0</small></div>
            <div class="panel-body">
                <pre style="padding:0;padding-bottom:4px;margin-bottom:0;font-size:8px;border:none;border-radius:0">
&lt;kit id=&quot;spawn-kit&quot;&gt;
    &lt;item slot=&quot;0&quot; material=&quot;iron sword&quot;/&gt;
    &lt;item slot=&quot;1&quot; material=&quot;bow&quot;&gt;
        &lt;enchantment&gt;arrow infinite&lt;/enchantment&gt;
    &lt;/item&gt;
    &lt;item slot=&quot;2&quot; enchantment=&quot;durability:3;dig speed:1&quot;&gt;iron pickaxe&lt;/item&gt;
    &lt;item slot=&quot;3&quot; enchantment=&quot;durability:3;dig speed:1&quot;&gt;iron axe&lt;/item&gt;
    &lt;item slot=&quot;4&quot; amount=&quot;64&quot; damage=&quot;2&quot;&gt;wood&lt;/item&gt;
    &lt;item slot=&quot;5&quot; amount=&quot;24&quot; lore=&quot;`5Use this iron to craft armor!&quot;&gt;iron ingot&lt;/item&gt;
    &lt;item slot=&quot;6&quot; amount=&quot;2&quot;&gt;golden apple&lt;/item&gt;
    &lt;item slot=&quot;7&quot; amount=&quot;64&quot;&gt;cooked fish&lt;/item&gt;
    &lt;item slot=&quot;8&quot;&gt;bucket&lt;/item&gt;
    &lt;item slot=&quot;28&quot;&gt;arrow&lt;/item&gt;
    &lt;item slot=&quot;31&quot; amount=&quot;32&quot;&gt;glass&lt;/item&gt;
    &lt;potion amplifier=&quot;3&quot; duration=&quot;5&quot;&gt;damage resistance&lt;/potion&gt;
&lt;/kit&gt;</pre>
            </div>
        </div>
    </div>
    <div class="col-md-6 col-sm-12">
        <div class="panel panel-success">
            <div class="panel-heading"><b>Walrus Plugin</b> <small>Protocol 2.0.0</small></div>
            <div class="panel-body">
                <pre style="padding:0;padding-bottom:4px;margin-bottom:0;font-size:8px;border:none;border-radius:0">
&lt;kit id=&quot;spawn-kit&quot;&gt;
    &lt;item slot=&quot;0&quot; material=&quot;iron sword&quot;/&gt;
    &lt;item slot=&quot;1&quot; material=&quot;bow&quot;&gt;
        &lt;enchantments&gt;
            &lt;enchantment&gt;arrow infinite&lt;/enchantment&gt;
        &lt;/enchantments&gt;
    &lt;/item&gt;
    &lt;item slot=&quot;2&quot; material=&quot;iron pickaxe&quot;&gt;
        &lt;enchantments&gt;
            &lt;enchantment level=&quot;3&quot;&gt;durability&lt;/enchantment&gt;
            &lt;enchantment&gt;dig speed&lt;/enchantment&gt;
        &lt;/enchantments&gt;
    &lt;/item&gt;
    &lt;item slot=&quot;3&quot; material=&quot;iron axe&quot;&gt;
        &lt;enchantments&gt;
            &lt;enchantment level=&quot;3&quot;&gt;durability&lt;/enchantment&gt;
            &lt;enchantment&gt;dig speed&lt;/enchantment&gt;
        &lt;/enchantments&gt;
    &lt;/item&gt;
    &lt;item slot=&quot;4&quot; material=&quot;wood&quot; amount=&quot;64&quot; damage=&quot;2&quot;/&gt;
    &lt;item slot=&quot;5&quot; material=&quot;iron ingot&quot; amount=&quot;24&quot;&gt;
        &lt;lore&gt;
            &lt;line&gt;^5Use this iron to craft armor!&lt;/line&gt;
        &lt;/lore&gt;
    &lt;/item&gt;
    &lt;item slot=&quot;6&quot; material=&quot;golden apple&quot; amount=&quot;2&quot;/&gt;
    &lt;item slot=&quot;7&quot; material=&quot;cooked fish&quot; amount=&quot;64&quot;/&gt;
    &lt;item slot=&quot;8&quot; material=&quot;bucket&quot;/&gt;
    &lt;item slot=&quot;28&quot; material=&quot;arrow&quot;/&gt;
    &lt;item slot=&quot;31&quot; material=&quot;glass&quot; amount=&quot;32&quot;/&gt;
    &lt;effect amplifier=&quot;3&quot; duration=&quot;5&quot;&gt;damage resistance&lt;/effect&gt;
&lt;/kit&gt;</pre>
            </div>
        </div>
    </div>
</div>

The differences between these XML snippets can be summarized by the following:

- An item's material is always defined through the `material="..."` attribute
- An enchantment is always a sub-element of an item, parented by `<enchantments/>`
    - This is also the case for `stored-enchantment`, `attribute`, and `effect`, each with their respective parents
- Item lore is now a sub-element instead of an attribute
    - Is defined with the `<lore>` element which each line being a `<line>` child
- Text formatting codes are now prefixed with `^` instead of the grave accent
- Potion effects always use `<effect>` instead of `<potion>`
- Item flag toggles (`show-enchantments`, `show-attributes`, `show-unbreakable`, `show-can-destroy`, and `show-can-place-on`) are now defined through a semicolon separated list of [bukkit item flags][1] in the `flags="..."` attribute
    - E.g. `flags="hide-attributes;hide-enchants"`

#### **Wools**

The location of wools has been replaced with the `source="..."` attribute, which is a bounded region covering the entire wool room. This aids in proximity while also automatically protecting any chests and spawners inside of the region. Additionally, any chests filled with wool inside of the source region will be automatically restocked with wool. The monument sub-element has been replaced with the `destination="..."` attribute which also requires a bounded region. This will most commonly just be a simple `<block>` region.

<div class="row">
    <div class="col-md-6 col-sm-12">
        <div class="panel panel-danger">
            <div class="panel-heading"><b>Project Aress</b> <small>Protocol 1.4.0</small></div>
            <div class="panel-body">
                <pre style="padding:0;padding-bottom:4px;margin-bottom:0;font-size:8px;border:none;border-radius:0">
&lt;wools&gt;
    &lt;wool team="blue-team" color="red" location="-169.5,10,69"&gt;
        &lt;monument&gt;
            &lt;block&gt;-242,7,1&lt;/block&gt;
        &lt;/monument&gt;
    &lt;/wool&gt;
    &lt;wool team="red-team" color="blue" location="-227.5,10,-28"&gt;
        &lt;monument&gt;
            &lt;block&gt;-156,7,39&lt;/block&gt;
        &lt;/monument&gt;
    &lt;/wool&gt;
&lt;/wools&gt;</pre>
            </div>
        </div>
    </div>
    <div class="col-md-6 col-sm-12">
        <div class="panel panel-success">
            <div class="panel-heading"><b>Walrus Plugin</b> <small>Protocol 2.0.0</small></div>
            <div class="panel-body">
                <pre style="padding:0;padding-bottom:4px;margin-bottom:0;font-size:8px;border:none;border-radius:0">
&lt;wools&gt;
    &lt;wool team=&quot;blue&quot; color=&quot;cyan&quot; source=&quot;cyan-woolroom&quot; destination=&quot;cyan-monument&quot;/&gt;
    &lt;wool team=&quot;red&quot; color=&quot;yellow&quot; source=&quot;yellow-woolroom&quot; destination=&quot;yellow-monument&quot;/&gt;
&lt;/wools&gt;
&lt;regions&gt;
    &lt;cuboid id=&quot;cyan-woolroom&quot; min=&quot;-17,0,66&quot; max=&quot;-37,25,79&quot;/&gt;
    &lt;block id=&quot;cyan-monument&quot;&gt;-2,10,-81&lt;/block&gt;
    &lt;cuboid id=&quot;yellow-woolroom&quot; min=&quot;17,0,-65&quot; max=&quot;37,25,-78&quot;/&gt;
    &lt;block id=&quot;yellow-monument&quot;&gt;1,10,81&lt;/block&gt;
&lt;/regions&gt;</pre>
            </div>
        </div>
    </div>
</div>

#### **Monument Modes**

Monument modes are now no longer limited to a single sequence and are more advanced in terms of _what_ is affected by a mode change. Instead of simply setting a core or monument to follow a sequence of modes, you can now define a specific `first-mode="..."` for each individual objective. In the example below, all cores have been given the first mode with the id `gold-core`, which will activate after 10 minutes. Based on the result of a filter, which defaults to `always`, the mode will either pass or fail. If the mode passes, the objective materials will change and the timer for the next `pass-mode="..."` will begin. In this case, the `glass-core` mode will activate 5 minutes after the `gold-core` mode passes. If the mode fails due to the filter returning deny, the mode will instead transform into the `fail-mode="..."` specified.

Another awesome change with monument modes is the ability to target specific materials in a multi-material objective. Say your monument is composed of both Emerald Blocks and Stained Clay. In Project Ares, both of these blocks changed when a monument mode was activated, however, in our plugin we can specify what we want each of these materials to individually transform into. In the example below, we are finding all the Obsidian Blocks in the core and changing them into Gold Blocks. Any other blocks that make up the core will be unaffected.

<div class="row">
    <div class="col-md-6 col-sm-12">
        <div class="panel panel-danger">
            <div class="panel-heading"><b>Project Ares</b> <small>Protocol 1.4.0</small></div>
            <div class="panel-body">
                <pre style="padding:0;padding-bottom:4px;margin-bottom:0;font-size:8px;border:none;border-radius:0">
&lt;cores mode-changes="true"/&gt;
&lt;modes&gt;
    &lt;mode after="10m" material="gold block" name="GOLD CORE MODE"/&gt;
    &lt;mode after="15m" material="glass" name="GLASS CORE MODE"/&gt;
&lt;/modes&gt;</pre>
            </div>
        </div>
    </div>
    <div class="col-md-6 col-sm-12">
        <div class="panel panel-success">
            <div class="panel-heading"><b>Walrus Plugin</b> <small>Protocol 2.0.0</small></div>
            <div class="panel-body">
                <pre style="padding:0;padding-bottom:4px;margin-bottom:0;font-size:8px;border:none;border-radius:0">

&lt;cores first-mode="gold-core"/&gt;
&lt;modes&gt;
    &lt;mode id="gold-core" pass-mode="glass-core" delay="10m" name="{mode.core.gold}"&gt;
        &lt;materials&gt;
            &lt;material find="obsidian" replace="gold block"/&gt;
        &lt;/materials&gt;
    &lt;/mode&gt;
    &lt;mode id="glass-core" delay="5m" name="{mode.core.glass}"&gt;
        &lt;materials&gt;
            &lt;material find="gold block" replace="glass"/&gt;
        &lt;/materials&gt;
    &lt;/mode&gt;
&lt;/modes&gt;</pre>
            </div>
        </div>
    </div>
</div>

While this example is for Cores, it works exactly the same for Monuments.

#### **Team Deathmatch**

All team deathmatch games automatically set the player to Adventure mode when playing. Usually, deathmatch maps do not have any block interaction, so this will be one less thing mapmakers will have to consider when making their XMLs. Block interaction can still be enabled by adding `<interactive>true</interactive>` to the XML if your map requires it.


#### **Score Is Only Used For Deathmatch**

Additionally, the `<score/>` facet is now only used for scoring in deathmatch games. In PGM, this module could be used for scoring in deathmatch, hills, flags, and much more. Each different game type now has its own way of measuring and limiting scores.

#### **Regions Cannot Use Infinite Coordinates**

This refers to the use of `oo` in region coordinates and bounds. Using `oo` is no longer allowed. Instead, unbound regions should be used in order to create the desired region coverage, with the help of region modifiers for more complex shapes and requirements.

#### **Applicators**

The application of filters to specific regions are no longer in the `<regions/>` element. In our plugin, this is exclusively used to define regions. Instead, you will use the new `<applicators/>` element in order to `<apply/>` filters to regions. Applying things to regions is the exact same as PGM's protocol 1.4.2 behavior.

<div class="row">
    <div class="col-md-6 col-sm-12">
        <div class="panel panel-danger">
            <div class="panel-heading"><b>Project Ares</b> <small>Protocol 1.4.0</small></div>
            <div class="panel-body">
                <pre style="padding:0;padding-bottom:4px;margin-bottom:0;font-size:8px;border:none;border-radius:0">
&lt;regions&gt;
    &lt;rectangle id="blue-spawn" min="-247,4" max="-236,-10"/&gt;
    &lt;rectangle id="red-spawn" min="-150,37" max="-161,51"/&gt;
    &lt;apply region="blue-spawn" enter="only-blue" message="You may not enter the other team's spawn"/&gt;
    &lt;apply region="red-spawn" enter="only-red" message="You may not enter the other team's spawn"/&gt;
&lt;/regions&gt;</pre>
            </div>
        </div>
    </div>
    <div class="col-md-6 col-sm-12">
        <div class="panel panel-success">
            <div class="panel-heading"><b>Walrus Plugin</b> <small>Protocol 2.0.0</small></div>
            <div class="panel-body">
                <pre style="padding:0;padding-bottom:4px;margin-bottom:0;font-size:8px;border:none;border-radius:0">
&lt;regions&gt;
    &lt;rectangle id="blue-spawn" min="-247,4" max="-236,-10"/&gt;
    &lt;rectangle id="red-spawn" min="-150,37" max="-161,51"/&gt;
&lt;/regions&gt;
&lt;applicators&gt;
    &lt;apply region="blue-spawn" enter="only-blue" message="{region.error.enter.enemy-spawn}"/&gt;
    &lt;apply region="red-spawn" enter="only-red" message="{region.error.enter.enemy-spawn}"/&gt;
&lt;/applicators&gt;</pre>
            </div>
        </div>
    </div>
</div>

#### **Translations**

A major component of the plugin is the attention given to standardization and translation. So, all strings in XMLs must now use translation keys where possible, for such things as applicator error messages, team names, and countdowns. While there is an entire [repository][2] filled with such translations ([CrowdIn page](https://crowdin.com/project/walrus-network)), our focus will be on [`maps.properties`][3] for map XMLs. Using these translation keys is as simple as substituting any string for `{the.translation.key}`. The following is a real example of how this can be used:

<pre>&lt;apply region="spawns" block="never" message="{region.error.modify.spawn}"/&gt;</pre>

In this situation, when a player tries to modify the `spawn` region, the `You cannot edit the spawn area!` message will be displayed to the player in the appropriate language for them. We have tried to cover as many scenarios as possible so that there should be a translation key for your requirements. However, if one doesn't quite suit your needs, please submit a pull request with the addition.

#### **Kill Rewards**

Kill rewards are basically the same as they are now with three differences. Firstly, `<kill-reward/>` element has been renamed to `<reward/>`, and this must always be parented by `<kill-rewards/>`. Secondly, effects no longer have to be inside of a `<kit/>` in order to be given through kill rewards. Rewards can still be awarded based off of a filter, however, the following example uses the new `team-color="..."` attribute, which is explained a little later, in order to simplify the kill rewards for this map. Lastly, the `<kill-streak/>` filter no longer exists. Instead, you must use the `after="..."` and `every="..."` attributes for `<reward>` in order to specify after how many kills the reward should be given to the player.

<div class="row">
    <div class="col-md-6 col-sm-12">
        <div class="panel panel-danger">
            <div class="panel-heading"><b>Project Ares</b> <small>Protocol 1.4.0</small></div>
            <div class="panel-body">
                <pre style="padding:0;padding-bottom:4px;margin-bottom:0;font-size:8px;border:none;border-radius:0">
&lt;kill-rewards&gt;
    &lt;kill-reward&gt;
        &lt;item material="wood" damage="1" amount="12" /&gt;
        &lt;item material="arrow" amount="12" /&gt;
        &lt;item material="golden apple" /&gt;
    &lt;/kill-reward&gt;
    &lt;kill-reward filter="only-blue"&gt;
        &lt;item material="stained clay" damage="11" amount="12" /&gt;
    &lt;/kill-reward&gt;
    &lt;kill-reward filter="only-red"&gt;
        &lt;item material="stained clay" damage="14" amount="12" /&gt;
    &lt;/kill-reward&gt;
    &lt;killreward&gt;
        &lt;filter&gt;
            &lt;kill-streak after=&quot;2&quot;/&gt;
        &lt;/filter&gt;
        &lt;item material=&quot;tnt&quot;/&gt;
    &lt;/killreward&gt;
&lt;/kill-rewards&gt;</pre>
            </div>
        </div>
    </div>
    <div class="col-md-6 col-sm-12">
        <div class="panel panel-success">
            <div class="panel-heading"><b>Walrus Plugin</b> <small>Protocol 2.0.0</small></div>
            <div class="panel-body">
                <pre style="padding:0;padding-bottom:4px;margin-bottom:0;font-size:8px;border:none;border-radius:0">
&lt;kill-rewards&gt;
    &lt;reward&gt;
        &lt;item material="wood" damage="1" amount="12"/&gt;
        &lt;item material="arrow" amount="12"/&gt;
        &lt;item material="golden apple"/&gt;
        &lt;item material="stained clay" team-color="true" amount="12"/&gt;
    &lt;/reward&gt;
    &lt;reward after="2"&gt;
        &lt;item material="tnt"/&gt;
    &lt;/reward&gt;
&lt;/kill-rewards&gt;</pre>
            </div>
        </div>
    </div>
</div>

#### **Item Remove, Repair, and Keep**

Item remove, repair, and keep have now been condensed into the new `<items/>` module. This module takes a filter based approach to either removing an item on drop, repairing an item, or allowing the player to keep it on death. While you can probably come up with some cool ways to use this, we have just provided an example of how to use this in a typical map.

<div class="row">
    <div class="col-md-6 col-sm-12">
        <div class="panel panel-danger">
            <div class="panel-heading"><b>Project Ares</b> <small>Protocol 1.4.0</small></div>
            <div class="panel-body">
                <pre style="padding:0;padding-bottom:4px;margin-bottom:0;font-size:8px;border:none;border-radius:0">
&lt;toolrepair&gt;
    &lt;tool&gt;diamond sword&lt;/tool&gt;
    &lt;tool&gt;bow&lt;/tool&gt;
    &lt;tool&gt;iron pickaxe&lt;/tool&gt;
    &lt;tool&gt;arrow&lt;/tool&gt;
&lt;/toolrepair&gt;
&lt;itemremove&gt;
    &lt;item&gt;obsidian&lt;/item&gt;
    &lt;item&gt;gold block&lt;/item&gt;
    &lt;item&gt;smooth brick&lt;/item&gt;
    &lt;item&gt;glass&lt;/item&gt;
    &lt;item&gt;ladder&lt;/item&gt;
    &lt;item&gt;ender stone&lt;/item&gt;
    &lt;item&gt;arrow&lt;/item&gt;
    &lt;item&gt;golden carrot&lt;/item&gt;
    &lt;item&gt;wood&lt;/item&gt;
&lt;/itemremove&gt;</pre>
            </div>
        </div>
    </div>
    <div class="col-md-6 col-sm-12">
        <div class="panel panel-success">
            <div class="panel-heading"><b>Walrus Plugin</b> <small>Protocol 2.0.0</small></div>
            <div class="panel-body">
                <pre style="padding:0;padding-bottom:4px;margin-bottom:0;font-size:8px;border:none;border-radius:0">
&lt;items&gt;
    &lt;repair&gt;
        &lt;any&gt;
            &lt;material&gt;diamond sword&lt;/material&gt;
            &lt;material&gt;bow&lt;/material&gt;
            &lt;material&gt;iron pickaxe&lt;/material&gt;
            &lt;material&gt;arrow&lt;/material&gt;
        &lt;/any&gt;
    &lt;/repair&gt;
    &lt;remove&gt;
        &lt;any&gt;
            &lt;material&gt;obsidian&lt;/material&gt;
            &lt;material&gt;gold block&lt;/material&gt;
            &lt;material&gt;smooth brick&lt;/material&gt;
            &lt;material&gt;glass&lt;/material&gt;
            &lt;material&gt;ladder&lt;/material&gt;
            &lt;material&gt;ender stone&lt;/material&gt;
            &lt;material&gt;arrow&lt;/material&gt;
            &lt;material&gt;golden carrot&lt;/material&gt;
            &lt;material&gt;wood&lt;/material&gt;
        &lt;/any&gt;
    &lt;/remove&gt;
&lt;/items&gt;</pre>
            </div>
        </div>
    </div>
</div>

#### **Explicit Game Type Definition**

The game type for the map now needs to be explicitly defined at the top of the XML. This can be done through the `<game>...</game>` element and will contain game abbreviations like `ctw`, `dtm`, and so on.

#### **More Attributes, Less Sub-Elements**

In PGM, there were a lot of ways to define the exact same thing. One example is that you could define a region for many modules either through the `region="..."` attribute or a `<region>...</region>` sub-element. We've opted to use an element attribute as much as possible, meaning that the sub-element way is no longer supported. There are too many facets that this affects to list here, but you will begin to figure it out as you go through an XML.

#### **Other Major Changes**

Other major changes include how the Flags and Hills game will be defined in XML. These game are still being designed so we cannot share how you can convert them at this time. Stay tuned.


### **Useful Additions**

This is a brief list of new features which we offer, that were not present or possible in PGM. While these don't exactly relate to allowing your map to be used, they are either exceptionally cool or can make your life a little easier when creating the XML for your map.

#### **Automatic Material Coloring**

Gone are the days where you have to define a bajillion different kits just to provide items with their respective colors to specific teams. You can now simply add the `team-color="true"` attribute to _any_ material that has different color variations and those items will be automagically colored when applied to the player!

#### **Cardinal Directions**

When defining the `yaw="..."` for such facets as spawns, you can now use the cardinal directions instead of the angle in degrees. For example, instead of defining `yaw="-90"`, you can now do `yaw="east"`. Additionally, you can also use `south west` for a 45-degree angle, or `south south west` for a 22.5-degree angle. Pitch still only uses the angle in degrees.

#### **Water Cores**

Cores can now have water in them instead of lava. The liquid inside a core is automatically detected by the plugin and requires no additional configuration.

#### **Spawners**

You can now configure virtual item and effect spawners through the map's XML.

  [1]: https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/inventory/ItemFlag.html
  [2]: https://gitlab.com/WalrusNetwork/ux-ui/translations
  [3]: https://gitlab.com/WalrusNetwork/ux-ui/translations/blob/master/en_US/games/octc/maps.properties

  
## **XML Breakdown**

Here is a comparison of the XML for the map _Dry Outpost_:

<div class="row">
    <div class="col-md-6 col-sm-12">
        <div class="panel panel-danger">
            <div class="panel-heading"><b>Project Ares</b> <small>Protocol 1.4.2</small></div>
            <div class="panel-body">
                <pre style="padding:0;padding-bottom:4px;margin-bottom:0;font-size:8px;border:none;border-radius:0">
&lt;map proto=&quot;1.4.2&quot;&gt;
&lt;name&gt;Dry Outpost&lt;/name&gt;
&lt;version&gt;1.0.2&lt;/version&gt;

&lt;objective&gt;Capture the wool and return it to your victory monument&lt;/objective&gt;
&lt;authors&gt;
    &lt;author uuid=&quot;f690a591-348b-482e-a18d-7779d0c0a28c&quot;/&gt; &lt;!-- mitchiii_ --&gt;
&lt;/authors&gt;
&lt;teams&gt;
    &lt;team id=&quot;blue-team&quot; color=&quot;blue&quot; max=&quot;4&quot; max-overfill=&quot;5&quot;&gt;Blue&lt;/team&gt;
    &lt;team id=&quot;red-team&quot; color=&quot;dark red&quot; max=&quot;4&quot; max-overfill=&quot;5&quot;&gt;Red&lt;/team&gt;
&lt;/teams&gt;
&lt;time&gt;20m&lt;/time&gt;
&lt;kits&gt;
    &lt;kit id=&quot;main-kit&quot;&gt;
        &lt;clear/&gt;
        &lt;item slot=&quot;0&quot; unbreakable=&quot;true&quot; material=&quot;stone sword&quot;/&gt;
        &lt;item slot=&quot;1&quot; unbreakable=&quot;true&quot; material=&quot;bow&quot;/&gt;
        &lt;item slot=&quot;2&quot; unbreakable=&quot;true&quot; material=&quot;stone pickaxe&quot;/&gt;
        &lt;item slot=&quot;3&quot; unbreakable=&quot;true&quot; material=&quot;stone axe&quot;/&gt;
        &lt;item slot=&quot;4&quot; amount=&quot;48&quot; material=&quot;wood&quot; damage=&quot;4&quot;/&gt;
        &lt;item slot=&quot;8&quot; amount=&quot;64&quot; material=&quot;golden carrot&quot;/&gt;
        &lt;item slot=&quot;28&quot; amount=&quot;36&quot; material=&quot;arrow&quot;/&gt;
        &lt;chestplate unbreakable=&quot;true&quot; material=&quot;chainmail chestplate&quot;/&gt;
        &lt;boots unbreakable=&quot;true&quot; material=&quot;iron boots&quot;/&gt;
        &lt;effect duration=&quot;3&quot; amplifier=&quot;10&quot;&gt;resistance&lt;/effect&gt;
    &lt;/kit&gt;
    &lt;kit id=&quot;blue-kit&quot; parents=&quot;main-kit&quot;&gt;
        &lt;item slot=&quot;5&quot; amount=&quot;36&quot; damage=&quot;11&quot; material=&quot;stained clay&quot;/&gt;
        &lt;helmet unbreakable=&quot;true&quot; color=&quot;0066cc&quot; material=&quot;leather helmet&quot;/&gt;
        &lt;leggings unbreakable=&quot;true&quot; color=&quot;0066cc&quot; material=&quot;leather leggings&quot;/&gt;
    &lt;/kit&gt;
    &lt;kit id=&quot;red-kit&quot; parents=&quot;main-kit&quot;&gt;
        &lt;item slot=&quot;5&quot; amount=&quot;36&quot; damage=&quot;14&quot; material=&quot;stained clay&quot;/&gt;
        &lt;helmet unbreakable=&quot;true&quot; color=&quot;cd0000&quot; material=&quot;leather helmet&quot;/&gt;
        &lt;leggings unbreakable=&quot;true&quot; color=&quot;cd0000&quot; material=&quot;leather leggings&quot;/&gt;
    &lt;/kit&gt;
&lt;/kits&gt;
&lt;spawns&gt;
    &lt;default region=&quot;default-spawn&quot; yaw=&quot;0&quot;/&gt;
    &lt;spawn team=&quot;blue-team&quot; kit=&quot;blue-kit&quot;&gt;
        &lt;regions&gt;
            &lt;point yaw=&quot;-90&quot;&gt;-258.5,7.5,-116.5&lt;/point&gt;
        &lt;/regions&gt;
    &lt;/spawn&gt;
    &lt;spawn team=&quot;red-team&quot; kit=&quot;red-kit&quot;&gt;
        &lt;regions&gt;
            &lt;point yaw=&quot;90&quot;&gt;-166.5,7.5,-116.5&lt;/point&gt;
        &lt;/regions&gt;
    &lt;/spawn&gt;
&lt;/spawns&gt;




&lt;filters&gt;
    &lt;team id=&quot;only-blue&quot;&gt;blue-team&lt;/team&gt;
    &lt;team id=&quot;only-red&quot;&gt;red-team&lt;/team&gt;
    &lt;not id=&quot;deny-void&quot;&gt;
        &lt;void/&gt;
    &lt;/not&gt;
    &lt;any id=&quot;wool-room-blacklist&quot;&gt;
        &lt;material&gt;chest&lt;/material&gt;
        &lt;material&gt;redstone wire&lt;/material&gt;
        &lt;material&gt;redstone torch on&lt;/material&gt;
    &lt;/any&gt;
    &lt;not id=&quot;deny-blue-wool-room&quot;&gt;
        &lt;any&gt;
            &lt;filter id=&quot;only-blue&quot;/&gt;
            &lt;filter id=&quot;wool-room-blacklist&quot;/&gt;
        &lt;/any&gt;
    &lt;/not&gt;
    &lt;not id=&quot;deny-red-wool-room&quot;&gt;
        &lt;any&gt;
            &lt;filter id=&quot;only-red&quot;/&gt;
            &lt;filter id=&quot;wool-room-blacklist&quot;/&gt;
        &lt;/any&gt;
    &lt;/not&gt;
&lt;/filters&gt;
&lt;regions&gt;
    &lt;block id=&quot;default-spawn&quot;&gt;-212.5,5,-152.5&lt;/block&gt;
    &lt;rectangle id=&quot;blue-spawn&quot; min=&quot;-261,-113&quot; max=&quot;-237,-121&quot;/&gt;
    &lt;rectangle id=&quot;red-spawn&quot; min=&quot;-164,-113&quot; max=&quot;-188,-121&quot;/&gt;
    &lt;rectangle id=&quot;blue-wool&quot; min=&quot;-231,-164&quot; max=&quot;-219,-152&quot;/&gt;
    &lt;rectangle id=&quot;red-wool&quot; min=&quot;-194,-152&quot; max=&quot;-206,-164&quot;/&gt;
    &lt;rectangle id=&quot;middle-wall&quot; min=&quot;-219,-164&quot; max=&quot;-206,-145&quot;/&gt;
    &lt;apply region=&quot;middle-wall&quot; block=&quot;never&quot; message=&quot;You may not modify this area&quot;/&gt;
    &lt;apply region=&quot;middle-wall&quot; enter=&quot;never&quot; message=&quot;You may not cross this area&quot;/&gt;
    &lt;apply region=&quot;blue-spawn&quot; enter=&quot;only-blue&quot; message=&quot;You may not enter the other team's spawn&quot;/&gt;
    &lt;apply region=&quot;blue-spawn&quot; block=&quot;never&quot; message=&quot;You may not modify the spawn area&quot;/&gt;
    &lt;apply region=&quot;red-spawn&quot; enter=&quot;only-red&quot; message=&quot;You may not enter the other team's spawn&quot;/&gt;
    &lt;apply region=&quot;red-spawn&quot; block=&quot;never&quot; message=&quot;You may not modify the spawn area&quot;/&gt;
    &lt;apply region=&quot;blue-wool&quot; enter=&quot;only-red&quot; block=&quot;deny-blue-wool-room&quot; use=&quot;only-red&quot; message=&quot;You may not do that in this woolroom&quot;/&gt;
    &lt;apply region=&quot;red-wool&quot; enter=&quot;only-blue&quot; block=&quot;deny-red-wool-room&quot; use=&quot;only-blue&quot; message=&quot;You may not do that in this woolroom&quot;/&gt;
    &lt;apply block-place=&quot;deny-void&quot; message=&quot;You may not interact with that material here&quot;/&gt;
&lt;/regions&gt;



&lt;maxbuildheight&gt;17&lt;/maxbuildheight&gt;
&lt;wools&gt;
    &lt;wool team=&quot;blue-team&quot; color=&quot;red&quot; location=&quot;-199.5,4,-158&quot;&gt;
        &lt;monument&gt;
            &lt;block&gt;-254.5,6,-116.5&lt;/block&gt;
        &lt;/monument&gt;
    &lt;/wool&gt;
    &lt;wool team=&quot;red-team&quot; color=&quot;blue&quot; location=&quot;-225.5,4,-158&quot;&gt;
        &lt;monument&gt;
            &lt;block&gt;-170.5,6,-116.5&lt;/block&gt;
        &lt;/monument&gt;
    &lt;/wool&gt;
&lt;/wools&gt;
&lt;kill-rewards&gt;
    &lt;kill-reward&gt;
        &lt;item amount=&quot;12&quot; material=&quot;wood&quot; damage=&quot;4&quot;/&gt;
        &lt;item amount=&quot;12&quot; material=&quot;arrow&quot;/&gt;
        &lt;item material=&quot;golden apple&quot;/&gt;
    &lt;/kill-reward&gt;
    &lt;kill-reward filter=&quot;only-blue&quot;&gt;
        &lt;item amount=&quot;12&quot; damage=&quot;11&quot; material=&quot;stained clay&quot;/&gt;
    &lt;/kill-reward&gt;
    &lt;kill-reward filter=&quot;only-red&quot;&gt;
        &lt;item amount=&quot;12&quot; damage=&quot;14&quot; material=&quot;stained clay&quot;/&gt;
    &lt;/kill-reward&gt;
    &lt;kill-reward&gt;
        &lt;filter&gt;
            &lt;kill-streak count=&quot;6&quot; repeat=&quot;false&quot;/&gt;
        &lt;/filter&gt;
        &lt;item damage=&quot;61&quot; material=&quot;flint and steel&quot;/&gt;
        &lt;item amount=&quot;2&quot; material=&quot;golden apple&quot;/&gt;
    &lt;/kill-reward&gt;
    &lt;kill-reward&gt;
        &lt;filter&gt;
            &lt;kill-streak count=&quot;8&quot; repeat=&quot;true&quot;/&gt;
        &lt;/filter&gt;
        &lt;item amount=&quot;1&quot; material=&quot;tnt&quot;/&gt;
    &lt;/kill-reward&gt;
&lt;/kill-rewards&gt;
&lt;toolrepair&gt;
    &lt;tool&gt;bow&lt;/tool&gt;
&lt;/toolrepair&gt;
&lt;itemremove&gt;
    &lt;item&gt;stone sword&lt;/item&gt;
    &lt;item&gt;stone pickaxe&lt;/item&gt;
    &lt;item&gt;stone axe&lt;/item&gt;
    &lt;item&gt;stained clay&lt;/item&gt;
    &lt;item&gt;golden carrot&lt;/item&gt;
    &lt;item&gt;leather helmet&lt;/item&gt;
    &lt;item&gt;chainmail chestplate&lt;/item&gt;
    &lt;item&gt;leather leggings&lt;/item&gt;
    &lt;item&gt;iron boots&lt;/item&gt;
    &lt;item&gt;seeds&lt;/item&gt;
    &lt;item&gt;sapling&lt;/item&gt;
    &lt;item&gt;apple&lt;/item&gt;
    &lt;item&gt;arrow&lt;/item&gt;
    &lt;item&gt;string&lt;/item&gt;
&lt;/itemremove&gt;
&lt;itemkeep&gt;
    &lt;item&gt;wood&lt;/item&gt;
&lt;/itemkeep&gt;
&lt;/map&gt;
</pre>
            </div>
        </div>
    </div>
    <div class="col-md-6 col-sm-12">
        <div class="panel panel-success">
            <div class="panel-heading"><b>Walrus Plugin</b> <small>Protocol 2.0.0</small></div>
            <div class="panel-body">
                <pre style="padding:0;padding-bottom:4px;margin-bottom:0;font-size:8px;border:none;border-radius:0">
&lt;map proto=&quot;2.0.0&quot;&gt;
&lt;name&gt;Dry Outpost&lt;/name&gt;
&lt;version&gt;1.0.1&lt;/version&gt;
&lt;game&gt;ctw&lt;/game&gt;
&lt;objective&gt;Capture the wool and return it to your victory monument&lt;/objective&gt;
&lt;authors&gt;
    &lt;author uuid=&quot;f690a591-348b-482e-a18d-7779d0c0a28c&quot;/&gt; &lt;!-- mitchiii_ --&gt;
&lt;/authors&gt;
&lt;teams&gt;
    &lt;team color=&quot;blue&quot; max=&quot;4&quot; max-overfill=&quot;5&quot;&gt;Blue&lt;/team&gt;
    &lt;team color=&quot;red&quot; max=&quot;4&quot; max-overfill=&quot;5&quot;&gt;Red&lt;/team&gt;
&lt;/teams&gt;
&lt;time-limit&gt;20m&lt;/time-limit&gt;
&lt;kits&gt;
    &lt;kit id=&quot;spawn-kit&quot;&gt;
        &lt;clear/&gt;
        &lt;item slot=&quot;0&quot; unbreakable=&quot;true&quot; material=&quot;stone sword&quot;/&gt;
        &lt;item slot=&quot;1&quot; unbreakable=&quot;true&quot; material=&quot;bow&quot;/&gt;
        &lt;item slot=&quot;2&quot; unbreakable=&quot;true&quot; material=&quot;stone pickaxe&quot;/&gt;
        &lt;item slot=&quot;3&quot; unbreakable=&quot;true&quot; material=&quot;stone axe&quot;/&gt;
        &lt;item slot=&quot;4&quot; amount=&quot;48&quot; material=&quot;wood&quot; damage=&quot;4&quot;/&gt;
        &lt;item slot=&quot;5&quot; amount=&quot;36&quot; team-color=&quot;true&quot; material=&quot;stained clay&quot;/&gt;
        &lt;item slot=&quot;8&quot; amount=&quot;64&quot; material=&quot;golden carrot&quot;/&gt;
        &lt;item slot=&quot;28&quot; amount=&quot;36&quot; material=&quot;arrow&quot;/&gt;
        &lt;chestplate unbreakable=&quot;true&quot; material=&quot;chainmail chestplate&quot;/&gt;
        &lt;boots unbreakable=&quot;true&quot; material=&quot;iron boots&quot;/&gt;
        &lt;helmet unbreakable=&quot;true&quot; team-color=&quot;true&quot; material=&quot;leather helmet&quot;/&gt;
        &lt;leggings unbreakable=&quot;true&quot; team-color=&quot;true&quot; material=&quot;leather leggings&quot;/&gt;
        &lt;effect duration=&quot;3&quot; amplifier=&quot;10&quot;&gt;damage resistance&lt;/effect&gt;
    &lt;/kit&gt;
&lt;/kits&gt;







&lt;spawns&gt;
    &lt;default yaw=&quot;0&quot;&gt;
        &lt;region&gt;
            &lt;block&gt;-212.5,5,-152.5&lt;/block&gt;
        &lt;/region&gt;
    &lt;/default&gt;
    &lt;spawn team=&quot;blue&quot; kit=&quot;spawn-kit&quot;&gt;
        &lt;region&gt;
            &lt;point yaw=&quot;-90&quot;&gt;-258.5,7.5,-116.5&lt;/point&gt;
        &lt;/region&gt;
    &lt;/spawn&gt;
    &lt;spawn team=&quot;red&quot; kit=&quot;spawn-kit&quot;&gt;
        &lt;region&gt;
            &lt;point yaw=&quot;90&quot;&gt;-166.5,7.5,-116.5&lt;/point&gt;
        &lt;/region&gt;
    &lt;/spawn&gt;
&lt;/spawns&gt;
&lt;filters&gt;
    &lt;team id=&quot;only-blue&quot;&gt;blue&lt;/team&gt;
    &lt;team id=&quot;only-red&quot;&gt;red&lt;/team&gt;
    &lt;not id=&quot;deny-void&quot;&gt;
        &lt;void/&gt;
    &lt;/not&gt;
    &lt;any id=&quot;wool-room-blacklist&quot;&gt;
        &lt;material&gt;chest&lt;/material&gt;
        &lt;material&gt;redstone wire&lt;/material&gt;
        &lt;material&gt;redstone torch on&lt;/material&gt;
    &lt;/any&gt;
    &lt;not id=&quot;deny-blue-wool-room&quot;&gt;
        &lt;any&gt;
            &lt;filter id=&quot;only-blue&quot;/&gt;
            &lt;filter id=&quot;wool-room-blacklist&quot;/&gt;
        &lt;/any&gt;
    &lt;/not&gt;
    &lt;not id=&quot;deny-red-wool-room&quot;&gt;
        &lt;any&gt;
            &lt;filter id=&quot;only-red&quot;/&gt;
            &lt;filter id=&quot;wool-room-blacklist&quot;/&gt;
        &lt;/any&gt;
    &lt;/not&gt;
&lt;/filters&gt;
&lt;regions&gt;
    &lt;block id=&quot;red-wool&quot;&gt;-254.5,6,-116.5&lt;/block&gt;
    &lt;block id=&quot;blue-wool&quot;&gt;-170.5,6,-116.5&lt;/block&gt;
    &lt;rectangle id=&quot;blue-spawn&quot; min=&quot;-261,-113&quot; max=&quot;-237,-121&quot;/&gt;
    &lt;rectangle id=&quot;red-spawn&quot; min=&quot;-164,-113&quot; max=&quot;-188,-121&quot;/&gt;
    &lt;rectangle id=&quot;blue-wool-room&quot; min=&quot;-231,-164&quot; max=&quot;-219,-152&quot;/&gt;
    &lt;rectangle id=&quot;red-wool-room&quot; min=&quot;-194,-152&quot; max=&quot;-206,-164&quot;/&gt;
    &lt;rectangle id=&quot;middle-wall&quot; min=&quot;-219,-164&quot; max=&quot;-206,-145&quot;/&gt;
&lt;/regions&gt;
&lt;applicators&gt;
    &lt;apply region=&quot;middle-wall&quot; block=&quot;never&quot; message=&quot;You may not modify this area&quot;/&gt;
    &lt;apply region=&quot;middle-wall&quot; enter=&quot;never&quot; message=&quot;You may not cross this area&quot; /&gt;
    &lt;apply region=&quot;blue-spawn&quot; enter=&quot;only-blue&quot; message=&quot;You may not enter the other team's spawn&quot;/&gt;
    &lt;apply region=&quot;blue-spawn&quot; block=&quot;never&quot; message=&quot;You may not modify the spawn area&quot;/&gt;
    &lt;apply region=&quot;red-spawn&quot; enter=&quot;only-red&quot; message=&quot;You may not enter the other team's spawn&quot;/&gt;
    &lt;apply region=&quot;red-spawn&quot; block=&quot;never&quot; message=&quot;You may not modify the spawn area&quot;/&gt;
    &lt;apply region=&quot;blue-wool-room&quot; enter=&quot;only-red&quot; block=&quot;deny-blue-wool-room&quot; use=&quot;only-red&quot; message=&quot;You may not do that in this woolroom&quot;/&gt;
    &lt;apply region=&quot;red-wool-room&quot; enter=&quot;only-blue&quot; block=&quot;deny-red-wool-room&quot; use=&quot;only-blue&quot; message=&quot;You may not do that in this woolroom&quot;/&gt;
    &lt;apply block-place=&quot;deny-void&quot; region=&quot;everywhere&quot; message=&quot;You may not interact with that material here&quot;/&gt;
&lt;/applicators&gt;
&lt;max-build-height&gt;17&lt;/max-build-height&gt;
&lt;wools&gt;
    &lt;wool team=&quot;blue&quot; color=&quot;red&quot; destination=&quot;red-wool&quot; source=&quot;red-wool-room&quot;/&gt;
    &lt;wool team=&quot;red&quot; color=&quot;blue&quot; destination=&quot;blue-wool&quot; source=&quot;blue-wool-room&quot;/&gt;
&lt;/wools&gt;








&lt;kill-rewards&gt;
    &lt;reward&gt;
        &lt;item amount=&quot;12&quot; material=&quot;wood&quot; damage=&quot;4&quot;/&gt;
        &lt;item amount=&quot;12&quot; material=&quot;arrow&quot;/&gt;
        &lt;item material=&quot;golden apple&quot;/&gt;
        &lt;item amount=&quot;12&quot; team-color=&quot;true&quot; material=&quot;stained clay&quot;/&gt;
    &lt;/reward&gt;
    &lt;reward after=&quot;6&quot;&gt;
        &lt;item damage=&quot;61&quot; material=&quot;flint and steel&quot;/&gt;
        &lt;item amount=&quot;2&quot; material=&quot;golden apple&quot;/&gt;
    &lt;/reward&gt;
    &lt;reward every=&quot;8&quot;&gt;
        &lt;item amount=&quot;1&quot; material=&quot;tnt&quot;/&gt;
    &lt;/reward&gt;
&lt;/kill-rewards&gt;











&lt;items&gt;
    &lt;repair&gt;
        &lt;any&gt;
            &lt;material&gt;bow&lt;/material&gt;
        &lt;/any&gt;
    &lt;/repair&gt;
    &lt;remove&gt;
        &lt;any&gt;
            &lt;material&gt;stone sword&lt;/material&gt;
            &lt;material&gt;stone pickaxe&lt;/material&gt;
            &lt;material&gt;stone axe&lt;/material&gt;
            &lt;material&gt;stained clay&lt;/material&gt;
            &lt;material&gt;golden carrot&lt;/material&gt;
            &lt;material&gt;leather helmet&lt;/material&gt;
            &lt;material&gt;chainmail chestplate&lt;/material&gt;
            &lt;material&gt;leather leggings&lt;/material&gt;
            &lt;material&gt;iron boots&lt;/material&gt;
            &lt;material&gt;seeds&lt;/material&gt;
            &lt;material&gt;sapling&lt;/material&gt;
            &lt;material&gt;apple&lt;/material&gt;
            &lt;material&gt;arrow&lt;/material&gt;
            &lt;material&gt;string&lt;/material&gt;
        &lt;/any&gt;
    &lt;/remove&gt;
    &lt;keep&gt;
        &lt;any&gt;
            &lt;material&gt;wood&lt;/material&gt;
        &lt;/any&gt;
    &lt;/keep&gt;
&lt;/items&gt;
&lt;/map&gt;
</pre>
            </div>
        </div>
    </div>
</div>


## **XML Templates**

We understand that learning the XML protocol is tough for a lot of people, so we have created detailed templates for all the game types for a typical map. For specialized requirements, we would advise consulting the documentation or asking one of our Map team specialists.

**You can find each of the templates [here](https://docs.walrus.network/examples/templates).** More templates will be added as more game types are supported and more features are released.

Additionally, we plan to have a section with complex XML snippets for specific use cases which you will be able to copy into your own XML configurations.


## **Converting The Minecraft World**

With each new version of Minecraft, there are often changes made to the way entity and tile entity NBT is stored. Because of this, maps created or loaded in newer versions of Minecraft will contain entities and tile entities that Minecraft 1.8 does not understand. This either results in them being broken or simply not existing when the world is loaded.

However, we have created an extremely basic script which will convert most NBT structures to be Minecraft 1.8 compatible. Please note that this script will only work if the map was created in Minecraft versions 1.9 through to 1.12.2. Worlds created in Minecraft 1.13 and above will not work.

1. Install [Python][4] (version 3.4 to 3.7, or 2.7)
2. Clone the [nbt-converter][5] repository
    - You can download it, however, you will have to redownload it each time a change is made in comparison to running `git pull` in the command line
3. Open your command line and navigate to the nbt-converter folder
4. Run `python converter.py "<path to world folder>" `
    - If the python command cannot be found, make sure that you have added Python to your system variables
    - Any blocks used that were added in Minecraft 1.9 and after will be attempted to be converted to something similar, but may not always be perfect

When you run the script you will see summaries of the changes being made in each chunk. Once the script has finished running, the world can now be used in Minecraft 1.8 without losing any important NBT data. Also, please note that not everything is converted with this script. You can see what is currently converted by looking at [the README file in the GitHub repository][6].

Our NBT converter cannot convert worlds saved in versions beyond Minecraft 1.12.2, but there are other tools such as [Minecraft-Tools][7] which has the capability to convert worlds saved in Minecraft 1.13 (and potentially 1.14 in the future) to Minecraft 1.12. From here you can then use our own converter to convert the save to Minecraft 1.8, so that it may be used on our servers.


  [4]: https://www.python.org/downloads/
  [5]: https://github.com/mitchiiii/nbt-converter
  [6]: https://github.com/mitchiiii/nbt-converter/blob/master/README.md
  [7]: https://github.com/Jupisoft111/Minecraft-Tools


## **Final Notes**

There is a _huge_ amount of information to take in in this thread, and it's completely okay if you are unable to. It has taken the Map team months to become familiar with everything and we are still learning everything that is new. This thread will be updated as new features come out and we ourselves gain more experience with everything. We can only encourage you to try your hand at the new XML protocol and see how you do as that's the best way to learn it right now.

If you would like to try converting a map, have a go at converting the XML for [Covert Fortress](https://gist.github.com/mitchts/b90707d72e3c3bb3e624780664ad1484). When you're ready, you can then compare what you have done to [what we produced](https://gist.github.com/mitchts/a2dac81bf0eeedf25c4553515cccf121) in order to track how you're doing.

If you have any questions regarding any part of this thread or map making in general, please reach out to someone on our Map team (you may reach out to our staff from our public [Discord](https://discord.gg/eySJYEb)), and we will try our best to answer your questions.