# DMG Adventure III
A continuation of DMG Adventure [part I](https://github.com/john-lay/dmg-adventure) and [part II](https://github.com/john-lay/dmg-adventure-ii)

Created with a [fork](https://github.com/john-lay/gb-studio) of [GB Studio](https://www.gbstudio.dev/)

### Weapons / Spells
- [x] calm (mystery island)
- [x] gold necklace (strength)
- [x] hammer
- [x] Joust
- [x] roar stick (strength)

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
  * (Flag 5 is ???)
  * (Flag 6 is ???)
  * (Flag 7 is ???)
  * (Flag 8 is ???)
* `$10$: Variable 010` Wand Equipped - `bool`.
* `$11$: Variable 011` Spell Equipped - `byte`.
  * (Flag 1 represents Zelda has the Calm spell equipped - costs 1 Rupee to cast) 
  * (Flag 2 is ???)
  * (Flag 3 is ???)
  * (Flag 4 is ???)
  * (Flag 5 is ???)
  * (Flag 6 is ???)
  * (Flag 7 is ???)
  * (Flag 8 is ???)
* `$12$: Variable 012` Spell Cost - `number`. (Cost of the equipped spell)
* `$13$: Variable 013` Collectable - `byte`.
  * (Flag 1 is the Calm spell)
  * (Flag 2 is ???)
  * (Flag 3 is ???)
  * (Flag 4 is ???)
  * (Flag 5 is ???)
  * (Flag 6 is ???)
  * (Flag 7 is ???)
  * (Flag 8 is ???)
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
* `$16$: Variable 016` Cursot PosY - `number`. (Stores the cursor's position. Used to maintain its relative position between screen)
