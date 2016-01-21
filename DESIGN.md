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
*Knows score
*Updates scores
*Selects weapon from weapon set
* Resets score


**Collaborators**
*WeaponSet

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

You can put blocks of code in here like this:
```java
    public int getTotal (Collection<Integer> data) {
        int total = 0;
        for (int d : data) {
            total += d;
        }
        return total;
    }
```