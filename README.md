# TextDF
TextDF is a way of expressing the DiamondFire code system in text formatting.

### Methods
  
  * PlayerEvent [] - When the player does something...
    * Join - When a player joins the plot.
    * Quit - When a player leaves the game.
    * RightClick - When a player right clicks.
    * LeftClick - When a player left clicks.
    * Respawn - When a player respawns after dying.
    * PlayKillPlay - When a player kills another player.
    * PlayDeath - When a player dies (not by another player)
    * Sneak - When a player sneaks.
    * Unsneak - When a player stops sneaking.
    * PlayDamagePlay - When a player damages another player.
    * ProjDamagePlay - When a projectile hits a player.
    * PlayDamage - When a player takes damage.
    * PlayKillMob - When a player kills a mob.
    * MobKillPlay -When a mob kills a player.
    * PlayDamageMob - When a player damages a mob.
    * MobDamagePlay - When a mob damages a player.
    * ProjHit - When a projectile hits something.
    * Command - When a player does a command.
    * ClickItem - When a player clicks an item in an inventory menu.
    * ClickItemOwn - When a player clicks an item inside their inventory.
    * RightClickEntity - When a player right clicks an entity.
    * PlaceBlock - When a player places a block.
    * BreakBlock - When a player breaks a block.
    * PickItem - When a player picks up an item.
    * DropItem - When a player drops an item.
    * ConsumeItem - When a player eats/drinks an item.
    * SwapHands - When a player swaps held items.
    * ChangeSlot - When a player changes their held slot.
    * Sprint - When a player starts sprinting.
    * StopSprint - When a player stops sprinting.
    * Walk - When a player walks.
    * FallDamage - When a player takes fall damage.
  * PlayerAction [] - Do something to the player.
    * GiveItem - Give a player an item(s). (Item(s))
    * SetItem - Give a player an item(s) in direct slots. (Item, Item, Ect)
    * SetArmor - Equips the set of armor to the player. (Item, Item, Item, Item)
    * SetOffHand - Sets an item in the player's offhand. (Item)
    * RemoveItem - Removes an item(s) from the player's inventory. (Item(s))
    * ClearInventory - Clears the player inventory.
    * ShowMenu - Opens an inventory menu. (Item(s));
    * CloseMenu - Closes an open inventory menu.
    * ExpandMenu - Expands an open inventory menu. (Item(s))
    * SaveInventory - Saves the player's inventory to a stored value.
    * LoadInventory - Loads the player's inventory from a stored value.
    * SetSlot - Sets the player's currently selected slot. (Number)
    * GiveRandomItem - Gives a player a random item. (Item(s))
    * SendMessage - Sends a message to the targeted player. (Text)
    * SendDialogue - Sends a series of messages to the targeted player. (Text, Number)
    * SendHover - Sends a message with hover text. (Text, Text)
    * ClearChat - Clears the players chat.
    * Sound - Plays a sound effect to the targeted player. (Sound, Number, Location)
    * SoundSequence - Plays a series of sounds to the targeted player. (Sound, Number, Location)
    * StopSound - Stops all sounds being played to the targeted player.
    * Particle - Shows a particle effect to the targeted player. (Particle, Location, Number)
    * Title - Sends a title to the targeted player. (Text, Text, Number, Number, Number)
    * ChatTag - Sets the player's chat tag. (Text)
    * BossBar - Adds a boss health bar to the player's HUD. (Text, Number, Item)
    * ClearBoosBar - Removes all boss bars on the player's HUD.
    * ActionBar - Sends a message to the player's action bar. (Text)
    * ChatColor - Sets the player's chat color.
    * Teleport - Teleports a player to the specified location. (Location)
    * RandomTeleport - Teleports a player to a random location. (Location(s))
    * TeleportSequence - Teleports a player through the series of locations. (Location(s), Number)
    * LaunchUp - Launches the player upwards. (Number)
    * LaunchForward - Launches the player forward. (Number)
    * LaunchToward - Launches the player towards a location. (Location, Number)
    * RideEntity - Makes the player ride an entity. (Text)
    * LaunchProjectile - Launches a projectile from the player. (Item, Text, Number, Location, Particle)
    * RemoveArrows - Removes all arrows in the players body.
    * DisguiseAsMob - Disguise the player as a mob. (Item, Text)
    * DisguiseAsPlayer - Disguise the player as a player. (Text)
    * DisguiseAsBlock - Disguise the player as a block. (Item, Text, Number)
    * Undisguise - Undisguises the player.
    * HideDisguise - Hides the players disguise from themself.
    * RollBack - Rollback the player's block changes.
    * AutoRespawn - Respawns a dead player.
    * Kick - Kicks the player from the plot.
    * RewardDFC - Rewards the player with DFC.
  * IfPlayer [] - If a player ___, then...
  * Var [] - Set custom variables.
  * IfVar [] - Compare custom variables.
  * EntityEvent [] - When an entity does something...
  * IfEntity [] - If an entity ___, then...
    * IsType - If an entity is type. (SpawnEgg)
    * CustomName - If a mobs name equals. (Text)
    * IsStandingOn - If a mob is standing on a block. (Block or Location)
    * IsNear - If a mob is near a location. (Location, Number)
    * IsMob - If an entity is a mob.
    * IsProj - If an entity is a projectile.
  * EntityAction [] - Do something to an entity,
  * Repeat [] - Repeat code multiple times.
    * NTimes - Repeats code (N) times. (Number)
    * Forever - Loops forever.
    * RepeatWhile - Repeats while a condition is true.
  * Else [] - Place after an if block for if...else statements.
  * Loop [] - An event that fires for every player, every x amount of ticks. (Number)
  * IfGame [] - Conditions not related to players or entities.
    * BlockEquals - If a block is. (Location, Block)
    * ContainerHas - If a countainer has an item. (Location, Item)
    * SignContains - If a sign contains text. (Location, Text)
  * Control [] - Break out of **Repeats**, return from **Functions**, and more.
    * EndRepeat - Stops a repeating sequence.
    * Skip - Skip to the next repetition of a repeating sequence.
    * Return - Return from a function.
    * End - Completely stop reading code.`
  * SelectObject [] - Select players, mobs, entities. Code blocks after the **Select Object** block will target the chosen object.
    * Default - The main player involved in an event.
    * DefaultEntity - The main non-player entity involved in an event.
    * RandomPlay - A randomly selected player.
    * RandomEntity - A randomly selected non-player entity.
    * All - Every player on the plot.
    * AllMobs - Every mob (non-player living entity) on the plot.
    * AllEntity - Every non-player entity on the plot.
    * LastSpawned - The most recently spawned mob.
    * Killer - The killer in kill event.
    * Damager - The damager in damage events.
    * Shooter - The shooter in projectile events.
    * Projectile - The Projectile in projectile events.
    * Victim - The victim in kill / damage events.
    * PlayName - The player whose name is in the chest.
    * MobName - All mobs with the name in the chest.
    * EntityName - All entities with the name in the chest.
    * PlayCondition - All players that satisfy a condition.
    * MobCondition - All mobs that satisfy a condition.
    * EntityCondition - All non-player entities that satisfy a condition.
    * RandomSelect - A randomly selected player or entity from the current selection. (Number)
    * FilterSelect - All objects in the current selection that satisfy a condition.
    * CurrentSelect - The currently selected object.
    * None - Nothing (all code blocks will use defaults).
  * Function [] - Define custom functions! When called by a **Call Function** block, code will be read from here, then return to the call block. (text)
  * CallFunction [] - Call a custom function. Define functions with the **Function** block. This can be a way of splitting up long lines! (text)
  
### Syntax

  * parameters - ()
  * grouping - {}
  * strings - ''
  * method class - []
  * target - <>
  * end statement - ;
  * seperate condition - ,
  * variable targets %%
  * NOT !!
  * comment /* */
  ```javascript
  PlayerEvent ['Join']
    PlayerAction ['GiveItems'] (Item(WATER_BUCKET), Item(LAVA_BUCKET), Item(MILK_BUCKET)) <%default_player%>;
    
  PlayerEvent ['Quit']
    PlayerAction ['SendDialogue'] (Text('Goodbye %default%'), Number(1)) <%all_player%>;
  ```
  NOT example:
  ```javascript
  PlayerEvent ['Join']
    IfPlayer[!'NameEquals'!] (Text('Jeremaster')) <%default_player%> {
      PlayerAction ['SendMessage'] (Text('Someone joined...')) <%all_player%>;
    } Else {
      PlayerAction ['GiveItems'] (Item(DIAMOND, 64)) <%all_player%>;
    }
  ```
    
 ### Variable Targets
 
Variable targets are denoted using `%target_class%`.
  * default - %default%
  * all - %all%
  * selection - %selection%
  * attacker - %damager%
  * killer - %killer%
  * victim - %victim%
  * global - %global%
  * _Bind `_entity` or `_player` to target a specific entity class or the default target for the method will be used._
  
### Parameter Classes

  * Item - define item values
  * Text - defines string values
  * Number - define number values
  * Sound - sound values
  * Particle - define particle values
  * Var - define custom variables _use a variable name instead of a text string to define nested variables_
  * Value - internal variables
  
  ```javascript
  PlayerEvent ['Join']
    Var ['Set'] (Var('var1'), Text('example')) <%global%>;]
    Var ['Set'] (Var(Var('var1')), Text('example2')) <%global%>;
    Var ['Set'] (Var(Var('var1')) + 'var1'), Text('example3')) <%global%>;
    PlayerAction ['SendMessage'] (Var(example)) <%all%>;
  ```
  
### Indentation
When starting with an *event*, *loop* or *function* you must indent all of the code included in the event/loop/function.
```javascript
PlayerEvent ['Sneak']
  /* Indented code will denote it is part of the PlayerEvent */
  PlayerAction ['LaunchUp'] (Number(20)) <%default_player%>;
PlayerAction ['LaunchForward'] (Number(20)) <%default_player%>; /* this is not part of the PlayerEvent, and does not function; is not part of any event, loop, or function */
```
  
### File System
  * TextDF files end in the file extension `.tdf`. One `.tdf` file is equivalent to one plot in DiamondFire. You cannot transfer or load variables or functions between files.
