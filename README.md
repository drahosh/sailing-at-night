# sailing-at-night
Multiplayer (both synchronous and asynchronous) game about using spaceships for trade, combat, and avoiding detection.

This file contains my initial plan for the project.

Basic gameplay loop:
  In harbors, players can buy gacha-style (no real money involved) components and ships, and use various systems to enhance them and outfit one or more ships. 
  From a harbor, they can set out with their main ships to another connected harbor or other point on map with one ship. They also have options to send other ships to do repeating autonomous voyages elsewhere, trading or hunting other players or npcs along the way.

  While sailing, travel time depends on distance, weather and propulsion (sails are quiet, depend on space weather and distance from ports, don't use fuel. Engines use fuel, are independent from weather, more useful in combat, and are louder if used while travelling).
  Depending on travel time, a certain number of travel events occur. These pause travel if they take longer to resolve than another event can occur. Events can be self contained (spotting resources, accidents, maybe passenger plot conversations if we do those) or depend on other ships travelling the same route - Those can be live players, or async automated ships of other players, or npc ships if there are not enough players on this route. 
  Even when meeting another ship, they may not notice them - each ship has a chance to  detect the other depending on their detection rating and the others obscurity rating. After detection, they can decide what to do - greet (TODO think of what this means, maybe gaining reputation? or some quest content? boosting each others speed?), ignore, or attack. Chance to detect details about the other ship (like components used or cargo held) is also based on this chance.
  If one ship decides to attack, game goes to turn based mode, where ships can move closer or farther away, deal damage, or try to escape. They can also surrender. Ships can do multiple things at once in the same turn (like fire multiple weapons while also moving farther away and also boosting shields), however they can't exceed their energy capacity to do this. Losing ship can also surrender.

  To prevent griefing, ships and equipment are classified by level, and each region is limited to a level range. Within each level, ships and components still have randomized stats. The intended gameplay loop is for a player to stay in a region, build up their arsenal, randomly gaining components to improve their ship while competing against mostly better ships, until they eventually gain enough power to move to the next region. Detection mechanics, npc ships, quests and obscurity mechanics will be used to give a chance to players on lower end of power, either by preying on npc ships or trade-focused ships, or by making a quiet ship and hoping to trade while escaping detection.

  Ports each generate and consume resources, difference between stockpiled and desired resources determines price. High price differentials can incentivize npc trade ships (simulated), which can incentivize npc pirate ships that then deincentivize them. There is also a security rate determining npc faction warships or bounties offered to players. We do not simulate each ship voyage, we just calculate those two rates, use them to calculate diffusion of goods and chances of npc ships encountered by players when travelling that route.

Tech stack:
  Doing this project to refresh/learn and demonstrate marketable skills.
  Backend handmade in Java spring with database. Frontend AI assisted in javascript, probably react. Deployment in azure.

Other notes:
  - Using spaceships instead of real ships because sci-fi magic gives more leeway in ship upgrade system and in making decisions that would otherwise seem unrealistic ( considered using a fantasy ocean-world setting with magic, but space sci-fantasy seems more evocative, + i'd need to invent some very good day/night mechanic to justify the title)
  - Considered using godot for frontend, because i already know it and for easy deployment to web, pc, mobile... decided for js because it's a more marketable skill
  
