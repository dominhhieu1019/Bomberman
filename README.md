# Bomberman 

**3D, static top-down view, 1 vs 1 version created with Unreal Engine 4.22.1**

## About the game
 
To play the game right away, go to *BomberMan\Release\WindowsNoEditor\BomberMan.exe*

The timer count down right away after the application execute succesfully.

There is one pre-defined map.

At the beginning, each player has only one bomb to place at a time. The bomb returns to the Player after explotion. Amount of bombs, blast length as well as player run speed can be upgraded by pickups. Bomb blast can destroy destructible walls, pickups and players in its range when going off.

Pickups can be spawned in the map by destructible walls randomly upon destruction. There are three type of pickups: *Longer bomb blasts*, *More boms*, *Faster run speed*.

A player wins if he is the last one standing in the game. If there are more than one player when timer runs out or last players died at the same time, there is draw. When the game over, the end screen will be loaded in a few seconds. Then, the result will be announced and it is the restart option on that screen.


## Source code

Entire game is made in Blueprints.
Assets:
- **Bomb1_Player1**, **Bomb1_Player2**: Weapon of players. Handles blast tracing. Sends *DestroyActor* to all actors in its blast range.
- **NewGameInstance**: Holds the blast range of each player (*P1BombRange*, *P2BombRange*), amount of game time in seconds (*Time*),the game state (*EndGame*), the state of player (died or not?) (*P1Death*, *P2Death*) and the current level (*currentLevel*).
- **PickUpBombAmountRange**, **PickUpBombRangeIncrease**, **PickUpSpeedIncrease**: The pickups that upgrade player and his weapon. Store logic for being picked up. Send *DestroyActor* if player pick it.
- **Player1**, **Player2**: Main character (distinguish by color: P1 is blue, P2 is yellow). Stores logic for movement, bomb placing.
- **WallDestructible1**: Store the funtion *PickUpChance* that choose randomly float number in range from 0 to 10 and drop the pickups depending on the chosen number at the location of destroyed wall. If random number is smaller than 1, drop the **PickUpBombAmountIncrease**. If it is higher than 9, drop the **PickUpBombRangeIncrease**. If it is between 4.5 and 5.5, drop **PickUpSpeedIncrease** (~30% chance to spawn something).
- **Map1**: The pre-define map. Sets the default value of **NewGameInstance** at the beginning of the round. Check if the game finished. Show result and freeze game at its current state after the round end.
- The materials of board, bomb, bomb effect, pickups, players and walls.
- The particle system of bomb effect.


## Next steps
- Main menu, pause menu.
- Setting options.
- Decorate materials of players, bombs, walls,...
- Add audio.
- Add procedural generated maps.
- Upgrade the bomb blast (should not be spherical but linear in the four main directions by using boxes, stopped by walls and indestructible walls).
- 4 playes mode.
- Allow players to choose or create their character.
- Multiplayer version over network.
- Create AI enemies as long as no player has join game session.
- Players and bombs placed at exact place, in the middle of the square.

