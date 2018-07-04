# TextDF
TextDF is a way of expressing the DiamondFire code system in text formatting.

### Methods
  * IfPlayer [] - If a player ___, then...
  * Var [] - Set custom variables.
  * IfVar [] - Compare custom variables.
  * IfEntity [] - If an entity ___, then...
    * IsType - If an entity is type. (Item(Spawn Egg))
    * CustomName - If a mobs name equals. (Text)
    * IsStandingOn - If a mob is standing on a block. (Item(Block) or Location)
    * IsNear - If a mob is near a location. (Location, Number(Range))
    * IsMob - If an entity is a mob.
    * IsProj - If an entity is a projectile.
  * Repeat [] - Repeat code multiple times.
    * NTimes - Repeats code (N) times. (Number)
    * Forever - Loops forever.
    * RepeatWhile - Repeats while a condition is true.
  * Else [] - Place after an if block for if...else statements.
  * IfGame [] - Conditions not related to players or entities.
    * BlockEquals - If a block is. (Location, Item(Block))
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
  
    ##### Sound
     * AmbientCave
     * FireAmbient
     * FireExtinguish
     * FurnaceCrackle
     * AmbientLava
     * ExtinguishLava
     * LavaPop
     * AmbientPortal
     * PortalFillFrame
     * PortalSpawn
     * PortalTravel
     * AmbientWater
     * MusicCreative
     * MusicCredits
     * MusicDragon
     * MusicEnd
     * MusicGame
     * MusicMenu
     * MusicNether
     * Record11
     * Record13
     * RecordBlocks
     * RecordCat
     * RecordChirp
     * RecordFar
     * RecordMall
     * RecordMellohi
     * RecordStal
     * RecordStrad
     * RecordWait
     * RecordWard
     * GatewaySpawn
     * WaterlilyPlace
     * LightningImpact
     * LightningThunder
     * MooshroomShears
     * Rest
     * ChallengeComplete
     * WeatherRain
     * WeatherRainUp
     * ItemBreak
     * ItemPickup
     * FrameAdd
     * FrameBreak
     * FramePlace
     * FrameRemove
     * FrameRotate
     * LeashBreak
     * LeashPlace
     * PaintingBreak
     * PaintingPlace
     * EquipChain
     * EquipDiamond
     * EquipGeneric
     * EquipGold
     * EquipIron
     * EquipLeather
     * BottleEmpty
     * BottleFill
     * FillBreath
     * BucketEmpty
     * BucketEmptyLava
     * BucketFill
     * BucketFillLava
     * ChorusTeleport
     * ElytraFly
     * FireChargeUse
     * FlintSteelUse
     * HoeTill
     * ShieldBlock
     * ShieldBreak
     * ShovelFlatten
     * TotemUse
     * StandBrew
     * LingeringThrow
     * PotionBreak
     * PotionThrow
     * EnchantmentUse
     * Thorns
     * ExperienceThrow
     * OrbPickup
     * AnvilBreak
     * AnvilDestroy
     * AnvilFall
     * AnvilHit
     * AnvilLand
     * AnvilPlace
     * AnvilStep
     * AnvilUse
     * ChestClose
     * ChestLocked
     * ChestOpen
     * EnderChestClose
     * EnderChestOpen
     * ShulkerBoxClose
     * ShulkerBoxOpen
     * ChorusDeath
     * ChorusGrow
     * ClothBreak
     * ClothFall
     * ClothHit
     * ClothPlace
     * ClothStep
     * ComparatorClick
     * DispenserDispense
     * DispenserFail
     * DispenserLaunch
     * LeverClick
     * MetalPlateOn
     * MetalPlateOff
     * PistonContract
     * PistonExtend
     * TorchBurnout
     * StoneButtonOff
     * StoneButtonOn
     * StonePlateOff
     * StonePlateOn
     * TripwireAttach
     * TripwireOff
     * TripwireOn
     * TripwireDetach
     * WoodButtonOff
     * WoodButtonOn
     * WoodPlateOff
     * WoodPlateOn
     * MinecartInside
     * MinecartRiding
     * TNTPrimed
     * UIClick
     * GlassBreak
     * GlassFall
     * GlassHit
     * GlassPlace
     * GlassStep
     * GrassBreak
     * GrassFall
     * GrassHit
     * GrassPlace
     * GrassStep
     * GravelBreak
     * GravelFall
     * GravelHit
     * GravelPlace
     * GravelStep
     * GateClose
     * GateOpen
     * IronDoorClose
     * IronDoorOpen
     * IronTrapClose
     * IronTrapOpen
     * WoodDoorClose
     * WoodDoorOpen
     * WoodTrapClose
     * WoodTrapOpen
     * LadderBreak
     * LadderFall
     * LadderHit
     * LadderPlace
     * LadderStep
     * MetalBreak
     * MetalFall
     * MetalHit
     * MetalPlace
     * MetalStep
     * Basedrum
     * Bass
     * Bell
     * Chime
     * Flute
     * Guitar
     * Harp
     * Hat
     * Pling
     * Snare
     * Xylophone
     * SandBreak
     * SandFall
     * SandHit
     * SandPlace
     * SandStep
     * SlimeBreak
     * SlimeFall
     * SlimeHit
     * SlimePlace
     * SlimeStep
     * SlimeAttack
     * SlimeDeath
     * SlimeHurt
     * SlimeJump
     * SlimeSquish
     * SmallSlimeDeath
     * SmallSlimeJump
     * SmallSlimeSquish
     * SnowBreak
     * SnowFall
     * SnowHit
     * SnowPlace
     * SnowStep
     * StoneBreak
     * StoneFall
     * StoneHit
     * StonePlace
     * StoneStep
     * WoodBreak
     * WoodFall
     * WoodHit
     * WoodPlace
     * WoodStep
     * BigFall
     * Burn
     * Death
     * Drink
     * Eat
     * Explode
     * ExtinguishFire
     * Hurt
     * SmallFall
     * Splash
     * Swim
     * ArmorStandBreak
     * ArmorStandFall
     * ArmorStandHit
     * ArmorStandPlace
     * ArrowHit
     * ArrowHitPlay
     * ArrowShoot
     * BobberSplash
     * BobberRetrieve
     * BobberThrow
     * EggThrow
     * EnderEyeLaunch
     * EyeDeath
     * PearlThrow
     * SbowThrow
     * BatAmbient
     * BatDeath
     * BatHurt
     * BatLoop
     * BatTakeoff
     * BlazeAmbient
     * BlazeBurn
     * BlazeDeath
     * BlazeHurt
     * BlazeShoot
     * CatAmbient
     * CatDeath
     * CatHiss
     * CatHurt
     * CatPurr
     * CatPurreow
     * ChickenAmbient
     * ChickenDeath
     * ChickenEgg
     * ChickenHurt
     * ChickenStep
     * CowAmbient
     * CowDeath
     * CowHurt
     * CowMilk
     * CowStep
     * CreeperDeath
     * CreeperHurt
     * CreeperPrimed
     * DonkeyAmbient
     * DonkeyAngry
     * DonkeyChest
     * DonkeyDeath
     * DonkeyHurt
     * ElderGuardAmbient
     * ElderGuardAmbientLand
     * ElderGuardCurse
     * ElderGuardDeath
     * ElderGuardDeathLand
     * ElderGuardHurt
     * ElderGuardHurtLand
     * GuardAmbient
     * GuardAmbientLand
     * GuardAttack
     * GuardDeath
     * GuardDeathLand
     * GuardFlop
     * GuardHurt
     * GuardHurtLand
     * DragonAmbient
     * DragonDeath
     * DragonFireball
     * DragonFlap
     * DragonGrowl
     * DragonHurt
     * DragonShoot
     * EndermanAmbient
     * EndermanDeath
     * EndermanHurt
     * EndermanScream
     * EndermanStare
     * EndermanTeleport
     * MiteAmbient
     * MiteDeath
     * MiteHurt
     * MiteStep
     * FireworkBlast
     * FireworkBlastFar
     * FireworkBlastLarge
     * FireworkBlastLargeFar
     * FireworkLaunch
     * FireworkShoot
     * FireworkTwinkle
     * FireworkTwinkleFar
     * GhastAmbient
     * GhastDeath
     * GhastHurt
     * GhastScream
     * GhastShoot
     * GhastWarn
     * HorseAmbient
     * HorseAngry
     * HorseArmor
     * HorseBreathe
     * HorseDeath
     * HorseEat
     * HorseGallop
     * HorseHurt
     * HorseJump
     * HorseLand
     * HorseSaddle
     * HorseStep
     * HorseStepWood
     * HostileBigFall
     * HostileDeath
     * HostileHurt
     * HostileSmallFall
     * HostileSplash
     * HostileSwim
     * HuskAmbient
     * HuskAmbient2
     * HuskHurt
     * HuskStep
     * IronGolemAttack
     * IronGolemDeath
     * IronGolemHurt
     * IronGolemStep
     * MagmaDeath
     * MagmaHurt
     * MagmaJump
     * MagmaSquish
     * SmallMagmaDeath
     * SmallMagmaHurt
     * SmallMagmaSquish
     * MuleAmbient
     * MuleDeath
     * MuleHurt
     * ParrotAmbient
     * ParrotDeath
     * ParrotEat
     * ParrotFly
     * ParrotHurt
     * ParrotImitateBlaze
     * ParrotImitateCreeper
     * ParrotImitateElderGuard
     * ParrotImitateDragon
     * ParrotImitateEnderman
     * ParrotImitateMite
     * ParrotImitateEvoker
     * ParrotImitateGhast
     * ParrotImitateHusk
     * ParrotImitateIllusioner
     * ParrotImitateMagma
     * ParrotImitatePolar
     * ParrotImitateShulker
     * ParrotImitateSilver
     * ParrotImitateSkeleton
     * ParrotImitateSlime
     * ParrotImitateSpider
     * ParrotImitateStray
     * ParrotImitateVex
     * ParrotImitateVindicator
     * ParrotImitateWitch
     * ParrotImitateWither
     * ParrotImitateWitherSkeleton
     * ParrotImitateWolf
     * ParrotImitateZombie
     * ParrotImitateZombiePig
     * ZombieImitateZombieVillager
     * ParrotStep
     * PigAmbient
     * PigDeath
     * PigHurt
     * PigSaddle
     * PigStep
     * PlayAttackCrit
     * PlayAttackKnock
     * PlayAttackNoDamage
     * PlayAttackStrong
     * PlayAttackSweep
     * PlayAttackWeak
     * PlayBigFall
     * PlayBreathe
     * PlayBurn
     * PlayBurp
     * PlayDeath
     * PlayDrown
     * PlayHurt
     * PlayLevelUp
     * PlaySmallFall
     * PlaySplash
     * PlaySwim
     * PolarAmbience
     * PolarBabyAmbience
     * PolarDeath
     * PolarHurt
     * PolarStep
     * PolarWarn
     * RabbitAmbient
     * RabbitAttack
     * RabbitDeath
     * RabbitHurt
     * RabbitJump
     * SheepAmbient
     * SheepDeath
     * SheepHurt
     * SheepShear
     * SheepStep
     * ShulkerAmbient
     * ShulkerBulletHit
     * ShulkerBulletHurt
     * ShulkerClose
     * ShulkerDeath
     * ShulkerHurt
     * ShulkerHurtClose
     * ShulkerOpen
     * ShulkerShoot
     * ShulkerTeleport
     * SilverAmbient
     * SilverDeath
     * SilverHurt
     * SilverStep
     * SkeletonAmbient
     * SkeletonDeath
     * SkeletonHorseAmbient
     * SkeletonHorseDeath
     * SkeletonHorseHurt
     * SkeletonHurt
     * SkeletonShoot
     * SkeletonStep
     * SnowmanAmbient
     * SnowmanDeath
     * SnowmanHurt
     * SnowmanShoot
     * SpiderAmbient
     * SpiderDeath
     * SpiderHurt
     * SpiderStep
     * SquidAmbient
     * SquidDeath
     * SquidHurt
     * StrayAmbient
     * StrayDeath
     * StrayHurt
     * StrayStep
     * VillagerAmbient
     * VillagerDeath
     * VillagerHurt
     * VillagerNo
     * VillagerTrading
     * VillagerYes
     * WitchAmbient
     * WitchDeath
     * WitchDrink
     * WitchHurt
     * WitchThrow
     * WitherAmbient
     * WitherBreak
     * WitherDeath
     * WitherHurt
     * WitherShoot
     * WitherSpawn
     * WitherSkeletonAmbient
     * WitherSkeletonDeath
     * WitherSkeletonHurt
     * WitherSkeletonStep
     * WolfAmbient
     * WolfDeath
     * WolfGrowl
     * WolfHowl
     * WolfHurt
     * WolfPant
     * WolfShake
     * WolfStep
     * WolfWhine
     * ZombieAmbient
     * ZombieAttackWoodDoor
     * ZombieAttackIronDoor
     * ZombieBreakWoodDoor
     * ZombieDeath
     * ZombieHorseAmbient
     * ZombieHorseDeath
     * ZombieHorseHurt
     * ZombieHurt
     * ZombieInfect
     * ZombiePigAmbient
     * ZombiePigAngry
     * ZombiePigDeath
     * ZombiePigHurt
     * ZombieStep
     * ZombievillagerAmbient
     * ZombieVillagerConvert
     * ZombieVillagerCure
     * ZombieVillagerDeath
     * ZombieVillagerHurt
     * ZombieVillagerStep
     * EvocationAmbient
     * EvocationCast
     * EvocationDeath
     * EvocationHurt
     * EvocationAttack
     * EvocationSummon
     * EvocationWololo
     * IllusionerAmbient
     * IllusionerCast
     * IllusionerDeath
     * IllusionHurt
     * IllusionerMove
     * IllusionerBlindness
     * IllusionerMirror
     * VexAmbient
     * VexCharge
     * VexDeath
     * VexHurt
     * VindicationAmbient
     * VindicationDeath
     * VindicationHurt
     * LlamaAmbient
     * LlamaAngry
     * LlamaChest
     * LlamaDeath
     * LlamaEat
     * LlamaHurt
     * LlamaSpit
     * LlamaStep
     * LlamaSwag
     
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
