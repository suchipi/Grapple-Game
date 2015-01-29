# Grapple Game Development Document

### Goal: Create a Multiplayer Arena Shooter that uses a Grapple Hook

#### Development Goals
* Create a grapple hook SWEP that has viewmodel animations
  * Use viewmodel arms with articulated fingers
  * If possible, use cl_hands
* Create in-game tools that facilitate quick turnaround of map prototyping, demoing, exporting, and finalization
  * Final game should load the same format that is used by these tools
  * Will behave similar to advanced duplicator
  * Should be able to export a static mesh of the area created
* Create a new gamemode from as close to a bare base as possible
* Attempt to capture the pacing, tactility, and depth of Super Smash Brothers Project M in a 3D, first-person environment
  * Encourage planned execution of actions that require an initial charge or have a cooldown afterwards
  * Create advanced actions that build on simple actions and require an intentional choice to learn by the player (like rocket jumping)
  * Make the initial experience easy to pick up, but give hidden depth for the "pros" to uncover
    * Encourage players to try new tactics and methods without ever telling them to. They should believe it was their own choice, even if we subconsciously told them to
  * Make each action reliable and reproducible so that players can predict enemy movements and make a guess into the future
  * Duels should be (able to be) fast-paced and require split-second thinking
  * Find a way to balance space between players
    * Getting closer should be a risk/reward
      * But be careful about the weird melee fights where no one can see
    * Being farther should be more "safe" but give you less power over the situation
    * Craft mechanics so that players don't find themselves in the "awkward zone", where you're neither close nor far and if I keep clicking on you you'll die
  * Experiment with different types of health systems that gives duels length but don't make them pointless
* Focus on game mechanics that employ the change in acceleration to maximize the fun in movement
  * Velocity vectors changing direction abruptly and rapidly are a great way to achieve this
  * If you are alone in a server you should still be able to have fun trying different "parkour" techniques
  * Employ the following techniques:
    * Grappling
    * Wall jumping
    * "Grapple running" (using the grapple to accelerate your ground running speed)
    * Chain grappling (players grappling and following other players)
    * "Gun bursting" (overcharging your gun to create an explosion in front of you, which is basically a melee attack)
* Encourage teamplay, but let the system shine in one-on-one encounters
  * The gameplay should have a flow and certain parts of the game should require a push as a team effort to get through
  * In team-based gamemodes, gameplay should be mostly one-on-one encounters as you are moving towards the current team objective, then team-based once you get there
    * In a way this is two different types of metagames
  * Make the transition between being individual and being part of a team feel natural and chosen by the player while intentionally orchestrating it behind the scenes
  * Don't rely on a behind-the-scenes Director (ala L4D) to manipulate numbers; players should be able to "count frames" and rely on numbers
* Give players the ability to customize their gameplay experience
  * Allow loading in external assets (3D or 2D) as "keychains" that can be attached to the gun
  * Give players a hue slider for their gun's glowing parts and bullet effects
* Only have one loading screen upon join, and then never again
  * All map changes will just be arrangements of entities, and therefore can be done very quickly
  * Loading screens are a necessary evil due to computational limitations, and should be minimized and avoided rather than accepted and even glorified
  * Load as many things asynchronously as possible; attempt to use background threads/workers if the engine supports this
  * Avoid loading anything during the midst of gameplay as this can affect framerate
    * This includes sounds! Precache all sounds that will ever be used in the gamemode when the player first joins. There is nothing more annoying than having gameplay be blocked by an explosion sound loading and then coming back to find yourself dead because you were unable to dodge it
* Play off of the map's mood and structure to direct players into certain encounters and behaviours
  * Again, never tell them to do anything, be discrete and furtive while still directing with a purpose

#### Art/Asset Creation Goals
* Create assets that cohesively give the "feel" of a gritty-but-colorful 80s NeoTokyo (ala Akira, Blade Runner)
  * Frequently juxtapose bright color and simple shapes against more monochrome, complex shapes
    * Bright colors and simple shapes are the important gameplay elements the player should be aware of (explosions, bullets, particles)
      * But feel free to highlight map details and create player direction with color, too
    * Monochrome complex shapes are the map behind everything
      * Don't go too monochrome, though. It should feel rewarding to "stop and smell the roses". We just don't want anything to be too distracting, either
  * Make the in-game world feel unique and intentionally constructed
  * Use sound effects as well as visual pieces to make the world feel "whole"
    * Create small prop assets
    * Create dynamic assets that change state as gameplay progresses (cars exploding)
    * Attempt to replace every boxed HL2 explosion and metal hit sound effect with something else
    * Create skyboxes for each map
    * Consider the weather in each map
* Create at least one map that has a distinct mood and feel
  * Use color overlays, weather, and atmospheric effects to give a mood to an area
  * Design map to encourage the most fun types of movement
    * Encourage grappling into a wall and immediately walljumping off of it, then going forward into another grapple
    * Give maps a great sense of vertical space
* Create a grapple gun weapon whose appearance encourages the player to improvise and try new things
* Create player animations that make the state of the player obvious to onlookers, and, where necessary, the player themself
  * Wall-jumping
  * Sense of acceleration
    * Legs moving behind the player as they grapple forward
    * Per-bone ragdolling techniques might be applicable here (they would be visual only)
  * Particle effects describe the size, shape, and frame duration of hurtboxes effectively
    * Players should rarely if ever be surprised that they were in range of an attack
* Prototype a block mesh map that encourages the kinds of gameplay we want, then build a rich world by placing assets on top of and around it


#### Personal Goals

###### Stephen

* Learn more about the Source Engine asset creation pipeline and where it succeeds and fails
  * Experiment using nontraditional maps built from entities
  * Learn how to compile flexes/shapekeys into a model
  * Use the new dmx model format instead of smd, if tools support it
* Become more used to adapting to particular APIs implemented in a familiar language
* Explore using the undocumented incredibly fast but unreliable networking functions in GMod to transfer game state quickly, frequently, and rapidly
* Explore using movetypes to keep entities predicted clientside as much as possible
* Craft a cohesive game that feels intentionally designed and encourages player learning as a rewarding experience
  * Each match should be fun because you had personal gains and also enjoyed social interaction

###### Chris

* Please fill in your personal goals and add any other more big-picture goals as you see fit


##### Works to remember and draw from

* Portal: Encourages the player to teach themselves; every learned action is a personal triumph instead of a forced adherence to a game mechanic
* Smash Brothers: Creates a great framework for paced duels that can have varying levels of depth given a relatively simple pallet of inputs
* Quake-likes: Encourages use of acceleration and motion continued momentum as a gameplay mechanic. The progenitor of Rocket Jumping.
* TF2 Mannpower Mode: The grapple hook in this game forces players to wait as it shoots out, which encourages grappling while moving along as a natural progression. It also creates a fantastic change in acceleration.
* Final Fantasy XIV: MMOs are really boring but this game managed to make you feel accomplished when you learned, because every spell you learned wasn't about numbers as much as "how can I fit this into my flow". By the time you reached level 50 you really "felt" like a Mage/etc.

