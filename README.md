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
  * IfPlayer [] - If a player ___, then...
  * Var [] - Set custom variables.
  * IfVar [] - Compare custom variables.
  * EntityEvent [] - When an entity does something...
  * IfEntity [] - If an entity ___, then...
  * EntityAction [] - Do something to an entity,
  * Repeat [] - Repeat code multiple times.
  * Else [] - Place after an if block for if...else statements.
  * Loop [] - An event that fires for every player, every x amount of ticks.
  * IfGame [] - Conditions not related to players or entities.
  * Control [] - Break out of **Repeats**, return from **Functions**, and more.
  * SelectObject [] - Select players, mobs, entities. Code blocks after the **Select Object** block will target the chosen object.
  * Function [] - Define custom functions! When called by a **Call Function** block, code will be read from here, then return to the call block.
  * CallFunction [] - Call a custom function. Define functions with the **Function** block. This can be a way of splitting up long lines!
  
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
  * Var - define custom variables _Bind `_nest(var)` to define a nested variable_ 
  * Value - internal variables
  
  ```javascript
  PlayerEvent ['Join']
    Var ['Set'] (Var('var1'), Text('example')) <%global%>;
    Var ['Set'] (Var_nest(var1), Text('example2')) <%global%>;
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
