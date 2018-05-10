# TextDF
TextDF is a way of expressing the DiamondFire code system in text formatting.

### Methods
  
  * PlayerEvent [] - When the player does something...
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
  * comment /* */
  ```javascript
  PlayerEvent ['Join']
    PlayerAction ['GiveItems'] (Item(WATER_BUCKET)) <%default_player%>;
    
  PlayerEvent ['Quit']
    PlayerAction ['SendMessage'] (Text('Goodbye %default%')) <%all_player%>;
  ```
    
 ### Variable Targets
 
Variable targets are denoted using `%target_name%`.
  * default - %default%
  * all - %all%
  * selection - %selection%
  * attacker - %damager%
  * killer - %killer%
  * victim - %victim%
  * _Bind `_entity` or `_player` to target a certain or the default target for the method will be used._
  
### Indentation
When starting with an *event*, *loop* or *function* you must indent all of the code included in the event/loop/function.
```javascript
PlayerEvent ['Sneak']
  /* Indented code will denote it is part of the PlayerEvent */
  PlayerAction ['LaunchUp'] (20) <%default_player%>
PlayerAction ['LaunchForward'] (20) <%default_player%> /* this is not part of the PlayerEvent, and does not function; is not part of any event, loop, or function */
```
  
