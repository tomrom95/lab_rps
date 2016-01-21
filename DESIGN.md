CompSci 308 : RPS Design
===================

> This is the link to the Lab Description: 
[Lab - RPS](http://www.cs.duke.edu/courses/compsci308/spring16/classwork/02_design_rps/index.php)

Initial Design
=======

###Weapon

* General class for each weapon, doesn’t store what it beats/what beats it

###WeaponSet

* Stores all of the weapons the Player can use

###Rules

* Rule set decides what beats what- game gives it 2 weapons and it decides on the winner based on its info

###Player

* Creates player, attaches weapon selected, and maintains win/loss for player

###Game

* Runs game after creating x players, uploading data file for game, and populating the weapon set

CRC Design
=======

###Game
**Responsibilities**

* Knows Players in match
* Plays game between players
* Initiates new rounds

**Collaborators**

* Players
* Rules

###Rules
**Responsibilities**

* Knows win/loss rules (store in directed graph)
* Add rule
* Change rule
* Delete rule
* Return winner between weapons

**Collaborators**

* Weapons

###Player
**Responsibilities**
* Knows score
* Updates scores
* Selects weapon from weapon set
* Resets score

**Collaborators**

* WeaponSet

###WeaponSet
**Responsibilities**

* Knows all weapons
* Updates enum based on input data file
* Add weapon
* Delete Weapon

**Collaborators**

* Weapon

###Weapon
**Responsibilities**

* Knows display attributes


**Collaborators**

* WeaponSet
* Rules

You can add images as well:

![This is cool, too bad you can't see it](crc-example.png "Our CRC cards")


Use Cases
=======

* A new game is started with two players, their scores are reset to 0.
```java
// In Game class
List<Players> newPlayers = createPlayers(2);
// Assuming Rule rules, WeaponSet weaponset
startGame(rules, weaponset, newPlayers);
```
* A player chooses his RPS "weapon" with which he wants to play for this round.

```java
// In Game class
// Assuming Player player
Weapon w = player.chooseWeapon();

```
* Given two players' choices, one player wins the round, and their scores are updated.

```java
// In Game class
int getWinner(Player p1, Player p2){
    //compare weapons
    //1 - p1 weapon wins, 0 - tie, -1 p2 weapon wins
}

```
* A new choice is added to an existing game and its relationship to all the other choices is updated.
```java
// In Game class
Weapon newChoice = new Weapon(name);
weaponset.addWeapon(newChoice);
// Assume choices it beats is in List<Weapon> winners -> from input file
// Assume choices it loses to is in List<Weapon> losers -> from input file
for(Weapon w: winners){
    rules.addRule(newChoice, w); // Winning choice comes first
}
for(Weapon w: losers){
    rules.addRule(w, newChoice); 
}
```
* A new game is added to the system, with its own relationships for its all its "weapons".
```java
// In RPS class
// Assuming Game g
game.resetGame()
// Assuming Rules rules
game.updateRules(rules)
```
