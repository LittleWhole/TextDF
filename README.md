# TextDF
TextDF is a way of expressing the DiamondFire code system in text formatting.

### Methods
  * Var [] - Set custom variables.
  
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
    IfPlayer [!'NameEquals'!] (Text('Jeremaster')) <%default_player%> {
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
    Var ['Set'] (Var('var1'), Text('example')) <%global%>;
    Var ['Set'] (Var(Var('var1')), Text('example2')) <%global%>;
    Var ['Set'] (Var(Var('var1')) + 'var1'), Text('example3')) <%global%>;
    PlayerAction ['SendMessage'] (Var(example)) <%all%>;
  ```
  #### Parameter SubClasses
     
    ##### Values
    
     * CurrentHealth
     * MaximumHealth
     * CurrentFoodLevel
     * CurrentSaturationLevel
     * CurrentXPLevel
     * CurrentXP%
     * CurrentArmorPoints
     * CurrentFireTicks
     * CurrentAirRemaining
     * CurrentEyeLocation
     * CurrentHeldSlot
     * TargetBlockLocation
     * X-Coordinate
     * Y-Coordinate
     * Z-Coordinate
     * Pitch
     * Yaw
     * TotalPlayerCount
     * EventDamage
     * NewSlot
     * OldSlot
     * Command
     
    ##### Potion Effects
    
     * SPEED
     * SLOW
     * FAST_DIGGING
     * SLOW_DIGGING
     * INCREASE_DAMAGE
     * HEAL
     * HARM
     * JUMP
     * CONFUSION
     * REGENERATION
     * DAMAGE_RESISTANCE
     * FIRE_RESISTANCE
     * WATER_BREATHING
     * INVISIBILITY
     * BLINDNESS
     * NIGHT_VISION
     * HUNGER
     * WEAKNESS
     * POISON
     * WITHER
     * HEALTH_BOOST
     * ABSORPTION
     * SATURATION
     * GLOWING
     * LEVITATION
     * LUCK
     * UNLUCK
     
    ##### Particle Effects
    
     * Smoke
     * LargeSmoke
     * Flame
     * AngryVillager
     * HappyVillager
     * Heart
     * MusicNote
     * FireworkSparkles
     * Lava
     * Barrier
     * SmallExplosion
     * HugeExplosion
     * LavaDrip
     * WaterDrip
     * DragonBreath
     * Slime
     * Portal
     * EnchantmentRunes
     * Redstone
     * Crit
     * MagicCrit
     * DamageHearts
     * Cloud
     * Spit
     * Totem
     
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
