# DMG Adventure III
A continuation of DMG Adventure [part I](https://github.com/john-lay/dmg-adventure) and [part II](https://github.com/john-lay/dmg-adventure-ii)

Created with a [fork](https://github.com/john-lay/gb-studio) of [GB Studio](https://www.gbstudio.dev/)

### Weapons / Spells
- [x] calm (mystery island)
- [x] gold necklace (strength)
- [x] hammer
- [x] Joust
- [x] roar stick (strength)
- [x] bow + arrow

### Items / Treasures
- [x] Bouquet (strength)
- [x] candle
- [x] coal
- [x] compass
- [x] golden boots
- [x] map (Destiny shrine, water, strength, fire)
- [x] plank (water shrine)
- [x] raft
- [x] red ribbon (strength)
- [x] repellant (Zora)
- [x] saltcellar (strength)
- [x] tickets x2 (strength)
- [x] vial of wind (piece of power)


3x overworld hearts
start with 8 (3 + earth, illusion, air, destiny, torian)

### sprite duplication
gold necklace = jade amulet (mermaid necklace)
red boots = golden boots (pegasus boots)

## Enemies
Crockarock (lizard enemies near fire shrine) 
Lanmola (centipede) -> pincer enemy, mini moldorm

# Technical notes

## Variable list

A listing of variables and their types in re-usable components (Actors/Scenes)

### Global
* `$00$: Variable 000` _Health - `number`. (Private variable. Represents the old/cached health. 2 health units equal 1 heart)
* `$01$: Variable 001` Health - `number`. (Public variable. Can be updated in GB Studio. If the value above is different it triggers a HUD redraw)
* `$02$: Variable 002` _Max Hearts - `number`. (Private variable. Represents the old/cached maximum hearts. 2 health units equal 1 heart)
* `$03$: Variable 003` Max Hearts - `number`. (Public variable. Can be updated in GB Studio. If the value above is different it triggers a HUD redraw)
* `$04$: Variable 004` _Rupees - `number`. (Private variable. Indicates the old/cached number of rupees Zelda has collected)
* `$05$: Variable 005` Rupees - `number`. (Public variable. Can be updated in GB Studio. If the value above is different it triggers a HUD redraw)
* `$06$: Variable 006` Zelda PosX - `number`. (Stores Zelda's position when she exits the screen. Used to maintain her relative position on the next screen)
* `$07$: Variable 007` Zelda PosY - `number`. (Stores Zelda's position when she exits the screen. Used to maintain her relative position on the next screen)
* `$08$: Variable 008` Exit Screen: Top, Right, Bottom, Left - `number`. (Indicates the direction Zelda was facing when exiting the screen. Used with the above)
    * (0 represents null/no position)
    * (1 represents Zelda exitted at the __top__ of the screen)
    * (2 represents Zelda exitted at the __right__ side of the screen)
    * (3 represents Zelda exitted at the __bottom__ of the screen)
    * (4 represents Zelda exitted at the __left__ side of the screen)
* `$09$: Variable 009` Scene Flags - `byte`.
  * (Flag 1 represents the enemy dropping a rupee)
  * (Flag 2 represents the enemy dropping a heart)
  * (Flag 3 represent the enemy dropped a rupee or a heart)
  * (Flag 4 represents Zelda has spoken to a fairy)
  * (Flag 5 represents Zelda has defeated the sea monster)
  * (Flag 6 is ???)
  * (Flag 7 is ???)
  * (Flag 8 is ???)
* `$10$: Variable 010` Wand Equipped - `bool`.
* `$11$: Variable 011` Spell Equipped - `byte`.
  * (Flag 1 represents Zelda has the Calm spell equipped - costs 1 Rupee to cast) 
  * (Flag 2 represents Zelda has the bow + arrow spell equipped - costs 1 Rupee to cast)
  * (Flag 3 represents Zelda has the joust spell equipped - costs 3 Rupee to cast)
  * (Flag 4 represents Zelda has the gold necklace spell equipped - costs 2 Rupee to cast)
  * (Flag 5 represents Zelda has the roar stick spell equipped - costs 3 Rupee to cast)
  * (Flag 6 represents Zelda has the hammer spell equipped - costs 2 Rupee to cast)
  * (Flag 7 represents Zelda has the turquoise ring spell equipped - costs 26 Rupee to cast)
  * (Flag 8 represents Zelda has the broadsword spell equipped - costs 2 Rupee to cast)
* `$12$: Variable 012` Spell Cost - `number`. (Cost of the equipped spell)
* `$13$: Variable 013` Collectable - `byte`.
  * (Flag 1 is the Destiny Shrine Map)
  * (Flag 2 is the Golden Boots)
  * (Flag 3 is the Joust spell)
  * (Flag 4 is the Plank)
  * (Flag 5 is the Lump of Coal)
  * (Flag 6 is the Gold Necklace)
  * (Flag 7 is the Roar Stick spell)
  * (Flag 8 is the Hammer spell)
* `$14$: Variable 014` Inventory Screen - `byte`.
  * (Flag 1 represents we've come from Quest Status screen 1)
  * (Flag 2 represents we've come from Quest Status screen 2)
  * (Flag 3 represents we've come from Quest Status screen 3)
  * (Flag 4 represents we've come from Quest Status screen 4)
  * (Flag 5 is ???)
  * (Flag 6 is ???)
  * (Flag 7 is ???)
  * (Flag 8 is ???)
* `$15$: Variable 015` Cursor PosX - `number`. (Stores the cursor's position. Used to maintain its relative position between screen)
* `$16$: Variable 016` Cursor PosY - `number`. (Stores the cursor's position. Used to maintain its relative position between screen)
* `$17$: Variable 017` Purchasable - `byte`.
  * (Flag 1 is the Zola Repellant)
  * (Flag 2 is the Candle)
  * (Flag 3 is the Life Potion)
  * (Flag 4 is the Salt Cellar)
  * (Flag 5 is the Bouquet)
  * (Flag 6 is the Red Ribbon)
  * (Flag 7 is ticket A)
  * (Flag 8 is ticket B)
* `$18$: Variable 018` Overworld Flags - `byte`.
  * (Flag 1 represents Zelda has completed the Water Shrine)
  * (Flag 2 represents Zelda has completed the Strength Shrine)
  * (Flag 3 represents Zelda has completed the Fire Shrine)
  * (Flag 4 represents Zelda has collected the Canvula Heart)
  * (Flag 5 represents Zelda has collected the South Port Heart)
  * (Flag 6 represents Zelda has collected the Mystery Island Heart)
  * (Flag 7 is ???)
  * (Flag 8 is ???)
* `$19$: Variable 019` Resume location - `byte`.
  * (Flag 1 represents a Save and Continue operation)
  * (Flag 2 represents a Save and Quit operation)
  * (Flag 3 represents Zelda should resume in the Water Shrine)
  * (Flag 4 represents Zelda should resume in the Strength Shrine)
  * (Flag 5 represents Zelda should resume in the Fire Shrine)
  * (Flag 6 is ???)
  * (Flag 7 is ???)
  * (Flag 8 is ???)
* ~~`$20$: Variable 020` Dungeon Room - `number`. (Indicates the dungeon room Zelda occupies)~~
* `$21$: Variable 021` Enemy Counter - `number`. (Indicates the number of Zelda has defeated in this scene)
* `$22$: Variable 022` Water Shrine Flags - `byte`.
  * (Flag 1 is the Water Shrine Map)
  * (Flag 2 is the Water Shrine Compass)
  * (Flag 3 is ???)
  * (Flag 4 is ???)
  * (Flag 5 is ???)
  * (Flag 6 is ???)
  * (Flag 7 is ???)
  * (Flag 8 is ???)
* `$23$: Variable 023` Strength Shrine Flags - `byte`.
  * (Flag 1 is the Strength Shrine Map)
  * (Flag 2 is the Strength Shrine Compass)
  * (Flag 3 represents Zelda has played the archery game, target 1)
  * (Flag 4 represents Zelda has played the archery game, target 2)
  * (Flag 5 represents Zelda has played the archery game, target 3)
  * (Flag 6 represents Zelda has unlocked the door in the Roar stick room)
  * (Flag 7 represents Zelda has defeated the blue knight)
  * (Flag 8 represents Zelda has defeated the green knight)
* `$24$: Variable 024` Fire Shrine Flags - `byte`.
  * (Flag 1 is the Fire Shrine Map)
  * (Flag 2 is the Fire Shrine Compass)
  * (Flag 3 is ???)
  * (Flag 4 is ???)
  * (Flag 5 is ???)
  * (Flag 6 is ???)
  * (Flag 7 is ???)
  * (Flag 8 is ???)
* `$25$: Variable 025` Is Sailing - `bool`. (Indicates whether or not Zelda is sailing from the Seacoast dock to the Sea Island)
* `$26$: Variable 026` Map PosX - `number`. (Stores the player's dungeon position. Shows which dungeon room the player is in on the minimap)
* `$27$: Variable 027` Map PosY - `number`. (Stores the player's dungeon position. Shows which dungeon room the player is in on the minimap)
