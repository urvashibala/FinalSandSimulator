# FinalSandSimulator
A physics-based interactive (cellular-automata + OOPS) particle system!

## SETUP
Run the code for the given files in p5.js web editor, or directly visit these links:
1. **SandSim Stationary** https://editor.p5js.org/urvashicodes/sketches/oXPAP6CrC
2. **SandSim Rotatable** https://editor.p5js.org/urvashicodes/sketches/h2R2wqaoW

## ABOUT THIS CODE: THE CHALLENGE
1. Sand usually slows down as more particles are created, because of the need for more collision checks and object-handling. At thousands of particles, the system inevitaly slows down. Challenging myself to optimise the program so it draws fast even with many particles.
2. P5.js isn't build for 3D. It doesn't have any inbuilt libraries for matrix multiplication, projection, rayshading etc. Challenge myself to implement the system on this, instead of something like three.js which is optimised for 3D.
3. Using WEBGL instead of local compiling and running, because it's slower. If I get sand simulated very fast despite this, then that's an achievement in optimising.
4. Didn't let myself use hacks like deterministic shapes getting larger/smaller as sand piles and flows.
5. No use or reference of external libraries, and thus much lower-level! (Original implementation)

## NOVELTY
1. Builds on the idea of using cellular automata, but also uses particle-system OOPS for each cell of the grid. This **hybrid system** combines the **effiency** of a cellular automata and the **physical realism** of an object-oriented physics system.
2. Designed and implemented a **new** CA-rule-based **simulation system in 3D** (cellular automata generally used for 2D for sand)
3. Sand is **reactive to rotation** (SandSim_Rotate) of the sandbox: Each particle has a 3vec _velocity_ that accumulates gravity each frame – we’re literally adding the acceleration every time. When a particle falls, it first tries to move to the directly gravity-aligned cell, the information of which is drawn from the rotation of the wireframe sandbox. Upon collision, velocities are multiplied by factors that **mimics the physics energy loss in real granular materials**, so piles settle naturally rather than **bouncing** forever. (Bouncing doesn't exist in normal CA sims)

## OPTIMISING
1. **Optimised** from **O(n^3) to O(P)** for every operation _(creating new particle, checking collisions etc)_
2. **Double-buffered** cellular automata – we have an original grid and an update grid – this automatically means that I get faster rewrites and fewer errors than if we modified the grid directly.
3. **Timespan checks**: Only begins checking the grid for collisions and falling when the user creates sand and till that created sand hits the ground. This means that if you keep the program running, it won't inherently noticeably slow down, which used to be a problem with sand simulators.

## MORE FEATURES
1. User-controlled sand emission locations.
2. Removed inherent ordered appearance common in CA-based systems during piling (ensures compactness) using cubes rather than spheres
3. Sand-like colours: linearly interpolated between two commonly found shades of sand, and added a random constant to ensure variety in colouring.
