[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/5YTzVbxp)
## 50.002 1D Project Group 21 - What The Whack

- Lee Jun Hui Ryan 1006652
- Cai Junjie 1006918
- Ho Xiaoyang 1007006
- Sun Sitong 1007132
- Shah Pankti Amish 1007130
- Yee Jia Zhen 1006969



## The Project - What the Wack
![New Project (3)](https://github.com/50002-computation-structures/1d-project-group-21/assets/121916370/1f2e5925-b8e0-4682-a03c-2caea0185556)

Defeat your foes in this new and improved version of rock-paper-scissors! win by crushing your enemies with a hammer and catch them off guard as they desperately try to defend themselves with a shield

### User Manual
1. Round commences with each player starting with HP = 3
2. Each player has 5 seconds to press from (stone, paper, scissors), the time indicated by a LED screen.
3. After 5 seconds, the result of the rock-paper-scissors will be revealed through LEDs indicating each player’s choice.
4. The winner of the scissor, paper, stone shall immediately press the hammer button. The loser should try and defend by pressing the shield button
5. If the loser fails to defend before the winner attacks their HP decreases by one.
6. The next round will begin after a 2-second cooldown.
7. The final winner of the game is the last one standing with nonzero HP.

### How it works
Our game is a rock-paper-scissors with a twist. When a round begins, a timer starts and each player (secretly) makes their choice of rock, paper, or scissors. After the timer runs out, both player’s choices are shown on screen. The winner (of rock, paper, scissors) needs to press the attack button first to deal damage to the loser. However, if the loser presses the defend button faster (before the attacking player presses the attack button), they successfully defend themselves and no damage is taken, and then the next round begins. The attack and defend button are in the middle, shared by both players. The game continues until a player reaches 0 hit points. 

The machine understands which player won the game of rock, paper, scissors. Then, if the attack button is pressed first, the loser of rock, paper, scissors will take damage. If the defend button is pressed first, there will be no change in hit-points. The machine does not actually care which player presses the button - it wouldn’t know, because the attack and defend buttons are shared. What happens is that once the result is shown on screen, a player might panic and scramble for the attack/defend button but might actually press the wrong one. For example, player A might have won the game of rock paper scissors. However, in a panic, the player thinks they lost and scrambles for the defend button and presses it first. What happens is that the player has essentially saved their opponent, and the opponent loses no hit points. Alternatively, a player might have lost the game of rock paper scissors and in a panic, rushes to press the defend button first. But in their panic, the player presses the attack button instead. The player ends up dealing damage to themself.

  
## Under the hood
### The FSM
- Save player choices - Black	
- Compute winner (game logic) - Purple
- Reset registers - Grey
- Main timer count down- Blue
- Wait 2 seconds before new round - Green
![image](https://github.com/50002-computation-structures/1d-project-group-21/assets/89905861/cf710758-3e3b-4312-907d-f85bdd414074)

### Datapath
1. 0x0: Hit points of P1
2. 0x1: Hit points of P2
3. 0x2: Time Left
4. 0x3: Selection of P1 (scissor, paper or stone)
5. 0x4: Selection of P2 (scissor, paper or stone)
6. 0x5: Outcome of the whole game (1 -> P1 wins, 2 -> P2 wins)
7. 0x6: Attack/Defend state
8. 0x7 to 0xE: Temp Regs 
9. 0xF: Temp Reg for Comparison

![image](https://github.com/50002-computation-structures/1d-project-group-21/assets/89905861/00579036-8700-4498-96de-1438619a2aef)



## Prototype hardaware details
### Input
- 9 Buttons:
Player 1: rock, paper, scissors buttons (3)
Player 2: rock, paper, scissors buttons (3)
“Shared” attack and defend buttons (2)
- Reset button (1)  -- once pressed, will reset both players health to 3 and reset all registers.
### Output
- 12 Leds
- “Screen”: 6 Leds indicating scissors, paper stone for each player after the timer runs out. 
In other words, after timer runs out, each player’s choices are revealed to both players
- Health: 6 leds indicating the health of the players.

- 1 7-Seg
Timer: 1 x 7-seg Led indicating the time left in the game.









# FPGA-Project
