# Game settings
## Player Variables
Most of these are set in the **StoryInit** and **storyMenu** passages.

### Head of Household
The "head of household" status affects the player's ability to make decisions and their experience playing the game. It is primarily determined by age, not gender. Players who are not the head of their household may not be able to make certain decisions or need to convince family members to take certain actions.

* 0 = not head of household
* 1 = head of household

### Plague Infection
The $plagueInfection variable checks whether you are currently healthy, infected, or previously infected and recovered. It runs at the beginning of each monthly passage and quarantine passages to check your status.
* 0 = not infected
* 1 = currently infected
* 2 = infected and recovered 

### Reputation
All players begin with a reputation score of 6, which can be increased/decreased based on actions.

$reputation:
* 9+: _a worthy soul_
* 6-8: _Of good credit and quality_
* 3-5: _bad credit is better than none_
* 3 or lower: _a worthless and base rogue_

## Household Character Generator Settings
_These settings are found in the passage "char-gen-widgets" and called into the "bio" widget._

These settings determine the number, age, and status of members of your household, including children, partners, and siblings. They are dependent on the age, marital status, and socioeconomic status of the main character.

Players may also have **extended family members** who do not reside in their household, but about whom they receive regular updates.

* Characters who are **unmarried** and **young adult** or younger may reside in a household with parents and other siblings.
* **Married** or **widowed** young adult and middle-aged adult characters may reside in a household with their children. If the character is older than middle-aged, their children are treated as "extended" (i.e., not residing in the same household).

### Partners
_<<widget "addPartnerNPC">>_

The age and gender of the main character's partner is determined by their marital status, gender, and age.
* **Young adults** can be partnered with young or middle-aged adults.
* **Middle-aged adults** can be partnered with young or middle-aged adults.
* **Elderly adults** may be partnered with middle-aged or elderly adults.

### Children
_<<widget "addChildNPC">>_ 
The main character's number of children is based on their age, marital status, and socioeconomic status.

Childrens' age ranges are determined based on the main character's age.
* **Young adults** can only have infants or young children.
* **Middle-aged adults** can have adolescent children, young adults, or middle-age adult children.
* **Elderly adults** can have young adult or middle-aged children.

Actual numerical ages are randomly determined, within a defined range for each bracket.
* **Infant:**
* **Child:**
* **Adolescent:** 
* **Young Adult:**
* **Middle-aged Adult:**
* **Elderly Adult:**

### Parents
_<<widget "addParentNPC">>_
The age and likelihood of having living parents is determined based on the main character's age. Younger characters are more likely to have both living parents. For characters **middle-aged** or younger, there is a slightly higher chance of only having a living mother.

### Siblings
_<<widget "addSiblingsNPC">>_

Age and number of siblings is determined based on main character age. If the main character is an unmarried **young adult** or younger, siblings may live in their household (added to the total # of household members), or they may 

# Game Decisions
## FLEEING THE CITY
Choices to flee the city vary based on socioeconomic class, family size, place of origin, and whether you are the head of household.

* Players who are head of household (i.e., not a child) will have the choice to remain in the city with their household, remain in the city alone and send away their family, or flee with their household.
* * **Servants** have an additional choice: they can follow their master or break from their master's choice.

**Choices**: #1-3 only apply to servants.
* 1: Stay with your master
* 2: Flee with your master (no reputation impact, no income hit)
* 3: Flee <b>without</b> your master: you abandon your duties and take a reputation/income hit.
* 4: Stay with your household
* 5: Stay but send your household away
* 6: Flee with your household
* 7: You attempt to flee but are prevented from doing so, due to lack of funds.

The "Family Status" sidebar reflects where your family is, depending on whether you choose to send them away. _Currently, family member status remains unchanged while they are "fled", but future versions may allow them to become infected or fall ill for other reasons_.

## PESTHOUSE

## FIRE

## REPUTATION

# Documentation by Passage
## STORYINIT
This passage sets up most of the game variables like character names, prounouns, and plague remedies.

**Character variables**:
* $article, $heshe, $hishers set the pronouns and articles used for family members
* $impressed: 0 = not impressed in the Navy; 1 = impressed in the Navy
* $disability: 0 = not disabled; 1 = disabled
* $reputation: baseline reputation is 6 and can be increased/decreased by character actions.
* $quarantine: 0 = not actively in quarantine; 1 = quarantined. This variable is checked in the header passage to determine if a player has already spent time in quarantine, and helps prevent putting players in an endless loop of quarantine if other family members fall ill.
* $fNames, $mNames, $nbNames: based on frequency of names occuring in records. Players who select non-binary characters have a option to choose from a set of names.
* $childRole: **currently not used**; intended to be used to define the relationship of the character to the head-of-household, if playing as a child/adolescent. Currently, this variable is being set directly in passages (e.g., "As the daughter/son/child of a merchant...") 

**Plague remedies:** These variables set which treatments are available for purchase through the apothecary.
* $fumes: a range of fumigant options that may work better than most other treatments, as they can kill fleas
* $remedies: only the blistering plaster remedy has real effect on 

## storyMenu

## PassageHeader
* Checks if a player has purchased fumigants, thus reducing their usual chances of plague infection by 50%.
* Displays the current month of the game _or_ weeks in quarantine.
* Determines when players can see the Apothecary passage
* Creates an _infectedFamily array if it hasn't previously been triggered

## preventatives-treatments
Includes widgets that set up the preventative efforts and remedies players can take to stave off plague infection, treatment options if they or a family member fall ill.

<<widget "fumigant-check">> checks if the player has any type of fumigant on hand (which is depleted month by month). If there are fumigants in the player's inventory, it reduces their usual plague infection chances by 50%.

