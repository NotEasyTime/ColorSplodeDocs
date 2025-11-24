# ColorSplodeDocs
An overview of the ColorSplode game architecture 

# File Structure
LICENSE  
README.md  
actor.js  
button.js  
font/  
images/  
index.html  
items.js  
levelsys.js  
libraries/  
sketch.js  
sounds/  
style.css  

# Important classes per file

## actor.js
This file holds the actor class which is the base for both the Bucket class and obsticle classes like the Cat and RogueBucket. 

### Base Class: Actor
Key features
- Position, size, sprite
- Circular collision radius (r)
- Randomized roaming movement with edge-bounce
- Center getters (cx, cy)
- Basic drawing logic

### Bucket
The primary game piece that the player sorts.
### Logic Features
- Autonomous roaming with collision avoidance
- Full collision system:
  - Actor–Actor circle bounce
  - Actor–Zone wall constraints
- Freeze mechanic with time-based unfreeze
- Life timer (lifeMs) with wobble animation as death approaches
- Paint trail drawing
- Particle explosions (splode())
- Player Interaction
- Can be grabbed / dragged
- When entering a matching color zone → becomes sorted
- Can be freed by enemies (state preserved)

### Cat
A roaming hunter enemy that attacks buckets.
### Behavior
- Wanders until it finds a target
- Moves toward the nearest unsorted, alive bucket
- Performs a “swipe” attack within range:
- Damages bucket by reducing its lifetime
- Triggers particle burst

### RogueBucket
An enemy that steals sorted buckets and releases them back into play.
1. Roams for a short duration.
2. Selects a color from existing sorted buckets.
3. Tracks all sorted buckets of that color.
4. Moves toward closest one.
5. When in range → frees it (resets state).
6. Repeats or pauses when no targets exist.


## sketch.js
This file is where the entry point to the game is, handling game state and the UI

## items.js
This file is where the item functions and effects are defined.

## levelsys.js
This file holds the level class as well as the classes that level stores like vents and zones
